# Comando do git

mostrar o que foi adicionado no staged: git diff --staged


git merge --no-ff (gera o commit de merge)
git log --oneline --graph --decorate ()
git remote show origin (detalhes adicionais)
git pull --verbode (detalhes do download dos arquivos)

## Dicas essenciais

git rebase -i
git add -p
git reflog (usar com reset ou cherry-pick)
git stash
git reset
git cherry-pick
git pull --rebase ()
git bisect (encontre bugs inserido por um commit mais rapido)

- nao modifique o historico dos commits quando outras pessoas estao com esses codigos
- so mude o historico dos commit caso ninguem tenha esses codigos, ou seja, somente quando voce fez commits e tem branches, mas ainda nao fez push, a partir de quando voce faz push, nao mude mais o historico 
- faça push e pull todos os dias, isso evita que aconteca conflitos de merge muito grandes e trabalhosos de se resolver. essa pratica também é conhecida como integração contínua, alem de integrar o código local com o remoto, deve haver testes automatizados para assegurar que tudo esteja funcionando.
- antes de fazer o push faça squash caso necessario para deixar o historico mais limpo
- nao abra um pull request e envie uma quantidade muito grande de modificações isso desmotiva pela quantidade. melhor abrir um PR e envie os commit conforme eles forem feitos. uma lista gradativa de reviews pendente é melhor que uma lista enorme.
- use git pull --rebase para sincronizar o repositorio local com o remoto.

comandos perigosos

git reset
git rebase
git push --force (evite ao máximo)

### Outras dicas:

1. https://ohshitgit.com/pt_BR
1. https://css-tricks.com/interactive-rebase-clean-up-your-commit-history/
1. existe a primeira edição de um livro do scott chacon sobre o git que foi traduzido pelo Eric Douglas, você pode baixar de graça ou dar uns trocados pra ele: https://leanpub.com/pro-git
1. use alias do proprio git ou do bash, configure assim: 

## tattuagens

half life (lambda, g man)
sandman 
berserk (cao, marca)
vagabond
dark souls
programacao (so, )

##

resetar todos os arquivo como era antes: git reset --hard HEAD
resetar um arquivo: git checkout HEAD -- src/arquivo.txt
mudancas entre um commit e outro: git diff 236aed5..a8ace786
mudancas entre um commit e outro em um arquivo: git diff 236aed5..a8ace786 -- src/arquivo.txt
mudancas entre o commit anterior e as mudancas atuais: git diff --stage
fez o commit e quer reverter mas sem perder: git reset --soft HEAD~1
deletou uma branch sem querer: gir reflog, git reset @HEAD{1}
tirar os arquivos untracked: git clean -f
procurar commit que tenha certa mensagem: git log --all --grep='alguma mensagem'
log resumido e curto: git log --oneline


-- tag

git tag -a v1.0.0 -m "Nova tag"
git tag -n
git tag -n5
git tag -d v1.0.0

git show v1.0.0

git push --tag

-- fetch
git fetch 

git fetch origin main
git diff main origin/main
git merge origin/main

//caso queira ver o codigo no editor
git checkout origin/main
git checkout main

--pull
git pull origin main

--diff
em relacao ao branch
em relacao ao commit
em relacao ao ultimo commit

--log


## Resumo comando uteis

- `git add -i`
- `git add -p`
- `git rebase -i <commit-head>`
- `git commit '' --amend`
- `git reset <commit-hash-head>`
- `git stash`
- `git reflog`
- `git restore`

## Iniciando

- `git init`: inicia repositorio local
- `git config --global usar.name ""`: configura o nome no git
- `git config --global usar.email ""`: configura o email no git
- `git config user.name`: mostra o name configurado
- `git config user.email`: mostra o email configurado
- `git add .`
- `git commit -m ""`
- `git remote add origin https://www.github.com/username/repository.git`
- `git push -u origin main`

## Remote

git remote add <alias> <url>
git remote -v
git remote remove <alias>

## Config

git config --list
git config --system --edit: edita as configs do git pra todos os usuarios
git config --global --edit: edita as configs do git pro usuario que esta logado
git config --local --edit: edita as configs do git pro projeto

git config --local --edit core.editor nvim: configura o vscode como editor padrao

./.gitconfig

```.git
[user]
	name = Felippe Deiró
	email = sergiofelippe.deiro@gmail.com
[alias]
	s = !git status -s
	c = !git add --all && git commit -m
	l = !git log --pretty=format:'%C(blue)%h %C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
```

## Pull e Fetch

git pull --rebase: quando tiver conflitos, as suas modificações vira depois do commit conflitantes, o que evita quebrar a branch de todos, pois não reescreve o historico dos commits

## Restore, Rm, Clear

git restore: tira os arquivos da staged

git clean: tira os arquivos do untracked
git clean -n
git clean -f
git clean -d

git rm: tira os arquivos do tracked

## Diff

- de commit
	- git diff 
git diff
git diff --staged
git diff <branch1> <branch2>
git diff arquivo.js

## Checkout

git checkout -b <branch>: cria branch e muda pra ela
git checkout <branch>: muda pra branch
git checkout <commit>: muda pro commit
git checkout <arquivo>: muda pro arquivo na ultima branch, descarta todas as alterações feitas
git checkout add -t <remote-branch> -f origin <repo-url>: clena uma branch remota especifica

## Branch

git branch: lista branches
git branch <branch>: cria branch
git branch -d <branch>: deleta
git branch -a: mostra as branches locais e remotas
git branch -m <old-branch> <new-branch>: renomeia a branch

## Add

- `git add -i`: quando há muitos arquivos na area de staged e quer fazer alguma operação em cima dele, como tirar da area de staged.
- `git add -p`: um arquivo tem várias modificações, as uma parte da modificação quer que vá pra um commit e outra parte vá pra outro. -p quebra o add em vários pequenos add.

## Commit

### --amend (corrigindo mensagem do commit)

```sh
git commit -m 'initial commit'
git commit -m 'padoniza o código'
git commit -m 'adiciona pacote no package.json'
git commit -m 'adcionando arquivos'
# corrige a mensagem do ultimo commit
git commit --amend -m 'adicionando arquivos'
```

### --amend (corrigindo arquivos do commit)

```sh
# altera o html
git add index.html
git commit --amend
```

### --amend --no-edit (edita adicionando arquivos, mas sem editar a mensagem)

```sh
# altera o html
git add index.html
git commit --amend --no-edit
```

## Log, Shortlog, Show

git log
git log --oneline
git log --oneline --graph --decorate
git log --oneline <branch>
git log --oneline=pretty

pode usar --pretty=format:"" ou --format=""

git log --pretty=format:'%C(blue)%h %C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
git log --pretty=format:"%C(white)%h %C(green)%ad %C(auto)%s" --date=format:"%d/%m/%y %T"

caso queira formatar a data: https://linux.die.net/man/3/strftime

git shortlog

git show <commit>

## HEAD

HEAD
HEAD^ ou HEAD~1
HEAD^^ ou HEAD~2
HEAD~3

## Revertendo (add, commit e push)

### add

-  `git add --staged <arquivo-diretorio>`: tira da area de staged
-  `git checkout <arquivo-diretorio>`: volta o arquivo como era no ultimo commit

### commit

-  `git reset [--soft, --hard] <commit-hash-head>`: reverte o commit, alterando o histórico do projeto
   -  ex: `git reset --soft HEAD~1`
   -  **--soft**: reverte o commit.
   -  **--mixed** (padrão): reverte o commit e o add.
   -  **--hard**: reverte o commit, o add e as alterações no arquivo.
-  `git revert <commit-hash-head>`: reverte o commit, criando um novo commit que anula
   -  ex: `git revert HEAD^^`

### push

-  `git revert <commit-hash-head>`: depois da um push, sobe pro remoto um commit que anula outros.
-  `git push -f`: quando há commits no remote que não tem no local, tem que fazer um pull. Esse comando força uma alteração de reversão no remote.
- git push -d develop

## Tag

1 - 276ddaf d7ae0333ad3bd1ea5863f2241beafac07
2 - f7d19bc bb98440140c5c368ce63dc8c5350ad07a

git tag -a v2.0 f7d19bc -m "Carrinho, historico e serverless"
git tag -a v1.0 276ddaf -m "Basico" (cria tag apontando p um commit especifico do checksum)

git log -g --pretty=oneline (lista os ids dos commits)

git tag -d v1.0 (deleta a tag)
git tag -a v3.0 -m "Nova!" (cria tag apontando pro ultimo commit)
git push origin --tags

## Revert vs Reset

git revert <hash-commit>

git reset 
git reset --soft
git reset --hard

## Rebase vs Merge

[video](https://www.youtube.com/watch?v=Lxm5EA2WTMg)

- rebase: reescreve o histórico, deixando ele mais linear, sem ramificacoes.
- merge: cria um commit unindo as branches.

**Não fazer rebase quando o push já foi dado e tem pessoas já trabalhando. Ele deve ser feito só quando você tem o código e mais ninguém.**

## Rebase (Squash e Pick)

Rebase vs Merge

-  `git checkout main`
-  `git rebase -i <commit-hash-head>`
   -  ex: `git rebase -i HEAD~10`
   -  **-i**: abre o modo interativo do terminal

-  merge: não modifica o histórico.
-  rebase: modifica o histórico. cria novos commits baseado nos do develop, coloca os commits antes da master,

-  **cenário de uso**: há commits adicionando uma feature nova, depois é feito commits que padroniza o código, refetora o código. É mais vantajoso ter somente commits relacionado a adição de uma feature do que ter também commits de refatoração, que não é relevante pro projeto.

Exemplo:

```bash
git commit -m 'Initial commit' # HEAD~3
git commit -m 'Add type hint' # HEAD~2 2b84f30
git commit -m 'Fix parameters' # HEAD~1 118ddbe
git commit -m 'Add function say_hello' # HEAD a26fa6b
git rebase -i HEAD~3 # modo interativo apresentado abaixo
git push -f origin develop
```

```bash
# modo interativo
p a26fa6b Add function say_hello # vai querer o commit
s 118ddbe Fix parameters # não quer o commit, mas quer o que foi feito nele
s 2b84f30 Add type hint # não quer o commit, mas quer o que foi feito nele

# p, pick = escolhe o commit que vai ser usado
# s, squash = o foi feito no commit não vai ser descartado, ele será comprimido em um só commit
```

## Stash

- `git stash`: guarda o código numa area especial, sem fazer commit
- `git stash apply`: busca o que foi guardado
- `git stash save "descrição do stash"`: da uma descrição pro stash
- `git stash list`: lista os stash feitos
- `git stash apply stash@{0}`: busca um stash especifico na lista de stash

- **Cenário de uso**: não fez commit da modificação do código, porque não está pronto, mas precisa mostrar pra alguem o projeto funcionando. Então faz um stash (volta automaticamento ao ultimo commit), mostra o projeto funcionando e depois remonta o código guardado na area de stash.

```bash
git stash # guarda o código não commitado
# ...
# faz o que tiver que fazer...
# ...
git stash apply # abre o codigo guardado
```

## Cherry pick

- `git cherry-pick <commit-hash>`: pegar um commit de outra branch e colocar na atual, sem remover da outra branch
   - ex: `git cherry-pick a26fa6b`

- **Cenário de uso**: fez um commit na branch errada, troca de branch, faz um cherry pick no commit e da um revert na branch errada pra limpar a sujeira.

## Reflog

- guarda o histórico de operações do git.
- reverter coisas perdidas como no caso de `git reset --hard` e `git rebase`, caso não tenha copia. Se tiver trabalhando num repositorio remoto e sempre sincronizando, não será tão ruim.

```sh
git reflog # mostra o histórico de operações
git reset HEAD@{1} # volta no momento da operação
git restore . # volta tudo que foi feito
```

ou

```sh
git reflog # mostra o histórico de operações
git cherry-pick a26fa6b
```

## Bisect

qual commit que incluiu bug

```sh
git bisect start

git bisect bad # atualmente esta no commit com bug

git checkout 8529499 # commit que não tem o bug
git bisect good

# git vai dar checkout automaticamente pra um commit
# faz um teste com a aplicação (rodar o postman, test, ...)
git bisect bad # depois dos testes, o commit ainda tem o bug

# git envia pra outro commit
# faz os testes
git bisect good

# mesma coisa...
git bisect bad

# mesma coisa ...
git bisect good

# mostra o commit que inseriu o bug
# commit: 0d14b72

git show 0d14b72 # ver o que foi feito no commit

git checkout main
git revert 0d14b72 # revert vai criar um commit que anula o outro
```