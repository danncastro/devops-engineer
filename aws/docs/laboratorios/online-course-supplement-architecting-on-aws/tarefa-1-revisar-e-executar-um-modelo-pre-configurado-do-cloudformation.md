# Tarefa 1 – Revisar e executar um modelo pré-configurado do CloudFormation

***

## <mark style="color:red;">**Contexto da tarefa**</mark>

A empresa deseja implantar um novo aplicativo web no WordPress na conta de hospedagem na web existente. O primeiro passo é reunir os requisitos para o projeto de arquitetura. Para ajudar você a começar, a equipe de rede forneceu uma lista de solicitações para garantir que não haja problemas com o cenário existente. Isso inclui o intervalo CIDR da Amazon VPC. Usando esse intervalo de endereços, crie uma VPC com duas sub-redes públicas, duas sub-redes de aplicativo privado e duas sub-redes de banco de dados privado. Lembre-se de anexar um internet gateway à VPC com um gateway NAT para rotear o tráfego. Eles também solicitaram dois endereços de IP elásticos. Verifique se você associou:&#x20;

* A sub-rede pública ao internet gateway
* As sub-redes de aplicativo privado e do banco de dados privado com o gateway NAT

Eles também forneceram as tabelas de rotas necessárias com as associações de sub-rede.

Seu engenheiro de nuvem transferiu a solicitação de informações para um modelo do CloudFormation e configurou os security groups e as saídas necessárias para implantações futuras. Revise o modelo do CloudFormation com seu engenheiro de nuvem, implante o modelo e verifique novamente com a equipe de rede para validar se a compilação atende a todos os requisitos.

***

### <mark style="color:red;">**Descrição da tarefa**</mark>

Você vai projetar e implementar uma implantação altamente disponível e dimensionável da pilha de aplicativos do WordPress. Use um modelo do CloudFormation para implantar os recursos de rede necessários para dar suporte ao aplicativo.

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

| Tarefas                                                                                          |
| ------------------------------------------------------------------------------------------------ |
| _Baixe e revise o arquivo de modelo para entender a infraestrutura que está sendo implantada._   |
| _Faça upload do arquivo de modelo para criar a pilha do CloudFormation._                         |
| _Ver recursos criados na console._                                                               |

<details>

<summary><mark style="color:purple;">Tarefa 1.1 – Navegar até a console do CloudFormation</mark></summary>

1. No AWS Management Console, no menu Services (Serviços), selecione CloudFormation.

_**Observação**: você também pode pesquisar por "CloudFormation" na barra de pesquisa unificada na parte superior da console._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 1.2 – Obter e examinar o modelo do CloudFormation</mark></summary>

1. Baixar o modelo do CloudFormation. _(As informações de download são fornecidas após esta seção)_ &#x20;
2. Abra o arquivo baixado em um editor de texto (não em um processador de texto).
3. Revise o modelo do CloudFormation.
4. Preveja quais recursos são criado por esse modelo.

</details>

<details>

<summary><mark style="color:purple;">Tarefa 1.3 – Criar uma pilha do CloudFormation</mark></summary>

1. Selecione o botão **Create stack** (Criar pilha).&#x20;
   * A página **Create stack** (Criar pilha) é exibida.

_**Observação**: se a console iniciar você na página Stacks (Pilhas) em vez da página inicial do Amazon CloudFormation, você poderá acessar a página 'Create stack' (Criar pilhas) em duas etapas._

1. Selecione o menu suspenso **Create stack** (Criar pilha).
2. Selecione o botão **With new resources (standard)** (Com novos recursos (padrão)).&#x20;
   * A página **Create Stack** (Criar pilha) é exibida.&#x20;
3. Escolha a opção **Template is ready** (O modelo está pronto).
4. Selecione a opção **Upload a template file** (Carregar um arquivo de modelo).
5. Selecione o botão **Choose file** (Escolher arquivo) e selecione o modelo da Tarefa 1 no armazenamento local.
6. Selecione o botão **Next** (Próximo).&#x20;
   * A página **Specify stack details** (Especificar detalhes da pilha) é exibida.
7. **Defina o nome da pilha como:** _VPCStack_
8. Deixe os parâmetros configurados com os valores-padrão.
9. Selecione o botão **Next** (Próximo).&#x20;
   * A página **Configure stack options** (Configurar opções da pilha) é exibida.&#x20;

_**Observação**: essa página pode ser usada para especificar parâmetros adicionais. Você pode navegar pela página, mas deixe as configurações nos valores-padrão._

1. Selecione o botão **Next** (Próximo).&#x20;
   * A página **Review** (Revisar) é exibida.
2. Selecione o botão **Create stack** (Criar pilha).
   * A página de **detalhes da pilha** é exibida.

_**Observação**: a pilha agora entrará no status CREATE\_IN\_PROGRESS._

1. Selecione a guia **Stack info** (Informações da pilha).
2. De tempos em tempos, selecione o botão de console **Refresh** (Atualizar).
3. Espere o status mudar para **CREATE\_COMPLETE.**\
   _**Observação**: essa pilha pode levar até cinco minutos para implantar os recursos._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 1.4 – Ver recursos criados na console</mark></summary>

1. Selecione a guia **Resources** (Recursos).
2. Revise os recursos que foram implantados na pilha.
3. Selecione a guia **Outputs** (Saídas).
4. Revise os pares de chave-valor na seção de saídas. Esses valores serão úteis em tarefas posteriores do laboratório.

</details>

{% tabs %}
{% tab title="VERIFICAÇÃO DE SAÍDAS" %}
Você deve ver uma lista de saídas na guia **Outputs** (Saídas). Examine os pares de chave-valor nesta seção. Esses valores podem ser úteis em tarefas posteriores do laboratório.

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="VERIFICAÇÃO DOS RECURSOS" %}
Procure na guia **Resources** (Recursos) para revisar os recursos que foram implantados na pilha.

<figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

***
