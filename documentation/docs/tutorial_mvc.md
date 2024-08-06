### 1. Configuração do Ambiente

1. **Instale o Node.js e npm**: Certifique-se de ter o Node.js e o npm instalados no seu sistema. Você pode baixá-los [aqui](https://nodejs.org/).

2. **Crie um novo projeto**: Abra o terminal e crie uma nova pasta para o seu projeto.
```bash
mkdir meu-projeto-mvc
cd meu-projeto-mvc
npm init -y
```

3. **Instale as dependências necessárias**:
```bash
npm install express typescript ts-node @types/node @types/express
```

4. **Configure o TypeScript**: Crie um arquivo `tsconfig.json` na raiz do projeto com o seguinte conteúdo:
```json
{
    "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "outDir": "./dist"
    },
    "include": ["src/**/*"],
    "exclude": ["node_modules"]
}
```

### 2. Estrutura do Projeto

Crie a seguinte estrutura de pastas e arquivos no seu projeto:

```
meu-projeto-mvc/
├── src/
│   ├── controllers/
│   │   └── userController.ts
│   ├── models/
│   │   └── userModel.ts
│   ├── routes/
│   │   └── userRoutes.ts
│   ├── views/
│   │   └── userView.ts
│   ├── app.ts
├── tsconfig.json
├── package.json
```

### 3. Implementação

#### `src/app.ts`

Este é o ponto de entrada do seu aplicativo.

```typescript
import express from 'express';
import userRoutes from './routes/userRoutes';

const app = express();
const port = 3000;

app.use(express.json());
app.use('/users', userRoutes);

app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
```

#### `src/models/userModel.ts`

Aqui você define a estrutura dos dados.

```typescript
export interface User {
  id: number;
  name: string;
  email: string;
}

export const users: User[] = [];
```

#### `src/controllers/userController.ts`

Aqui você implementa a lógica de negócios.

```typescript
import { Request, Response } from 'express';
import { users, User } from '../models/userModel';

export const getUsers = (req: Request, res: Response): void => {
  res.json(users);
};

export const createUser = (req: Request, res: Response): void => {
  const newUser: User = {
    id: users.length + 1,
    ...req.body
  };
  users.push(newUser);
  res.status(201).json(newUser);
};
```

#### `src/routes/userRoutes.ts`

Aqui você define as rotas do seu aplicativo.

```typescript
import { Router } from 'express';
import { getUsers, createUser } from '../controllers/userController';

const router = Router();

router.get('/', getUsers);
router.post('/', createUser);

export default router;
```

#### `src/views/userView.ts`

Neste exemplo simples, a camada de visualização pode ser omitida ou usada para formatar a saída de dados. Em um ambiente mais complexo, você pode usar templates.

### 4. Executando o Projeto

Para rodar seu projeto, adicione um script no `package.json`:

```json
"scripts": {
  "start": "ts-node src/app.ts"
}
```

Então, no terminal, execute:

```bash
npm start
```

### 5. Testando com o RestClient no VSCode

Para testar sua API, você pode usar a extensão [RestClient](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) no VSCode. Crie um arquivo `requests.http` na raiz do projeto com o seguinte conteúdo:

```text
### Get all users
GET http://localhost:3000/users
Content-Type: application/json

###

### Create a new user
POST http://localhost:3000/users
Content-Type: application/json

{
    "name": "John Doe",
    "email": "john.doe@example.com"
}
```

Para realizar os testes, basta abrir o arquivo `requests.http` no VSCode e clicar no botão "Send Request" que aparece acima de cada bloco de requisição.

### 6. Adicionando um .gitignore

Crie um arquivo `.gitignore` na raiz do projeto com o seguinte conteúdo para ignorar arquivos e pastas desnecessárias:

```gitignore
# Node modules
node_modules/

# TypeScript output
dist/

# Environment variables
.env

# Logs
logs/
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Editor directories and files
.vscode/
.idea/
.DS_Store
```