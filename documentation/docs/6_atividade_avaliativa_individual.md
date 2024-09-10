# Vamos Expandir as Rotas e Controllers!

## **Modularizando um Projeto Node.js com Express e TypeScript**

Nesta aula, vamos modularizar o nosso projeto para separá-lo em rotas, controllers e a configuração do banco de dados, proporcionando uma organização mais clara e facilitando a manutenção.

### **Estrutura do Projeto**

1. Vamos criar três novas pastas:
    - `routes`: para definir as rotas da API.
    - `controllers`: para a lógica de cada rota.
    - `config`: para a configuração do banco de dados.

2. Reorganizaremos o código do servidor, movendo as rotas, controllers e a configuração do banco de dados para arquivos separados.

### **Estrutura Final do Projeto**

```
src/
│
├── config/
│   └── database.ts
│
├── controllers/
│   └── userController.ts
│
├── routes/
│   └── userRoutes.ts
│
├── migrations/
│   └── migrations.ts
│
├── server.ts
```

### **Passos para Modularizar o Código**

#### 1. **Configuração do Banco de Dados em `config/database.ts`**

Vamos mover a configuração do banco de dados para a pasta `config`:

```typescript
import { Pool } from 'pg';

// Substitua pela sua string de conexão do Render.com
const connectionString = 'sua_string_de_conexao_do_render_aqui';

const pool = new Pool({
  connectionString,
  ssl: {
    rejectUnauthorized: false, // Permite conexões SSL não autorizadas
  }
});

export default pool;
```

#### 2. **Controllers em `controllers/userController.ts`**

Agora, a lógica das rotas será movida para o controller. Este arquivo lidará com as requisições e interações com o banco de dados:

```typescript
import { Request, Response } from 'express';
import pool from '../config/database';

// Função para obter todos os usuários
export const getUsers = async (req: Request, res: Response) => {
  try {
    const { rows } = await pool.query('SELECT * FROM users');
    res.status(200).json(rows);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: 'Erro ao buscar usuários' });
  }
};

// Função para adicionar um novo usuário
export const addUser = async (req: Request, res: Response) => {
  const { name, email } = req.body;
  try {
    const queryText = 'INSERT INTO users(name, email) VALUES($1, $2) RETURNING *';
    const { rows } = await pool.query(queryText, [name, email]);
    res.status(201).json(rows[0]);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: 'Erro ao adicionar usuário' });
  }
};
```

#### 3. **Rotas em `routes/userRoutes.ts`**

As rotas serão movidas para a pasta `routes`. Aqui, simplesmente vincularemos as rotas com seus respectivos controllers:

```typescript
import { Router } from 'express';
import { getUsers, addUser } from '../controllers/userController';

const router = Router();

router.get('/users', getUsers);
router.post('/users', addUser);

export default router;
```

#### 4. **Atualização do Servidor em `src/server.ts`**

Agora vamos atualizar o arquivo do servidor para utilizar as novas rotas:

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

#### 5. **Script de Migração para Criar Tabela em `migrations/migrations.ts`**

Aqui não haverá mudança. Certifique-se de executar a migração corretamente:

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

#### 6. **Executar o Servidor**

Agora, vamos executar o servidor com o comando:

```bash
npx ts-node src/server.ts
```

#### 7. **Testar Rotas com `curl`**

Use os comandos `curl` abaixo para testar as rotas.

- **Testar a Rota `GET /users`**:

```bash
curl -X GET http://localhost:3000/users
```

- **Testar a Rota `POST /users`**:

```bash
curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"name": "João Silva", "email": "joao.silva@example.com"}'
```

# Agora é com você, leia o tutorial e faça a aplicação modularizada em camadas.