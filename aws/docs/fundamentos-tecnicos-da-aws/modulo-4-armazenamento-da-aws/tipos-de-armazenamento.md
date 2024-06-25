---
description: >-
  Os serviços de armazenamento da AWS são agrupados em três categorias:
  armazenamento de blocos, armazenamento de arquivos e armazenamento de objetos.
---

# Tipos de Armazenamento

***

## <mark style="color:red;">Armazenamento de Arquivos</mark>

O armazenamento de arquivos é um conceito familiar para muitos, especialmente se você já utilizou sistemas como o Windows File Explorer ou o Finder no macOS. Nesse sistema, os arquivos são organizados em uma hierarquia em forma de árvore, composta por pastas e subpastas.

#### <mark style="color:blue;">**Organização Hierárquica**</mark>

Por exemplo, se você possui centenas de fotos de gatos em seu laptop, pode criar uma pasta chamada "Fotos de Gatos" e colocar todas as imagens nessa pasta. Se essas imagens são usadas em uma aplicação, talvez queira colocar a pasta **"Fotos de Gatos"** dentro de outra pasta chamada **"Arquivos de Aplicações"**.

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719288000/qv1ubG4XmDzlGeSEaz41BQ/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/Bj0HlEgjqWjzzHUw_lCPr0zICA_gk-HiL.jpg" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Estrutura e Metadados**</mark>

Cada arquivo possui metadados, como:

* Nome do arquivo
* Tamanho do arquivo
* Data de criação

Além disso, cada arquivo tem um caminho que especifica sua localização na hierarquia de arquivos, por exemplo: `computer/Application_files/Cat_photos/cats-03.png`. Esse caminho é usado pelo sistema para localizar e recuperar o arquivo quando necessário.

#### <mark style="color:blue;">**Acesso Centralizado**</mark>

O armazenamento de arquivos é ideal para situações onde é necessário um acesso centralizado a arquivos que devem ser facilmente compartilhados e gerenciados por vários computadores host. Esse tipo de armazenamento é geralmente montado em vários hosts e requer:

* Bloqueio de arquivos para evitar conflitos de acesso simultâneo
* Integração com protocolos de comunicação do sistema de arquivos existentes

#### <mark style="color:blue;">**Casos de Uso Comuns**</mark>

O armazenamento de arquivos é comumente utilizado em:

| Grandes repositórios de conteúdo                                        | Ambientes de desenvolvimento                                                    | Diretórios iniciais do usuário                                                            |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Onde uma grande quantidade de dados precisa ser organizada e acessível. | Onde múltiplos desenvolvedores precisam acessar e modificar os mesmos arquivos. | Para armazenar e gerenciar os dados pessoais de cada usuário em um sistema compartilhado. |

Essa abordagem de armazenamento permite uma gestão eficiente e organizada dos dados, facilitando o acesso e a colaboração entre diversos usuários e sistemas.

***

## <mark style="color:red;">**Armazenamento de blocos**</mark>

O armazenamento de blocos difere do armazenamento de arquivos ao tratar os dados de forma mais granular. Em vez de considerar arquivos inteiros como unidades únicas, o armazenamento de blocos divide os arquivos em pedaços de tamanho fixo chamados blocos. Cada bloco tem seu próprio endereço, permitindo recuperação eficiente dos dados.

#### <mark style="color:blue;">Funcionamento do Armazenamento em Blocos</mark>

| Divisão em Blocos                                                   | Recuperação Eficiente                                                                                                                                                | Alteração de Dados                                                                                                                                                     |
| ------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Os arquivos são divididos em blocos, cada um com um endereço único. | Quando os dados são solicitados, o sistema de armazenamento utiliza os endereços para organizar e recuperar os blocos na ordem correta, formando o arquivo completo. | Para modificar um caractere em um arquivo, apenas o bloco que contém o caractere precisa ser alterado, não o arquivo inteiro. Isso economiza tempo e largura de banda. |

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719288000/qv1ubG4XmDzlGeSEaz41BQ/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/cIRRR_XX7wFefVX6_0RsOlGBIbMKrVjc1.png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Benefícios do Armazenamento em Blocos**</mark>

| Baixa Latência                                                                                                 | Eficiência                                                                                            |
| -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Projetado para operações rápidas, o armazenamento em bloco é ideal para workloads que exigem alta performance. | Usa menos largura de banda devido à capacidade de acessar e modificar blocos específicos diretamente. |

#### <mark style="color:blue;">**Casos de Uso Comuns**</mark>

O armazenamento de blocos é preferido em ambientes corporativos que demandam alta performance e baixa latência, como:

| Bancos de Dados                                      | Sistemas de Planejamento de Recursos Empresariais (ERP)            |
| ---------------------------------------------------- | ------------------------------------------------------------------ |
| Onde a rápida leitura e gravação de dados é crucial. | Que necessitam de operações de armazenamento eficientes e rápidas. |

A granularidade e eficiência do armazenamento em blocos o tornam uma solução ideal para aplicações que exigem desempenho elevado e acesso rápido aos dados.

***

## <mark style="color:red;">**Armazenamento de objeto**</mark>

O armazenamento de objetos trata cada unidade de dados como um único objeto. Diferentemente do armazenamento de arquivos, onde os dados são organizados em uma hierarquia de pastas e subpastas, o armazenamento de objetos utiliza uma estrutura plana. Cada objeto é identificado de forma única e armazenado com seus metadados.

#### <mark style="color:blue;">**Funcionamento do Armazenamento de Objetos**</mark>

| Estrutura Plana                                                                                                                                                | Empacotamento de Dados                                                                                                              | Atualização de Dados                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
|  Os objetos são armazenados em uma estrutura plana, o que significa que não há pastas ou subpastas. Cada objeto é identificado por um identificador exclusivo. | Cada objeto inclui os dados, um identificador único e metadados adicionais. Esses componentes são empacotados juntos e armazenados. | Para modificar um caractere em um objeto, todo o objeto precisa ser atualizado, o que é mais trabalhoso comparado ao armazenamento em blocos. |

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719288000/qv1ubG4XmDzlGeSEaz41BQ/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/P8yjYgmziZkVVdbk_PwD9kxga24sM5_H3.jpg" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Benefícios do Armazenamento de Objetos**</mark>

| Escalabilidade                                                                                    | Flexibilidade                                                                                                                            |
| ------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Não há limite para o número de objetos que podem ser armazenados, tornando-o altamente escalável. | Capaz de armazenar qualquer tipo de dado, o armazenamento de objetos é ideal para grandes conjuntos de dados e arquivos não estruturados |

#### <mark style="color:blue;">**Casos de Uso Comuns**</mark>

O armazenamento de objetos é particularmente útil em cenários onde grandes volumes de dados precisam ser gerenciados e acessados de forma eficiente.&#x20;

Exemplos incluem:

| Ativos de Mídia                 | Dados Não Estruturados             | Ativos Estáticos      |
| ------------------------------- | ---------------------------------- | --------------------- |
| Como vídeos, músicas e imagens. | Como documentos e arquivos de log. | Como fotos e backups. |

A estrutura plana e a capacidade de gerenciar uma quantidade ilimitada de objetos, tornam o armazenamento de objetos uma solução robusta e flexível para diversas necessidades de armazenamento de dados.

***

### <mark style="color:red;">Relacionando aos Sistemas de Armazenamento Tradicionais</mark>

Se você já trabalhou com soluções de armazenamento on-premises, pode reconhecer as semelhanças entre essas tecnologias e os sistemas de armazenamento na nuvem.&#x20;

Aqui estão as correspondências:

#### <mark style="color:blue;">**Armazenamento em Bloco**</mark>

| Equivalente On-Premises                                                       | Características                                                                                                                        |
| ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Similar ao Direct-Attached Storage (DAS) ou a uma Storage Area Network (SAN). | No DAS ou SAN, os dados são divididos em blocos que podem ser acessados rapidamente, proporcionando alta performance e baixa latência. |

#### <mark style="color:blue;">**Armazenamento de Arquivos**</mark>

| Equivalente On-Premises                          | Características                                                                                                                                              |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Equiparável a um Network Attached Storage (NAS). | Um NAS organiza arquivos em uma hierarquia de pastas e subpastas, permitindo acesso centralizado e compartilhamento fácil de arquivos entre múltiplos hosts. |

#### <mark style="color:blue;">**Armazenamento de Objetos**</mark>

| Equivalente On-Premises                                                                                                                                          | Características                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Embora menos comum em implementações on-premises, algumas soluções de armazenamento de objetos existem para lidar com grandes volumes de dados não estruturados. | Armazenamento de objetos organiza dados em uma estrutura plana, com cada objeto possuindo um identificador único e metadados. |

#### <mark style="color:blue;">**Vantagens da Nuvem sobre o On-Premises**</mark>

| Flexibilidade                                                                                                                                                                                                               | Escalabilidade                                                                                                                                                          | Gestão Simplificada                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Adicionar armazenamento em um datacenter tradicional é um processo rígido, envolvendo a compra, instalação e configuração de hardware. Na nuvem, você pode criar, excluir e modificar soluções de armazenamento em minutos. | As soluções de armazenamento na nuvem podem ser escaladas conforme a demanda, sem a necessidade de planejamento e investimento em capacidade adicional antecipadamente. | Com a nuvem, a gestão de armazenamento é simplificada, eliminando a necessidade de manutenção física e permitindo focar em outras prioridades de negócios. |

Ao entender essas correspondências, você pode apreciar como as soluções de armazenamento na nuvem replicam e ampliam as funcionalidades dos sistemas on-premises, proporcionando uma abordagem mais flexível e escalável para gerenciar dados.

***

### **Recursos**

[O que é armazenamento em nuvem(opens in a new tab)](https://aws.amazon.com/what-is-cloud-storage/)

[Tipos de armazenamento em nuvem](https://aws.amazon.com/what-is-cloud-object-storage/#types)

***
