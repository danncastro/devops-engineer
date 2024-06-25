# Armazenamento de objeto com o Amazon Simple Storage Service

***

## <mark style="color:red;">Amazon S3</mark>

O Amazon Simple Storage Service (Amazon S3) é uma solução de armazenamento de objetos na nuvem oferecida pela AWS. Diferente do Amazon Elastic Block Store (Amazon EBS), o Amazon S3 é independente da computação e permite acessar seus dados de qualquer lugar na web.

#### <mark style="color:blue;">**Características do Amazon S3**</mark>

| Armazenamento de Objetos                                                                                                                                                                                                                                                          | Independência da Computação                                                                                                                                                                                                             | Escalabilidade Ilimitada                                                                                                                                                                                                        | Resiliência e Durabilidade                                                                                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>O Amazon S3 armazena dados em uma estrutura plana, usando identificadores exclusivos para localizar objetos. Cada objeto é composto por dados (o arquivo) e metadados (informações sobre o arquivo).</p> | <p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>O Amazon S3 não está vinculado a instâncias de computação específicas. Os dados armazenados no S3 podem ser acessados de qualquer lugar na web.</p>            | <p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>Você pode armazenar uma quantidade praticamente ilimitada de dados no Amazon S3. Não há limite para o número de objetos que você pode armazenar.</p>   | <p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>O Amazon S3 armazena dados de forma redundante em várias zonas de disponibilidade, garantindo alta durabilidade e disponibilidade dos dados.</p> |
| <p><mark style="color:green;"><strong>Benefício</strong></mark>: </p><p>Permite a fácil organização, recuperação e gerenciamento de grandes quantidades de dados sem a complexidade de estruturas hierárquicas.</p>                                                               | <p><mark style="color:green;"><strong>Benefício</strong></mark>: </p><p>Proporciona alta flexibilidade e acessibilidade, permitindo que os dados sejam usados por diferentes serviços e aplicações na nuvem ou em outros ambientes.</p> | <p><mark style="color:green;"><strong>Benefício</strong></mark>: </p><p>Ideal para casos de uso que requerem armazenamento de grandes volumes de dados, como backups, repositórios de conteúdo e grandes arquivos de dados.</p> | <p><mark style="color:green;"><strong>Benefício</strong></mark>: </p><p>Proporciona segurança e confiabilidade, assegurando que os dados estejam sempre disponíveis e protegidos contra falhas.</p>                       |

#### <mark style="color:blue;">**Casos de Uso Comuns**</mark>

<table><thead><tr><th>Backup e Recuperação</th><th>Armazenamento de Arquivos Estáticos</th><th width="200">Repositório de Dados para Análise</th><th>Distribuição de Conteúdo</th></tr></thead><tbody><tr><td><p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>O Amazon S3 é amplamente utilizado para backup e recuperação de dados devido à sua durabilidade e escalabilidade.</p></td><td><p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>Ideal para armazenar arquivos estáticos como imagens, vídeos e documentos que precisam ser acessados de forma rápida e eficiente.</p></td><td><p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>Utilizado como um repositório central para armazenar grandes volumes de dados não estruturados que podem ser analisados posteriormente.</p></td><td><p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>Pode ser integrado com Amazon CloudFront para distribuir conteúdo globalmente com baixa latência.</p></td></tr><tr><td><mark style="color:green;"><strong>Benefício</strong></mark>: Proporciona uma solução de backup confiável que pode ser acessada de qualquer lugar, facilitando a recuperação de dados em caso de falhas ou desastres.</td><td><p><mark style="color:green;"><strong>Benefício</strong></mark>: </p><p>Permite a entrega rápida e eficiente de conteúdo para usuários finais, melhorando a experiência do usuário.</p></td><td><p><mark style="color:green;"><strong>Benefício</strong></mark>: </p><p>Facilita a análise de grandes conjuntos de dados usando serviços de análise da AWS, como Amazon Athena e Amazon Redshift.</p></td><td><p><mark style="color:green;"><strong>Benefício</strong></mark>: </p><p>Melhora a performance e a disponibilidade do conteúdo para usuários em diferentes partes do mundo.</p></td></tr></tbody></table>

O Amazon S3 é uma solução robusta e flexível para armazenamento de objetos na nuvem, oferecendo alta durabilidade, escalabilidade e acessibilidade. Ele é ideal para uma ampla gama de casos de uso, desde backups e recuperação de dados até distribuição de conteúdo e análise de grandes volumes de dados.

***

### <mark style="color:red;">Conceitos do Amazon S3</mark>

No Amazon S3, os objetos são armazenados em contêineres chamados **buckets**. A criação de um bucket é um passo obrigatório antes de fazer upload de qualquer objeto. Vamos detalhar os principais conceitos do Amazon S3.

#### <mark style="color:blue;">**Buckets**</mark>

| Criação de Buckets                                                                                                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><mark style="color:purple;"><strong>Região</strong></mark>: </p><p>Ao criar um bucket, é necessário especificar a região da AWS onde ele deve residir. Escolher a mesma região dos outros recursos pode reduzir latências e custos de transferência de dados.</p> |
| <p><mark style="color:purple;"><strong>Nome</strong></mark>: </p><p>O nome do bucket deve ser único em todas as contas da AWS. A exclusividade global garante que os nomes de buckets não conflitem.</p>                                                             |

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719327600/cwky-UKh-jfddaL_CDJzyw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/pBxkWuItmb7cQSVP_VOKwWkKMaPqtNjqh.jpg" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Estrutura do URL**</mark><mark style="color:blue;">:</mark>&#x20;

O URL de um objeto no S3 inclui o nome do bucket, o serviço S3, o provedor de serviços (amazonaws.com), e o caminho do objeto dentro do bucket. Por exemplo:

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719327600/cwky-UKh-jfddaL_CDJzyw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/rUlunlFG0cgIgqmr_lN3qi2oH8LJi2EOC.jpg" alt=""><figcaption></figcaption></figure>

| Exemplo de URL de Objeto                                                                                            |
| ------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;">**Nome do Bucket**</mark><mark style="color:purple;">:</mark> `doc`                     |
| <mark style="color:purple;">**Serviço e Provedor**</mark><mark style="color:purple;">:</mark> `s3.amazonaws.com`    |
| <mark style="color:purple;">**Nome da Chave**</mark><mark style="color:purple;">:</mark> `2006-03-01/AmazonS3.html` |

#### <mark style="color:blue;">**Organização de Objetos**</mark>

| Pastas e Estrutura Plana                                                                                                                                                                                                                                    |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><mark style="color:purple;"><strong>Pastas</strong></mark>: </p><p>Embora o S3 permita a criação de pastas para organizar objetos, a estrutura subjacente é plana. As pastas são implícitas e ajudam na organização visual e na navegação dos dados.</p> |
| <p><mark style="color:purple;"><strong>Nome da Chave</strong>:</mark> </p><p>Cada objeto possui um nome de chave que representa seu identificador único dentro do bucket. As pastas são representadas como parte desse nome de chave.</p>                   |

#### <mark style="color:blue;">**Durabilidade e Disponibilidade**</mark>

| Alta Durabilidade                                                                                                                         | Alta Disponibilidade:                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| O Amazon S3 oferece 99,999999999% (11 noves) de durabilidade, garantindo que os objetos armazenados sejam altamente resilientes a falhas. | Com 99,99% de disponibilidade anual, o S3 assegura que os objetos estejam acessíveis na maioria do tempo. |

#### <mark style="color:blue;">**Exemplo Prático**</mark>

1. **Criando um Bucket**:
   * Se você deseja armazenar fotos, pode criar um bucket chamado `meus-arquivos-fotos` na região `us-east-1`.
2.  **Organização com Pastas**:

    * Dentro do bucket `meus-arquivos-fotos`, você pode criar uma pasta chamada `2024/Fotos_Viagem` e fazer upload de fotos com nomes como `foto1.jpg`, `foto2.jpg`.
    * O caminho do objeto seria:



    ```bash
    http://meus-arquivos-fotos.s3.amazonaws.com/2024/Fotos_Viagem/foto1.jpg
    ```

O Amazon S3 simplifica o armazenamento e a recuperação de objetos, oferecendo alta durabilidade, disponibilidade e flexibilidade. A criação de buckets e a organização de objetos com pastas proporcionam uma estrutura compreensível e eficaz para gerenciar grandes volumes de dados na nuvem.

***

### <mark style="color:red;">Casos de uso do Amazon S3</mark>

O Amazon S3 é um serviço de armazenamento versátil e amplamente utilizado devido à sua capacidade de armazenar grandes quantidades de dados com alta durabilidade e disponibilidade. Aqui estão alguns dos casos de uso mais comuns:

#### <mark style="color:blue;">**Backup e Armazenamento**</mark>

| Backup de Arquivos:                                                                                                                                                                          | Arquivamento:                                                                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| O Amazon S3 é um destino ideal para backups devido à sua redundância e durabilidade. Por exemplo, os snapshots do Amazon EBS são armazenados no S3 para aproveitar sua alta disponibilidade. | O Amazon S3 pode ser usado para arquivar dados que precisam ser armazenados por longos períodos, como registros financeiros ou dados de conformidade. |

#### <mark style="color:blue;">**Hospedagem de Mídia**</mark>

| Upload de Vídeos, Fotos e Música                                                                                                                                                                                                             | Streaming de Mídia                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Com suporte para objetos de até 5 TB e capacidade ilimitada de armazenamento, o S3 é ideal para hospedar mídia. Plataformas que lidam com grandes volumes de arquivos de mídia, como serviços de streaming, podem se beneficiar muito do S3. | Arquivos armazenados no S3 podem ser facilmente integrados com serviços de entrega de conteúdo (CDN) para streaming de áudio e vídeo. |

#### <mark style="color:blue;">**Entrega de Software**</mark>

| Distribuição de Aplicações                                                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Empresas podem usar o S3 para hospedar aplicações e atualizações de software que os clientes podem baixar. Isso é útil para empresas de software que precisam distribuir pacotes grandes ou atualizações frequentes. |

#### <mark style="color:blue;">**Data Lakes**</mark>

| Armazenamento Escalável de Dados                                                                                                                                                                         | Integração com Ferramentas de Análise                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| O Amazon S3 é perfeito para a criação de data lakes devido à sua capacidade de escalar de gigabytes para petabytes. Empresas podem consolidar dados de diferentes fontes em um único local para análise. | O S3 se integra facilmente com ferramentas de análise da AWS, como AWS Glue e Amazon Athena, facilitando a análise de grandes conjuntos de dados. |

#### <mark style="color:blue;">**Hospedagem de Sites Estáticos**</mark>

| Sites de HTML, CSS e JavaScript                                                                                                                                                           | Baixo Custo e Alta Disponibilidade                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| O S3 pode ser configurado para hospedar sites estáticos. Isso é ideal para páginas web que não necessitam de processamento no servidor, como portfólios pessoais, blogs ou landing pages. | Hospedar um site estático no S3 é uma solução econômica e com alta disponibilidade. |

#### <mark style="color:blue;">**Armazenamento de Conteúdo Estático**</mark>

| Armazenamento de Arquivos Grandes                                                                                                                   | Acesso Global                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Com suporte para grandes arquivos e escalabilidade ilimitada, o S3 é ideal para armazenar conteúdo estático, como documentos, relatórios e imagens. | Os objetos armazenados no S3 podem ser acessados de qualquer lugar do mundo, facilitando o compartilhamento e a distribuição de conteúdo estático. |

#### <mark style="color:blue;">Benefícios Gerais do Amazon S3</mark>

| Alta Durabilidade e Disponibilidade                                          | Escalabilidade e Flexibilidade                                                    | Segurança                                                                    | Economia de Custo                                                                                 |
| ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Garantia de 99,999999999% de durabilidade e 99,99% de disponibilidade anual. | Escalabilidade praticamente ilimitada, permitindo crescer conforme a necessidade. | Suporte para criptografia de dados e gerenciamento de permissões detalhadas. |  Modelo de pagamento por uso, permitindo economizar ao pagar apenas pelo armazenamento utilizado. |

O Amazon S3 é uma solução poderosa e flexível para uma ampla variedade de casos de uso, desde backup e armazenamento de mídia até data lakes e hospedagem de sites estáticos. Sua capacidade de escalar e oferecer alta durabilidade e disponibilidade o torna uma escolha confiável para empresas de todos os tamanhos.

***

### <mark style="color:red;">Escolha a opção de conectividade certa para os recursos</mark>

O Amazon S3 oferece controle granular sobre a acessibilidade e a segurança dos seus recursos, garantindo que você possa gerenciar quem tem acesso a seus buckets, pastas e objetos de maneira adequada.

#### <mark style="color:blue;">**Privacidade Padrão**</mark>

| Privado por Padrão                                                                                                                                                          | Proteção de Recursos                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Inicialmente, todos os recursos no Amazon S3, incluindo buckets, pastas e objetos, são privados. Somente o usuário ou a conta da AWS que criou o recurso pode visualizá-lo. | Esta configuração padrão garante que os dados são protegidos contra acessos não autorizados. |

#### <mark style="color:blue;">**Tornando Recursos Públicos**</mark>

| Recursos Públicos                                                                                                                                                                                                 | Acessibilidade                                                                                                                                            |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Se desejar que todos na Internet possam ver determinados recursos, você pode optar por torná-los públicos. Isso pode ser útil, por exemplo, para hospedar um site estático ou compartilhar arquivos publicamente. | Quando um recurso é público, qualquer pessoa na Internet pode visualizá-lo, o que pode ser apropriado para conteúdos que não requerem proteção de acesso. |

#### <mark style="color:blue;">**Gerenciamento Granular de Acesso**</mark>

Na maioria das situações, você vai querer um controle mais detalhado sobre quem pode acessar seus recursos e o que eles podem fazer com eles. Para isso, o Amazon S3 oferece dois principais mecanismos de gerenciamento de acesso:

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719327600/cwky-UKh-jfddaL_CDJzyw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/iFGbZ4vGe-DM1kIV_xoovb5kIZBeTCfwO.png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Políticas do IAM (Identity and Access Management)**</mark>

| Objetivo                                                                                            | Escopo                                                          | Flexibilidade                                                                                       |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Definem permissões que determinam quem pode acessar os recursos do S3 e o que podem fazer com eles. | Aplicáveis a usuários, grupos e funções dentro da conta da AWS. | Permite especificar ações permitidas ou negadas para diferentes recursos e em diferentes condições. |

#### <mark style="color:blue;">**Políticas de Bucket do S3**</mark>

| Objetivo                                                       | Escopo                                                                                       | Controle Detalhado                                                                                                             |
| -------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Especificam permissões para os buckets e objetos dentro deles. | Aplicam-se diretamente aos buckets e controlam o acesso aos objetos contidos nesses buckets. | Permite definir quem (quais usuários ou contas) pode acessar o bucket, e quais ações (como leitura ou escrita) são permitidas. |

#### <mark style="color:blue;">Implementação de Políticas de Acesso</mark>

Ao implementar políticas de acesso, você pode ser específico sobre:

| Quem                                                                 | O Que                                                                                                                                             | Condições                                                                                                                |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Especificar usuários, grupos ou funções que podem acessar o recurso. | Definir quais ações esses usuários podem realizar, como listar objetos em um bucket, fazer upload de novos objetos ou excluir objetos existentes. | Aplicar condições adicionais, como restringir o acesso a partir de determinados endereços IP ou em horários específicos. |

#### <mark style="color:blue;">Exemplo de Política</mark>

Aqui está um exemplo de uma política de bucket que permite que qualquer pessoa na Internet possa ler (baixar) um objeto, mas não permite a escrita (upload) ou exclusão de objetos:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::meu-bucket-exemplo/*"
        }
    ]
}
```

Gerenciar o acesso aos seus recursos no Amazon S3 com políticas de IAM e políticas de bucket permite um controle granular sobre quem pode fazer o quê com seus dados. Isso garante que você possa proteger informações sensíveis enquanto compartilha de forma segura os dados públicos com a Internet, tudo de acordo com suas necessidades específicas de segurança e acessibilidade.

***

### <mark style="color:red;">Políticas do IAM</mark>

As políticas do IAM (Identity and Access Management) são uma ferramenta poderosa para gerenciar o acesso aos recursos da AWS, incluindo o Amazon S3. Elas permitem definir permissões detalhadas para usuários, grupos e funções, controlando quem pode executar quais ações em quais recursos. Ao aplicar esse conhecimento ao Amazon S3, você pode gerenciar de forma eficiente e segura o acesso aos seus buckets e objetos.

#### <mark style="color:blue;">**Aplicando Políticas do IAM ao Amazon S3**</mark>

Quando você anexa políticas do IAM a usuários, grupos ou funções, essas políticas especificam as ações que eles podem executar nos recursos do Amazon S3. As políticas do IAM são versáteis e podem ser usadas para controlar o acesso a uma ampla variedade de serviços da AWS, não se limitando apenas ao Amazon S3.

#### <mark style="color:blue;">**Cenários para Usar Políticas do IAM com Amazon S3**</mark>

<table><thead><tr><th width="375">Muitos Buckets com Diferentes Requisitos de Permissão</th><th>Gerenciamento Centralizado de Políticas</th></tr></thead><tbody><tr><td><p><mark style="color:purple;"><strong>Simplificação</strong>:</mark> </p><p>Em vez de criar e gerenciar múltiplas políticas de bucket do S3, você pode usar políticas do IAM para centralizar e simplificar o gerenciamento de permissões.</p></td><td><p><mark style="color:purple;"><strong>Centralização</strong>:</mark> </p><p>Mantendo todas as políticas em um único local centralizado, é mais fácil gerenciar, revisar e auditar as permissões.</p></td></tr><tr><td><p><mark style="color:purple;"><strong>Eficiência</strong>:</mark> </p><p>Reduz a complexidade de gerenciar várias políticas individuais de bucket, permitindo aplicar permissões de forma consistente e eficiente.</p></td><td><p><mark style="color:purple;"><strong>Consistência</strong>:</mark> </p><p>Garante que todas as políticas aplicadas estejam de acordo com as práticas de segurança e conformidade da sua organização.</p></td></tr></tbody></table>

#### <mark style="color:blue;">**Exemplo de Política do IAM para Amazon S3**</mark>

Aqui está um exemplo de uma política do IAM que concede permissões a um usuário para listar todos os buckets e acessar objetos em um bucket específico:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:ListAllMyBuckets",
            "Resource": "arn:aws:s3:::*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::meu-bucket-exemplo",
                "arn:aws:s3:::meu-bucket-exemplo/*"
            ]
        }
    ]
}
```

#### <mark style="color:blue;">**Benefícios de Usar Políticas do IAM**</mark>

| Flexibilidade                                                                                           | Segurança                                                                                                   | Centralização                                                                                               |
| ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Permite definir permissões de forma detalhada e específica para diferentes usuários, grupos ou funções. | Garante que as permissões sejam atribuídas de maneira segura, minimizando o risco de acesso não autorizado. | Facilita o gerenciamento e a auditoria de permissões, mantendo todas as políticas em um local centralizado. |

Usar políticas do IAM para gerenciar o acesso ao Amazon S3 oferece uma maneira flexível e eficiente de controlar quem pode fazer o quê com seus dados. Ao centralizar as políticas, você pode garantir uma gestão de permissões mais consistente e segura, adaptando-se às necessidades específicas de sua organização e garantindo que os recursos do Amazon S3 sejam acessados apenas por aqueles que realmente precisam.

***

### <mark style="color:red;">Políticas de buckets do S3</mark>

As políticas de buckets do Amazon S3 permitem que você controle o acesso aos buckets e aos objetos armazenados dentro deles. Semelhante às políticas do IAM, as políticas de buckets são definidas em formato JSON. No entanto, ao contrário das políticas do IAM que são anexadas a usuários, grupos e funções, as políticas de buckets do S3 são anexadas diretamente aos buckets.

#### <mark style="color:blue;">**Estrutura das Políticas de Buckets do S3**</mark>

As políticas de buckets do S3 especificam quais ações são permitidas ou negadas no bucket e são altamente personalizáveis. A estrutura básica de uma política de bucket do S3 é composta por uma ou mais instruções (**statements**), cada uma especificando um conjunto de permissões.

#### <mark style="color:blue;">**Exemplo de Política de Bucket do S3**</mark>

Aqui está um exemplo de uma política de bucket do S3 que permite acesso público de leitura a todos os objetos em um bucket chamado `employeebucket`:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": ["s3:GetObject"],
            "Resource": ["arn:aws:s3:::employeebucket/*"]
        }
    ]
}
```

#### <mark style="color:blue;">**Componentes da Política**</mark>

* **Version**: Especifica a versão da política. Neste exemplo, a versão é `2012-10-17`.
* **Statement**: Uma lista de instruções. Cada instrução contém:
  * **Sid**: Um identificador opcional para a instrução.
  * **Effect**: Pode ser `Allow` (permitir) ou `Deny` (negar).
  * **Principal**: Especifica o principal ao qual a instrução se aplica. `*` significa qualquer pessoa (acesso público).
  * **Action**: As ações permitidas ou negadas. `s3:GetObject` permite leitura dos objetos.
  * **Resource**: Especifica o bucket e objetos aos quais a instrução se aplica. `arn:aws:s3:::employeebucket/*` refere-se a todos os objetos no bucket `employeebucket`.

#### <mark style="color:blue;">**Cenários para Usar Políticas de Buckets do S3**</mark>

| Acesso Entre Contas                                                                                                                                                                      | Gerenciamento de Acessos Públicos                                                                                                                                                                                                      | Limite de Tamanho de Políticas                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><mark style="color:purple;"><strong>Simplificação</strong>:</mark> </p><p>Permite que outra conta da AWS coloque objetos no seu bucket sem a necessidade de criar funções do IAM.</p> | <p><mark style="color:purple;"><strong>Leitura Pública</strong>:</mark> </p><p>Permite que qualquer pessoa na internet leia os objetos no bucket. Ideal para hospedar conteúdo público, como sites estáticos ou arquivos de mídia.</p> | <p><mark style="color:purple;"><strong>Capacidade</strong>:</mark> </p><p>Políticas de buckets do S3 têm um limite de tamanho maior em comparação com políticas do IAM, permitindo gerenciar permissões mais complexas sem atingir os limites de tamanho.</p> |
| <p><mark style="color:purple;"><strong>Flexibilidade</strong>:</mark> </p><p>Facilita o compartilhamento de acesso entre diferentes contas da AWS de forma simples e direta.</p>         | <p><mark style="color:purple;"><strong>Granularidade</strong>:</mark> </p><p>Controle granular sobre quem pode executar quais ações nos objetos do bucket.</p>                                                                         |                                                                                                                                                                                                                                                               |

#### <mark style="color:blue;">**Benefícios das Políticas de Buckets do S3**</mark>

<table><thead><tr><th width="249">Facilidade de Configuração</th><th>Escalabilidade</th><th>Segurança</th></tr></thead><tbody><tr><td>Simples de configurar e gerenciar, especialmente para cenários de acesso público ou entre contas.</td><td>Adequado para ambientes onde as políticas do IAM atingem limites de tamanho.</td><td>Permite aplicar regras de acesso específicas e seguras diretamente aos buckets.</td></tr></tbody></table>

As políticas de buckets do Amazon S3 são uma ferramenta essencial para gerenciar o acesso aos seus dados de forma segura e eficiente. Elas oferecem uma maneira direta e flexível de definir permissões, permitindo que você controle quem pode acessar e interagir com os objetos nos seus buckets. Seja para acesso público, compartilhamento entre contas ou gerenciamento centralizado de permissões, as políticas de buckets do S3 fornecem a granularidade e a segurança necessárias para proteger seus dados.

***

### <mark style="color:red;">Criptografia do Amazon S3</mark>

O Amazon S3 oferece uma segurança robusta para proteger seus dados tanto em trânsito quanto em repouso. A criptografia é uma parte essencial dessa segurança.

#### <mark style="color:blue;">**Criptografia em Trânsito**</mark>

Para garantir a segurança dos dados enquanto eles se movimentam entre você e o Amazon S3, você pode utilizar:

| Criptografia no Lado do Cliente                                                                                             | Secure Sockets Layer (SSL)                                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Criptografa os dados antes de enviá-los ao Amazon S3. Isso requer que você gerencie o processo de criptografia e as chaves. | Um protocolo padrão de segurança para estabelecer um link criptografado entre o cliente e o servidor. O Amazon S3 suporta SSL para transferir dados de maneira segura. |

#### <mark style="color:blue;">**Criptografia em Repouso**</mark>

Para proteger os dados armazenados no Amazon S3, você pode utilizar dois métodos principais de criptografia em repouso:

1. **Criptografia do Lado do Servidor (SSE)**:

* O Amazon S3 criptografa os dados antes de armazená-los em seus datacenters e descriptografa os dados ao serem acessados.
* Existem três tipos de SSE:

| SSE-S3                                          | SSE-KMS                                                                                                                              | SSE-C                                                                                                                     |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| O Amazon S3 gerencia as chaves de criptografia. | Usa o AWS Key Management Service (KMS) para gerenciar as chaves de criptografia, permitindo controle mais detalhado sobre as chaves. | O cliente fornece as chaves de criptografia, e o Amazon S3 usa essas chaves para criptografar e descriptografar os dados. |

2. **Criptografia do Lado do Cliente (CSE)**:

* Os dados são criptografados no lado do cliente antes de serem enviados para o Amazon S3.
* O cliente gerencia o processo de criptografia, as chaves de criptografia e todas as ferramentas relacionadas.
* Esse método proporciona controle total sobre a criptografia, mas também requer um gerenciamento mais complexo das chaves.

#### <mark style="color:blue;">**Comparação entre SSE e CSE**</mark>

| SSE                                                                                                                                                                                          | CSE                                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| <p><mark style="color:green;"><strong>Vantagens</strong>:</mark> </p><p>Fácil de configurar e gerenciar; o Amazon S3 cuida de todo o processo de criptografia e gerenciamento de chaves.</p> | <p><mark style="color:green;"><strong>Vantagens</strong>:</mark> </p><p>Controle total sobre o processo de criptografia e as chaves.</p> |
| <p><mark style="color:purple;"><strong>Desvantagens</strong>:</mark> </p><p>Menor controle sobre o processo de criptografia e as chaves.</p>                                                 | <p><mark style="color:purple;"><strong>Desvantagens</strong>:</mark> </p><p>Maior complexidade na configuração e gerenciamento.</p>      |

A criptografia no Amazon S3 é um componente crucial para proteger seus dados contra acessos não autorizados. Seja utilizando a criptografia do lado do servidor, onde o Amazon S3 gerencia o processo, ou a criptografia do lado do cliente, onde você controla as chaves, o Amazon S3 oferece flexibilidade para atender às suas necessidades de segurança. A utilização de SSL para dados em trânsito complementa essas medidas, garantindo que seus dados estejam protegidos durante toda a sua jornada.

***

### <mark style="color:red;">Versionamento do Amazon S3</mark>

O versionamento no Amazon S3 é uma funcionalidade poderosa que permite manter múltiplas versões de um mesmo objeto no mesmo bucket. Isso é útil para prevenir perdas de dados devido a exclusões acidentais ou substituições inadvertidas de arquivos. Vamos explorar como o versionamento funciona e seus benefícios.

#### <mark style="color:blue;">**Funcionamento do Versionamento**</mark>

Quando o versionamento está habilitado em um bucket do Amazon S3, cada vez que você faz upload de um novo objeto com o mesmo nome de um objeto existente, o Amazon S3 gera automaticamente um ID de versão exclusivo para o novo objeto. Isso significa que você pode ter várias versões de um mesmo arquivo, todas identificadas pelo mesmo nome de chave, mas com diferentes IDs de versão.

Por exemplo, imagine que você tenha um bucket chamado `funcionarios` e faça upload de uma foto de um funcionário com o nome `employee.jpg`. Se você ativar o versionamento, o S3 gerará um ID de versão para essa foto. Se, posteriormente, você fizer upload de uma nova versão de `employee.jpg`, o Amazon S3 não substituirá a versão anterior, mas criará uma nova versão com um ID de versão diferente.

#### <mark style="color:blue;">**Benefícios do Versionamento**</mark>

| Preservação de Dados                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><mark style="color:purple;"><strong>Prevenção de Perdas Acidentais</strong>:</mark> </p><p>Se um objeto for excluído, ele não é removido permanentemente. Em vez disso, o Amazon S3 coloca um marcador de exclusão no objeto, permitindo que você restaure a versão anterior removendo o marcador.</p> | <p><mark style="color:purple;"><strong>Rastreamento de Versões</strong>:</mark> </p><p>Facilita o rastreamento de mudanças ao longo do tempo, mantendo um histórico completo das modificações feitas aos objetos.</p>                       |
| <p><mark style="color:purple;"><strong>Proteção contra Substituições</strong>:</mark> </p><p>Substituir um objeto resulta na criação de uma nova versão do objeto. As versões anteriores permanecem disponíveis para acesso ou restauração.</p>                                                           | <p><mark style="color:purple;"><strong>Recuperação Simples</strong>:</mark> </p><p>Em caso de falhas de aplicação ou erros humanos, você pode facilmente recuperar uma versão anterior de um objeto, evitando perdas de dados críticas.</p> |

#### <mark style="color:blue;">**Como Funciona na Prática**</mark>

| Habilitando o Versionamento                                                                                                                                                 | Exclusão e Restauração:                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| No console do Amazon S3, você pode habilitar o versionamento para um bucket específico. Uma vez ativado, cada upload subsequente do mesmo objeto gera um novo ID de versão. | Quando você tenta excluir um objeto, o S3 adiciona um marcador de exclusão. Para restaurar o objeto, você remove esse marcador. |
|                                                                                                                                                                             | Para sobrescrever um objeto, você faz upload de uma nova versão, e a versão antiga permanece disponível.                        |

#### <mark style="color:blue;">**Exemplo de Política de Versionamento**</mark>

Suponha que você habilite o versionamento para um bucket chamado `funcionarios`. Você faz upload de `employeephoto.gif` e o S3 atribui o ID de versão `111111`. Posteriormente, você faz upload de uma nova versão de `employeephoto.gif`, e o S3 atribui o ID de versão `121212`. Agora, você tem duas versões do mesmo objeto:

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719327600/cwky-UKh-jfddaL_CDJzyw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/pT89ErCPAA_stgj5_cwXT1yuQPJJYQa6M.png" alt=""><figcaption></figcaption></figure>

* `employeephoto.gif` (versão `111111`)
* `employeephoto.gif` (versão `121212`)

Se você excluir `employee.jpg`, o S3 não removerá as versões, mas adicionará um marcador de exclusão. Para restaurar a versão anterior, você simplesmente remove o marcador de exclusão.

O versionamento do Amazon S3 é uma ferramenta essencial para a gestão e proteção de dados. Ele não só protege contra exclusões acidentais e substituições inadvertidas, mas também facilita a recuperação e o rastreamento de mudanças ao longo do tempo, tornando-o uma escolha confiável para qualquer estratégia de armazenamento de dados robusta.

***

### <mark style="color:red;">Estados de versionamento</mark>

Os buckets no Amazon S3 podem estar em um dos três estados de versionamento, que controlam como os objetos são armazenados e gerenciados em relação às suas versões. Esses estados são:

| Unversioned (Sem versão - padrão)                                                                                                                                                                                                                                        | Versioning-enabled (Versionamento ativado)                                                                                                                                                                                                                                                                               | Versioning-suspended (Versionamento suspenso)                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>No estado padrão, o versionamento não está habilitado. Nenhum objeto no bucket tem um ID de versão. Qualquer objeto novo que for carregado substituirá o objeto existente com o mesmo nome.</p> | <p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>O versionamento está habilitado para todos os objetos no bucket. Cada vez que você faz upload de um objeto com o mesmo nome de um objeto existente, o Amazon S3 cria uma nova versão do objeto, mantendo as versões anteriores disponíveis.</p> | <p><mark style="color:purple;"><strong>Descrição</strong></mark>: </p><p>O controle de versão está suspenso para novos objetos. Todos os novos objetos carregados no bucket não terão um ID de versão, mas os objetos existentes que foram carregados antes da suspensão do versionamento manterão suas versões.</p> |
| <p><mark style="color:green;"><strong>Cenário</strong></mark>: </p><p>Ideal para buckets onde o controle de versões não é necessário, e a simplicidade é preferida.</p>                                                                                                  | <p><mark style="color:green;"><strong>Cenário</strong></mark>: </p><p>Útil para casos onde a preservação de versões históricas dos objetos é importante, como backups e registros de mudanças.</p>                                                                                                                       | <p><mark style="color:green;"><strong>Cenário</strong></mark>: </p><p>Adequado para situações onde você quer parar temporariamente de criar novas versões dos objetos, mas ainda quer manter as versões existentes.</p>                                                                                              |

#### <mark style="color:blue;">**Gerenciamento de Custos**</mark>

Os custos de armazenamento no Amazon S3 são calculados com base em todos os objetos no bucket, incluindo todas as versões dos objetos quando o versionamento está ativado. Para gerenciar e reduzir os custos de armazenamento, você pode optar por excluir versões antigas de objetos que não são mais necessários. Isso pode ser feito manualmente ou configurando regras de ciclo de vida que automatizam a exclusão de versões antigas.

#### <mark style="color:blue;">Exemplo Prático</mark>

| Estado Padrão (Unversioned)                                                                        | Estado Versioning-enabled:                                              | Estado Versioning-suspended                                                                        |
| -------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Você faz upload de `employee.jpg`.                                                                 | Você faz upload de `employee.jpg` (versão `111111`).                    | Você faz upload de `employee.jpg` enquanto o versionamento está ativado (versão `111111`).         |
| Se você fizer upload de um novo `employee.jpg`, ele substituirá o anterior, sem manter uma versão. | Você faz upload de uma nova versão de `employee.jpg` (versão `121212`). | Você suspende o versionamento.                                                                     |
|                                                                                                    | Ambas as versões estão disponíveis para recuperação.                    | Você faz upload de um novo `employee.jpg` que substitui o anterior sem criar um novo ID de versão. |
|                                                                                                    |                                                                         | A versão `111111` ainda está disponível para recuperação, mas o novo upload não tem ID de versão.  |

Compreender e gerenciar os estados de versionamento no Amazon S3 é crucial para uma estratégia eficaz de armazenamento de dados. O uso apropriado do versionamento pode fornecer uma camada adicional de proteção contra a perda de dados, enquanto a suspensão do versionamento pode ajudar a controlar os custos de armazenamento, mantendo a flexibilidade para futuras necessidades de versionamento.

***

### <mark style="color:red;">Seis Classes de Armazenamento do Amazon S3</mark>

O Amazon S3 oferece seis classes de armazenamento, cada uma projetada para diferentes cenários de uso com base na frequência de acesso aos dados e nos requisitos de durabilidade e disponibilidade. Quando você faz o upload de um objeto sem especificar a classe de armazenamento, ele é carregado para a classe de armazenamento padrão. Vamos explorar essas classes e suas características principais.

<details>

<summary><mark style="color:purple;"><strong>S3 Standard (Padrão)</strong></mark></summary>

Isso é considerado armazenamento de uso geral para aplicaçãoes em nuvem, sites dinâmicos, distribuição de conteúdo, aplicações móveis e de jogos e análises de big data.

**Descrição**: A classe de armazenamento padrão, ideal para dados acessados com frequência.

**Durabilidade**: 99.999999999% (11 9's).

**Disponibilidade**: 99.99% em um ano.

**Casos de Uso**: Aplicações de alta performance, distribuição de conteúdo, e dados críticos que precisam de acesso rápido.

</details>

<details>

<summary><mark style="color:purple;"><strong>S3 Intelligent-Tiering</strong></mark></summary>

Esse nivel é útil se seus dados tiverem padrões de acesso desconhecidos ou alterados. S3 Intelligent-Tiering armazena objetos em duas camadas: uma camada de acesso frequente e uma camada de acesso não frequente. O Amazon S3 monitora os padrões de acesso de seus dados e, automaticamente, move os dados para a camada de armazenamento mais econômica com base na frequência de acesso.

**Descrição**: Automatiza a movimentação de dados entre duas camadas de acesso (frequente e infrequente) com base em padrões de acesso.

**Durabilidade**: 99.999999999%.

**Disponibilidade**: 99.9% em um ano.

**Casos de Uso**: Dados com padrões de acesso desconhecidos ou que mudam frequentemente, para otimização automática de custos.

</details>

<details>

<summary><mark style="color:purple;"><strong>S3 Standard-IA (Infrequent Access)</strong></mark></summary>

Essa camada é indicada para dados acessados com menos frequência, mas que precisam de acesso rápido, quando necessário. S3 Standard - IA oferece alta durabilidade, alta taxa de  transferência e baixa latência de S3 Standard, com preços de armazenamento por GB reduzido e com base na taxa de recuperação de GB. Essa camada de armazenamento é ideal se você quiser armazenar backups de longo prazo, arquivos de recuperação de desastres etc.

**Descrição**: Armazenamento para dados acessados com menos frequência, mas que ainda precisam de rápida recuperação.

**Durabilidade**: 99.999999999%.

**Disponibilidade**: 99.9% em um ano.

**Casos de Uso**: Dados de recuperação de desastres, backups de longa duração, e arquivos que são raramente acessados.

</details>

<details>

<summary><mark style="color:purple;"><strong>S3 One Zone-IA (Acesso Infrequente em Uma Zona)</strong></mark></summary>

Ao contrário de outras classes de armazenamento do S3, que armazenam dados em, no mínimo, três zonas de disponibilidade (AZs), a S3 One Zone - IA armazena dados em uma única AZ, com um custo 20% inferior á S3 Standar - IA. A S3 One Zone IA é ideal para clientes que querem uma opção com custo menor para dados acessados com pouca frequência, mas não precisam da disponibilidade e da resiliência S3 Standard ou S3 Standard - IA. É uma ótima opção para armazenar cópias de backup secundárias de dados on-premises ou que possam ser recriados com facilidade.

**Descrição**: Armazenamento de baixo custo para dados acessados com menos frequência e armazenados em uma única zona de disponibilidade.

**Durabilidade**: 99.999999999% (em uma única zona).

**Disponibilidade**: 99.5% em um ano.

**Casos de Uso**: Dados que podem ser facilmente recriados, como cópias de backup não críticas.

</details>

<details>

<summary><mark style="color:purple;"><strong>S3 Glacier</strong></mark></summary>

O S3 Glacier é uma classe de armazenamento segura, durável e de baixo custo para arquivamento de dados. Você pode armazenar com confiança qualquer volume de dados por um custo competitivo ou inferior ao de soluções on-premises. Para manter os custos baixos, mas com condições de suprir necessidades variáveis, o S3 Glacier disponibiliza três opções de recuperação, que podem demorar alguns minutos ou várias horas.

**Descrição**: Armazenamento de baixo custo para arquivamento de dados que não precisam de acesso imediato.

**Durabilidade**: 99.999999999%.

**Disponibilidade**: Varia conforme o tempo de recuperação (de minutos a horas).

**Casos de Uso**: Arquivos de longa duração, conformidade e arquivamento de dados históricos.

</details>

<details>

<summary><mark style="color:purple;"><strong>S3 Glacier Deep Archive</strong></mark></summary>

O S3 Glacier Deep Archive é a classe de armazenamento mais econômica do Amazon S3 e oferece suporte á retenção e preservação digitais de longo prazo para dados que podem ser acessados uma ou duas vezes por ano. Essa classe é projetada para clientes que retêm conjuntos de dados por 7 a 10 anos, ou mais, para atender requisitos de conformidade regulatòrios, principalmente aqueles em setores altamente regulamentados, como serviços financeiros, saúde e setores públicos.

**Descrição**: A classe de armazenamento mais barata, projetada para dados que raramente são acessados (uma ou duas vezes por ano).

**Durabilidade**: 99.999999999%.

**Disponibilidade**: Varia conforme o tempo de recuperação (de 12 a 48 horas).

**Casos de Uso**: Arquivamento de dados de longo prazo, dados de conformidade e retenção.

</details>

#### <mark style="color:blue;">Escolha da Classe de Armazenamento</mark>

Selecionar a classe de armazenamento correta depende dos padrões de acesso e das necessidades de custo e performance dos dados. A flexibilidade do Amazon S3 permite que você altere a classe de armazenamento dos objetos conforme necessário para otimizar os custos e atender às necessidades de acesso.

Essas classes de armazenamento permitem que você gerencie eficientemente os dados no Amazon S3, garantindo que você possa balancear custos e performance conforme as necessidades de acesso aos dados evoluem.

***

### <mark style="color:red;">Automatização das Transições de Camada com Gerenciamento do Ciclo de Vida de Objetos no Amazon S3</mark>

O gerenciamento do ciclo de vida de objetos no Amazon S3 permite automatizar a transição entre diferentes classes de armazenamento e a expiração de objetos, facilitando a otimização de custos e o cumprimento de requisitos de retenção de dados. Aqui está como você pode utilizar essa funcionalidade:

| Ações de Transição                                                                                                                                                                                                                                                                                                                                                                        | Ações de Expiração                                                                                                                                                                                                                                                                                                                          |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| As ações de transição permitem definir quando os objetos devem ser movidos automaticamente para uma classe de armazenamento diferente                                                                                                                                                                                                                                                     | As ações de expiração definem quando os objetos devem ser permanentemente excluídos                                                                                                                                                                                                                                                         |
| <p><mark style="color:purple;"><strong>Exemplo</strong>:</mark> </p><p>Você pode configurar uma política de ciclo de vida para transicionar objetos para a classe de armazenamento S3 Standard-IA (Acesso Infrequente) 30 dias após sua criação inicial. Isso é útil para objetos que são frequentemente acessados no início, mas depois passam a ser acessados com menos frequência.</p> | <p><mark style="color:purple;"><strong>Exemplo</strong>:</mark> </p><p>Após um determinado período de tempo, como um ano, você pode configurar uma ação de expiração para excluir automaticamente os objetos. Isso é útil para conformidade com políticas de retenção de dados ou para evitar o acúmulo desnecessário de dados antigos.</p> |

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719327600/cwky-UKh-jfddaL_CDJzyw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/YoZi-yUCVwEkLtLY_815fL99IQ5LjljMn.jpg" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Casos de Uso para Gerenciamento do Ciclo de Vida**</mark>

O gerenciamento do ciclo de vida é ideal para diversos cenários onde os padrões de acesso e as políticas de retenção variam ao longo do tempo:

| Logs Periódicos                                                                                                                                                                      | Dados com Diferentes Frequências de Acesso                                                                                                                                                                                        | Conformidade e Retenção                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Logs que são frequentemente acessados por um período limitado de tempo podem ser automaticamente movidos para classes de armazenamento de menor custo após o período inicial de uso. | Documentos ou dados que são acessados com frequência inicialmente, mas que depois passam a ser acessados com pouca frequência, podem ser movidos para classes de armazenamento mais econômicas após um período de tempo definido. | Para atender a requisitos regulatórios ou organizacionais, você pode automatizar a transição de objetos para classes de armazenamento de longo prazo, como o S3 Glacier, após um período específico, e também definir ações de expiração para garantir que os dados sejam excluídos conforme necessário. |

#### <mark style="color:blue;">Benefícios do Gerenciamento do Ciclo de Vida</mark>

| Economia de Custos                                                                                                                                                                      | Conformidade                                                                                                                             | Simplicidade Operacional                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Ao mover automaticamente objetos para classes de armazenamento mais baratas conforme sua frequência de acesso diminui, você pode reduzir significativamente os custos de armazenamento. | Garante conformidade com políticas de retenção de dados, permitindo a expiração automática de objetos quando não forem mais necessários. | Automatiza tarefas de gerenciamento de dados, reduzindo a necessidade de intervenção manual e potenciais erros. |

O Amazon S3 oferece uma flexibilidade significativa para adaptar o gerenciamento do ciclo de vida às necessidades específicas de suas aplicações e requisitos de armazenamento, permitindo uma gestão eficaz e econômica dos seus dados ao longo do tempo.

***

## <mark style="color:red;">**Recursos**</mark>

[Amazon S3(opens in a new tab)](https://aws.amazon.com/s3/)

[Classes de armazenamento do Amazon S3(opens in a new tab)](https://aws.amazon.com/s3/storage-classes/)

[Uso de versionamento em buckets do S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html)

***
