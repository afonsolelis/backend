# Queries SQLs Avançadas em Banco de Dados (Padrão Repository)

Vamos expandir o conteúdo da aula anterior, adicionando o uso de **models** e **repositories** para uma maior separação de responsabilidades, seguindo boas práticas de design.

## **Modularizando com Models e Repositories**

Agora, vamos incluir o padrão **repository** para lidar com a lógica de acesso ao banco de dados, enquanto os **models** representarão os dados que manipulamos.

### **Nova Estrutura do Projeto**

1. Vamos adicionar duas novas pastas:
    - `models`: para definir os esquemas de dados.
    - `repositories`: para manipulação dos dados no banco.

2. A estrutura final do projeto ficará assim:

```
src/
│
├── config/
│   └── database.ts
│
├── controllers/
│   └── userController.ts
│
├── models/
│   └── userModel.ts
│
├── repositories/
│   └── userRepository.ts
│
├── routes/
│   └── userRoutes.ts
│
├── migrations/
│   └── migrations.ts
│
├── server.ts
```

### **Passos para Implementação de Models e Repositories**

#### 1. **Definindo o Model em `models/userModel.ts`**

O **model** vai representar a estrutura dos nossos dados. Vamos criar um modelo simples para o usuário:

```typescript
export interface User {
  id: number;
  name: string;
  email: string;
}
```

#### 2. **Implementando o Repositório em `repositories/userRepository.ts`**

O **repository** vai concentrar a lógica de interação com o banco de dados, isolando a camada de acesso ao banco do restante da aplicação:

```typescript
import { Pool } from 'pg';
import pool from '../config/database';
import { User } from '../models/userModel';

export class UserRepository {
  private pool: Pool;

  constructor() {
    this.pool = pool;
  }

  // Método para buscar todos os usuários
  async getAllUsers(): Promise<User[]> {
    const { rows } = await this.pool.query('SELECT * FROM users');
    return rows;
  }

  // Método para adicionar um novo usuário
  async addUser(name: string, email: string): Promise<User> {
    const queryText = 'INSERT INTO users(name, email) VALUES($1, $2) RETURNING *';
    const { rows } = await this.pool.query(queryText, [name, email]);
    return rows[0];
  }
}
```

#### 3. **Atualizando o Controller em `controllers/userController.ts`**

Agora, o controller utilizará o **UserRepository** para manipular os dados:

```typescript
import { Request, Response } from 'express';
import { UserRepository } from '../repositories/userRepository';

const userRepository = new UserRepository();

export const getUsers = async (req: Request, res: Response) => {
  try {
    const users = await userRepository.getAllUsers();
    res.status(200).json(users);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: 'Erro ao buscar usuários' });
  }
};

export const addUser = async (req: Request, res: Response) => {
  const { name, email } = req.body;
  try {
    const user = await userRepository.addUser(name, email);
    res.status(201).json(user);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: 'Erro ao adicionar usuário' });
  }
};
```

#### 4. **Mantendo as Rotas em `routes/userRoutes.ts`**

As rotas permanecem simples, sem mudanças:

```typescript
import { Router } from 'express';
import { getUsers, addUser } from '../controllers/userController';

const router = Router();

router.get('/users', getUsers);
router.post('/users', addUser);

export default router;
```

#### 5. **Servidor e Migrations**

Nenhuma alteração no servidor ou nas migrações, mas aqui estão os arquivos para referência:

- **Servidor**: `src/server.ts`
  
```typescript
import express from 'express';
import userRoutes from './routes/userRoutes';

const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

// Utilizando as rotas de usuários
app.use(userRoutes);

app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

- **Migrações**: `migrations/migrations.ts`

```typescript
import pool from '../config/database';

const createUsersTable = async () => {
  const client = await pool.connect();
  try {
    const queryText = `
      CREATE TABLE IF NOT EXISTS users (
        id SERIAL PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        email VARCHAR(100) UNIQUE NOT NULL
      );
    `;
    await client.query(queryText);
    console.log('Tabela "users" criada com sucesso!');
  } catch (err) {
    console.error('Erro ao criar tabela:', err);
  } finally {
    client.release();
  }
};

createUsersTable().then(() => process.exit(0));
```

#### 6. **Testar o Projeto**

Para testar o projeto modularizado com **models** e **repositories**, utilize os mesmos comandos `curl` da aula anterior:

- **GET /users**:

```bash
curl -X GET http://localhost:3000/users
```

- **POST /users**:

```bash
curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"name": "Maria", "email": "maria@example.com"}'
```

Com isso, seu projeto estará organizado em camadas, facilitando a manutenção, expansão e reutilização dos componentes!

Agora é sua vez de implementar o padrão com **models** e **repositories** no seu projeto.