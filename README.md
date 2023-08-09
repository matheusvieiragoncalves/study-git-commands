# study-git-commands

Esse repositório tem o objetivo de listar os principais comandos e boas práticas na utilização do git.

## Principais comandos

| Comando                                 | Resultado                                                                                                                                                                                                                                                 |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| git init                                | Inicializa um repositório Git vazio em um diretório local. Esse comando cria um novo subdiretório oculto chamado ".git" que contém todos os metadados do repositório.                                                                                     |
| git clone **URL**                       | Clona um repositório Git existente para o seu computador. A URL pode ser um caminho local ou um endereço remoto, como um repositório no GitHub. Vale ressaltar que o clone de repositório pode ser feito via HTTP ou SSH. Hoje é recomendado o uso do SSH |
| git add **arquivo**                     | Adiciona um arquivo específico à área de preparação (staging area). Isso prepara o arquivo para ser incluído no próximo commit.                                                                                                                           |
| git add .                               | Adiciona todos os arquivos contidos no diretório que o consoe está aberto à área de preparação (staging area). Isso prepara TODOS os arquivo contidos na pasta para ser incluídos no próximo commit.                                                      |
| git commit -m **"mensagem"**            | Cria um novo commit com as mudanças na área de preparação. A mensagem entre aspas fornece uma descrição do commit.                                                                                                                                        |
| git status                              | Mostra o status atual do repositório. Ele exibe informações sobre quais arquivos foram modificados, quais estão na área de preparação e quais não foram rastreados pelo Git.                                                                              |
| git log                                 | Exibe o histórico de commits do repositório, mostrando informações sobre cada commit, como autor, data e mensagem. É preciso utilizar a tecla Q para finalizar o histórico                                                                                |
| git pull                                | Atualiza o repositório local com as alterações mais recentes do repositório remoto. É comumente usado para trazer mudanças de outras pessoas para o seu repositório local.                                                                                |
| git push                                | Envia os commits locais para o repositório remoto. Isso atualiza o repositório remoto com as mudanças feitas localmente.                                                                                                                                  |
| git branch                              | Lista as branches (ramificações) existentes no repositório. A branch atual é destacada com um asterisco.                                                                                                                                                  |
| git branch **nome_branch**              | Cria uma nova branch com o nome especificado.                                                                                                                                                                                                             |
| git checkout **nome_branch**            | Alterna para uma branch específica, permitindo que você trabalhe no contexto daquela branch.                                                                                                                                                              |
| git checkout -b **nome_branch**         | Cria uma nova branch com o nome especificado e já alterna para ela. Seria uma junção do git branch + git checkout                                                                                                                                         |
| git reset                               | remove os arquivos da área de preparação (staging area) mas mantém as mudanças não comprometidas em seu diretório de trabalho.                                                                                                                            |
| git reset --hard                        | Descarta todas as mudanças não comprometidas no diretório de trabalho e na área de preparação, retornando ao estado do último commit.                                                                                                                     |
| git fetch                               | Busca as informações mais recentes do repositório remoto, mas não mescla as alterações com o repositório local. É útil para ver o que foi alterado antes de decidir mesclar.                                                                              |
| git stash                               | Armazena temporariamente as mudanças não comprometidas em uma "stash" (reserva). Isso é útil quando você precisa alternar rapidamente para outra branch sem fazer um commit incompleto.                                                                   |
| git stash list                          | Lista todas as "stashes" armazenadas e suas descrições.                                                                                                                                                                                                   |
| git stash apply                         | Aplica a última stash armazenada, mas mantém a stash na lista                                                                                                                                                                                             |
| git stash drop                          | Remove as modificações armazenadas no git stash, uma a uma                                                                                                                                                                                                |
| git stash pop                           | Aplica a última stash armazenada e a remove da lista, seria uma junção do git stash apply + git stash drop                                                                                                                                                |
| git config                              | Permite configurar opções do Git, como nome de usuário, email, e outros comportamentos.                                                                                                                                                                   |
| git remote -v                           | Exibe a lista de repositórios remotos associados ao seu repositório local.                                                                                                                                                                                |
| git remote add **nome** **URL**         | Adiciona um repositório remoto ao seu repositório local, permitindo que você faça push e pull para esse repositório.                                                                                                                                      |
| git diff                                | Mostra as diferenças entre o estado atual do repositório e o último commit. Isso ajuda a identificar as mudanças feitas nos arquivos.                                                                                                                     |
| git diff **commitA**..**commitB**       | Mostra as diferenças entre dois commits específicos. Mostra as diferenças entre dois commits específicos. Substitua **commitA** e **commitB** pelos identificadores dos commits desejados.                                                                |
| git cherry-pick **commit**              | Aplica um commit específico de outra branch na branch atual.                                                                                                                                                                                              |
| git tag                                 | Lista as tags existentes no repositório. As tags são usadas para marcar pontos específicos na história do projeto.                                                                                                                                        |
| git tag **nome_tag**                    | Cria uma nova tag no commit atual com o nome especificado.                                                                                                                                                                                                |
| git tag -a **nome_tag** -m **mensagem** | Cria uma nova tag anotada com uma mensagem detalhada.                                                                                                                                                                                                     |
| git push --tags                         | Envia todas as tags locais para o repositório remoto.                                                                                                                                                                                                     |

## Conventional Commits

Commits convencionais referem-se a uma prática de criar mensagens de commit de forma padronizada e descritiva, seguindo um formato predefinido. Essa abordagem ajuda a comunicar claramente as mudanças feitas em um commit, o que é especialmente útil em projetos de desenvolvimento de software colaborativo, onde várias pessoas trabalham juntas. A Convenção de Mensagens de Commit (Commit Message Convention) mais comumente usada é conhecida como "Conventional Commits".

A estrutura básica de um commit convencional segue este padrão:

```
tipo(escopo): descrição

Corpo da mensagem

Rodapé da mensagem
```

#### Cada parte acima se refere a:

- **Tipo**: Indica o propósito geral do commit. Pode ser algo como "feat" (adição de uma nova funcionalidade), "fix" (correção de um bug), "chore" (tarefa de manutenção ou ajuste), "docs" (atualização de documentação), etc.

- **Escopo** (opcional): Refere-se a uma parte específica do projeto que está sendo afetada pelo commit. Isso pode ser um nome de módulo, um componente ou qualquer outra divisão lógica do código.

- **Descrição**: Fornece uma breve descrição do que o commit faz. Deve ser curta e clara, explicando o que foi alterado.

- **Corpo da mensagem** (opcional): Permite fornecer informações mais detalhadas sobre as mudanças feitas no commit. Isso pode incluir a motivação por trás das alterações, detalhes técnicos ou qualquer contexto necessário.

- **Rodapé da mensagem** (opcional): Usado para fazer referência a problemas (como números de problemas ou solicitações de pull) ou para adicionar informações adicionais relevantes.

#### Exemplo

```
feat(user-register): adiciona cadastro de usuário

Adiciona campos para o cadastro de usuários do sistema: Nome, email, senha e data de nascimento.
Isso permite o cadastro de novos usuários e também possibilita o login no sistema com as informações de email e senha.

Closes #453
```

#### O mais comum é a utilização resumida para atividades simples

```
feat(user-register): adiciona cadastro de usuário
```

### Lista dos **tipos** mais utilizados

| Tipo     | Significado                                                                                                                             |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| feat     | Adição de uma nova funcionalidade ao código ou ao projeto.                                                                              |
| fix      | Correção de um bug ou problema existente no código.                                                                                     |
| chore    | Tarefas de manutenção, ajustes no código, melhorias na estrutura, refatorações, etc. Geralmente não afetam a funcionalidade principal.  |
| docs     | Atualizações na documentação, como comentários no código, guias, manuais, etc.                                                          |
| style    | Mudanças relacionadas à formatação do código, como espaçamento, indentação, ponto e vírgula, etc.                                       |
| refactor | Mudanças no código que não adicionam uma nova funcionalidade nem corrigem um bug, mas melhoram a estrutura, legibilidade ou desempenho. |
| test     | Adição ou modificação de testes de código existentes.                                                                                   |
| build    | Mudanças no processo de compilação, configuração, dependências, scripts de construção, etc.                                             |
| revert   | Reverte um commit anterior.                                                                                                             |
| ci       | Mudanças relacionadas à configuração de integração contínua (CI) ou automação de implantação.                                           |
| wip      | rabalho em progresso. Geralmente usado para commits intermediários que ainda não estão prontos para serem finalizados.                  |
| merge    | Usado para comunicar uma mesclagem de branches                                                                                          |
