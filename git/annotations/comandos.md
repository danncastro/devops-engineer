# **Comandos básicos**

*Permite clonar um repositório remoto na maquina de forma local*
~~~bash
git clone
~~~

---
*inicializa um repositório no diretório em que o comando for executado. A partir deste comando, o Git poderá gerenciar as modificações realizadas nos arquivos.*
~~~bash
git init 
~~~

*Com este comando nós criamos um repositório que não terá a working tree, ou seja, não conterá uma cópia dos nossos arquivos. Como o repositório servirá apenas como servidor, para que outros membros da equipe sincronizem seus trabalhos, poupamos espaço de armazenamento desta forma.*
~~~bash
git init --bare
~~~

---
*Informa todas as branchs existente e a qual está conectado atualmente*
~~~bash
git branch
~~~
*Cria uma nova branch mas sem se conectar a ela automaticamente*
~~~bash
git branch 'nome-branch' 
~~~
*Deleta uma branch existente*
~~~bash
git branch -D 'nome-branch'
~~~

---
*Conecta nas branchs*
~~~bash
git switch 'nome-branch'
~~~
---
*Conecta a uma branch existente*
~~~bash
git checkout nome-branch
~~~
*Cria uma nova branch e muda automaticamente para ela*
~~~bash
git checkout -b nome-branch
~~~
*Retorna o arquivo commitado ao estado anterior*
~~~bash
git checkout HEAD -- 'arquivo'
~~~

---
*Retornar o status atual dos diretórios, assim como qual **“branch”** ele está ou se está com algum **“commit”** pendente de execução*
~~~bash
git status
~~~

---
*Informa quais arquivo foram alterados*
~~~bash
git diff --name-only
~~~
*Valida quais alterações foram feitas*
~~~bash
git diff “arquivo” - 
~~~

---
*Adiciona os aquivos ainda pendentes no "working dir" ("repositório local") para um repositório remoto.*
~~~bash
git add
~~~

*Adiciona todos arquivos pendentes no repositorio local atual*
~~~bash
git add *
~~~

*Adiciona todos arquivos **untracked** na **branch** atual*
~~~bash
git add -A 
~~~

*Adiciona todos arquivos **untracked** presente no **repositorio** local*
~~~bash
git add .
~~~

---
*Comando responsavél por commitar alterações feitas no código*
~~~bash
git commit
~~~

*Como boas, praticas adiciona um comentario*
~~~bash
git commit -m "comentário"
~~~

---
*Junta a branch informada a ramificação principal*
~~~bash
git merge nome-branch
~~~

---
*Verifica o histórico de alterações, as mensagens de commits, o nome do autor daquele commit e outras informações sobre o projeto*:

https://devhints.io/git-log

~~~bash
git log
~~~

*visualizar todos os commits, um em cada linha*
~~~bash
git log --oneline
~~~

*Mostra mais informações das alterações do commit*
~~~bash
git log -p
~~~

*Pesquisar as informações do autor daquele commit*
~~~bash
git log --author="user_name"
~~~

*Pesquisa informações por data [Do último primeiro ao último dia dos meses informados*
~~~bash
git log --since=1.month.ago --until=1.day.ago
~~~

~~~bash
git log --pretty
~~~

*Verifica as versões incluidas ao codigo*
~~~bash	
git reflog
~~~

---
*Envia os arquivos(logs, modificações, tags) para o **repositório remoto***
~~~bash
git push
~~~

*Adiciona uma branch ao repositorio remoto*
~~~bash
git push --u origin "nome da branch"
~~~

*Remove a branch no repositorio remoto*
~~~bash
git push origin :“nome da branch”
~~~

---
*Atualiza os conteúdos remotos para os repositórios locais*
~~~bash
git pull
~~~

---
*Volta ao estado anterior antes de commitar*
~~~bash
git reset --soft "id commit"
~~~

*Volta a versão anterior mas sem as alteraçõe feitas antes commit*
~~~bash
git reset --mixed "id commit"
~~~

*Navega entre as versões podendo voltar a um commit anterior com ID*
~~~bash
git reset --hard "id commit"
~~~

---
*Volta o commit a versão anterior, sem perder as informações efetuadas*
~~~bash
git revert "id commit"
~~~

# **Comandos de controle de arquivos**
~~~bash
git rm --cached
~~~

~~~bash
git show "hash"
~~~

~~~bash
git tag
~~~

~~~bash
git stash
~~~

~~~bash
git stash apply
~~~

~~~bash
git stash list
~~~

~~~bash
git stash clear
~~~
