  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css" rel="stylesheet">
  <!-- jQuery -->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <!-- Font Awesome -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" rel="stylesheet">

  <style>
    a {
      color: inherit;
      text-decoration: none;
    }
    .btn a {
      color: inherit;
      text-decoration: none;
    }
    .directory-structure {
            background-color: #fff;
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    .directory {
        margin-left: 20px;
    }
    .file {
        color: #555;
    }
  </style>

<h1>Comunidade Discord</h1>
<a href="https://discord.gg/C8qXnBATgG" class="btn btn-info" style="color: white; font-weight: bold;" target="blank_">💻 Discord</a>

<div class="container my-1">
    <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQp88zM4qBed7UudJY9xW56ADiDGOrabMz1dT_dh28b0G_nUwybzxDRXpTWNiq4o8MncU8FoSdyI3C3/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>

<div class="container my-1">
    <p>Salas: Terças no Lab4 Principal, Quartas Lab3 Centro</p>
</div>


<h1>Revisão de Conceitos Bases</h1>
<section class="container my-1">
    <div class="row">
        <div class="col-12 text-center">
            <h2>Protocolo HTTP e Comunicação Web</h2>
            <p>O HyperText Transfer Protocol (HTTP) é a espinha dorsal da World Wide Web. Ele define como as mensagens são formatadas e transmitidas, e como servidores e navegadores respondem a diferentes comandos. O HTTP usa um modelo cliente-servidor, onde o navegador é o cliente e a aplicação no servidor web é o servidor.</p>
        </div>
    </div>

    <div class="row mt-4">
        <div class="col-12">
            <img src="https://res.cloudinary.com/dyhjjms8y/image/upload/v1717986853/Captura_de_tela_2024-06-10_023128_kwkkzh.png" alt="Funcionamento do HTTP" class="img-fluid w-100">
            <p class="mt-2 text-center">O diagrama acima ilustra o processo de requisição e resposta entre cliente e servidor, fundamental para o funcionamento do HTTP.</p>
        </div>
    </div>

    <div class="row mt-4">
        <div class="col-12">
            <img src="https://res.cloudinary.com/dyhjjms8y/image/upload/v1717986853/Captura_de_tela_2024-06-10_023237_mkvsaj.png" alt="Verbos, URLs e URIs" class="img-fluid w-100">
            <p class="mt-2 text-center">Verbos HTTP (GET, POST, PUT, DELETE, etc.), URLs e URIs são elementos cruciais para especificar ações e recursos na comunicação web.</p>
        </div>
    </div>

    <div class="row mt-4">
        <div class="col-12">
            <img src="https://res.cloudinary.com/dyhjjms8y/image/upload/v1717986853/Captura_de_tela_2024-06-10_023249_bjkpyw.png" alt="Arquitetura MVC" class="img-fluid w-100">
            <p class="mt-2 text-center">A arquitetura MVC (Model-View-Controller) é frequentemente usada em aplicações web para organizar a lógica, apresentação e interação com o usuário.</p>
        </div>
    </div>

    <div class="row mt-4">
        <div class="col-6">
            <img src="https://res.cloudinary.com/dyhjjms8y/image/upload/v1717986853/Captura_de_tela_2024-06-10_023225_sgoflp.png" alt="Método GET" class="img-fluid w-100">
            <p class="mt-2 text-center">O método GET é usado para solicitar dados do servidor.</p>
        </div>
        <div class="col-6">
            <img src="https://res.cloudinary.com/dyhjjms8y/image/upload/v1717986853/Captura_de_tela_2024-06-10_023219_pwmfrl.png" alt="Método POST" class="img-fluid w-100">
            <p class="mt-2 text-center">O método POST é usado para enviar dados ao servidor para processamento.</p>
        </div>
    </div>

    <div class="row mt-4">
        <div class="col-12 text-center">
            <p>Outros protocolos importantes na web incluem HTTPS (HTTP seguro), FTP (transferência de arquivos) e WebSocket (comunicação bidirecional em tempo real).</p>
        </div>
    </div>
</section>

<section class="container">
    <div class="card text-dark bg-light mb-3">
        <div class="card-header">Como a World Wide Web Funciona</div>
        <div class="card-body">
        <h5 class="card-title">Entendendo a Web</h5>
        <p class="card-text">A World Wide Web (WWW) é um sistema de documentos interligados acessíveis via Internet. Esses documentos são formatados em HTML (HyperText Markup Language) e podem ser visualizados por navegadores web. A comunicação na web é feita através do protocolo HTTP (HyperText Transfer Protocol).</p>
        <p class="card-text">Quando um usuário digita um endereço web (URL) em um navegador, este envia uma solicitação HTTP ao servidor onde o site está hospedado. O servidor responde com o código HTML da página solicitada, que o navegador renderiza para o usuário. Esse processo permite que informações e serviços sejam acessados de maneira rápida e eficiente.</p>
        </div>
    </div>
</section>

<h2>Estrutura do Nosso Projeto</h2>

<div class="directory-structure">
    <div>/src</div>
        <div class="directory">
            <div>/controllers</div>
            <div class="directory">
                <div class="file">- userController.ts</div>
                <div class="file">- productController.ts</div>
            </div>
            <div>/models</div>
            <div class="directory">
                <div class="file">- userModel.ts</div>
                <div class="file">- productModel.ts</div>
            </div>
            <div>/views</div>
            <div class="directory">
                <div class="file">- userView.ts</div>
                <div class="file">- productView.ts</div>
            </div>
            <div>/routes</div>
            <div class="directory">
                <div class="file">- userRoutes.ts</div>
                <div class="file">- productRoutes.ts</div>
            </div>
            <div>/services</div>
            <div class="directory">
                <div class="file">- userService.ts</div>
                <div class="file">- productService.ts</div>
            </div>
            <div>/config</div>
            <div class="directory">
                <div class="file">- database.ts</div>
                <div class="file">- server.ts</div>
            </div>
            <div>/middlewares</div>
            <div class="directory">
                <div class="file">- authMiddleware.ts</div>
            </div>
            <div>/utils</div>
            <div class="directory">
                <div class="file">- helpers.ts</div>
            </div>
            <div class="file">- app.ts</div>
        <div class="file">- server.ts</div>
    </div>
</div>

<div class="container mt-5">
    <h2 class="mb-4">Cronograma de Aulas</h2>
    <table class="table table-bordered table-striped">
        <thead class="thead-dark">
            <tr>
                <th>Data</th>
                <th>Aula</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Semana de 06/08</td>
                <td>Análise de Requisitos e Viabilidade</td>
            </tr>
            <tr>
                <td>Semana de 13/08</td>
                <td>GitFlow e Conventional Commits - Boas Práticas de Desenvolvimento e Documentação (Criação do repositório individual) 0,5 pontos</td>
            </tr>
            <tr>
                <td>Semana de 20/08</td>
                <td>Virtualização, node e Docker (Criação de banco de dados postgres com docker compose e ambiente node)</td>
            </tr>
            <tr>
                <td>Semana de 27/08</td>
                <td>Modelagem de banco de dados e Models (Arquiteturas de Softwares em MVC e Padrões de Projeto)</td>
            </tr>
            <tr>
                <td>Semana de 03/09</td>
                <td>Rotas e Controllers (Continuação do MVC)</td>
            </tr>
            <tr>
                <td>Semana de 10/09</td>
                <td>TechWeek</td>
            </tr>
            <tr>
                <td>Semana de 17/09</td>
                <td>Queries SQLs avançadas em banco de dados</td>
            </tr>
            <tr>
                <td>Semana de 24/09</td>
                <td>Teste SQL Avançado 2,5 pontos</td>
            </tr>
            <tr>
                <td>Semana de 01/10</td>
                <td>Feriado</td>
            </tr>
            <tr>
                <td>Semana de 08/10</td>
                <td>Helpers e Camadas Auxiliares do MVC</td>
            </tr>
            <tr>
                <td>Semana de 14/10</td>
                <td>Avaliação Multidisciplinar - 1 ponto</td>
            </tr>
            <tr>
                <td>Semana de 15/10</td>
                <td>III TechWeek</td>
            </tr>
            <tr>
                <td>Semana de 22/10</td>
                <td>Filas com RabbitMQ e controle assíncrono de requisições</td>
            </tr>
            <tr>
                <td>Semana de 29/10</td>
                <td>TDD e testes unitários</td>
            </tr>
            <tr>
                <td>Semana de 05/11</td>
                <td>Deploy com render (web Service + PostgreSQL)</td>
            </tr>
            <tr>
                <td>Semana de 12/11</td>
                <td>Autenticação com criptografia de usuários</td>
            </tr>
            <tr>
                <td>Semana de 19/11</td>
                <td>Revisão e direcionamento de projetos</td>
            </tr>
            <tr>
                <td>Semana de 26/11</td>
                <td>Avaliação Semestral - Prova (2 pontos) + Projeto (4 pontos)</td>
            </tr>
        </tbody>
    </table>
</div>
