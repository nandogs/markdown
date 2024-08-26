# Resumo dos Principais Comandos do Git

## Comandos Básicos

- **`git init`**
  - Cria um novo repositório Git vazio no diretório atual.

- **`git clone <url>`**
  - Clona um repositório remoto para o diretório local.

- **`git add <arquivo>`**
  - Adiciona arquivos ao índice (staging area) para o próximo commit.

- **`git commit -m "<mensagem>"`**
  - Cria um novo commit com a mensagem fornecida.

- **`git status`**
  - Mostra o status dos arquivos no repositório (modificados, não rastreados, etc.).

- **`git log`**
  - Exibe o histórico de commits.

- **`git diff`**
  - Mostra as diferenças entre arquivos modificados e o último commit.

## Comandos de Ramificação (Branching)

- **`git branch`**
  - Lista todas as branches no repositório ou cria uma nova branch.

- **`git branch <nome-branch>`**
  - Cria uma nova branch.

- **`git checkout <nome-branch>`**
  - Troca para a branch especificada.

- **`git checkout -b <nome-branch>`**
  - Cria e troca para uma nova branch.

- **`git merge <nome-branch>`**
  - Mescla a branch especificada na branch atual.

- **`git branch -d <nome-branch>`**
  - Exclui a branch especificada (só pode ser excluída se já foi mesclada).

## Comandos de Controle Remoto

- **`git remote add <nome> <url>`**
  - Adiciona um repositório remoto com o nome fornecido.

- **`git fetch <nome>`**
  - Baixa as alterações do repositório remoto, mas não as mescla com a branch atual.

- **`git pull <nome> <branch>`**
  - Baixa e mescla as alterações do repositório remoto com a branch atual.

- **`git push <nome> <branch>`**
  - Envia commits da branch local para o repositório remoto.

- **`git remote -v`**
  - Lista os repositórios remotos e suas URLs.

## Outros Comandos Úteis

- **`git reset <arquivo>`**
  - Remove arquivos da área de staging (prepara para o commit).

- **`git rm <arquivo>`**
  - Remove arquivos do repositório e da área de staging.

- **`git stash`**
  - Salva temporariamente alterações não comitadas para limpar o diretório de trabalho.

- **`git stash apply`**
  - Restaura as alterações salvas com `git stash`.

- **`git tag <nome-tag>`**
  - Cria uma nova tag no commit atual.

Para mais informações, consulte a [documentação oficial do Git](https://git-scm.com/doc).

=====================================================================================================================================================================

# Gitflow: Uma Visão Geral

Gitflow é uma estratégia de ramificação popular para gerenciar o desenvolvimento de software usando Git. Foi criada por Vincent Driessen e visa fornecer um fluxo de trabalho estruturado para lidar com diferentes tipos de desenvolvimento e releases.

## Principais Conceitos

### Branches Principais

1. **`main` (ou `master`)**
   - A branch principal onde o código de produção está sempre estável. É a base para todas as releases.

2. **`develop`**
   - A branch de desenvolvimento onde o trabalho de integração das novas features e correções acontece. É uma ramificação da `main` e serve como base para novas features e correções antes da liberação para produção.

### Branches de Suporte

1. **`feature/<nome>`**
   - Usada para desenvolver novas funcionalidades. É criada a partir da branch `develop` e é mesclada de volta na `develop` quando a feature está completa.
   - **Criar**: `git checkout -b feature/<nome> develop`
   - **Mesclar**: `git checkout develop` e `git merge feature/<nome>`

2. **`release/<versão>`**
   - Usada para preparar uma nova versão de produção. É criada a partir da branch `develop` quando as novas features estão completas e estão prontas para serem preparadas para produção.
   - **Criar**: `git checkout -b release/<versão> develop`
   - **Mesclar**: `git checkout main` e `git merge release/<versão>`; também mescle de volta para `develop` para garantir que as correções sejam incorporadas.

3. **`hotfix/<nome>`**
   - Usada para corrigir problemas críticos em produção. É criada a partir da branch `main` e é mesclada de volta tanto em `main` quanto em `develop` para garantir que o hotfix esteja disponível para o próximo ciclo de desenvolvimento.
   - **Criar**: `git checkout -b hotfix/<nome> main`
   - **Mesclar**: `git checkout main` e `git merge hotfix/<nome>`; também mescle de volta para `develop`.

### Fluxo de Trabalho Básico

1. **Desenvolvimento de Features**
   - Crie uma branch de feature a partir de `develop`.
   - Desenvolva a feature e teste localmente.
   - Quando a feature estiver completa, faça o merge de volta em `develop`.

2. **Preparação para Release**
   - Crie uma branch de release a partir de `develop`.
   - Teste e faça os ajustes finais.
   - Quando a release estiver pronta, faça o merge em `main` e `develop`.

3. **Correção de Problemas em Produção**
   - Crie uma branch de hotfix a partir de `main`.
   - Corrija o problema e teste.
   - Quando a correção estiver pronta, faça o merge em `main` e `develop`.

### Benefícios do Gitflow

- **Organização**: Ajuda a manter um fluxo de trabalho organizado e previsível.
- **Separação de Tarefas**: Distinções claras entre desenvolvimento de novas features, preparação de releases e correção de problemas.
- **Facilidade de Gestão**: Facilita a gestão de releases e hotfixes.

Para mais informações, você pode consultar a [documentação oficial do Gitflow](https://nvie.com/posts/a-successful-git-branching-model/).

