# Criação de seu primeiro Amazon Virtual Private Cloud (VPC)

### Tarefa 1: criar uma VPC <a href="#tarefa-1-criar-uma-vpc" id="tarefa-1-criar-uma-vpc"></a>

3. Nesta tarefa, você criará uma VPC básica.
4. &#x20;Lembre-se: uma nuvem privada virtual (VPC) é uma rede virtual dedicada em sua conta AWS. Ela oferece isolamento lógico das outras redes virtuais na nuvem AWS. É possível executar recursos da AWS, como Instâncias Amazon EC2, na VPC. Você pode configurar a VPC para modificar o intervalo de endereços IP, criar sub-redes e definir configurações de tabelas de rota, de gateways de rede e de segurança.
5.  No campo de pesquisa do **console de gerenciamento da AWS**, digite&#x20;

    VPC
6. Selecione **VPC** no menu suspenso

&#x20;Caso a mensagem **Experiência da nova VPC** apareça no canto superior esquerdo da tela, selecione a opção  **New VPC Experience** (Nova experiência da VPC). Este laboratório foi projetado para usar o novo console da VPC.

7. No painel de navegação à esquerda, escolha **Suas VPCs**.
8. Escolha Criar VPC e configure:
9. Escolha **Somente VPC**.

* **Tag do nome:** My VPC
* **Bloco CIDR da sub-rede IPv4:** 10.0.0.0/16
* Escolha Criar VPC

### Tarefa 2: criar a sub-rede pública <a href="#tarefa-2-criar-a-sub-rede-publica" id="tarefa-2-criar-a-sub-rede-publica"></a>

Nesta tarefa, você cria uma sub-rede pública. Depois, você inicia o servidor web na sub-rede pública.

&#x20;Uma sub-rede é um intervalo de endereços IP na VPC. Você pode executar recursos da AWS em uma subnet especificada. Use sub-redes públicas para recursos que devem ser conectados à internet e uma sub-rede privada para recursos que não serão conectados à internet.

#### Criar a sub-rede pública <a href="#criar-a-sub-rede-publica" id="criar-a-sub-rede-publica"></a>

10. No painel de navegação à esquerda, escolha **Sub-redes**.
11. Selecione Criar sub-rede e configure:

* **ID da VPC**: _My VPC_
* **Nome da sub-rede:** Public 1
* **Zona de Disponibilidade:** selecione a _primeira_ AZ da lista
* **Bloco CIDR da sub-rede IPv4:** 10.0.1.0/24

12. Escolha Criar sub-rede
13. Selecione  **Pública 1**.
14. No menu **Ações**, selecione **Editar configurações de sub-rede** e configure:

* Selecione  **Enable auto-assign public IPv4 address** (Habilitar endereço IPv4 público de atribuição automática)
* Selecione Salvar

&#x20;**Enable auto-assign public IPv4 address** (Habilitar endereço IPv4 público de atribuição automática) cria um endereço IPv4 público para todas as instâncias executadas na sub-rede selecionada.

Embora a sub-rede seja chamada de **Pública 1**, ela ainda não é uma sub-rede pública. Uma sub-rede pública deve ter um gateway de internet, que você vai anexar na próxima tarefa.

### Tarefa 3: criar um gateway de internet <a href="#tarefa-3-criar-um-gateway-de-internet" id="tarefa-3-criar-um-gateway-de-internet"></a>

Nesta tarefa, você vai criar um gateway de internet para que o tráfego possa chegar ao servidor web.

&#x20;O gateway de internet é um componente da VPC dimensionado de modo horizontal, redundante e altamente disponível que permite a comunicação entre as instâncias na VPC e a internet. Portanto, não impõe nenhum risco de disponibilidade ou restrições de largura de banda no tráfego da rede.

O gateway de internet tem duas finalidades: servir como destino nas tabelas de rota da VPC para o tráfego roteável na internet e executar a conversão de endereços de rede (NAT) para instâncias que têm endereços IPv4 públicos.

15. No painel de navegação à esquerda, escolha **gateways da internet**.
16. Escolha Criar gateway da internet e configure:

* **Tag do nome:** My IG
* Escolha Criar gateway da internet

17. No menu **Ações**, selecione **Anexar à VPC** e configure:

* **VPCs disponíveis:** _My VPC_
* Selecione Associar gateway da internet

Isso associa o gateway de internet à VPC. Mesmo que você tenha criado um gateway de internet e anexado-o à VPC, ainda é necessário informar às instâncias na sub-rede pública como acessar a internet.

### Tarefa 4: criar uma tabela de rota, adicionar rotas e associar sub-redes públicas <a href="#tarefa-4-criar-uma-tabela-de-rota-adicionar-rotas-e-associar-sub-redes-publicas" id="tarefa-4-criar-uma-tabela-de-rota-adicionar-rotas-e-associar-sub-redes-publicas"></a>

Nesta tarefa, você vai:

* Criar uma tabela de rota para tráfego destinado à internet
* Adicionar uma rota à tabela para direcionar o tráfego destinado à internet ao gateway de internet
* Associar a sub-rede pública à tabela de rota

&#x20;A tabela de rota contém um conjunto de regras, denominadas rotas, que são usadas para determinar para onde o tráfego de rede é direcionado. Toda subnet em sua VPC deve ser associada a uma tabela de rotas; a tabela controla o roteamento para a subnet. Uma subnet só pode ser associada a uma única tabela de rotas por vez, mas é possível associar várias subnets a uma mesma tabela de rotas.

&#x20;Para usar um Internet gateway, a tabela de rotas da subnet deve conter uma rota que direcione o tráfego destinado à Internet para o Internet gateway. Você pode definir o escopo da rota para todos os destinos não explicitamente conhecidos na tabela de rotas (0.0.0.0/0 para IPv4 ou ::/0 para IPv6) ou pode definir o escopo da rota para um intervalo mais restrito de endereços IP; por exemplo, os endereços IPv4 públicos dos endpoints públicos da sua empresa fora da AWS ou os Elastic IP addresses de outras Instâncias Amazon EC2 fora da VPC. As sub-redes associadas a uma tabela que contém uma rota para um gateway de internet são chamadas de sub-redes públicas.

18. No painel de navegação à esquerda, selecione **Tabelas de rota**.

Atualmente, há uma tabela-padrão de rota associada à VPC, **My VPC** (Minha VPC). Isso direciona o tráfego localmente. Crie outra tabela de rota para rotear o tráfego público ao gateway de internet.

19. Escolha Criar tabela de rota
20. Na seção **Configurações da tabela de rotas**, configure:

* **Nome opcional:** Public Route Table
* **VPC:** _My VPC_ (Minha VPC)
* Escolha Criar tabela de rota

21. Na guia **Rotas**, na metade inferior da página.

Observe que a tabela contém uma rota que permite a passagem de tráfego dentro da rede 10.0.0.0/16, mas não permite que o tráfego saia dessa rede. Adicione uma nova rota para habilitar o tráfego público.

22. Selecione Editar rotas.
23. Escolha Adicionar rota e configure:

* **Destino:** 0.0.0.0/0
* **Alvo:** selecione **Gateway da internet** na lista suspensa e selecione o ID **Gateway da internet** exibido
* Escolha Salvar alterações

24. Selecione a guia **Associações de sub-rede**.
25. Na seção **Editar associações de sub-rede**, escolha Editar associações de sub-rede
26. Selecione  **Pública 1**.
27. Escolha Salvar associações.

A sub-rede agora é _pública_ porque está conectada à internet por meio do gateway de internet.

### Tarefa 5: criar um grupo de segurança para o servidor web <a href="#tarefa-5-criar-um-grupo-de-seguranca-para-o-servidor-web" id="tarefa-5-criar-um-grupo-de-seguranca-para-o-servidor-web"></a>

Nesta tarefa, você adicionará um grupo de segurança para que os usuários possam acessar o servidor web via HTTP.

&#x20;O grupo de segurança atua como um firewall virtual da instância para controlar o tráfego de entrada e saída. Quando você executa uma instância na VPC, é possível atribuir até cinco grupos de segurança à instância. Os grupos de segurança atuam no nível da instância, não no nível da subnet. Portanto, cada instância em uma subnet na VPC poderá ser atribuída a um conjunto diferente de grupos de segurança. Se você não especificar um grupo em particular no momento da execução, a instância será automaticamente atribuída ao grupo-padrão da VPC.

28. No painel de navegação à esquerda, escolha **Grupos de segurança**.
29. Selecione Criar grupo de segurança e configure:

* **Nome do grupo de segurança:** Web server
* **Descrição:** My Web Server Security Group
* **VPC:** _My VPC_ (Minha VPC)

30. Em **Regras de entrada**

* Escolha Adicionar regra
* **Tipo:** HTTP
* **Origem:** _Anywhere-Ipv4_

31. Na parte inferior da tela, escolha Criar grupo de segurança

### Tarefa 6: iniciar um servidor web na sub-rede pública <a href="#tarefa-6-iniciar-um-servidor-web-na-sub-rede-publica" id="tarefa-6-iniciar-um-servidor-web-na-sub-rede-publica"></a>

Nesta tarefa, você vai iniciar um servidor web que executa uma aplicação de catálogo de endereços. Mais tarde no laboratório, você conectará a aplicação de catálogo de endereços a uma instância do Amazon RDS para MySQL.

32. No campo de pesquisa do **console de gerenciamento da AWS**, digite&#x20;

    EC2
33. Selecione **EC2** no menu suspenso

&#x20;Se a mensagem **New EC2 Experience** (Nova experiência do EC2) aparecer no canto superior esquerdo da tela, selecione a opção  **New EC2 Experience** (Experiência do novo EC2). Este laboratório usa o novo console do EC2.

34. Escolha Executar instâncias > **Executar instâncias**.
35. Na página “Executar uma instância”, configure:

* Na seção **Nome e tags**, digite: Web Server
* Para **Application and OS Images (Amazon Machine Image)** (Imagens da aplicação e do SO \[imagem de máquina da Amazon]), escolha **Amazon Linux 2 AMI** (AMI do Amazon Linux 2).
* Para **Tipo de instância**, escolha **t3.micro**
* Na seção **Par de chaves (login)**, selecione **Continuar sem par de chaves**
* Na seção **Configurações de rede**, selecione Editar
  * Para **VPC**, escolha My VPC\
    Observação: Public 1 é preenchido automaticamente na seção de sub-rede
  * Em **Firewall (grupos de segurança)**, selecione  **Selecionar um grupo de segurança existente**
  * **Grupos de segurança comuns**, selecione **Servidor Web**
* Expanda  **Advanced Details** (Detalhes avançados) (na parte inferior da página)
* Copie e cole esse script na caixa de texto **Dados do usuário**:

```
#!/bin/bash -ex
yum -y update
yum -y install httpd php mysql php-mysql
chkconfig httpd on
service httpd start
cd /var/www/html
wget https://us-west-2-aws-training.s3.amazonaws.com/courses/spl-13/v4.2.31.prod-c349af66/scripts/app.tgz
tar xvfz app.tgz
chown apache:root /var/www/html/rds.conf.php
```

Esse script é executado na primeira vez que a instância é executada. Ele instala um servidor web na instância do EC2 e executa uma aplicação que pode ser configurada para apontar para a instância do MySQL RDS. Depois que você configurar a instância do RDS, ela apresentará um catálogo de endereços que você poderá editar.

36. Selecione Executar instância
37. Selecione Visualizar todas as instâncias

A janela **Instâncias** é aberta, exibindo os detalhes do servidor web.

38. Aguarde até que o servidor web seja totalmente iniciado. Ele deve exibir o seguinte:

* **Estado da instância:**  em execução
* **Verificação de status:** 2/2 verificações aprovadas

Você pode selecionar o ícone de atualização  para atualizar o status das instâncias.

39. Sua instância deve ser selecionada , caso contrário, selecione-a.
40. Copie o **Public IPv4 address** (Endereço de IPv4 público) da instância para a área de transferência.
41. Abra uma nova guia do navegador da Web e cole o endereço IP no navegador.
42. Pressione **Enter** para ir para a página da Web.

&#x20;Caso você receba um erro, aguarde 60 segundos e atualize  a página para tentar novamente. Pode levar alguns minutos para a instância EC2 inicializar e executar o script que instala o software.

Uma aplicação será aberta:

![WebServer](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/spl-13/v4.2.31.prod-c349af66/images/frontend-webserver.png)

&#x20;Parabéns! Você deve ser capaz de ver esta página. Atualmente, você não tem um banco de dados. Depois de criar uma instância do RDS, você poderá conectá-la ao servidor web.

### Tarefa 7: criar sub-redes privadas para o servidor MySQL <a href="#tarefa-7-criar-sub-redes-privadas-para-o-servidor-mysql" id="tarefa-7-criar-sub-redes-privadas-para-o-servidor-mysql"></a>

Para implantar o banco de dados RDS, a VPC deve ter pelo menos duas sub-redes. Essas sub-redes precisam estar em duas Zonas de Disponibilidade diferentes na Região AWS em que você deseja implantar a instância de banco de dados. Nesta tarefa, você criará duas sub-redes privadas para sua instância do Amazon RDS.

#### Crie a primeira sub-rede privada <a href="#crie-a-primeira-sub-rede-privada" id="crie-a-primeira-sub-rede-privada"></a>

43. No campo de pesquisa do **console de gerenciamento da AWS**, digite&#x20;

    VPC
44. Selecione **VPC** no menu suspenso
45. No painel de navegação à esquerda, escolha **Sub-redes**.
46. Selecione Criar sub-rede e configure:

* **VPC:** _My VPC_ (Minha VPC)
* **Nome da sub-rede:** Private 1
* **Zona de Disponibilidade:** selecione a _primeira_ AZ da lista
* **Bloco CIDR da sub-rede IPv4:** 10.0.2.0/24
* Escolha Criar sub-rede

#### Crie a segunda sub-rede privada <a href="#crie-a-segunda-sub-rede-privada" id="crie-a-segunda-sub-rede-privada"></a>

47. Selecione Criar sub-rede e configure:

* **VPC:** _My VPC_ (Minha VPC)
* **Nome da sub-rede:** Private 2
* **Zona de Disponibilidade:** selecione a _segunda AZ_ na lista
* **Bloco CIDR da sub-rede IPv4:** 10.0.3.0/24
* Escolha Criar sub-rede

### Tarefa 8: criar um grupo de segurança para o servidor de banco de dados <a href="#tarefa-8-criar-um-grupo-de-seguranca-para-o-servidor-de-banco-de-dados" id="tarefa-8-criar-um-grupo-de-seguranca-para-o-servidor-de-banco-de-dados"></a>

Agora que as sub-redes privadas estão configuradas, você protegerá os tipos de tráfego que podem acessar o banco de dados MySQL. Nesta tarefa, você criará um grupo de segurança para permitir apenas o tráfego MySQL vindo do servidor web.

48. No painel de navegação à esquerda, escolha **Grupos de segurança**.
49. Copie o valor do **ID do grupo de segurança** do grupo de segurança _Servidor Web_ e cole-o em um editor de texto.
50. Selecione Criar grupo de segurança e configure:

* **Nome do grupo de segurança:** Database
* **Descrição:** My Database Security Group
* **VPC:** _My VPC_ (Minha VPC)

51. Em **Regras de entrada**

* Escolha Adicionar regra
* **Tipo:**  MySQL/Aurora\
  &#x20;Observação: selecione MySQL, _não_ MSSQL,
* **Origem:**
  * _Custom_ (Personalizada)
  * Cole o ID do grupo de segurança do servidor web que você copiou para o editor de texto

52. Na parte inferior da tela, escolha Criar grupo de segurança

Isso permitirá que o servidor web se comunique com o banco de dados.

### Tarefa 9: criar um grupo de sub-redes de banco de dados <a href="#tarefa-9-criar-um-grupo-de-sub-redes-de-banco-de-dados" id="tarefa-9-criar-um-grupo-de-sub-redes-de-banco-de-dados"></a>

As instâncias do Amazon RDS exigem um grupo de sub-redes de banco de dados. Nesta tarefa, você criará um grupo de sub-redes de banco de dados.

&#x20;Um grupo de sub-redes de banco de dados é uma coleção de sub-redes (geralmente privadas) que você cria em uma VPC e designa às instâncias de banco de dados. Cada grupo de sub-redes de banco de dados deve ter sub-redes em pelo menos duas zonas de disponibilidade em uma determinada região. Ao criar uma instância de banco de dados na VPC, selecione um grupo de sub-redes de banco de dados.

53. No campo de pesquisa do **console de gerenciamento da AWS**, digite&#x20;

    RDS
54. Selecione **RDS** no menu suspenso
55. No painel de navegação à esquerda, selecione **Grupos de sub-redes**.
56. Escolha Criar grupo de sub-redes de banco de dados e configure:

* **Nome:** My Subnet Group
* **Descrição:** My Subnet Group
* **VPC:** _My VPC_ (Minha VPC)

#### Adicione suas sub-redes privadas <a href="#adicione-suas-sub-redes-privadas" id="adicione-suas-sub-redes-privadas"></a>

57. Na seção **Adicionar sub-redes**, configure o seguinte:

* **Zona de Disponibilidade:** selecione a primeira e a segunda Zonas de Disponibilidade na lista.

58. Na seção **Sub-redes**, selecione:

* &#x20;_10.0.2.0/24_
* &#x20;_10.0.3.0/24_

59. Na parte inferior da tela, escolha Criar

### Tarefa 10: criar um banco de dados do Amazon RDS <a href="#tarefa-10-criar-um-banco-de-dados-do-amazon-rds" id="tarefa-10-criar-um-banco-de-dados-do-amazon-rds"></a>

Agora você pode iniciar um banco de dados do Amazon RDS executando o MySQL.

60. No painel de navegação à esquerda, clique em **Bancos de dados**.
61. Escolha Criar banco de dados e configure:

* **Opções do mecanismo:** _MySQL_
* **Versão:** _MySQL 5.7.X_

&#x20;É muito importante selecionar a versão mais recente do 5.7.X. Selecione a versão com o maior número. Este laboratório exige isso para a aplicação.

62. Na seção _Modelos_, selecione **Dev/Teste**.
63. Na seção **Configurações**, configure:

* **Identificador da instância de banco de dados:** myDB
* **Nome de usuário principal:** admin
* Para **Credentials management** (Gerenciamento de credenciais), escolha a opção **Autogerenciado**
* **Senha principal:** lab-password
* **Confirmar senha:** lab-password

64. Na seção **Classe da instância de banco de dados**, configure:

* **Classe da instância de banco de dados**: _Classes com capacidade de intermitência_
* Selecione **db.t3.micro**.

65. Na seção **Armazenamento**, expanda **Escalabilidade automática do armazenamento** e, em seguida, desmarque  **Habilitar escalabilidade automática do armazenamento**
66. Na seção **Conectividade**, configure:

* **Virtual Private Cloud (VPC)** _My VPC_ (Minha VPC)
* **Acesso público:**  _Não_
* **Grupos de segurança da VPC existentes:**
  * Adicione o grupo de segurança **Banco de dados**
  * Remova o grupo de segurança **padrão**

67. Na seção **Monitoramento**, desmarque a opção  **Habilitar monitoramento avançado**
68. Na seção **Configuração adicional** _(localizada próximo da parte inferior)_, escolha  **Configuração adicional** e configure:

* **Nome do banco de dados inicial:** myDB
* Desmarque  **Habilitar backups automatizados** Isso desabilitará os backups, o que iniciará o banco de dados um pouco mais rápido para o laboratório.
* Desmarque  **Habilitar a atualização automática da versão secundária**

69. Na parte inferior da tela, escolha Criar banco de dados
70. Se for exibido um pop-up indicando **Suggested add-ons for mydb** (Complementos sugeridos para mydb), escolha Fechar
71. Escolha atualizar  a cada 60 segundos até que a instância tenha um status de  **disponível**.

&#x20;Parabéns! Você implantou um banco de dados MySQL.

### Tarefa 11: conectar a aplicação de catálogo de endereços ao banco de dados <a href="#tarefa-11-conectar-a-aplicacao-de-catalogo-de-enderecos-ao-banco-de-dados" id="tarefa-11-conectar-a-aplicacao-de-catalogo-de-enderecos-ao-banco-de-dados"></a>

Nesta tarefa, você vai conectar a aplicação de catálogo de endereços (na sub-rede pública) ao banco de dados (na sub-rede privada).

#### Obtenha o endpoint do banco de dados MySQL <a href="#obtenha-o-endpoint-do-banco-de-dados-mysql" id="obtenha-o-endpoint-do-banco-de-dados-mysql"></a>

Antes de conectar a aplicação de catálogo de endereços ao banco de dados, você precisa conhecer o _endpoint_ da instância do RDS. Esse é o endereço da instância do RDS.

72. Escolha a instância **mydb**.
73. Na seção **Segurança e conexão**, copie o **Endpoint** para a área de transferência.

Seu endpoint do RDS deve ser semelhante a:

_mydb.ciljcs3yv1rb.us-west-2.rds.amazonaws.com_

#### Conecte-se ao seu banco de dados <a href="#conecte-se-ao-seu-banco-de-dados" id="conecte-se-ao-seu-banco-de-dados"></a>

74. Volte para a guia do navegador que está exibindo o servidor Web e configure:

* **Endpoint:** cole o endpoint do MySQL
* **Banco de dados:** myDB
* **Nome de usuário:** admin
* **Senha:** lab-password
* Escolha Enviar

Após a conexão, você verá um catálogo de endereços com duas entradas.

&#x20;Parabéns! Você conectou com êxito a aplicação de catálogo de endereços ao banco de dados.

75. Tente adicionar e remover um contato do catálogo de endereços.

![address-book](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/spl-13/v4.2.31.prod-c349af66/images/address-book.png)

As informações do catálogo de endereços são salvas no banco de dados do Amazon RDS para MySQL.

### Conclusão <a href="#conclusao" id="conclusao"></a>

&#x20;Parabéns! Agora você:

* Criou uma Amazon Virtual Private Cloud (VPC)
* Criou sub-redes públicas e privadas
* Criou um Internet gateway
* Criou uma tabela de rotas e adicionou uma rota para a Internet
* Criou um grupo de segurança para o servidor web para permitir apenas o tráfego HTTP para o servidor
* Criou um grupo de segurança para a instância do MySQL RDS para permitir apenas o tráfego do MySQL vindo da sub-rede pública
* Implantou um servidor web e uma instância do MySQL RDS
* Configurou sua aplicação para se conectar à instância do MySQL RDS

### Finalizar laboratório <a href="#finalizar-laboratorio" id="finalizar-laboratorio"></a>

Siga as etapas a seguir para fechar a console e finalizar o laboratório.

76. Retorne ao Console de gerenciamento da AWS.
77. Na guia de navegação, clique em **AWSLabsUser** e em **Sign Out** (Sair).
78. Clique em End Lab (Finalizar laboratório) e confirme que você deseja finalizar o laboratório.

### Recursos adicionais <a href="#recursos-adicionais" id="recursos-adicionais"></a>

* [O que é Amazon VPC?](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC\_Introduction.html)
* [Tabelas de rotas para sua VPC](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC\_Route\_Tables.html)
* [Grupos de segurança para sua VPC](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC\_SecurityGroups.html)
* [Gateways da internet](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC\_Internet\_Gateway.html)
* [Zonas de Disponibilidade](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-availability-zones)
* [Amazon RDS](https://aws.amazon.com/rds/)
