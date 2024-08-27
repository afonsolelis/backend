Para criar um tutorial completo de modelagem de banco de dados utilizando o JSON Server Generator e DBeaver, além de exemplos de SQL do básico ao avançado, siga os passos abaixo. Este tutorial inclui a configuração de um ambiente com Docker e PostgreSQL, bem como uma explicação das linguagens DDL e DML em SQL.

## Introdução às Linguagens DDL e DML

**DDL (Data Definition Language):**  
DDL é a parte do SQL que permite definir e modificar a estrutura dos objetos do banco de dados, como tabelas e índices. Comandos DDL incluem `CREATE`, `ALTER`, e `DROP`.

**DML (Data Manipulation Language):**  
DML é a parte do SQL usada para manipular os dados dentro das estruturas definidas. Comandos DML incluem `INSERT`, `UPDATE`, `DELETE`, e `SELECT`.

## Modelagem de Banco de Dados

### **1. Modelagem de Dados**

- **Modelo Conceitual:** Identifique as entidades e os relacionamentos. Exemplo: *Alunos*, *Professores*, *Cursos*.
- **Modelo Lógico:** Defina os atributos, chaves primárias e estrangeiras para cada entidade.
- **Modelo Físico:** Converta o modelo lógico em tabelas no banco de dados.

### **2. JSON Server Generator**

Utilize o [JSON Server Generator](https://www.jsonservergenerator.com) para criar um servidor JSON que simula uma API RESTful. Isso é útil para prototipar dados que serão usados no banco de dados.

## Configuração do Ambiente

### **1. Docker Compose para PostgreSQL**

Crie um arquivo `docker-compose.yml` para configurar um container PostgreSQL:

```yaml
version: '3.1'

services:
  db:
    image: postgres:latest
    restart: always
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase
    ports:
      - "5432:5432"
```

### **2. DBeaver**

- **Instalação e Configuração:** Instale o DBeaver e configure uma nova conexão com o PostgreSQL. O DBeaver é uma ferramenta gráfica que facilita a interação com bancos de dados, permitindo executar comandos SQL e visualizar dados de forma intuitiva.

## Exemplos de SQL

![exemplos](https://miro.medium.com/v2/format:webp/1*KJ0tDRYSeg-gMo_6nRH-XA.png)

### **1. DDL (Data Definition Language)**

- **CREATE TABLE:**

```sql
CREATE TABLE Alunos (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100),
    curso_id INT
);
```

- **ALTER TABLE:**

```sql
ALTER TABLE Alunos ADD COLUMN email VARCHAR(100);
```

- **DROP TABLE:**

```sql
DROP TABLE Alunos;
```

### **2. DML (Data Manipulation Language)**

- **INSERT:**

```sql
INSERT INTO Alunos (nome, curso_id) VALUES ('João Silva', 1);
```

- **SELECT:**

```sql
SELECT * FROM Alunos;
```

- **UPDATE:**

```sql
UPDATE Alunos SET email = 'joao.silva@example.com' WHERE id = 1;
```

- **DELETE:**

```sql
DELETE FROM Alunos WHERE id = 1;
```

### **3. CRUD Completo**

Para um CRUD completo, você pode seguir o seguinte fluxo:

- **Create:** Inserir novos registros.
- **Read:** Consultar registros existentes.
- **Update:** Atualizar registros existentes.
- **Delete:** Remover registros.

Para ensinar conceitos como *primary key*, *foreign key*, *joins*, e relações de 1 para N e N para N, podemos criar um exemplo prático utilizando tabelas de um sistema acadêmico. Vamos usar as tabelas de *Cursos*, *Alunos*, e *Matrículas* para ilustrar esses conceitos.

## Estrutura das Tabelas

### **Criação das Tabelas**

Vamos criar três tabelas: *Cursos*, *Alunos*, e *Matrículas*. As tabelas *Cursos* e *Alunos* terão uma chave primária, enquanto a tabela *Matrículas* será usada para representar uma relação N para N entre *Alunos* e *Cursos*.

```sql
CREATE TABLE Cursos (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100)
);

CREATE TABLE Alunos (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100)
);

CREATE TABLE Matriculas (
    aluno_id INT REFERENCES Alunos(id),
    curso_id INT REFERENCES Cursos(id),
    PRIMARY KEY (aluno_id, curso_id)
);
```

### **Explicação**

- **Primary Key:** A chave primária é um identificador único para cada registro em uma tabela. Nas tabelas *Cursos* e *Alunos*, a coluna `id` é a chave primária.
- **Foreign Key:** A chave estrangeira é usada para criar um relacionamento entre duas tabelas. Na tabela *Matriculas*, `aluno_id` e `curso_id` são chaves estrangeiras que referenciam as tabelas *Alunos* e *Cursos*, respectivamente.

## Inserção de Dados

### **Inserir Dados em Várias Tabelas**

Vamos inserir dados nas tabelas *Cursos*, *Alunos*, e *Matrículas*.

```sql
-- Inserir dados na tabela Cursos
INSERT INTO Cursos (nome) VALUES ('Matemática'), ('Física'), ('Química');

-- Inserir dados na tabela Alunos
INSERT INTO Alunos (nome) VALUES ('João Silva'), ('Maria Oliveira'), ('Carlos Souza');

-- Inserir dados na tabela Matriculas
INSERT INTO Matriculas (aluno_id, curso_id) VALUES 
(1, 1),  -- João Silva matriculado em Matemática
(1, 2),  -- João Silva matriculado em Física
(2, 1),  -- Maria Oliveira matriculada em Matemática
(3, 3);  -- Carlos Souza matriculado em Química
```

## Consultas e Joins

### **Exemplos de Joins**

- **Inner Join:** Retorna registros que têm correspondências em ambas as tabelas.

```sql
SELECT Alunos.nome AS aluno, Cursos.nome AS curso
FROM Matriculas
JOIN Alunos ON Matriculas.aluno_id = Alunos.id
JOIN Cursos ON Matriculas.curso_id = Cursos.id;
```

- **Left Join:** Retorna todos os registros da tabela à esquerda e os registros correspondentes da tabela à direita.

```sql
SELECT Alunos.nome AS aluno, Cursos.nome AS curso
FROM Alunos
LEFT JOIN Matriculas ON Alunos.id = Matriculas.aluno_id
LEFT JOIN Cursos ON Matriculas.curso_id = Cursos.id;
```

- **Right Join:** Retorna todos os registros da tabela à direita e os registros correspondentes da tabela à esquerda.

```sql
SELECT Alunos.nome AS aluno, Cursos.nome AS curso
FROM Cursos
RIGHT JOIN Matriculas ON Cursos.id = Matriculas.curso_id
RIGHT JOIN Alunos ON Matriculas.aluno_id = Alunos.id;
```

### **Relações 1 para N e N para N**

- **1 para N:** Um curso pode ter muitos alunos matriculados. Isso é representado pela tabela *Matriculas*, onde um `curso_id` pode aparecer várias vezes.
- **N para N:** Um aluno pode estar matriculado em vários cursos, e um curso pode ter vários alunos. A tabela *Matriculas* representa essa relação.

Esses exemplos fornecem uma base sólida para entender como modelar e consultar dados em um banco de dados relacional, utilizando conceitos fundamentais de SQL.

# Leituras Complementares

[SQL commans (DDL, DQL, DML, DCL and TCL) Comprehensive Guide](https://medium.com/@aqilzeka99/a-comprehensive-guide-to-sql-commans-ddl-dql-dml-dcl-and-tcl-cd2de3540d4e)