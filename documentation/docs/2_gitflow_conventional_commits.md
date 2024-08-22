# Aula Básica de Git via Terminal

<iframe width="100%" height="640" src="https://www.youtube.com/embed/veTxtkXXKPg?si=oNBjc5BlMTIx3oFO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## O que é Git?

Git é um sistema de controle de versão distribuído, amplamente utilizado para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele permite que múltiplos desenvolvedores trabalhem simultaneamente em um projeto sem conflitos.

## Instalação do Git

### No Windows:
1. Baixe o instalador do Git em [git-scm.com](https://git-scm.com/downloads).
2. Execute o instalador e siga as instruções.

### No macOS:
```sh
brew install git
```

### No Linux (Ubuntu/Debian):
```sh
sudo apt-get install git
```

## Mas nós iremos fazer no Replit.com

1. Vá ao [repli.com](https://replit.com/)
2. Faça seu cadastro com o github!
3. Inicie uma máquina para Typescript
4. No shell faça "gh auth login" e ele vai perguntar se você precisa instalar o gh
5. Após a instalação, digite novamente `gh auth login` e faça o login com o github em https

## Configuração Inicial

Após instalar o Git, você precisa configurar seu nome de usuário e e-mail:

```sh
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"
```

![flow](https://blog.openreplay.com/images/automating-releases-in-github-with-conventional-commits/images/image4.jpg)

## Comandos Básicos do Git

### 1. `git init`

Inicializa um novo repositório Git no diretório atual.

```sh
git init
```

### 2. `git clone`

Clona um repositório remoto para o diretório local.

```sh
git clone https://github.com/usuario/repo.git
```

### 3. `git status`

Exibe o status dos arquivos no diretório de trabalho e no índice.

```sh
git status
```

### 4. `git add`

Adiciona arquivos ao índice (staging area).

```sh
git add nome_do_arquivo
# Ou para adicionar todos os arquivos alterados:
git add .
```

### 5. `git commit`

Grava as mudanças do índice no repositório local.

```sh
git commit -m "Mensagem descritiva sobre a mudança"
```

### 6. `git push`

Envia as mudanças do repositório local para o repositório remoto.

```sh
git push origin nome_da_branch
```

### 7. `git pull`

Atualiza o repositório local com as mudanças do repositório remoto.

```sh
git pull origin nome_da_branch
```

### 8. `git branch`

Lista todas as branches no repositório. Para criar uma nova branch:

```sh
git branch nome_da_nova_branch
```

### 9. `git checkout`

Muda para uma branch específica.

```sh
git checkout nome_da_branch
```

### 10. `git merge`

Mescla uma branch na branch atual.

```sh
git merge nome_da_branch
```

## Conventional Commits

[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) é uma convenção para escrever mensagens de commit que facilita a leitura e entendimento do histórico de commits. Uma mensagem de commit convencional tem a seguinte estrutura:

```
tipo(escopo opcional): descrição

[corpo opcional]
```

### Tipos Comuns de Commits

- **feat**: Uma nova funcionalidade.
- **fix**: Correção de bug.
- **docs**: Mudanças na documentação.
- **style**: Mudanças que não afetam o significado do código (espaços em branco, formatação, etc).
- **refactor**: Mudança de código que não corrige um bug nem adiciona uma funcionalidade.
- **test**: Adição ou correção de testes.
- **chore**: Mudanças no processo de build ou ferramentas auxiliares e bibliotecas.

![logo conventional](https://hashnode.com/utility/r?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1620343062221%2FBFETDzbJj.png%3Fw%3D1200%26h%3D630%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp%26fm%3Dpng)

### Exemplo de Conventional Commit

![exemplos conventional](https://miro.medium.com/v2/resize:fit:1400/1*izVKF4AT1iDtv4fJO8oWWA.png)

```sh
git commit -m "feat(login): adicionar autenticação de usuário"
```

## Passo a Passo para Treinar Commits

1. **Clonar o repositório** (se ainda não estiver clonado):
    ```sh
    git clone https://github.com/usuario/repo.git
    ```

2. **Criar uma nova branch** para sua feature ou correção:
    ```sh
    git checkout -b minha_feature
    ```

3. **Fazer mudanças** no código.

4. **Adicionar** os arquivos alterados ao índice:
    ```sh
    git add .
    ```

5. **Escrever uma mensagem de commit** usando Conventional Commits:
    ```sh
    git commit -m "feat(minha_feature): adicionar nova funcionalidade de exemplo"
    ```

6. **Enviar** as mudanças para o repositório remoto:
    ```sh
    git push origin minha_feature
    ```

7. **Criar um Pull Request** no repositório remoto para mesclar suas mudanças na branch principal.

[documentação oficial do Git](https://git-scm.com/doc).

## Commit Perfeito?

<iframe width="100%" height="640" src="https://www.youtube.com/embed/sStBPj7JJpM?si=IrNuhSsCGLv5hkJe" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Entendendo GIT

<iframe width="100%" height="640" src="https://www.youtube.com/embed/6Czd1Yetaac?si=rtI6AR96OhyY8x66" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## GIT Flow

<iframe width="100%" height="640" src="https://www.youtube.com/embed/oweffeS8TRc?si=HrRRyQNsJHbWShTX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Git Project Setup with Husky, Conventional Commits, and branching strategies

<iframe width="100%" height="640" src="https://www.youtube.com/embed/jNxDNoYEGVU?si=3k_iOZUmr8sUM5Zn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Write git commit messages like a PRO with Conventional Commits

<iframe width="100%" height="640" src="https://www.youtube.com/embed/OJqUWvmf4gg?si=6zoFJraKqqWii3JR" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Trabalhando em equipe com Git Flow

<iframe width="100%" height="640" src="https://www.youtube.com/embed/394mc6PV8t8?si=HGiQNR6SqbCcb_fN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<iframe width="100%" height="640" src="https://www.youtube.com/embed/wAJcX9KqxR8?si=hV5eQpPAgyMn8GeK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>