# Tarefa 2 – Criar um banco de dados do Amazon RDS

***

## <mark style="color:red;">**Contexto da tarefa**</mark>

A equipe de rede verificou os requisitos de implantação anteriores e tudo parece estar bem. A próxima fase do projeto é estabelecer um banco de dados de back-end seguro para fornecer ao administrador do banco de dados (DBA) acesso a todas as operações de migração antes da disponibilização do banco de dados.&#x20;

O banco de dados atual requer muita sobrecarga administrativa e a empresa concordou em migrar para um serviço de banco de dados gerenciado. Eles querem que a arquitetura seja altamente disponível e você recomenda a configuração de uma camada de banco de dados multi-AZ RDS do Aurora. Depois de revisar o design proposto, o DBA delineou os requisitos do banco de dados. Devido a problemas de desempenho anteriores, o banco de dados não requer criptografia e você concorda que essa é a melhor opção.

A solução de monitoramento existente pesquisa os dados a cada 10 minutos. A equipe de engenharia não tem espaço no orçamento para recursos adicionais, portanto, o monitoramento aprimorado não é necessário.

***

### <mark style="color:red;">**Requisitos e configuração**</mark>

* As instâncias do banco de dados precisam ser do **Amazon Aurora compatíveis com o MySql** e **com intermitência.**
* O tamanho da instância de banco de dados precisa ser **db.t3.small.**
* A camada do banco de dados precisa ser implantada no **LabVPC.**
* O grupo de sub-rede precisa ser configurado apenas com as **Sub-redes do banco de dados**.
* O banco de dados precisa ser configurado com o **Security Group do RDS** configurado apenas pela equipe segurança.
* Lembre-se de fornecer um **nome do banco de dados inicial,** como _WPDatabase_**. Anote o nome do banco de dados.** Você precisará dele mais tarde.
* Verifique se você forneceu um **identificador de cluster do banco de dados**, como _MyDBCluster._ \

* Desativar a **criptografia.**
* Desative o **monitoramento aprimorado.**
* Anote o **Nome de usuário do administrador** e **a senha.** Você precisará deles mais tarde.
* Anote o **Endpoint de escrita.**

***

### <mark style="color:red;">**Descrição da tarefa**</mark>

Crie uma instância de DB do Amazon Aurora e o grupo de sub-rede para dar suporte a ela.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

| Tarefas                                         |
| ----------------------------------------------- |
| _Criar um grupo de sub-rede do banco de dados._ |
| _Criar um banco de dados do Aurora._            |
| _Copiar os metadados do banco de dados._        |

<details>

<summary><mark style="color:purple;">Tarefa 2.1 – Criar um banco de dados do Amazon RDS</mark></summary>

1. No AWS Management Console, no menu Services (Serviços), selecione RDS.

_**Observação:** você também pode localizar um serviço no AWS Management Console pesquisando-o pelo nome na barra de pesquisa unificada na parte superior central da página. A barra de pesquisa unificada está localizada à direita do menu Services (Serviços) e é rotulada como "Search for services, features, marketplace products, and docs" (Pesquisar serviços, recursos, produtos do Marketplace e documentos)._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 2.2 – Criar um grupo de sub-redes de DB</mark></summary>

1. No painel de navegação à esquerda, selecione **Subnet groups** (Grupos de sub-rede).
2. Selecione o botão **Create DB Subnet Group** (Criar grupo de sub-rede do banco de dados).&#x20;
   * A página **Create DB Subnet Group** (Criar grupo de sub-rede do DB) é exibida.
3. Na seção **Subnet group details** (Detalhes do grupo de sub-rede), configure:
   * **Nome:** _AuroraSubnetGroup_
   * **Descrição:** grupo de sub-rede de AZ A2 do meu banco de dados.
   * **VPC:** selecione _LabVPC_ no menu suspenso.
4. Na seção **Add subnets** (Adicionar sub-redes), configure:
   * Na seção **Availability Zones** (Zonas de Disponibilidade):
     * Marque a caixa de seleção ao lado da Zona de Disponibilidade que termina com _a_.
     * Marque a caixa de seleção ao lado da Zona de Disponibilidade que termina com _b_.
   * Na seção **Subnets** (Sub-redes):
     * selecione a sub-rede com o bloco CIDR **10.0.4.0/24** na Zona de Disponibilidade que termina com 'a'.
     * Selecione a sub-rede com o bloco CIDR **10.0.5.0/24** na Zona de Disponibilidade que termina com 'b'.
5. Selecione o botão **Create** (Criar).

_**Observação**: um banner com uma mensagem "Successfully created AuroraSubnetGroup" (O AuroraSubnetGroup foi criado com êxito) é exibido na parte superior da página._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 2.3 – Criar um banco de dados do Amazon Aurora</mark></summary>

1. No painel de navegação esquerdo, selecione **Databases** (Bancos de dados).
2. Selecione o botão **Create database** (Criar banco de dados).
   * A página **Create database** (Criar banco de dados) é exibida.
3. Na seção **Choose a database creation method** (Escolher um método de criação de banco de dados), selecione a opção _Standard Create (Criação Standard)_.
4. Na seção **Engine options** (Opções de mecanismo), configure:
   * Em **Engine type** (Tipo de mecanismo), selecione a opção _Amazon Aurora_.
   * Em **Edition** (Edição), selecione a opção _Amazon Aurora with MySQL compatibility_ (Amazon Aurora com compatibilidade no MySQL).
   * Em **Capacity type** (Tipo de capacidade), selecione a opção _Provisioned_ (Provisionado).
5. Na seção **Templates** (Modelos), selecione a opção _Production_ (Produção).
6. Na seção **Settings** (Configurações), configure:
   * **Identificador de cluster do banco de dados:** _MyDBCluster_
   * **Nome de usuário primário:** _admin_
   * **Senha primária:** _admin123_
   * **Confirme a senha**: _admin123_ \
     _**Observação:** lembre-se das suas credenciais._
7. Na seção **DB instance class** (Classe da instância de banco de dados), configure:
   * **Classe da instância de banco de dados:** selecione a opção de classes _Burstable_ (Com capacidade de intermitência).
   * Selecione o tipo de instância _**db.t3.small**_ no menu suspenso.
8. Na seção **Availability & durability** (Disponibilidade e durabilidade) de **Multi-AZ deployment** (Implantação multi-AZ), selecione _**Create an Aurora Replica or Reader node in a different AZ** (Criar uma réplica do Aurora ou nó do leitor em uma AZ diferente)._
9. Na seção **Connectivity** (Conectividade), configure:
   * **Virtual Private Cloud (VPC):** _LabVPC_
   * **Grupo de sub-rede:** _aurorasubnetgroup_
   * **Acesso público**: _Não_
   * **Security group de VPC:** _selecione um existente_
   * **Security groups de VPC existentes:**
     * Remova o security group **default** (padrão).
     * Selecione **RDSSecurityGroup** no menu suspenso.
10. Na seção **Additional configuration** (Configurações adicionais):
    * **Porta do banco de dados:** deixe a configuração com o valor-padrão.
11. Expanda a seção principal **Additional configuration** (Configurações adicionais) no final da página.
    * Na seção **Database options** (Opções do banco de dados), configure:
      * **Nome do banco de dados inicial:** _WPDatabase_
12. Na seção **Encryption** (Criptografia), desmarque **Enable encryption** (Ativar criptografia).
13. Na seção **Monitoring** (Monitoramento), desmarque **Enable Enhanced monitoring** (Ativar monitoramento aprimorado).
14. Na seção **Maintenance** (Manutenção), desmarque **Enable auto minor version upgrade** (Ativar atualização automática de versão secundária).
15. Na seção **Deletion protection** (Proteção contra exclusão), desmarque **Enable deletion protection** (Ativar proteção contra exclusão).
16. Role para o fim da tela e selecione o botão **Create database** (Criar banco de dados).

_**Observação**: seu cluster do banco de dados SQL do Aurora está sendo executado. O cluster que você configurou consiste em duas instâncias, cada uma em uma Zona de Disponibilidade diferente. O cluster do banco de dados do Amazon Aurora levará até cinco minutos para ser executado. Espero o status **mydbcluster** ser exibido como **Available** (Disponível). Você não precisa esperar pela disponibilidade das instâncias para continuar._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 2.4 – Copiar os metadados do banco de dados</mark></summary>

1. Selecione **Databases** (Bancos de dados) no menu de navegação.
2. Selecione o link de _mydbcluster_.&#x20;
   * A página de detalhes do **mydbcluster** é exibida.
3. Selecione a guia **Connectivity & Security** (Conectividade e segurança).
4. Copie o valor de **endpoint** da **Instância do gravador** em um bloco de notas.
5. Selecione a guia **Configuration** (Configuração).
6. Copie o valor do **nome do banco de dados** em um bloco de notas.
7. Copie o valor **Nome de usuário primário** em um bloco de notas.
8. Copie o valor **Senha primária** em um bloco de notas. Esse valor está oculto na console. Você precisa lembrar qual era ele no momento da criação do banco de dados.

</details>

***
