# **Sobre o GIT**
### **O que é o git**
 Git é um sistema de **controle de versão** de arquivos. Através deles podemos desenvolver projetos na qual diversas pessoas podem contribuir simultaneamente no mesmo, editando e criando novos arquivos e permitindo que os mesmos possam existir sem o risco de suas alterações serem sobrescritas.

---
### **HEAD**
Estado atual do nosso código, ou seja, onde o Git os colocou

---
### **Working dir**
Repositorio local

---
### **Working tree**
Local onde os arquivos realmente estão sendo armazenados e editados

---
### **Index (stage)**
Local onde o Git armazena o que será commitado, ou seja, o local entre a working tree e o repositório Git em si.

---
### **Stach**
Armazenar temporariamente as alterações antes de executar um commit.

---
### **Branch** 
Versões diferentes, utilizado para commitar os codigos, podendo fazer alterações em diversas branchs diferentes, assim como também é possível definir uma "branch" principal, por padrão é a "main"

---
### **Commit** 
Basicamente é quando ocorre mudanças no sistema, ou seja tudo que estiver fazendo de alterações no ***git*** é chamado de ***commit***, e como boas praticas, se utiliza um comentário com a opção ***-m*** para explicar quais foram as alterações aplicadas neste commit.
Casa seja gerado um commit no repositório local com nickname e email diferentes os commits apareceram com as informações diferentes no ***GitHub*** 

---
### **Fork** 
Utilizado para contribuir com projetos de outras pessoas, fork faz uma copía do projeto no repositorio remoto para efetuar alterações e correções de possivéis bugs

---
### **Hotfix**

---
### **Merge**
Junta os trabalhos e gera um merge commit

---
### **Rebase**
Aplica commits de outra branch na branch atual

---
### **Checkout**
O git checkout, serve para navegarmos em estados do repositório, seja por meio de branches ou desfazendo modificações no arquivo, Com o **git checkout** nós desfazemos uma alteração que ainda não foi adicionada ao **index** ou **stage**, ou seja, antes do git add, também é possivel navegar em estados anteriores de um commit.

---
### **Diff**
É possível visualizar quais alterações foram realizadas em cada arquivo com o comando **git diff**, comparar as alterações entre duas branches com git diff **branch1**.>.**branch2** e as alterações não commitadas no codigo (com git add), comparar as alterações feitas entre um commit e outro, através do comando **git diff commit1**.>.**commit2**;. O sinal de subtração (-) antes da linha indica que ela não está mais presente no arquivo. Já o sinal de adição (+) mostra que é uma linha nova. Alterações são representadas por uma remoção e uma adição de linha.

---
### **Tag**
O Git nos possibilita salvar marcos da nossa aplicação, como por exemplo, lançamento de versões, através do **git tag**; isso nos gera uma **Release**, ou seja, conseguimos baixar um arquivo compactado com o nosso código neste ponto e o GitHub nos dá a possibilidade de baixar um arquivo compactado contendo o código no estado em que a tag foi gerada. O comando **git tag -a** é utilizado para gerar uma nova tag; As Releases do GitHub, que são geradas para cada tag do Git criada em nosso repositório.

---
### **Blobs** 
Objeto que contém meta dados, dentro dos blobs contém:
 
- ***tipo do objeto*** 
- ***tamanho da string(arquivo)*** 

A barra contraria com **0 (\0)**, e o conteúdo armazenado no blob.

***Exemplo:***
~~~bash
echo 'conteudo' | git hash-object --stdin > fc31e91b26cf85a55e072476de7f263c89260eb1
	
echo -e 'blob 9\0conteudo' | openssl sha1 > fc31e91b26cf85a55e072476de7f263c89260eb1
~~~

#### **Trees** 
Armazena um conjunto de blobs
~~~
commit >> tree >> blobs.
~~~
Quando alterado um arquivo altera toda arvore do arquivo

---
### **Ciclo de vida dos status dos arquivos**

#### ***Untracked***
~~~
Ainda não identificado pelo git
~~~

#### ***Unmodified***
~~~
Não houve mudanças no arquivo
~~~

#### ***Modified***
~~~
Editado mas ainda não commitado
~~~

#### ***Staged***
~~~
Pronto para ser commitado
~~~

---
### **Git ignore**
https://git-scm.com/docs/gitignore

---
### **Issues**
As Issues ajudam a reportar e controlar os problemas e bugs de um projeto. Além disso, com o tempo, passaram a perceber que havia mais possibilidades nas issues, e elas foram utilizadas para sugestão de melhorias no projeto e pedidos de novas funcionalidades. Por fim, ótimos exemplos de usos das issues no GitHub são das comunidades PHPSP e PHPRio, que as utilizam para organizar os palestrantes e sugestões de palestras.

---
### **Cherry-pick**
Se uma implementação é necessária em sua branch e já foi feita em outra branch, pode fazer sentido trazer um commit específico

---
### **Bisect**

---
### **Blame**
Podemos ver quem é o responsável por cada linha no código.

---
### **GIT Flow**

---
### **Hooks**

---
### **Ferramentas para gerenciamento**
- Git Cola
- Github Desktop
- GitKraken

---
### **Sistema distribuido**
Sistema que possui multiplas cópias de si mesmo em diferentes locais.