# Tarefa 6 – Criar um modelo de execução usando o CloudFormation

***

## <mark style="color:red;">**Visão geral da tarefa**</mark>

Até este momento, você criou os recursos de rede subjacentes, o banco de dados, um mecanismo de armazenamento em cache, o Amazon EFS e um Application Load Balancer (ALB). Está na hora de integrá-los. A Empresa de Exemplo já tem uma conta do WordPress, então o engenheiro de nuvem usará as configurações e definições do ambiente existente para criar um modelo do CloudFormation. Isso inclui todos os novos recursos provisionados para configurar um modelo de execução.&#x20;

Examine um modelo do CloudFormation e crie os recursos necessários. Preste uma atenção especial ao script de dados do usuário. Verifique se há erros na implantação e resolva-os, se necessário. Depois de concluído, você pode criar servidores de aplicativos para dar suporte ao tráfego para o novo ambiente.

***

### <mark style="color:red;">**Requisitos e configuração**</mark>

* Baixe o seguinte arquivo .yaml. _**Observação:** se ele abrir em uma nova janela do navegador, copie o texto e cole-o em um editor de texto._
* Faça upload do arquivo modelo no CloudFormation.
* Você precisa ter as seguintes informações das tarefas anteriores. Se você não tem certeza de onde encontrá-las, consulte Lab Instructions (Instruções do laboratório):
  * **Nome do banco de dados:** cole o nome do banco de dados (Tarefa 2)
  * **Endpoint do banco de dados:** cole o endpoint de escrita (Tarefa 2)
  * **Nome do usuário do banco de dados:** Cole o nome de usuário primário (Tarefa 2)
  * **Senha do banco de dados:** Cole a senha do banco de dados primário (Tarefa 2)
  * **Nome do administrador do WordPress:** o padrão é _wpadmin_
  * **Senha do administrador do WordPress:** o padrão é _wpadmin123_
  * **Endereço de email do administrador do WordPress:** insira um endereço de email
  * **Tipo de instância:** o padrão é _t3.medium_
  * **ALBDnsName:** Cole o valor DNS (Tarefa 5)
  * **LatestAL2AmiId:** deixe o valor padrão
  * **WPElasticFileSystemID:** Cole o valor do ID do sistema de arquivos (Tarefa 4)

***

### <mark style="color:red;">**Descrição da tarefa**</mark>

Nesta tarefa, você usará um modelo do CloudFormation para implantar os dados do usuário do WordPress em um modelo de execução do EC2 Auto Scaling. O modelo inclui os pontos de montagem do EFS e as configurações do Aurora e do ElastiCache.

<figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

| Tarefas                                                        |
| -------------------------------------------------------------- |
| _Obter e revisar o modelo do CloudFormation._                  |
| F_azer upload do modelo para criar a pilha do CloudFormation._ |
| V_er os recursos criados na console._                          |

<details>

<summary><mark style="color:purple;">Tarefa 6.1: Navegar até a console do CloudFormation</mark></summary>

1. No **AWS Management Console**, no menu Services (Serviços), selecione **CloudFormation**.

_**Observação**: você também pode pesquisar por CloudFormation na barra de pesquisa unificada na parte superior da console._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 6.2: Obter e examinar o modelo do CloudFormation</mark></summary>

1. Baixar o modelo do CloudFormation. _(_[_task6.yml_](https://github.com/danncastro/aws-hands-on-labs/blob/main/architecting-on-aws/task6.yml)_)_ &#x20;
2. Abra o arquivo baixado em um **editor de texto**. **Não** use um processador de texto.
3. Examine o modelo do CloudFormation.

</details>

<details>

<summary><mark style="color:purple;">Tarefa 6.3: Criar uma pilha do CloudFormation</mark></summary>

1. Selecione o menu suspenso **Create stack** (Criar pilha).
2. Selecione o botão **With new resources (standard)** (Com novos recursos (padrão)).
   * A página **Create Stack** (Criar pilha) é exibida.
3. Configure o seguinte:
   * Selecione a opção **Template is ready** (O modelo está pronto).
   * Selecione a opção de arquivo **Upload a template** (Carregar um modelo).
   * Selecione o botão **Choose file** (Selecionar arquivo) e selecione _Task 6 template_ (Modelo da tarefa 6) no seu armazenamento local.
   * Selecione o botão **Next** (Próximo).
   * A página **Specify stack details** (Especificar detalhes da pilha) é exibida.
4. **Defina o nome da pilha** como _WPLaunchConfigStack_.
5. **Configure os parâmetros:**
   * **Nome do DB:** cole o nome do banco de dados que você copiou na Tarefa 2.&#x20;
   * **Endpoint do banco de dados:** cole o endpoint de escrita que você copiou na Tarefa 2.
   * **Nome do usuário do banco de dados:** cole o nome de usuário primário copiado na Tarefa 2.
   * **Senha do banco de dados:** cole a senha primária copiada na Tarefa 2.
   * **Nome de usuário do administrador do WordPress:** o padrão é _wpadmin._
   * **Senha de administrador do WordPress:** o padrão é _wpadmin123._
   * **Endereço de email do administrador do WordPress:** insira um endereço de email.
   * **Tipo de instância:** o padrão é _t3.medium_.
   * **ALBDnsName:** cole o valor DNS copiado na Tarefa 5.
   * **LatestAL2AmiId:** deixe o valor-padrão.
   * **WPElasticFileSystemID:** cole o valor do ID do sistema de arquivo que você copiou na Tarefa 4.
6. Selecione o botão **Next** (Próximo).
   * A página **Configure stack options** (Configurar opções de pilha) é exibida.&#x20;
   * Esta página pode ser usada para especificar parâmetros adicionais. Você pode navegar pela página, mas deixe as configurações com os valores-padrão.
7. Selecione o botão **Next** (Próximo).
   * A página **Review** (Revisar) é exibida.&#x20;
8. Selecione o botão **Create stack** (Criar pilha).
   * Agora a pilha entrará no status **CREATE\_IN\_PROGRESS**.
9. Selecione a guia **Stack info** (Informações da pilha).
10. De tempos em tempos, selecione o botão **Refresh** (Atualizar) da console.
11. Aguarde o status mudar para **CREATE\_COMPLETE**.

</details>

<details>

<summary><mark style="color:purple;">Tarefa 6.4: Ver recursos criados na console</mark></summary>

1. Selecione a guia **Resources** (Recursos)

A lista mostra os recursos que estão sendo criados.

</details>

***
