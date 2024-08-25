# Virtualização, Node e Docker

<iframe src="https://docs.google.com/presentation/d/11zkGbgXviWX-QLiQZ2FMzt8A2lNFPZLm/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

### Parte 1: Introdução à Virtualização

#### 1.1 O que é Virtualização?

- **Definição:** Virtualização é a criação de uma versão virtual de algo, como hardware, sistema operacional, armazenamento ou recursos de rede.
- **Tipos de Virtualização:**
  - **Virtualização de Servidor:** Uso de máquinas virtuais (VMs) para executar múltiplos sistemas operacionais em um único servidor físico.
  - **Virtualização de Desktop:** Fornece desktops virtuais para usuários finais.
  - **Virtualização de Rede:** Combina recursos de rede em um único recurso virtualizado.

#### 1.2 Benefícios da Virtualização

- **Eficiência de Recursos:** Melhor utilização do hardware.
- **Isolamento:** VMs são isoladas umas das outras, aumentando a segurança.
- **Facilidade de Gerenciamento:** Facilita o backup, recuperação e migração de sistemas.

#### 1.3 Ferramentas de Virtualização Popular

- **VMware:** Solução líder em virtualização de servidores.
- **VirtualBox:** Ferramenta de virtualização de código aberto.
- **Hyper-V:** Tecnologia de virtualização da Microsoft.

---

### Parte 2: Introdução ao Node.js

#### 2.1 O que é Node.js?

- **Definição:** Node.js é um ambiente de execução JavaScript server-side, construído sobre o motor V8 do Chrome.
- **Características:**
  - **Assíncrono e Baseado em Eventos:** Ideal para aplicações I/O intensivas.
  - **Ecossistema Rico:** Grande quantidade de pacotes disponíveis via npm.

#### 2.2 Instalação do Node.js

- **Windows, macOS e Linux:**
  - Acesse [nodejs.org](https://nodejs.org/) e baixe o instalador adequado.
  - Use gerenciadores de pacotes como `nvm` (Node Version Manager) para gerenciar versões.

#### 2.3 Criando uma Aplicação Simples

- **Hello World:**
<pre><code class="language-javascript">
// app.js
const http = require('http');

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello World\n');
});

server.listen(3000, '127.0.0.1', () => {
    console.log('Server running at http://127.0.0.1:3000/');
});
</code></pre>

- **Executar a aplicação:**
  ```
  node app.js
  ```

---

### Parte 3: Introdução ao Docker

#### 3.1 O que é Docker?

- **Definição:** Docker é uma plataforma para desenvolver, enviar e executar aplicações em contêineres.
- **Conceitos Principais:**
  - **Imagens:** Template de contêineres que contém tudo o que é necessário para executar uma aplicação.
  - **Contêineres:** Instâncias em execução de imagens Docker.
  - **Dockerfile:** Script que contém instruções para criar uma imagem Docker.

#### 3.2 Instalação do Docker

- **Windows, macOS e Linux:**
  - Acesse [docker.com](https://www.docker.com/) e siga as instruções de instalação para seu sistema operacional.

#### 3.3 Dockerizando uma Aplicação Node.js

- **Criar um Dockerfile:**
<pre><code class="language-docker">
  # Use a imagem oficial do Node.js
  FROM node:14

  # Defina o diretório de trabalho
  WORKDIR /usr/src/app

  # Copie o package.json e package-lock.json
  COPY package*.json ./

  # Instale as dependências
  RUN npm install

  # Copie o restante do código da aplicação
  COPY . .

  # Exponha a porta que a aplicação irá rodar
  EXPOSE 3000

  # Comando para rodar a aplicação
  CMD ["node", "app.js"]
</code></pre>

- **Construir a Imagem Docker:**
  ```bash
  docker build -t my-node-app .
  ```

- **Executar o Contêiner:**
  ```
  docker run -p 3000:3000 my-node-app
  ```

#### 3.4 Benefícios do Docker

- **Portabilidade:** Execute contêineres em qualquer lugar.
- **Isolamento:** Contêineres são isolados do sistema host e de outros contêineres.
- **Eficiência:** Contêineres compartilham o kernel do host, tornando-os leves.

# Agora vamos para uma aplicação com o Compose

Para adicionar um arquivo .env ao projeto, que armazena variáveis de ambiente sensíveis como credenciais de banco de dados, você pode criar um arquivo chamado .env na raiz do seu projeto. Este arquivo será usado pelo Docker Compose e pela aplicação Node.js para configurar variáveis de ambiente de forma segura.

Criaremos os dockerfile e um compose:

<pre><code class="language-yml">
    # Use a imagem oficial do Node.js
    FROM node:14

    # Defina o diretório de trabalho
    WORKDIR /usr/src/app

    # Instale o TypeScript globalmente
    RUN npm install -g typescript

    # Copie o package.json e package-lock.json
    COPY package*.json ./

    # Instale as dependências
    RUN npm install

    # Copie o restante do código da aplicação
    COPY . .

    # Compile o TypeScript
    RUN tsc

    # Exponha a porta que a aplicação irá rodar
    EXPOSE 3000

    # Comando para rodar a aplicação
    CMD ["node", "dist/app.js"]
</code></pre>

<pre><code class="language-yml">
    version: '3.8'

    services:
    app:
        build: .
        ports:
        - "3000:3000"
        depends_on:
        - db
        environment:
        - DATABASE_URL=postgresql://postgres:password@db:5432/mydatabase
        volumes:
        - .:/usr/src/app
        - /usr/src/app/node_modules

    db:
        image: postgres:13
        environment:
        POSTGRES_USER: postgres
        POSTGRES_PASSWORD: password
        POSTGRES_DB: mydatabase
        ports:
        - "5432:5432"
        volumes:
        - pgdata:/var/lib/postgresql/data

    volumes:
    pgdata:
</code></pre>

#### Agora um app.ts

<pre><code class="language-typescript">
    import { Client } from 'pg';

    const client = new Client({
    connectionString: process.env.DATABASE_URL,
    });

    client.connect()
    .then(() => console.log('Connected to PostgreSQL'))
    .catch(err => console.error('Connection error', err.stack));

    client.query('SELECT NOW()', (err, res) => {
    if (err) {
        console.error(err);
    } else {
        console.log('Server time:', res.rows[0]);
    }
    client.end();
    });
</code></pre>

e um package.json

<pre><code class="language-typescript">
    {
    "name": "node-typescript-docker",
    "version": "1.0.0",
    "main": "dist/app.js",
    "scripts": {
        "build": "tsc",
        "start": "node dist/app.js"
    },
    "dependencies": {
        "pg": "^8.7.1"
    },
    "devDependencies": {
        "typescript": "^4.4.4"
    }
    }
</code></pre>

#### Vamos conectar com o DBeaver!

Para acessar o banco de dados PostgreSQL com o DBeaver:

1. Abra o DBeaver e crie uma nova conexão.
2. Selecione PostgreSQL como o tipo de banco de dados.
3. Use as seguintes configurações:
   - **Host**: `localhost`
   - **Port**: `5432`
   - **Database**: `mydatabase`
   - **Username**: `postgres`
   - **Password**: `password`

### Executando o Ambiente

1. **Inicie o Docker Compose**: No terminal, execute o comando:
   ```
   docker-compose up --build
   ```