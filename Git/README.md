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