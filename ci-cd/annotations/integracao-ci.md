Devido a sua importância, a Integração Contínua é um tópico bastante discutido na literatura e na web. Seguem algumas fontes que usamos para criar este curso:

Livro: Continuous Integration, de Paul M. Duvall
Artigo da ThoughtWorks: Continuous integration (CI)
Artigo do Martin Fowler: Continuous Delivery (CD)
Série de artigos da Caelum:
Branches e integração contínua: o problema de feature branches
Integração Contínua - Builds rápidos com Grids e paralelismo
Integração contínua: deploys e aprovações sem dor de cabeça para o cliente
Artigo no CodeBetter: Check in Dance

Nas alternativas abaixo, quais representam benefícios do uso da prática de Integração Contínua?
As falhas são detectadas mais rapidamente
Alternativa correta! Ao integrar o código o tempo todo, diminui a chance de não percebermos uma falha, já que menos código foi integrado de uma vez só.

Integrações mais simples
Alternativa correta! Menos código a integrar simplifica muito. Lembrando que não deve ter um evento especial para a integração e sim deve ser uma prática sólida e diária.


Código sem bugs
Alternativa errada! Bugs podem continuar a aparecer. Para aumentar a qualidade do código, só a integração contínua sozinha não resolve.

Construção mais rápida do software
Alternativa errada! A velocidade do build é importante, mas a integração contínua não influencia nisso.

O que deve ser guardado no repositório?
Código compilado (por exemplo, class files)
Alternativa errada! Esses arquivos são gerados durante o build e podem ser recriados

Scripts de testes
Alternativa correta! Os testes são uma parte essencial da aplicação. Testes também são códigos, e scripts relacionados a eles devem entrar no repositório.

Database Schema
Alternativa correta! Faz parte da aplicação e é preciso para construir e executar o projeto.

O artefato da construção do projeto (por exemplo, JAR, GEM, DLL)
Alternativa errada! Como regra geral, o que você pode construir, não precisa ser comitado.

Dentre as ferramentas abaixo, quais são obrigatórias para começar com integração contínua no seu projeto?

Sistema de controle de versão, como Git ou SVN
Alternativa correta! Precisamos de uma ferramenta, como SVN ou Git, para manter o histórico e facilitar a colaboração entre desenvolvedores. Isso serve para qualquer projeto de software!

Issue Tracker, como Jira
Alternativa errada! Pode fazer todo sentido organizar os bugs, tarefas, etc, em um issue tracker, mas não é obrigatório.

Servidor de integração contínua, como Jenkins
Alternativa errada! Apesar de ter o nome e ser útil para automatizar o build, um servidor de integração contínua (CI Daemon), como Jenkins, não é obrigatório. Usar Jenkins também não significa usar integração contínua! Lembre-se, integração é uma prática e não é uma ferramenta.

Usar GitHub ou GitLab
Alternativa errada! Realmente não importa onde o código é hospedado, pode ser dentro da intranet ou usando algum serviço como github, gitlab ou bitbucket (entre outras possibilidades).

Em comparação ao Mono-Repo, quais são as vantagens do *Multi-repo? Marque todas as alternativas corretas:

Possibilidade de definir permissões de acesso por projeto
Alternativa correta! Já que cada projeto/módulo tem o seu repositório, podemos definir as permissões por projeto!

Clone, commit e build do projeto simples e rápido
Alternativa correta! A base de código é apenas desse projeto/módulo e não do sistema todo. Isso agiliza na hora de usar o código, pensando no clone, importação na IDE, no commit e build do projeto.


Dependências entre projetos são simples de gerenciar
Alternativa errada! Como os projetos/módulos estão separados, precisa ter um cuidado extra para as versões ficarem sincronizadas, pois incompatibilidades não serão percebidas de imediato.

Facilidade de refatorações globais (entre projetos)
Alternativa errada! É justamente o contrário, pois o código está em vários repositórios, ou seja, complica ou impossibilita refatorações globais.

Aprendemos que, principalmente por causa do Git, surgiram vários modelos/estratégias de ramificação.
Em relação à estratégia, quais das alternativas abaixo são verdadeiras?
A estratégia de ramificação precisa ser conhecida por toda equipe
Alternativa correta! Todos e todas devem conhecer bem a estratégia, porque o trabalho no dia-a-dia se baseia nisso.

Os desenvolvedores podem usar os ramos e a estratégia como quiserem e entenderem
Alternativa errada! É justamente o contrário. A estratégia define as regras e o significado de cada ramo.

A estratégia de ramificação define o significado de cada ramo/branch
Alternativa correta! Correto, quais branches existem, duração e sincronização entre eles são definidos pela estratégia.

A estratégia de ramificação é definida para cada workspace do desenvolvedor
Alternativa errada! Deve ser uma única estratégia por projeto!

Você precisa escolher um modelo de ramificação para uma equipe nova. Há duas características que precisam ser seguidas:

As novas funcionalidades devem ser implementadas em uma nova branch
Cada funcionalidade deve ser revisada pela equipe antes de entrar no mainline
Qual modelo de ramificação você sugeria?
GitHub Flow
Alternativa correta! O GitHub Flow é um modelo leve, desde que as features branches sejam de vida curta (poucos dias). Também devemos ter em mente que os pull requests podem ser uma barreira para a integração contínua.

GitLab Flow
Alternativa errada! O GitLab Flow não seria ideal, pois também sugere ramificação para ambientes, como homologação ou produção.

Git Flow
Alternativa errada! O Git Flow, além das feature branches, também define outras branches como develop, hotfix ou release.

Sobre o comando rebase, do Git, quais das alternativas abaixo são verdadeiras?
Elimina o merge commit na integração de duas branches
Alternativa correta! O rebase sincroniza/pega os commits da outra branch e reaplica os novos commits da branch atual. Dessa forma, ele reescreve o histórico da branch atual.

Pode ser usado a partir de qualquer branch
Alternativa errada! Não podemos esquecer a regra de ouro (Golden rule). Não devemos usar o rebase em branches compartilhadas/públicas.

Ajuda a manter o histórico de commits linear
Alternativa correta! Esse é a grande vantagem do rebase. Os commits aparecem como eles fossem executados um após do outro

Ainda ficou com dúvida qual é a diferença entre merge e rebase? Quer saber mais sobre as estratégias específicas do comando merge?

Preparamos uma série de vídeos curtos sobre Git, que abordam com detalhe o assunto:

Git e Github para Sobrevivência (Episódios 02 e 03)
E claro, temos também os cursos da Alura sobre o assunto:

Git e Github: Controle e compartilhe seu código
Git e Github: Estratégias de ramificação, Conflitos e Pull Requests

Seguem alguns links externos das estratégias mencionadas:

https://trunkbaseddevelopment.com/
https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow
https://guides.github.com/introduction/flow/
https://docs.gitlab.com/ee/topics/gitlab_flow.html
https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html

Vimos que existem categorias de testes diferentes. Por exemplo:

Testes de unidade
Testes de integração
Testes funcionais
Entre várias outras... mas categorizar os testes é importante pois:
Existe um desenvolvedor responsável para cada categoria
Alternativa errada! Idealmente, todos os desenvolvedores são responsáveis pelos testes.

Podemos rodar os testes em etapas, com base na categoria
Alternativa correta! Dessa forma, podemos rodar com facilidade primeiro os testes de unidade, depois os de integração, etc. Os testes de unidade são os mais rápidos e devem garantir uma boa cobertura de teste.


Facilita a manutenção dos testes
Alternativa errada! Se é fácil ou não de manter os testes, depende do seu design. Lembre-se, trate os testes como se fossem código em produção e facilite refatorações.

Qual técnica é essencial, quando praticamos Integração Contínua?
Test Driven Development
Alternativa errada! TDD (Test Driven Development) é uma metodologia que pode ser muito útil para não esquecer o teste e ajudar a simplificar o design do código, mas não é essencial.

Testes automatizados
Alternativa correta! As integrações do novo código no repositório precisam ser verificadas o tempo todo. Isso só é possível com uma bateria de testes, executadas de maneira automatizada, É isso que vai garantir a corretude do código.

Debugging
Alternativa errada! As ferramentas de debug podem ajudar no entendimento do código, mas não são essenciais.

Refatorações constantes
Alternativa errada! A refatoração é uma técnica, se for usada corretamente, que pode melhorar o design do seu código. Portanto faz sentido usar no dia-a-dia, mas não é uma obrigação da integração contínua.

Quais das afirmações abaixo são consideradas boas práticas relacionadas ao build?
Otimize o build
Alternativa correta! Builds lentos vão afetar negativamente a integração contínua, atrasando commits e diminuindo o feedback. Otimize o build para receber feedback mais rápido!

Use para cada ambiente um script de build separado
Alternativa errada! Idealmente existe apenas um script de build, que pode ser parametrizado para o ambiente especifico.

Rode o build sempre até o final, mesmo com falha nos testes
Alternativa errada! Integração contínua é sobre feedback rápido e o status do build é um exemplo. Se um teste não passa, pare o build e notifique a equipe.

Use um single command build
Alternativa correta! O build deve ser simples de executar, idealmente através de um único comando (single command build).

As ferramentas de automação e construção variam muito pois são especificas da linguagem e plataforma mas também variam na área de uso como desenvolvimento web, mobile ou data science. Além disso, existem ferramentas especificas para uma etapa de build como teste ou deploy. Enfim, a lista abaixo representa apenas alguns exemplos.

Ferramentas de automação e construção, separado por linguagem/plataforma:

Java: Ant, Maven, Gradle
Front-end: Gulp, Grunt, Webpack
.NET: MSBuild
Ruby: Rake
Kotlin: Gradle
Clojure: Leiningen
C/C++: CMake/Make
PHP: Composer
E alguns frameworks famosos da área de teste:

Selenium (automação do navegador)
Cucumber (testes de aceitação)
Postman e SoapUI (testes de API)
JMeter (stress tests)
JUnit, xUnit, PHPUnit (automação de testes)
entre muitos outros frameworks e bibliotecas
Para o configuration management e provisioning podemos mencionar:

Ansible
Puppet
Chef
Salt
Terraform (cloud)
O configuration management / provisioning é sobre a instalação e manutenção da maquina.

Na Alura temos cursos específicos para a maioria das ferramentas.

Com qual frequência devemos iniciar a construção do software através do servidor de integração contínua?
A cada commit (commit build)
Alternativa correta! Idealmente a cada commit. Isso pode ser um desafio quando temos uma frequência alta de commits. Nesse caso pode ser necessário executar os builds em paralelo.

Sempre à noite ou madrugada (nigthly builds)
Alternativa errada! Isso é considerado uma má prática na integração contínua. Nesse caso, temos uma janela de tempo entre builds muito grande. Como vamos saber qual commit quebrou o projeto? Isso não é considerado continuous.

A cada 10 minutos (periodic build)
Alternativa errada! Isso é considerado uma má prática na integração contínua. Por exemplo, se nessa janela de tempo aconteceram dois commits, não sabemos qual dos dois quebrou o build.

Listamos abaixo alguns servidores de integração disponíveis no mercado. Isso não é uma lista ordenada por popularidade e algum outro critério.

Alguns servidores são opensource, outros não, alguns são pagos ou podem ser alocados na nuvem e outros só existem para nuvem ou instalação local.

Em geral, não existe uma bala de prata e a melhor ferramenta é aquela que te serve bem:

Jenkins (https://jenkins.io/)
GoCD (https://www.gocd.org/)
Bamboo (https://www.atlassian.com/br/software/bamboo)
Travis CI (https://travis-ci.org/)
Team City (https://www.jetbrains.com/teamcity/)
Circle CI (https://circleci.com/)
Gitlab (https://about.gitlab.com/product/continuous-integration/)
AWS Code Pipeline https://aws.amazon.com/codepipeline/
Azure (https://azure.microsoft.com/pt-br/services/devops/server/)
entre outras possibilidades!

Além de iniciar o build, quais são as responsabilidades do servidor de integração?
Publicar o artefato de build o repositório
Alternativa correta! O servidor de integração publica ou disponibiliza o artefato de build (jar, war, gem, dll, image etc). Dessa forma, os desenvolvedores sempre podem baixar a última versão.

Publicar o status do último build do projeto
Alternativa correta! Muitas vezes, o servidor de integração até publica um histórico sobre os últimos builds e mostra mais informações sobre o tempo do build, testes, etc.

Definir a estrutura de diretórios do projeto
Alternativa errada! Isso é a responsabilidade da equipe.

Reverter o commit que quebrou o build
Alternativa errada! Isso é a responsabilidade da equipe / desenvolvedor.

De quem é a responsabilidade de arrumar o projeto quando a construção do software falhou?
É responsabilidade de todos da equipe
Alternativa correta! Arrumar o build quebrado é responsabilidade de toda equipe, com máxima prioridade.

É responsabilidade do Scrum Master
Alternativa errada! Arrumar o build quebrado é responsabilidade de toda equipe.

É responsabilidade do QA (Quality Assurance)
Alternativa errada! Arrumar o build quebrado é responsabilidade de toda equipe.

É responsabilidade do desenvolvedor que fez o commit em questão
Alternativa errada! Arrumar o build quebrado é responsabilidade de toda equipe.

Ambos, tanto integração contínua quanto a entrega contínua, visam diminuir o risco no desenvolvimento de software.

Nessa aula identificamos alguns padrões e práticas da entrega contínua. Sinalize a afirmação que realmente ajuda a diminuir esse risco:

Deploys supervisionados por pessoas
Alternativa errada! Idealmente é tudo automatizado através da deployment pipeline.

Deploys agendados, se for preciso com downtime definido
Alternativa errada! Idealmente não há nenhuma razão técnica para agendar um deploy.

Deploys frequentes e menores
Alternativa correta! Como a integração contínua visa commits menores e frequentes, a entrega contínua prega deploys menores e frequentes.


Deploys planejados no final de várias iterações de desenvolvimento
Alternativa errada! O ideal é evitar um "*big bang deploys".

O termo DevOps foi mencionado pela primeira vez em 2009, em uma palestra chamada de 10+ Deploys Per Day, por uma dupla que trabalhava no Flickr. O termo vem da junção das palavras Development e Operations, mas qual é a real definição desse termo?
É um processo bem definido, que visa acelerar o "time to market" do software
Alternativa errada! Acreditamos que não existe um único processo padronizado e sim boas e más práticas. Ou seja, não há um processo específico para cada empresa e ambiente, e sim melhoria e aprendizagem contínua.

É uma ferramenta que permite criar pipelines de implantação
Alternativa errada! O pipeline de implantação é um padrão importante da entrega contínua, mas o DevOps é sobre a cultura da empresa. É sobre "derrubar as paredes" para melhorar a colaboração e entregar software mais rápido, sem perder a qualidade

É um cargo que mistura conhecimento de desenvolvimento e operações
Alternativa errada! DevOps não é um cargo, nem uma ferramenta. Realmente não é!!!

É um movimento cultural
Alternativa correta! DevOps é sobre colaboração, sobre melhoria, feedback e aprendizagem contínua. Ou seja, é muito mais um mudança cultural do que o uso de uma nova ferramenta ou um processo específico.