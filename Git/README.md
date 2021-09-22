# Comandos Linux
~~~
mkdir minhapasta => criar diretório (pasta)
cd minhapasta => abrir pasta 
...
~~~

# Comandos essenciais do Git
## Branches
O **master** é o branch principal do GIT.

O HEAD é um ponteiro especial que indica qual é o branch atual. Por padrão, o HEAD aponta para o branch principal, o master.

### Criando um novo branch
git branch nomeDaMinhaBranch

### Trocando para um branch existente
git checkout nomeDaMinhaBranch

Neste caso, o ponteiro principal HEAD esta apontando para o branch chamado nomeDaMinhaBranch.

### Criar um novo branch e trocar
git checkout -b nomeDaMinhaBranch

### Voltar para o branch principal (master)
git checkout master

### Resolver merge entre os branches
git merge nomeDaMinhaBranch

Para realizar o merge, é necessário estar no branch que deverá receber as alterações. O merge pode automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas.

A mensagem indicando um merge manual será:

_Automerging meu_arquivo.txt
CONFLICT (content): Merge conflict in meu_arquivo.txt
Automatic merge failed; fix conflicts and then commit the result._

### Apagando um branch
git branch -d nomeDaMinhaBranch

### Listar branches
git branch

### Listar branches com informações dos últimos commits
git branch -v

### Listar branches que já foram fundidos (merged) com o master
git branch --merged

### Listar branches que não foram fundidos (merged) com o master
git branch --no-merged

### Criando branches no repositório remoto
git push origin nomeDaMinhaBranch

### Criando um branch remoto com nome diferente
git push origin nomeDaMinhaBranch:new-branch

### Baixar um branch remoto para edição
git checkout -b nomeDaMinhaBranch origin/nomeDaMinhaBranch

### Apagar branch remoto
git push origin:nomeDaMinhaBranch

## Rebasing
### Fazendo o rebase entre um o branch nomeDaMinhaBranch e o master.

git checkout experiment

git rebase master
Mais informações e explicações sobre o Rebasing

## Stash

Para alternar entre um branch e outro é necessário fazer o commit das alterações atuais para depois trocar para um outro branch. Se existir a necessidade de realizar a troca sem fazer o commit é possível criar um stash. O Stash como se fosse um branch temporário que contem apenas as alterações ainda não commitadas.

### Criar um stash
git stash

### Listar stashes
git stash list

### Voltar para o último stash
git stash apply

### Voltar para um stash específico
git stash apply stash@{2}
Onde 2 é o indíce do stash desejado.

### Criar um branch a partir de um stash
git stash branch meu_branch

## Reescrevendo o histórico
### Alterando mensagens de commit
git commit --amend -m "Minha nova mensagem"

## Alterar últimos commits
### Alterando os três últimos commits

git rebase -i HEAD~3

### O editor de texto será aberto com as linhas representando os três últimos commits.

pick f7f3f6d changed my name a bit
pick 310154e updated README formatting and added blame
pick a5f4a0d added catfile

### Altere para edit os commits que deseja realizar alterações.

edit f7f3f6d changed my name a bit
pick 310154e updated README formatting and added blame
pick a5f4a0d added catfile
Feche o editor de texto.

## Digite o comando para alterar a mensagem do commit que foi marcado como edit.

git commit –amend -m “Nova mensagem”

### Aplique a alteração

git rebase --continue

Atenção: É possível alterar a ordem dos commits ou remover um commit apenas mudando as linhas ou removendo.

### Juntando vários commits
Seguir os mesmos passos acima, porém marcar os commtis que devem ser juntados com *squash

### Remover todo histórico de um arquivo
git filter-branch --tree-filter 'rm -f passwords.txt' HEAD

## Bisect
O bisect (pesquisa binária) é útil para encontrar um commit que esta gerando um bug ou uma inconsistência entre uma sequência de commits.

### Iniciar pequinsa binária

git bisect start

### Marcar o commit atual como ruim

git bisect bad

### Marcar o commit de uma tag que esta sem o bug/inconsistência

git bisect good vs-1.1

### Marcar o commit como bom
O GIT irá navegar entre os commits para ajudar a indentificar o commit que esta com o problema. Se o commit atual não estiver quebrado, então é necessário marca-lo como bom.

### git bisect good
Marcar o commit como ruim

### Se o commit estiver com o problema, então ele deverá ser marcado como ruim.

### git bisect bad

### Finalizar a pesquisa binária
Depois de encontrar o commit com problema, para retornar para o HEAD utilize:

git bisect reset