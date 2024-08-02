# Tarefa 5 – Criar um Application Load Balancer

***

## <mark style="color:red;">**Contexto da tarefa**</mark>

A equipe de SysOps está animada para a nova configuração do EFS e ansiosa para resolver o próximo tópico de atenção. O aplicativo atual sofre interrupções frequentes devido a cargas de tráfego variáveis e inesperadas. A equipe de SysOps quer saber se a AWS tem um serviço para resolver esse problema que pode ser usado na camada do aplicativo (camada 7). Após uma investigação mais aprofundada, você reconhece a necessidade de um Application Load Balancer para os recursos voltados para a web na sub-rede pública. Implante e configure um ALB com um health check e registre os destinos exigidos.

***

### <mark style="color:red;">**Requisitos e configuração**</mark>

* O **Application Load Balancer** (ALB) precisa ser configurado no _LabVPC_ e nas sub-redes públicas com as seguintes propriedades:
  * **Esquema: voltado para a internet**
  * **Sub-redes: todas as sub-redes públicas**
  * **SecurityGroups: AppInstanceSecurityGroup** (já criado pela sua equipe de segurança)
* O **grupo de destino** do ALB deve ser configurado para usar o _LabVPC_ para instâncias de balanceamento de carga com as propriedades a seguir:
  * **Protocolo: HTTP**
  * **Porta: 80**
  * **Versão do protocolo: HTTP1**
  * **Caminho de health check: /wp-login.php**
  * **Limite máximo de health: 2**
  * **Limite mínimo de health: 10**
  * **Tempo limite: 50**
  * **Intervalo: 60**
* Anote o **nome DNS do balanceador de carga**_._

***

### <mark style="color:red;">**Descrição da tarefa**</mark>

Nesta tarefa, você criará o Application Load Balancer e um grupo de destino.

<figure><img src="../../.gitbook/assets/image (10) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

| Tarefas                               |
| ------------------------------------- |
| C_riar um Application Load Balancer._ |
| C_opiar os metadados do ELB._         |

<details>

<summary><mark style="color:purple;">Tarefa 5.1: Navegar até a console do Amazon EC2</mark></summary>

1. No **AWS Management Console**, no menu Services (Serviços), selecione **EC2**.

_**Observação**: você também pode pesquisar por EC2 na barra de pesquisa unificada na parte superior da console._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 5.2: Criar um Application Load Balancer</mark></summary>

1. No painel de navegação esquerdo, selecione **Target Groups** (Grupos de destino).
2. Selecione o botão **Create target group** (Criar um grupo de destino).
   * A página **Specify group details** (Especificar os detalhes do grupo) é exibida.
3. Na seção **Basic configuration** (Configuração básica), configure o seguinte:
   * Em **Choose a target type** (Escolher um tipo de destino): selecione _Instances_ (Instâncias)
   * Em **Target group name** (Nome do grupo de destino): _myWPTargetGroup_
   * Em **VPC:** selecione _LabVPC_
   * Na seção **health checks**:
     * No **caminho do health check:** _/wp-login.php_
   * Na seção **Advanced health check settings** (Configurações de health check avançadas):
     * **Limite máximo de health:** 2
     * **Limite mínimo de health:** 10
     * **Tempo limite:** 50
     * **Intervalo:** 60
   * As configurações restantes na página podem ficar com os valores-padrão
4. Selecione o botão **Next** (Próximo).&#x20;
   * A página **Register targets** (Registrar destinos) é exibida.
   * Não há mais destinos a serem registrados no momento.
5. Selecione o botão **Create target group** (Criar um grupo de destino).
   * A seguinte mensagem é exibida:
   * **Successfully created target group: myWPTargetGroup** (O grupo de destino myWPTargetGroup foi criado com êxito)
6. No painel de navegação à esquerda, selecione **Load Balancers** (Balanceadores de carga).&#x20;
7. &#x20;Selecione o botão **CreateLoad Balancers** (Criar balanceadores de carga).
8. Selecione o botão **Create** (Criar) na seção **Application Load Balancer**.&#x20;
   * A página **Create Application Load Balancer** (Criar Application Load Balancer) é exibida.
9. Na seção **Basic Configuration** (Configuração básica), configure o seguinte:
   * Em **Load balancer name** (Nome do balanceador de carga): Insira _myWPAppALB_
10. Na seção **Network mapping** (Mapeamento de rede), configure o seguinte:
    * **VPC:** Selecione _LabVPC_
    * **Mapeamentos:**
      * Selecione a **caixa de seleção** na primeira Zona de Disponibilidade listada e selecione _PublicSubnet1_ na lista Subnet (Sub-rede).
      * Selecione a **caixa de seleção** da segunda Zona de Disponibilidade listada e selecione _PublicSubnet2_ na lista Subnet (Sub-rede).&#x20;
11. Na seção **Security groups**, configure o seguinte:
    * Remova o security group _padrão_.
    * Selecione _AppInstanceSecurityGroup_ no menu suspenso.
12. Na seção Listeners and routing (Ouvintes e roteamento), configure o seguinte:
    * Para **Listener HTTP:80:** (Ouvinte HTTP:80) Selecione _myWPTargetGroup_ na lista suspensa de ação-padrão.
13. Selecione o botão **Create load balancer** (Criar balanceador de carga).&#x20;
14. A seguinte mensagem é exibida:
    * **Successfully created load balancer: myWPAppALB** (O balanceador de carga myWPAppALB foi criado com êxito)
15. Selecione o botão **View load balancers** (Ver balanceadores de carga).

O estado do balanceador de carga é alterado para _Active_ (Ativo) quando fica pronto.

</details>

<details>

<summary><mark style="color:purple;">Tarefa 5.3: Copiar os metadados do ELB</mark></summary>

1. Selecione **myWPAppALB**.
2. Selecione a guia **Description** (Descrição).
3. Copie o **nome DNS** no seu bloco de notas.

</details>

***
