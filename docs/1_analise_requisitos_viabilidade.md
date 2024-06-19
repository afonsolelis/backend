# Análise de Requisitos e Viabilidade: Uma Aula Avançada com Desafio Prático

## Instalação do Sails.js, Criação do Projeto e Organização da Documentação

Vamos iniciar o processo desde a instalação do framework Sails.js até a criação da estrutura do projeto e a organização da documentação da Análise de Requisitos.

![](https://sailsjs.com/images/get_started_hero@2x.png)

### Passo a Passo

1. **Instalar o Sails.js:**
   * Certifique-se de ter o Node.js e o npm (gerenciador de pacotes do Node.js) instalados em sua máquina.
   * Abra o terminal ou prompt de comando.
   * Execute o comando `npm install sails -g` para instalar o Sails.js globalmente.

2. **Criar o Projeto Sails:**
   * Navegue até o diretório onde deseja criar o projeto.
   * Execute o comando `sails new nome-do-projeto`.
   * Escolha a opção "Empty App" quando solicitado.

3. **Criar a Pasta de Documentação:**
   * Dentro do diretório do projeto Sails (`nome-do-projeto`), crie uma pasta chamada `docs`.

4. **Iniciar o Projeto (Opcional):**
   * Para verificar se o projeto foi criado corretamente, navegue até o diretório do projeto e execute `sails lift`.
   * O Sails iniciará um servidor local e você poderá acessar a aplicação em `http://localhost:1337`.

5. **Adicionar e Commitar Arquivos:**
   * Crie o arquivo `README.md` dentro da pasta `docs`.
   * Utilize o Markdown para documentar a Análise de Requisitos, seguindo as instruções do Desafio Final.
   * Salve o arquivo.
   * No terminal, navegue até o diretório do projeto Sails.
   * Execute os comandos:
      * `git init` (para inicializar um repositório Git)
      * `git add docs/README.md` (para adicionar o arquivo ao stage)
      * `git commit -m "Adicionando documentação da Análise de Requisitos"` (para criar um commit com uma mensagem descritiva)

6. **Criar o Repositório no GitHub:**
   * Se desejar compartilhar seu projeto e a documentação, siga os passos:
      * Crie um novo repositório no GitHub.
      * No terminal, dentro do diretório do projeto, execute:
         * `git remote add origin <URL do repositório>` (para conectar o repositório local ao remoto)
         * `git push -u origin main` (para enviar as alterações para o repositório remoto)

### Organização da Documentação

Mantenha a pasta `docs` organizada, adicionando subpastas ou arquivos adicionais para cada tipo de requisito ou documento do projeto. Utilize a estrutura sugerida anteriormente.

### Documentação do Sails.js

Para mais informações sobre o Sails.js e suas funcionalidades, consulte a documentação oficial:

* **Sails.js Documentation:** [https://sailsjs.com/documentation](https://sailsjs.com/documentation)

### Observações

* Certifique-se de ter o Node.js e o npm instalados antes de começar.
* A pasta `docs` é uma convenção para armazenar documentação em projetos de software.
* A criação de um repositório no GitHub é opcional, mas recomendada para facilitar o compartilhamento e a colaboração.

Com este guia completo, você estará pronto para iniciar seu projeto Sails, documentar a Análise de Requisitos e compartilhar seu trabalho no GitHub.

### Introdução

A Análise de Requisitos e Viabilidade é essencial para o desenvolvimento de qualquer software, incluindo interfaces de usuário (frontend). Ela garante que o produto final atenda às necessidades dos usuários e seja viável dentro das restrições do projeto. Nesta aula, exploraremos os conceitos e técnicas da Análise de Requisitos e Viabilidade aplicados ao desenvolvimento frontend, culminando em um desafio prático para consolidar seu aprendizado.

![](https://profandreagarcia.wordpress.com/wp-content/uploads/2018/03/requisitos.jpg)

### Objetivos de Aprendizagem

Ao final desta aula, você será capaz de:

* Compreender a importância da Análise de Requisitos e Viabilidade no desenvolvimento frontend.
* Identificar e documentar requisitos funcionais, não funcionais e de usabilidade.
* Realizar análises de viabilidade técnica e de design para interfaces de usuário.
* Aplicar técnicas de elicitação e priorização de requisitos em projetos frontend.
* Utilizar ferramentas e modelos para auxiliar na Análise de Requisitos e Viabilidade em frontend.

![](https://analisederequisitos.com.br/wp-content/uploads/2018/03/Estrutura-dos-requisitos-de-nego%CC%81cio-usua%CC%81rio-e-requisitos-de-sistema.png)

### Conteúdo da Aula

## 1. Introdução à Análise de Requisitos em Backend

A Análise de Requisitos em Backend é o alicerce para o desenvolvimento de sistemas robustos e eficientes. Ela envolve a identificação, documentação e validação das necessidades e expectativas dos usuários e stakeholders em relação à lógica, aos dados e às funcionalidades internas do sistema.

### Definição e Importância

A Análise de Requisitos em Backend é um processo fundamental que visa entender e definir as regras de negócio, os fluxos de dados e as operações que o sistema deve realizar em segundo plano. Ela serve como um guia para o desenvolvimento do backend, garantindo que o sistema:

* **Funcional:** Execute as operações necessárias para atender às necessidades dos usuários e do negócio.
* **Confiável:** Processe e armazene dados de forma segura e consistente.
* **Escalável:** Suporte o crescimento do número de usuários e da quantidade de dados sem comprometer o desempenho.
* **Manutenível:** Seja fácil de atualizar e modificar para atender a novas demandas.
* **Integrável:** Comunique-se de forma eficiente com outros sistemas e componentes.

### Tipos de Requisitos

Os requisitos em backend podem ser classificados em três categorias principais:

#### Requisitos Funcionais

Descrevem as funcionalidades internas que o sistema deve oferecer para suportar as interações do usuário e as regras de negócio. São ações que o sistema deve realizar em segundo plano, como:

* **Processamento de dados:** Calcular valores, validar informações, transformar dados.
* **Gerenciamento de dados:** Armazenar, recuperar, atualizar e excluir dados em bancos de dados.
* **Comunicação:** Trocar informações com outros sistemas ou componentes através de APIs.
* **Autenticação e autorização:** Controlar o acesso aos recursos do sistema.
* **Lógica de negócio:** Implementar as regras e políticas que regem o funcionamento do sistema.

Exemplos de requisitos funcionais:

* "O sistema deve calcular o valor total de um pedido com base nos produtos e quantidades."
* "O sistema deve validar o formato de um endereço de e-mail antes de permitir o cadastro."
* "O sistema deve gerar um relatório mensal de vendas."

#### Requisitos Não Funcionais

Abrangem aspectos que não estão diretamente relacionados às funcionalidades do backend, mas que são essenciais para a qualidade e o desempenho do sistema. Incluem características como:

* **Desempenho:** Tempo de resposta das operações, capacidade de processamento de dados.
* **Segurança:** Proteção contra ataques cibernéticos, criptografia de dados sensíveis.
* **Escalabilidade:** Capacidade de lidar com um aumento no número de usuários e na quantidade de dados.
* **Disponibilidade:** Tempo em que o sistema está disponível para uso.
* **Manutenibilidade:** Facilidade de atualizar e modificar o código do sistema.

Exemplos de requisitos não funcionais:

* "O tempo de resposta de cada operação não deve exceder 1 segundo."
* "O sistema deve ser capaz de processar 10.000 transações por minuto."
* "O sistema deve estar disponível 24 horas por dia, 7 dias por semana."

#### Regras de Negócio

Definem as políticas e restrições que regem o funcionamento do sistema e como ele deve responder a diferentes eventos. São derivadas das necessidades do negócio e podem ser expressas em linguagem natural ou em uma linguagem de modelagem.

Exemplos de regras de negócio:

* "Um cliente só pode ter um pedido em aberto por vez."
* "O desconto máximo permitido em um produto é de 30%."
* "Um usuário só pode acessar determinadas áreas do sistema se tiver permissão de administrador."

### Técnicas de Elicitação

A elicitação de requisitos em backend envolve a coleta de informações de diversas fontes, como:

* **Stakeholders:** Entrevistas com usuários, gerentes de produto, especialistas de domínio e outros envolvidos no projeto.
* **Documentação existente:** Análise de documentos como manuais de usuário, especificações técnicas e relatórios de requisitos de sistemas similares.
* **Análise de sistemas legados:** Estudo de sistemas existentes que serão substituídos ou integrados ao novo sistema.
* **Workshops e brainstorming:** Sessões colaborativas para gerar ideias e identificar requisitos.

### Documentação de Requisitos

A documentação de requisitos em backend deve ser clara, concisa e organizada. Algumas formas comuns de documentar requisitos em backend são:

* **Casos de uso:** Descrevem as interações entre os atores (usuários, sistemas externos) e o sistema para alcançar um objetivo específico.
* **Histórias de usuário:** Descrições concisas e em linguagem natural das funcionalidades desejadas do ponto de vista do usuário.
* **Diagramas de sequência:** Representações visuais da sequência de mensagens trocadas entre os objetos do sistema.
* **Diagramas de classe:** Representações visuais da estrutura e das relações entre as classes do sistema.
* **Especificações de API:** Descrições detalhadas das interfaces de programação de aplicativos (APIs) que o sistema oferece.

Ao dominar a Análise de Requisitos em Backend, você estará apto a construir sistemas robustos, eficientes e que atendam às necessidades do negócio e dos usuários de forma eficaz.


## 2. Análise de Viabilidade em Backend

A Análise de Viabilidade em Backend é o processo de avaliar se os requisitos identificados na etapa anterior são realistas e podem ser implementados com sucesso, considerando as restrições técnicas, de tempo, de custo e de recursos disponíveis.

### Viabilidade Técnica

A viabilidade técnica avalia se os requisitos podem ser implementados com as tecnologias, ferramentas e conhecimentos disponíveis. É importante considerar:

* **Tecnologias:** As linguagens de programação, frameworks, bancos de dados e outras tecnologias escolhidas para o projeto são adequadas para atender aos requisitos? Elas oferecem o desempenho, a segurança e a escalabilidade necessários?
* **Ferramentas:** As ferramentas de desenvolvimento, como IDEs, depuradores e ferramentas de teste, são suficientes para construir e manter o sistema?
* **Equipe:** A equipe de desenvolvimento possui as habilidades e a experiência necessárias para trabalhar com as tecnologias escolhidas e implementar os requisitos?
* **Infraestrutura:** A infraestrutura de hardware e software disponível (servidores, redes, sistemas operacionais) é capaz de suportar o sistema em produção?

### Viabilidade de Design

A viabilidade de design avalia se os requisitos podem ser implementados de forma eficiente, escalável e manutenível. É importante considerar:

* **Arquitetura:** A arquitetura do sistema (monolítica, microsserviços, etc.) é adequada para atender aos requisitos de desempenho, escalabilidade e flexibilidade?
* **Design de dados:** O modelo de dados escolhido (relacional, NoSQL, etc.) é adequado para armazenar e recuperar os dados do sistema de forma eficiente?
* **Design de código:** O código do sistema segue boas práticas de programação, como modularidade, coesão e baixo acoplamento? Isso facilita a manutenção e evolução do sistema.
* **Padrões de projeto:** O uso de padrões de projeto estabelecidos pode ajudar a resolver problemas comuns de design e melhorar a qualidade do código.

### Ferramentas e Métodos

Existem diversas ferramentas e métodos que podem auxiliar na análise de viabilidade em backend:

* **Provas de conceito (PoCs):** Implementações em pequena escala de funcionalidades críticas para validar a viabilidade técnica e testar diferentes abordagens.
* **Análise de riscos:** Identificação e avaliação dos riscos técnicos que podem impactar o projeto, como a falta de experiência da equipe com uma determinada tecnologia ou a dependência de componentes externos.
* **Estimativas de esforço:** Cálculo do tempo e dos recursos necessários para implementar os requisitos, considerando a complexidade das tarefas e a experiência da equipe.
* **Análise de custos:** Estimativa dos custos de desenvolvimento, incluindo licenças de software, hardware, infraestrutura e salários da equipe.

Ao realizar uma análise de viabilidade completa, você pode tomar decisões informadas sobre a implementação dos requisitos, identificar e mitigar riscos e garantir que o projeto seja entregue com sucesso, dentro do prazo e do orçamento.


## 3. Priorização de Requisitos em Backend

A Priorização de Requisitos em Backend é o processo de organizar e classificar os requisitos identificados de acordo com sua importância e impacto no projeto. Essa etapa é crucial para garantir que os recursos sejam alocados de forma eficiente e que as funcionalidades mais importantes sejam desenvolvidas e entregues primeiro.

### Importância da Priorização

A priorização de requisitos oferece diversos benefícios para o projeto:

* **Foco:** Permite que a equipe de desenvolvimento se concentre nas funcionalidades mais importantes, evitando dispersão de esforços.
* **Gerenciamento de expectativas:** Ajuda a alinhar as expectativas dos stakeholders em relação ao que será entregue em cada fase do projeto.
* **Tomada de decisões:** Facilita a tomada de decisões sobre quais requisitos devem ser implementados primeiro, caso haja restrições de tempo ou recursos.
* **Flexibilidade:** Permite que o projeto se adapte a mudanças nas prioridades do negócio ou nas necessidades dos usuários.

### Critérios de Priorização

Existem diversos critérios que podem ser utilizados para priorizar os requisitos em backend:

* **Valor de negócio:** Qual o impacto do requisito no sucesso do negócio? Ele gera receita, reduz custos, melhora a eficiência ou aumenta a satisfação do cliente?
* **Urgência:** Qual a necessidade de implementar o requisito em curto prazo? Ele é essencial para o lançamento do produto ou para atender a uma demanda urgente do mercado?
* **Risco:** Qual o risco de não implementar o requisito? Ele pode causar problemas de segurança, perda de dados, insatisfação do cliente ou impacto negativo na imagem da empresa?
* **Custo:** Qual o custo de implementar o requisito? Ele requer recursos adicionais, como tempo, dinheiro ou mão de obra especializada?
* **Dependências:** O requisito depende de outros requisitos para ser implementado? Ele é um pré-requisito para outras funcionalidades?

### Técnicas de Priorização

Existem diversas técnicas que podem ser utilizadas para priorizar os requisitos em backend:

* **MoSCoW:** Classifica os requisitos em quatro categorias:
    * **Must Have:** Requisitos essenciais para o sucesso do projeto.
    * **Should Have:** Requisitos importantes, mas não essenciais.
    * **Could Have:** Requisitos desejáveis, mas que podem ser adiados.
    * **Won't Have:** Requisitos que não serão implementados nesta versão do projeto.
* **Kano:** Analisa a satisfação do cliente em relação aos requisitos, classificando-os em cinco categorias:
    * **Obrigatórios:** Requisitos básicos que, se não forem atendidos, causam insatisfação.
    * **Unidimensionais:** Requisitos que, quanto mais presentes, mais satisfação geram.
    * **Atraentes:** Requisitos que surpreendem e encantam o cliente.
    * **Indiferentes:** Requisitos que não geram nem satisfação nem insatisfação.
    * **Reversos:** Requisitos que, quanto mais presentes, mais insatisfação geram.
* **Matriz de Priorização:** Atribui pesos aos critérios de priorização e calcula uma pontuação para cada requisito, permitindo ordená-los por ordem de importância.

A escolha da técnica de priorização dependerá do contexto do projeto, dos critérios de priorização definidos e das preferências da equipe de desenvolvimento. É importante envolver os stakeholders nesse processo para garantir que as prioridades estejam alinhadas com as necessidades do negócio e dos usuários.

## 4. Ferramentas e Modelos para Backend

A Análise de Requisitos em Backend se beneficia de uma variedade de ferramentas e modelos que auxiliam na organização, visualização e comunicação dos requisitos, além de facilitar o processo de desenvolvimento e manutenção do sistema.

### Ferramentas para Backend

* **Ferramentas de gerenciamento de projetos:**
    * **Jira:** Permite o acompanhamento de tarefas, bugs e issues, facilitando a organização e o planejamento do desenvolvimento.
    * **Trello:** Oferece um quadro visual para organizar tarefas e acompanhar o progresso do projeto.
    * **Asana:** Permite a criação de projetos, tarefas e subtarefas, além de facilitar a colaboração entre equipes.
* **Ferramentas de documentação:**
    * **Confluence:** Plataforma colaborativa para criar, compartilhar e organizar documentos, como especificações de requisitos, diagramas e manuais.
    * **Swagger:** Ferramenta para documentar APIs REST, facilitando a compreensão e o uso da interface do sistema por outros desenvolvedores.
* **Ferramentas de modelagem de dados:**
    * **MySQL Workbench:** Ambiente visual para projetar, modelar e gerenciar bancos de dados MySQL.
    * **DBeaver:** Ferramenta universal para gerenciar e explorar diversos tipos de bancos de dados.
    * **ER Studio:** Software para modelagem de dados que permite criar diagramas entidade-relacionamento (ER) e gerar scripts SQL.
* **Ferramentas de teste:**
    * **Postman:** Ferramenta para testar APIs REST, enviando requisições e analisando as respostas.
    * **JMeter:** Ferramenta para realizar testes de carga e desempenho em aplicações web e APIs.
    * **SoapUI:** Ferramenta para testar APIs SOAP, permitindo criar e executar testes funcionais e de segurança.

### Modelos para Backend

* **Diagramas de Caso de Uso (UML):** Representam as interações entre os atores (usuários, sistemas externos) e o sistema para alcançar um objetivo específico.
* **Diagramas de Sequência (UML):** Ilustram a ordem temporal das mensagens trocadas entre os objetos do sistema durante a execução de um caso de uso.
* **Diagramas de Classe (UML):** Representam a estrutura estática do sistema, mostrando as classes, seus atributos e métodos, e as relações entre elas.
* **Diagramas de Entidade-Relacionamento (ER):** Modelam a estrutura de dados do sistema, mostrando as entidades, seus atributos e os relacionamentos entre elas.
* **Diagramas de Fluxo de Dados (DFD):** Representam o fluxo de dados através do sistema, mostrando os processos, os armazenamentos de dados e as entidades externas.

A escolha das ferramentas e modelos adequados dependerá das necessidades e preferências da equipe de desenvolvimento, bem como das características do projeto. A utilização dessas ferramentas e modelos pode agilizar o processo de desenvolvimento, facilitar a comunicação entre os membros da equipe e garantir a qualidade do produto final.

### Desafio Final: Análise de Requisitos para um Módulo Backend

**Cenário:**

Você faz parte da equipe de desenvolvimento de um novo sistema web. Sua tarefa é realizar a Análise de Requisitos para um módulo backend específico.

**Tarefas:**

1. **Escolha do Módulo:** Selecione um módulo backend do sistema (ex: autenticação de usuários, gerenciamento de produtos, processamento de pagamentos).
2. **Elicitação de Requisitos:** Entreviste usuários, stakeholders e especialistas de domínio para coletar requisitos funcionais, não funcionais, regras de negócio, requisitos de usuário e requisitos de sistema para o módulo escolhido.
3. **Documentação de Requisitos:** Documente os requisitos elicitados de forma clara e organizada, utilizando casos de uso, histórias de usuário, diagramas de sequência, diagramas de classe ou outros modelos adequados. Classifique os requisitos em suas respectivas categorias.
4. **Análise de Viabilidade:** Avalie a viabilidade técnica e de design dos requisitos, considerando as tecnologias disponíveis (linguagens de programação, frameworks, bancos de dados), as restrições de infraestrutura e os padrões de projeto aplicáveis.
5. **Priorização de Requisitos:** Priorize os requisitos de acordo com sua importância para o projeto, utilizando técnicas como MoSCoW, Kano ou matriz de priorização, levando em consideração o valor de negócio, a urgência, o risco e o custo de cada requisito.

**Entrega:**

Crie um repositório no GitHub para o projeto e adicione um arquivo README.md com a documentação completa da Análise de Requisitos. Inclua:

* Descrição detalhada do módulo backend escolhido.
* Lista completa dos requisitos elicitados, classificados por tipo (funcional, não funcional, regras de negócio, requisitos de usuário, requisitos de sistema).
* Análise de viabilidade técnica e de design, incluindo justificativas para as escolhas tecnológicas e de arquitetura.
* Priorização dos requisitos, com explicação dos critérios utilizados e da ordem de importância estabelecida.
* Diagramas ou modelos que auxiliem na compreensão dos requisitos e do funcionamento do módulo (opcional).

**Avaliação:**

Sua entrega será avaliada individualmente, considerando:

* A qualidade e completude da elicitação e documentação dos requisitos.
* A profundidade e a pertinência da análise de viabilidade.
* A coerência e a justificativa da priorização dos requisitos.
* A clareza e a organização da documentação.
* O uso adequado de ferramentas e modelos para representar os requisitos.

Este desafio prático permitirá que você aplique os conceitos e técnicas aprendidos em um cenário real de desenvolvimento backend, preparando você para os desafios do mercado de trabalho.

