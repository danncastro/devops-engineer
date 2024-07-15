# Tarefa 7 – Criar os servidores de aplicativos configurando um grupo do Auto Scaling e uma política d

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
