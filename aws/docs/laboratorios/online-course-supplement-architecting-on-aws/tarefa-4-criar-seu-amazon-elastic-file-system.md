# Tarefa 4 – Criar seu Amazon Elastic File System

***

## <mark style="color:red;">**Contexto da tarefa**</mark>

A Empresa de Exemplo está com problemas com o prazo de entrega do pedido de novo hardware. Isso está diminuindo a capacidade dela de integrar novos clientes e expandir os negócios. A equipe de SysOps tem uma solicitação para uma solução de armazenamento nativa da nuvem. Ela precisa confirmar se as políticas de backup e as configurações de criptografia atendem aos requisitos internos e de conformidade regulatória. Gerenciar o tempo, o custo e a conformidade dará à Empresa de Exemplo uma vantagem competitiva.&#x20;

Você recomenda o Amazon EFS para a empresa, por ser um sistema de arquivos elástico simples, sem servidor e com definição única. Com o EFS, eles podem compartilhar os dados com segurança, sem provisionar nem gerenciar o armazenamento.&#x20;

Sua tarefa é criar um sistema de arquivos elástico da Amazon que atende aos requisitos da equipe do SysOps.

***

### <mark style="color:red;">**Requisitos e configuração**</mark>

O sistema de arquivos elástico:

* Precisa ter disponibilidade e durabilidade regional
* Precisa ter um desempenho de **uso geral** para controlar os custos
* Precisa ter uma taxa de transferência com **intermitência** para dimensionar o tamanho do arquivo
* Não precisa de uma **política de sistema de arquivos** criada nesse momento

**Não se esqueça!**

* Desligue os **backups automáticos** e **criptografia de dados inativos.**
* Implante no **LabVPC** e nas sub-redes de aplicativo em **ambas as Zonas de Disponibilidade.**
* Use o **Security group do EFS** já configurado pela sua equipe de segurança.
* Anote o **ID do sistema de arquivos.**

***

### <mark style="color:red;">**Descrição da tarefa**</mark>

Nesta tarefa, você vai criar e configurar um Amazon EFS personalizado.

<figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

| Tarefas                       |
| ----------------------------- |
| _Criar um EFS_                |
| C_opiar os metadados do EFS._ |

<details>

<summary><mark style="color:purple;">Tarefa 4.1: Navegar até a console do Amazon EFS</mark></summary>

1. No AWS Management Console, no menu Services (Serviços), selecione EFS.
   * _Observação: você também pode pesquisar por EFS na barra de pesquisa unificada na parte superior da console._

</details>

<details>

<summary><mark style="color:purple;">Tarefa 4.2: Criar um Amazon EFS</mark></summary>

1. Selecione o botão **Create file system** (Criar sistema de arquivos).
2. Selecione o botão **Customize** (Personalizar).
   * A página **File system settings** (Configurações do sistema de arquivo) é exibida.
3. Na seção **General** (Geral), configure:
   * **Nome:** _myWPEFS_
   * **Desmarque** a opção _Enable automatic backups_ (Ativar backups automáticos).
   * **Desmarque** a opção _Enable encryption of data at rest_ (Ativar a criptografia de dados inativos).
   * Em **Tags** (seção opcional):
     * **Nome da tag:** _Nome_
     * **Valor de tag **_**–**_** opcional:** _myWPEFS_
   * Deixe todas as outras configurações como o valor-padrão.
   * Selecione o botão **Next** (Próximo).
   * A página **Network access** (Acesso de rede) é exibida.
4. No menu suspenso **Virtual Private Cloud (VPC)** , selecione _LabVPC_.
5. Em Mount Targets (Destinos de mount) configure o seguinte:
   * **Selecione** _Availability Zone A_ (Zona de Disponibilidade A).
   * **Selecione** _AppSubnet1_.
   * **Remova** o Security Group _padrão_.
   * **Selecione** _EFSMountTargetSecurityGroup_ no menu suspenso.&#x20;
   * **Selecione** _Availability Zone B_ (Zona de Disponibilidade B).
   * **Selecione** _AppSubnet2_.
   * **Remova** o Security Group _padrão_.
   * **Selecione** o _EFSMountTargetSecurityGroup_ no menu suspenso.
6. Selecione o botão **Next** (Próximo).
   * A página **File system policy – optional** (Política do sistema de arquivos – opcional) é exibida.
   * Configurar essa página não é necessário neste laboratório.
7. Selecione o botão **Next** (Próximo).&#x20;
   * A página **Review and create** (Revisar e criar) é exibida.
8. &#x20;Selecione o botão **Create** (Criar).
9. O estado do sistema de arquivos é exibido como **Available** (Disponível) após alguns minutos.

</details>

<details>

<summary><mark style="color:purple;">Tarefa 4.3: Copiar os metadados do EFS</mark></summary>

1. Selecione **File systems** (Sistemas de arquivos) no painel de navegação.
2. &#x20;Copie o **ID do sistema de arquivos** gerado para o **myWPEFS** em um bloco de notas. Ele tem um formato igual a _**fs-a1234567**_.

</details>

***
