Agora que sabemos o que é um pipeline, vamos criar um arquivo na raiz de nosso projeto chamado .gitlab-ci.yml. É neste arquivo que configuramos todo o processo de CI/CD.

Então, vamos criar no arquivo gitlab-ci a primeira tarefa da pipeline. Um detalhe que temos que nos atentar é que os arquivos com extensão .yml são organizados com indentação de 2 espaços, ou seja, caso não respeitemos essa regra, o processo inteiro para.
~~~bash
job1:
  script:
  - echo "hello world"
~~~
Já vamos versioná-lo em nosso projeto. Para isso vamos dar um "commit" e um "push" desse arquivo. Abra um terminal e navegue até a pasta do seu projeto e em seguida digite:
~~~bash
git add --all
~~~
Para adicionar todos os arquivos modificados no projeto:
~~~bash
git commit -m "adicionando pipeline"
~~~
Para registrar uma mensagem e criar um hash de commit, marcando sua alteração
E por fim vamos dar um Push:
~~~bash
git push gitlab master
~~~
Após o push do arquivo gitlab-ci.yml, ao entrarmos novamente no menu CI/CD do gitlab, podemos verificar que o pipeline foi criado, e que já temos um "job" iniciado automaticamente, que possivelmente irá funcionar com sucesso. Agora, por que esse pipeline foi executado?
Bom, como criamos o arquivo gitlab-ci.yml, na raiz do projeto, toda vez em que realizarmos qualquer alteração e versionamos com gitlab, automaticamente o pipeline será executado.

##
Temos na empresa um projeto no qual precisamos automatizar os processos de build, testes e deploy. Para isso, vamos versioná-lo no gitlab, pois além de controlar o versionamento, podemos criar nossa pipeline e automatizar esses processos.

Vou compartilhar com vocês, o projeto que pretendemos automatizar, juntamente com os exercícios desta aula.

Baixe o projeto nesse link e em seguida o descompacte em uma área do seu computador.

Abra um terminal na pasta raiz do projeto e execute os comandos para iniciar o versionamento.
~~~bash
git init
~~~
Caso seu projeto já esteja versionado em outro repositório git, não há necessidade de rodar esse comando acima.

Em seguida, vamos apontar para o repositório que criamos na primeira aula com o comando:
~~~bash
git remote add gitlab https://gitlab.com/jnlucas/meusistema.git
~~~
Com o repositório apontado, vamos agora dar um commit e push para o gitlab:
~~~bash
git add --all
git commit -m "iniciando o versionamento"
~~~
Por fim, vamos dar um push para subir o código fonte para o gitlab:
~~~bash
git push gitlab master 
~~~
Ao realizar o push, receberemos uma mensagem de "rejected", pois nossa branch master está protegida. Como a ideia é mostrar o processo de CI/CD, vamos desbloquear a branch master. Dessa forma não precisaremos ficar criando "branches" para nosso processo.

Para isso vamos acessar as configurações do projeto no menu settings -> repository , vamos até a sessão protected branches, e em seguida vamos desproteger a branch master

Com a branch desprotegida, podemos realizar o push e versionar nosso código.
~~~bash
git push gitlab master -f
~~~
Notem que estou utilizando o parâmetro "-f" no comando de "push", dessa forma o que estiver na master será apagado e dará lugar a este novo código.

##
Antes de implementarmos as melhorias em nosso processo, precisamos entender como funciona o arquivo gitlab-ci. Basicamente, ele é dividido em três etapas que chamamos de "stages", sendo a primeira reservada para "build", a segunda para "tests" e por fim "deploy", Em um pipeline, não precisamos implementar as três etapas, podemos implementar apenas as etapas que julgarmos necessário.

Pensando nisso, podemos certamente otimizar passo a passo nosso processo.

Em uma empresa de desenvolvimento de software, quem nunca ouviu o termo "na minha máquina funciona"? Pois é, estamos com o mesmo problema em nossa empresa, muito dos desenvolvedores alegam que as features desenvolvidas funciona em suas máquinas, mas ao subir para produção alguma coisa dá errado. Então esse será nosso primeiro desafio no processo de CI. Faremos então, com que o ambiente de produção se assemelhe ao ambiente de desenvolvimento. Sabemos que uma das maneiras de garantir tal semelhança é utilizar docker, criando uma imagem idêntica a de produção e subir um container com as configurações desejadas. Vamos então criar um Dockerfile para nossa aplicação, e nele vamos colocar tudo o que nossa imagem precisa ter. Na raiz do nosso projeto vamos criar o arquivo Dockerfile com o seguinte conteúdo:
~~~bash
FROM python:3.6
#Copiando os arquivos do projeto para o diretorio usr/src/app
COPY . /usr/src/app
#Definindo o diretorio onde o CMD será executado e copiando o arquivo de requerimentos
WORKDIR /usr/src/app
COPY requirements.txt ./
# Instalando os requerimentos com o PIP
RUN pip install --no-cache-dir -r requirements.txt
# Expondo a porta da APP
EXPOSE 8000
# Executando o comando para subir a aplicacao
CMD ["gunicorn", "to_do.wsgi:application", "--bind", "0.0.0.0:8000", "--workers", "3"]
~~~

Como nosso projeto está desenvolvido em python, criaremos uma imagem docker para atender nossa necessidade.

Com o Dockerfile criado, vamos adicionar à nossa pipeline uma imagem docker que precisaremos em todos os passos da pipeline; pois build, teste e deploy, devem ser feitos com base no ambiente de produção, evitando assim a frase "na minha máquina funciona".

Como a criação e definição da imagem é um pré requisito para nosso processo, vamos adicionar à nossa pipeline, um "job" que será responsável por realizar o build da imagem que vamos utilizar em nosso projeto. Para isso vamos editar o arquivo .gitlab-ci com o seguinte conteúdo:
~~~bash
build-docker:
  stage: build
  script:
  - docker build -t minha-imagem .
~~~

Em seguida vamos dar um push no gitlab, para dar inicio a pipeline
~~~bash
git add --all
git commit -m “realizando build da imagem”
git push gitlab master
~~~

Em seguida vamos dar um push no gitlab, para dar inicio a pipeline
~~~bash
git add --all
git commit -m “realizando build da imagem”
git push gitlab master
~~~

Ao realizarmos um push da alteração que fizemos no arquivo gitlab-ci, o pipeline será iniciado e teremos uma falha no pipeline, pois o comando "docker" não é reconhecido pela imagem que estamos utilizando.

Para nos prevenir desse problema, vamos com a palavra-chave "image" definir uma imagem para que nosso pipeline possa utilizar comandos docker, ficando assim:
~~~bash
image: docker:stable

build-docker:
  stage: build
  script:
  - docker build -t minha-imagem .

~~~

Em seguida vamos dar novamente um push no gitlab:
~~~bash
git add --all
git commit -m “realizando build da imagem”
git push gitlab master
~~~

Realizando novamente um push de nosso projeto, veremos que o pipeline falhou mais uma vez. Isso porque agora o serviço docker está sem permissão de uso, e para resolver isso vamos conhecer mais uma palavra-chave: a "services". A palavra-chave services define uma imagem do Docker que é executada durante uma tarefa vinculada à imagem do Docker que a palavra-chave image define. Isso permite que você acesse a imagem do serviço durante o tempo de criação

Então vamos no arquivo .gitlab-ci.yml e vamos adicionar o seguinte conteúdo:
~~~bash
image: docker:stable

services:
  - docker:dind 

before_script:
  - docker info

build-docker:
  stage: build
  script:
  - echo “hello world”
~~~

Adicionamos também ao pipeline a palavra reservada before_script, que se encarrega de executar qualquer script definido neste bloco antes da execução de cada job no pipeline.

Vamos então novamente realizar um push:
~~~bash
git add --all
git commit -m “realizando build da imagem”
git push gitlab master
~~~

##
Bom pessoal, agora vamos configurar o build do nosso projeto, os seja, vamos acabar com aquele papo de "na minha máquina funciona”! Como no passo anterior fizemos um build de uma imagem igual a de produção, vamos configurar tudo o que precisamos para que nosso projeto funcione, como conexão a banco de dados, migrations etc.

Até esse momento, toda vez em que fazemos um push no git, o gitlab está disparando os passos da CI utilizando uma imagem própria. Até então não temos controle do que está instalado nela, ou se ela tem todos os pacotes que precisamos para realizarmos os testes. Então vamos configurar e disponibilizar para o gitlab nosso próprio executor com tudo o que precisamos. Para isso, precisaremos utilizar o gitlab-runner, então vamos deixar o trabalho de build e teste para esse runner e assim que tiver terminado, ele envia os dados para o gitlab.

Para isso precisaremos subir em nossa máquina um container com o gitlab-runner. Vamos então fazer um pull da imagem do gitlab-runner e em seguida disponibilizar um container dessa imagem.
~~~bash
docker pull gitlab/gitlab-runner:latest
~~~

Com a imagem disponível em nossa máquina vamos subir um container e deixar o serviço de pé
~~~bash
docker run -d --name gitlab-runner --restart always -v /Users/Shared/gitlab-runner/config:/etc/gitlab-runner -v /var/run/docker.sock:/var/run/docker.sock gitlab/gitlab-runner:latest
~~~

Um detalhe nesse comando são com os volumes que estou montando, em máquinas linux utilize o diretório "/src" pois o diretório "Users/Shared" não existe. Caso você esteja trabalhando em máquinas linux, quando montamos um volume temos que criar no diretório /src, pois o diretório Users/shared não existe

Se rodarmos em nosso terminal um "docker ps", podemos verificar que agora temos um container gitlab-runner de pé, pronto para uso.

Agora que temos um container gitlab-runner rodando em nossa máquina, vamos configurá-lo e sincronizá-lo com o gitlab. Com isso feito, podemos garantir que o passo que precisarmos dar depois terá como base um ambiente semelhante ao de produção.

Para isso precisamos registrar nosso runner no gitlab. Vamos acessar no gitlab a área responsável pelos "runners" no menu settings-> CI/CD

Clicando no menu Runners, podemos ver que temos runners compartilhados, e runners específicos. Para criarmos nosso próprio runner, vamos precisar copiar uma chave de segurança que está disponível no menu:

Com a chave copiada, vamos agora sincronizar nosso gitlab runner com o gitlab. Para isso, vamos entrar pelo terminal no container do gitlab-runner e vamos registrar o runner no gitlab. Digite então no terminal o comando para entrar no container:
~~~bash
docker exec -it gitlab-runner bash
~~~

Após digitar esse comando, estamos dentro do container gitlab-runner. Agora precisamos registrar um serviço para que os passos do gitlab-ci sejam executados pelo nosso runner. Para isso digite no terminal:
~~~bash
gitlab-runner register
~~~

Ao digitar o comando de register, você precisará informar o endereço do gitlab que está utilizando:
~~~bash
https://gitlab.com/
~~~
Em seguida, precisará digitar a chave de segurança que copiou do gitlab.

Com a chave informada, vamos dar um nome para esse runner: vou chamá-lo de "meu-runner". Em seguida, podemos adicionar tags ao runner que será utilizada para vincular os jobs a esse executor, então vamos chamá-lo de “runner-build ” e dar um enter para próxima etapa. Precisamos agora informar ao registro que tipo de runner queremos registrar. Aqui podemos fazer runners do tipo kubernetes, parallels, shell, ssh, virtualbox, docker, docker-ssh, docker+machine e docker-ssh+machine, mas para nosso cenário vamos registrar um do tipo docker. Para isso, basta digitar docker no terminal e em seguida informar qual a imagem que pretendemos utilizar.

Como criamos uma imagem docker igual ao ambiente de produção, no passo de build da imagem vamos utilizá la em nosso runner. Dessa forma garantimos que o executor tenha as mesmas configurações de produção. Para isso informe o nome da imagem que criamos "jnlucas/minha-imagem:latest"

Pronto, nosso runner está configurado!

##
Bom pessoal, vamos agora configurar os testes de nossa aplicação, pois um dos problemas que temos no setor de desenvolvimento são os códigos que estão subindo para produção sem antes passar pelos testes, devido aos prazos muito curtos. Nossos desenvolvedores sempre queimam a etapa de testes e isso gera um enorme problema em produção, pois por várias vezes, temos trechos que não testamos ou não dimensionamos corretamente o impacto das melhorias implantadas em produção.

Para realizarmos os testes da aplicação, o ideal é que eles sejam rodados em um ambiente semelhante ao de produção. Como no passo anterior geramos uma imagem semelhante a de produção e a colocamos no docker hub, vamos utilizá-la também no passo de testes.

Para isso vamos adicionar um novo passo com o stage de testes:
~~~bash
test-project:
  image: jnlucas/minha-imagem:latest
  stage: test
  services:
  - docker:dind
  dependencies:
  - build-project
  tags:
  - executor-tarefas
  script:
  - python -m unittest setUp
~~~

Para este passo, notem que estamos utilizando o mesmo runner e a mesma imagem de produção que criamos para o build, assim garantimos um ambiente muito próximo ao ambiente de produção. Como nosso projeto tem apenas um teste, adicionei a chamada dele na tag script. Dessa forma, caso o teste passe, nosso pipeline terá mais um passo com sucesso. Vamos então dar mais um push em nosso projeto e veremos o que acontece em nossa pipeline.
~~~bash
git add --all
git commit -m “adicionando job de testes unitários”
git push gitlab master
~~~
Notem que aparecerá uma nova tarefa no pipeline, e ela será executada com sucesso somente após a tarefa de build ser concluída também com sucesso.

##
Com os testes unitários sendo executados com sucesso, precisamos garantir a publicação do software que estamos desenvolvendo em um ambiente externo, para que o cliente faça sua homologação. Para isso criamos então uma tarefa dentro da pipeline que garanta a publicação. Porém para que essa tarefa funcione, precisamos garantir o acesso entre o runner e o servidor de homologação. Para isso vamos nos conectar via ssh no gitlab-runner e em seguida gerar o par de chaves com o comando ssh-keygen:
~~~bash
docker exec -it gitlab-runner bash
~~~

Agora, dentro do container do gitlab-runner, precisamos alterar o usuário, pois o usuário que vai executar a tarefa de deploy é o usuário do gitlab-runner. Vamos então alterar o usuário com o comando
~~~bash
su gitlab-runner
~~~

Como o usuário anterior era o root, você não precisará informar a senha. Agora vamos criar o par de chaves com o comando:
~~~bash
ssh-keygen
~~~

Ao executar esse comando dentro do terminal, ele solicitará o local onde queremos guardar essa chave. Geralmente a chave é guardada em um diretório oculto dentro da pasta raiz do usuário, vamos então manter dessa forma, dando “enter” até que uma mensagem de sucesso apareça no terminal.

Com a chave criada, vamos adicionar todo o conteúdo da chave pública dentro do arquivo authorized_keys do servidor remoto. Então digite no terminal:
~~~bash
cat ~/.ssh/id_rsa.pub | ssh usuarioremoto@ipdamaquina "cat >>  ~/.ssh/authorized_keys"
~~~
Com o par de chaves criado e compartilhado já garantimos acesso do runner para realizar os deploys na máquina de homologação.

##
Precisamos garantir que todos os envolvidos no projeto sejam informados sobre o andamento das entregas. Vamos então adicionar ao nosso pipeline um job que notificará a todos sempre que tivermos um problema, e um outro job para notificar a todos sempre que uma pipeline se encerra com sucesso, o que significa que temos uma entrega para homologar. Para isso, vamos no arquivo .gitlab-ci.yml e vamos adicionar mais um stage, vamos colocar o stage de notificações:
~~~bash
image: docker:stable

stages:
- pre-build
- build
- test
- deploy 
- notificacao
~~~

Agora que temos o stage de notificação, vamos criar 2 jobs no final da pipeline, um para quando tudo der certo, e outro para quando tudo der errado. Então no final do arquivo digite:
~~~bash
notificacao-sucesso:
  stage: notificacao
  tags:
  - executor-deploy
  script:
  - echo “tudo deu certo”

notificacao-falhas:
  stage: notificacao
  tags:
  - executor-deploy
  script:
  - echo “tudo deu errado”
~~~

Notem que os dois jobs, tanto o notificacao-sucesso, quanto o notificacao-falhas, estão com o mesmo stage “notificacao”. Dessa forma, a tarefa de notificação será executada em paralelo, sem que uma dependa da outra. Na verdade, o que precisamos é que a tarefa de sucesso seja executada quando tudo der certo e a tarefa de falha quando tudo der errado. Então vamos adicionar o atributo “when” para as duas tarefas, dessa forma conseguiremos controlar o momento em que deverão ser iniciadas. Para a tarefa “notificacao-sucesso” vamos adicionar o “when: on_success”:
~~~bash
notificacao-sucesso:
  stage: notificacao
  when: on_success
  tags:
  - executor-deploy
  script:
  - echo “tudo deu certo”
~~~

E para a tarefa de “notificacao-falhas” vamos adicionar o “when: on_failure”:
~~~bash
notificacao-sucesso:
  stage: notificacao
  when: on_failure
  tags:
  - executor-deploy
  script:
  - echo “tudo deu errado”
~~~

Com as tarefas criadas vamos dar um commit e um push no gitlab e veremos nossa pipeline sendo executada novamente. Caso tudo ocorra sem problemas, a tarefa “notificacao-sucesso” será processada; caso aconteça alguma falha, a tarefa “notificacao-falha” será executada.
~~~bash
git add --all
git commit -m ‘adicionando notificações de falhas e de sucesso’
git push gitlab master
~~~