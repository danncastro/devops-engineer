# Tarefa 7 – Criar os servidores de aplicativos configurando um grupo do Auto Scaling e uma política

***

## <mark style="color:red;">**História da tarefa**</mark>

Agora que o modelo foi implantado, está na hora de criar servidores de aplicativo e um mecanismo de auto scaling. Na tarefa anterior, você escolheu implantar o auto scaling para que os servidores de aplicativo atendessem os requisitos de scaling do plano do projeto.&#x20;

Crie uma política de scaling e um grupo do Auto Scaling. Verifique se a instância tem o status com health e teste a disponibilidade do balanceador de carga. Entregue o ambiente às equipes de engenharia para validar a funcionalidade completa quando o "smoke test" estiver concluído, e solicite comentários.&#x20;

Quando a equipe estiver satisfeita, peça para migrar o site do WordPress para o ambiente da AWS e testar a funcionalidade do aplicativo. Uma prática comum é apresentar exemplos de falhas. Se o aplicativo estiver funcionando conforme o esperado, você apresentaria alguns exemplos de falha (excluir um servidor de aplicativos, reverter o banco de dados para um backup recente, entre outros). Essa etapa não é parte do nosso laboratório.

***

### <mark style="color:red;">**Requisitos e configuração**</mark>

* Use o modelo de execução da tarefa anterior.
* Use o **LabVPC** para configurações de rede.
* Use as **sub-redes do aplicativo** em ambas as **Zonas de Disponibilidade.**
* Use o balanceador de carga existente e os grupos de destino criados anteriormente.
* Use o health check do **ELB** e defina o período de carência dele como **300 segundos.**
* Configure o tamanho do grupo a ser usado:&#x20;
  * Capacidade desejada: **2**
  * Capacidade mínima: **2**
  * Capacidade máxima: **4**
* Configure as políticas de scaling com a **Política de scaling com monitoramento de alvo** e use os padrões.
* As notificações estão fora do escopo do laboratório e não precisam ser configuradas.&#x20;
* Verifique se o **Grupo do Auto Scaling** executou suas **instâncias do EC2.**

***

### <mark style="color:red;">**Descrição da tarefa**</mark>

Crie os servidores de aplicativos do WordPress, configurando um grupo do Auto Scaling e uma política de scaling.

<figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

| Tarefas                                                                                              |
| ---------------------------------------------------------------------------------------------------- |
| C_rie um grupo do Auto Scaling._                                                                     |
| V_erifique os grupos de destino e teste o servidor de aplicativos por meio do balanceador de carga._ |
| R_egistre-se no WordPress e explore._                                                                |

<details>

<summary><mark style="color:purple;">Tarefa 7.1: Navegar até a console do EC2</mark></summary>

1. No AWS Management Console, no menu **Services** (Serviços), selecione **EC2**.

_**Observação**: você também pode pesquisar por EC2 na barra de pesquisa unificada na parte superior da console._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 7.2: Criar um grupo do Auto Scaling</mark></summary>

1. No painel de navegação à esquerda, selecione **Auto Scaling Groups** (Grupos do Auto Scaling) na seção **Auto Scaling**.
2. Selecione o botão **Create Auto Scaling group** (Criar grupo do Auto Scaling).
   * A página **Choose launch template or configuration** (Escolher uma configuração ou modelo de execução) é exibida.
3. Configure o seguinte:
   * **Nome do grupo do Auto Scaling:** _WP-ASG_
   * **Modelo de execução:** selecione o modelo de execução criado na Tarefa 6.
   * Selecione o botão **Next** (Próximo).
   * A página **Configure settings** (Definir configurações) é exibida.
4. Na seção **Network** (Rede), configure:
   * **VPC:** _LabVPC_
   * **Sub-redes:** selecione _AppSubnet1_ e _AppSubnet2_
   * Selecione o botão **Next** (Próximo).
   * A página **Configure advanced options** (Configurar opções avançadas) é exibida.
5. Configure o seguinte:
   * Selecione a opção **Attach to an existing load balancer** (Conectar ao balanceador de carga existente).
   * Selecione a opção **Choose from your load balancer target groups** (Selecionar dos seus grupos de destino do balanceador de carga).
   * Em **Existing load balancer target groups** (Grupos de destino do balanceador de carga existente), selecione **myWPTargetGroup | HTTP** no menu suspenso.
   * **Tipo de health check:** selecione _ELB._
   * **Período de carência do health check:** deixe com o valor-padrão de _300_ ou mais.
   * **Monitoramento:** marque a caixa de seleção _Enable group metrics collection within CloudWatch_ (Ativar a coleção de métricas do grupo no CloudWatch).
   * Selecione o botão **Next** (Próximo).
   * A página **Configure group size and scaling policies** (Configurar tamanho do grupo e políticas de scaling) é exibida.
6. Configure o seguinte:
   * Na seção Group Size (Tamanho do grupo):
     * **Capacidade desejada:** _2_
     * **Capacidade mínima**: _2_
     * **Capacidade máxima:** _4_
   * Na seção **Scaling policies** (Políticas de scaling):
     * selecione a opção **Target tracking scaling policy** (Política de scaling com monitoramento de alvo).
     * As configurações restantes nessa seção podem ficar com os valores-padrão.
   * Selecione o botão **Next** (Próximo).
   * A página **Add notifications** (Adicionar notificações) é exibida.
7. Selecione o botão **Next** (Próximo).
   * A página **Add tags** (Adicionar tags) é exibida.
8. Selecione o botão **Add tag** (Adicionar tags) e configure:
   * **Chave:** _Nome_
   * **Valor:** _WP-App_
9. Selecione o botão **Next** (Avançar).
   * A página **Review** (Revisar) será exibida.
10. Verifique se a configuração do grupo do Auto Scaling tem precisão e selecione o botão **Create Auto Scaling group** (Criar grupo do Auto Scaling).
    * A página **Auto Scaling groups** (Grupos do Auto Scaling) é exibida.
11. Agora que você criou o grupo do Auto Scaling, você pode verificar se o grupo executou suas instâncias do EC2.
    * Selecione seu grupo do Auto Scaling.
    * Examine a seção **Group Details** (Detalhes do grupo) para verificar as informações sobre o grupo do Auto Scaling.
12. Abra a guia **Activity** (Atividade).
    * A seção **Activity History** (Histórico de atividade) mantém um registro dos eventos que ocorreram no Grupo do Auto Scaling. A coluna Status contém o status atual de suas instâncias. Quando suas instâncias estão sendo executadas, a coluna status mostra PreInService. O status será alterado para Successful (Bem-sucedido) quando uma instância for executada.
13. Abra a guia **Instance management** (Gerenciamento de instância).
    * Seu grupo do Auto Scaling executou duas instâncias do Amazon EC2 e elas estão no estado de ciclo de vida do InService. A coluna Health Status (Status de health) mostra o resultado da health check da instância do Amazon EC2 nas suas instâncias.
    * Se as suas instâncias ainda não estiverem no estado InService, você precisará aguardar alguns minutos. Você pode selecionar o botão atualizar para recuperar o estado atual do ciclo de vida das suas instâncias.
14. Abra a **guia Monitoring** (Monitoramento). Aqui você pode revisar as informações relacionadas ao monitoramento do seu grupo do Auto Scaling.
    * Esta página fornece informações sobre a atividade no seu grupo do Auto Scaling, bem como a utilização e o status de health das suas instâncias. A guia Auto Scaling exibe as métricas do Amazon CloudWatch sobre seu grupo do Auto Scaling, enquanto a guia EC2 exibe as métricas das instâncias do Amazon EC2 gerenciadas pelo grupo do Auto Scaling.

</details>

<details>

<summary><mark style="color:purple;">Tarefa 7.3: Verificar se os grupos de destino têm health</mark></summary>

1. No painel de navegação à esquerda, selecione **Target Groups** (Grupos de destino).
2. Selecione **myWPTargetGroup**.
3. Na guia **Targets** (Destinos), espere até que o status da instância seja exibido como **healthy** (com health).

_**Observação:** pode levar até cinco minutos antes que as health checks mostrem um status com health. Você pode passar para a próxima tarefa e voltar mais tarde para verificar após o tempo decorrido._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 7.4: Entrar no aplicativo web do WordPress</mark></summary>

1. No painel de navegação à esquerda, selecione **Load Balancers** (Balanceadores de carga).
2. Selecione a caixa de seleção para o balanceador de carga **myWPAppALB**.
3. Na guia **Description** (Descrição), copie o **nome DNS** em um bloco de notas e coloque o valor **'/wp-login.php'** no final dele para concluir sua URL do aplicativo do WordPress.
   * **Exemplo de uma URL de aplicativo do WordPress:** _myWPAppELB-4e009e86b4f704cc.elb.us-west-2.amazonaws.com/wp-login.php_
4. Cole o valor da URL do aplicativo do WordPress em uma nova guia do navegador.
   * A página _WordPress login_ (Entrada no WordPress) é exibida.
5. Insira o seguinte:
   * **Nome de usuário ou endereço de email:** _wpadmin_
   * **Senha:** _wpadmin123_
   * Selecione o botão **Login** (Entrar).

</details>

***
