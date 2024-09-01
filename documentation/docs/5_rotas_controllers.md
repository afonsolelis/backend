# Rotas e Controllers

A Partir deste momento em diante é 100% code-along, então estejam no seu replit para testarmos.

# Autoestudos

| Recurso | Descrição | Link |
|---------|-----------|------|
| Criando WebAPI | Tutorial sobre como criar uma WebAPI com Node.js, Express e TypeScript | [Link](https://www.luiztools.com.br/post/como-criar-uma-webapi-com-node-js-express-e-typescript/) |
| API Rest, Node e Typescript | Vídeo sobre criação de controller, tipagem de dados e melhorias no ESLINT | [Link](https://www.youtube.com/watch?v=xyjvNhoyVkI) |
| Introdução ao TS | Artigo introdutório sobre TypeScript | [Link](https://www.devmedia.com.br/introducao-ao-typescript/36729) |
| Configurando rotas no NodeJS com Typescript | Tutorial sobre configuração de rotas em NodeJS com TypeScript | [Link](https://dev.to/aryclenio/configurando-rotas-no-nodejs-com-typescript-la1) |
| Criando Controllers | Fórum de discussão sobre criação de controllers | [Link](https://cursos.alura.com.br/forum/topico-criar-controllers-87200) |
| Routes, Controllers, Express, NodeJS | Vídeo sobre separação de rotas e controllers em API Rest Express | [Link](https://www.youtube.com/watch?v=vNo3iyfAhMA) |
| Curso NodeJS com Typescript | Vídeo sobre criação de controller de usuários | [Link](https://www.youtube.com/watch?v=XBhOI2jrtDU) |

---

Vamos atualizar o tutorial para incluir uma rota adicional no servidor para adicionar dados ao banco de dados, além de fornecer exemplos de comandos `curl` para testar as funcionalidades do backend.

### Atualização do Projeto com Rotas Adicionais e Testes com `curl`

#### 1. **Configuração Básica do Projeto**

Conforme descrito anteriormente, certifique-se de que você já tenha configurado o seu projeto TypeScript no Replit com as dependências necessárias:

```bash
npm install pg express
npm install --save-dev typescript @types/node @types/pg @types/express ts-node
```

Crie o `tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "rootDir": "./src",
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

#### 2. **Atualizar o Script de Conexão ao Banco de Dados**

Certifique-se de que o arquivo `src/database.ts` contenha a configuração correta com SSL:

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

#### 3. **Script de Migração para Criar Tabela**

Verifique se o arquivo `src/migrations/migrations.ts` está conforme abaixo para criar a tabela `users`:

```typescript
import pool from '../database';

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

Execute o script de migração para garantir que a tabela seja criada:

```bash
npx ts-node src/migrations/migrations.ts
```

#### 4. **Adicionar Rotas no Servidor**

Atualize o arquivo `src/server.ts` para incluir rotas de obtenção de usuários e de adição de novos usuários:

```typescript
import express from 'express';
import pool from './database';

const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

// Rota para obter todos os usuários
app.get('/users', async (req, res) => {
  try {
    const { rows } = await pool.query('SELECT * FROM users');
    res.status(200).json(rows);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: 'Erro ao buscar usuários' });
  }
});

// Rota para adicionar um novo usuário
app.post('/users', async (req, res) => {
  const { name, email } = req.body;
  try {
    const queryText = 'INSERT INTO users(name, email) VALUES($1, $2) RETURNING *';
    const { rows } = await pool.query(queryText, [name, email]);
    res.status(201).json(rows[0]);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: 'Erro ao adicionar usuário' });
  }
});

app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

#### 5. **Executar o Servidor**

Execute o servidor:

```bash
npx ts-node src/server.ts
```

#### 6. **Testar Rotas com `curl`**

Use os comandos `curl` abaixo para testar as rotas do backend.

- **Testar a Rota `GET /users`**:

Execute este comando para buscar todos os usuários:

```bash
curl -X GET http://localhost:3000/users
```

Esse comando deve retornar uma lista de usuários armazenados no banco de dados.

- **Testar a Rota `POST /users`**:

Execute este comando para adicionar um novo usuário:

```bash
curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"name": "João Silva", "email": "joao.silva@example.com"}'
```

Esse comando deve adicionar um novo usuário ao banco de dados e retornar os dados do usuário recém-criado.

### Desafio

1. Agora entre no DBeaver, faça a conexão e veja pelo dbeaver os dados inseridos.
2. Faça o git commit e envie para o seu projeto no github.