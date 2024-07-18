# Tarefa 3 – Criar um ElastiCache for Memcached

***

## <mark style="color:red;">**Contexto da tarefa**</mark>

O acesso ao banco de dados confirmado por DBA e todos os requisitos foram cumpridos. O plano do projeto tinha uma nota informando que o desempenho do banco de dados estava muito lento. Para melhorar a taxa de resultados encontrados e o tempo de resposta, você recomenda que a empresa use um serviço de armazenamento em cache.&#x20;

A empresa não tem uma pessoa familiarizada com o gerenciamento de software de cache, mas o aplicativo precisa ser dimensionado em resposta às solicitações do usuário. A equipe de engenharia relatou altos níveis de latência no aplicativo legado. Eles também precisam de uma solução altamente disponível, mas que requer apenas um tipo de instância muito pequena. Você recomendou o ElastiCache com o Memcached.&#x20;

Crie um pequeno mecanismo de cache com dois nós e revise-o com o DBA e o engenheiro de nuvem, que será responsável por gerenciar esse serviço daqui para frente.

***

### <mark style="color:red;">**Requisitos e configuração**</mark>

Você precisará:

* Implantar um mecanismo de cluster do **Memcached**.
* Usar os tipos de nó **cache.t3.micro**.
* Implantar **dois nós.**
* Usar o **ElastiCacheSecurityGroup** que sua equipe de segurança já configurou.
* **Anotar o ARN do cluster.**

***

### <mark style="color:red;">**Descrição da tarefa**</mark>

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

| Tarefas                           |
| --------------------------------- |
| _Criar o cluster do ElastiCache._ |

<details>

<summary><mark style="color:purple;">Tarefa 3.1: Navegar até a console do Amazon ElastiCache</mark></summary>

1. No AWS Management Console, no menu Services (Serviços), selecione ElastiCache.

* _Observação: você também pode pesquisar por ElastiCache na barra de pesquisa unificada na parte superior de console._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 3.2: Criar um cluster do Amazon ElastiCache</mark></summary>

1. Selecione o botão **Get Started Now** (Começar agora).
   * A página **Create your Amazon ElastiCache cluster** (Criar o cluster do Amazon ElastiCache) será exibida.
2. Selecione a opção **Memcached** em **Cluster engine** (Mecanismo do cluster).
3. Verifique se a opção **Amazon Cloud** (Nuvem da Amazon) está selecionada na seção **Location** (Localização).
4. Na seção de configurações do Memcached, configure o seguinte:
   * **Nome:** _MyWPCache_
   * **Tipo de nó**
     * Selecione o menu suspenso.
     * A janela **select node type** (Selecionar tipo de nó) é exibida.
     * Selecione a guia chamada **t3**.
     * Selecione a opção **cache.t3.micro**.
     * Selecione o botão **Save** (Salvar).
   * **Número de nós** 2
5. Expanda a seção de configurações **Advanced Memcached** (Memcached avançado).
6. Configure os itens a seguir na seção de configurações Advanced Memcached:
   * **Grupo de sub-rede:** _elasticachesubnetgroup_\

   * **Colocação das zonas de disponibilidade:** selecione a opção _Select zones_ (Selecionar zonsa).
   * **Security Groups:** selecione o _ícone de edição_.&#x20;
     * Selecione o Security group chamado **ElastiCacheSecurityGroup**.
     * Desmarque **default** (padrão).
     * Selecione o botão **Save** (Salvar).
   * Tags:&#x20;
     * **Chave:** _Nome_
     * **Valor:** _MyWPCache_
7. Selecione o botão **Create** (Criar).

O status do ElastiCache será **available** (disponível) após alguns minutos. Não é necessário esperar.

</details>

***
