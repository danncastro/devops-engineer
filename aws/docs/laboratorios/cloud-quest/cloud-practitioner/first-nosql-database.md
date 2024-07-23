# First NoSQL Database

***

## <mark style="color:red;">Implementando banco NoSQL</mark>

| Título da tarefa              | Solicitação de negócios                                                                                                       |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Primeiro banco de dados NoSQL | Ajude o serviço de streaming de entretenimento da ilha a implementar um banco de dados NoSQL para desenvolver novos recursos. |

<figure><img src="../../../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">DynamoDB</mark>

**No SQL**: Esta solução utiliza o Amazon DynamoDB, que possui um esquema flexível, permitindo que cada linha tenha qualquer número de atributos em qualquer momento.

**Diferença entre SQL e NoSQL**: DynamoDB é um banco de dados chave-valor e de documentos que oferece desempenho de milissegundos na escala de um dígito, independente da escala. Esse nível de desempenho atende à rápida tempo de resposta exigido pela solução.

**Como criar uma tabela NoSQL**: As tabelas do DynamoDB suportam dois tipos de chaves primárias: apenas uma chave de partição ou uma chave de partição e uma chave de ordenação. Esta solução utiliza uma chave de partição (userId) e uma chave de ordenação (lastDataWatched).

Ao obter um item específico (Operação GetItem), você deve especificar a chave primária do item desejado. Você pode recuperar o item inteiro ou apenas um subconjunto de seus atributos.

**Visão geral do Amazon DynamoDB**: Para consultar esta tabela, você deve fornecer o valor da chave de partição e aplicar uma condição aos valores da chave de ordenação para recuperar apenas um subconjunto dos dados.

**Visão geral das consultas do Amazon DynamoDB**: Com um esquema flexível, você pode adicionar um novo atributo (como 'rating') a um registro específico mesmo depois que ele foi criado.

***

## <mark style="color:red;">Descrição da tarefa</mark>

Resuma os diferentes usos de bancos de dados comuns criados para propósitos específicos.&#x20;

* Descreva os recursos e benefícios do Amazon DynamoDB.&#x20;
* Interaja com os elementos e atributos de um banco de dados Amazon DynamoDB.&#x20;
* Configure um banco de dados NoSQL com o Amazon DynamoDB.

1. Criar um banco de dados NoSQL como uma tabela Amazon DynamoDB
2. Adicionar registros com um esquema dinâmico à tabela DynamoDB
3. Consultar a tabela DynamoDB.

***

### <mark style="color:purple;">Step 1</mark>

1. Na caixa de pesquisa da barra de navegação superior, digite: `DynamoDB`
2. Nos resultados da pesquisa, em Serviço, clique em `DynamoDB`.
3. Vá para o próximo passo

#### <mark style="color:blue;">Concept</mark>

Amazon DynamoDB é serverless. Não há servidores para provisionar, atualizar ou gerenciar. Não há software para instalar, manter ou operar. DynamoDB escala automaticamente as tabelas para cima e para baixo para ajustar a capacidade e manter o desempenho.

<figure><img src="../../../.gitbook/assets/image (177).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 2</mark>

1. Na página inicial do console do Amazon DynamoDB, clique em `Criar tabela`.
2. Vá para o próximo passo

#### <mark style="color:blue;">Concept</mark>

DynamoDB suporta modelos de dados chave-valor e de documentos. Portanto, DynamoDB possui um esquema flexível. Cada linha pode ter qualquer número de colunas a qualquer momento. Dessa forma, você pode adaptar rapidamente as tabelas conforme as necessidades do seu negócio mudam, sem precisar redefinir o esquema da tabela como faria em bancos de dados relacionais.

<figure><img src="../../../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 3</mark>

1. Na seção Detalhes da tabela, para Nome da tabela, digite: `UserVideoHistory`
2. Para Chave de partição, na caixa de texto à esquerda, digite: `userId`

* Você deve digitar a chave de partição exatamente como mostrado, userId com um "i" maiúsculo porque as chaves são sensíveis a maiúsculas e minúsculas.

3. No menu suspenso à direita, escolha `String`.

* String é o tipo de dado.

4. Para Chave de ordenação, na caixa de texto à esquerda, digite: `lastDataWatched`
5. No menu suspenso à direita, escolha `Number`
6. Role a página para baixo até o final.
7. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Ao criar uma tabela, além do nome da tabela, você deve especificar a chave primária da tabela. A chave primária identifica unicamente cada item na tabela, portanto, nenhum dois itens podem ter a mesma chave.

<figure><img src="../../../.gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 4</mark>

1. Na seção Configurações, mantenha as configurações padrão.
2. Clique em `Criar tabela`.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Se sua tabela possui uma chave primária simples (apenas chave de partição), o DynamoDB armazena e recupera cada item com base no valor da sua chave de partição.

<figure><img src="../../../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 5</mark>

1. Na seção Tabelas, em Status, revise o status da tabela.

* Aguarde até que o status mude para Ativo.

2. Quando estiver ativo, clique no nome da tabela.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Amazon DynamoDB armazena dados em partições. Uma partição é uma alocação de armazenamento para uma tabela, suportada por unidades de estado sólido (SSDs) e replicada automaticamente entre várias Zonas de Disponibilidade dentro de uma Região da AWS.

<figure><img src="../../../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 6</mark>

1. Clique em `Ações` para expandir o menu suspenso.
2. Escolha `Criar item`.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Uma chave composta utiliza tanto uma chave de partição quanto uma chave de ordenação. Em uma tabela que possui uma chave de partição e uma chave de ordenação, é possível que dois itens tenham o mesmo valor de chave de partição. No entanto, esses dois itens devem ter valores diferentes para a chave de ordenação.

<figure><img src="../../../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 7</mark>

1. Na seção Atributos, ao lado de `userId`, para Valor, digite: `12345-abcd-6789`
2. Ao lado de `lastDateWatched`, para o Valor, digite: `1619156406`

* Este é um timestamp UNIX.

3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Para escrever um item na tabela, o DynamoDB utiliza o valor da chave de partição como entrada para uma função de hash interna. O valor de saída da função de hash determina a partição na qual o item será armazenado.

<figure><img src="../../../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 8</mark>

1. Para adicionar outro atributo, clique em `Adicionar novo atributo` para expandir o menu suspenso.
2. Escolha `String`.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Para ler um item da tabela, você deve especificar o valor da chave de partição para o item. DynamoDB utiliza esse valor como entrada para sua função de hash, determinando a partição na qual o item pode ser encontrado.

<figure><img src="../../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 9</mark>

1. Para Nome do atributo, na nova caixa de texto, digite: `videoId`
2. Para Valor, na nova caixa de texto, digite: `9875-djac-1859`
3. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 10</mark>

1. Clique em `Adicionar novo atributo`.
2. Escolha `String`.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Você cria itens no DynamoDB. Itens são registros com atributos que armazenam dados. Você pode armazenar dados como o histórico de visualização de vídeos de um cliente. DynamoDB suporta vários tipos diferentes de dados.

<figure><img src="../../../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 11</mark>

1. Para Nome do atributo, digite: `preferredLanguage`
2. Para Valor, digite: `English`
3. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 12</mark>

1. Clique em `Adicionar novo atributo`.
2. Escolha Lista.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

DynamoDB também pode armazenar atributos mais complexos, como uma lista.

<figure><img src="../../../.gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 13</mark>

1. Para Nome do atributo, digite: `supportedDeviceTypes`
2. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 14</mark>

1. Para Valor, clique em Inserir um campo para expandir o menu suspenso.
2. Escolha `String`.
3. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 15</mark>

1. Para Nome do atributo, ao lado de `supportedDeviceTypes`, clique no sinal de mais `(+)`.
2. Para Valor, na nova caixa de texto, digite: `Amazon Fire TV`
3. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 16</mark>

1. Para Valor, clique em `Inserir um campo`
2. Escolha `String`
3. Vá para o próximo passo

<figure><img src="../../../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 17</mark>

1. Para Valor, na nova caixa de texto, digite: `Amazon Fire Tablet`
2. Clique em `Criar item.`
3. Vá para o próximo passo

<figure><img src="../../../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 18</mark>

1. No painel de navegação à esquerda, em Tabelas, clique em `Explorar itens`.
2. Na seção de itens retornados, ao lado de `userId`, clique em `12345-abcd-6789`.

* Agora você pode editar o registro novamente.

3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Depois de criar um registro, você ainda pode editá-lo, incluindo o conteúdo do registro e seus atributos.

<figure><img src="../../../.gitbook/assets/image (195).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 19</mark>

1. Clique em `Adicionar novo atributo.`
2. Escolha `Número`.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

DynamoDB é sem esquema, você pode adicionar atributos à tabela para qualquer registro. Por exemplo, você pode adicionar um atributo `lastStopTime` com o tipo de dado `Número` que armazena o tempo total em segundos para visualização de vídeos. Estes dados podem ser usados para uma funcionalidade de retomada em sua aplicação.

<figure><img src="../../../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 20</mark>

1. Para Nome do atributo, digite: `lastStopTime`
2. Para Valor, digite: `90`
3. Clique em Salvar e fechar.
4. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

<figure><img src="../../../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 21</mark>

1. Para expandir a seção, clique em `Scan/Query items`.
2. Clique na aba `Query`.
3. Para `userId` (Chave de partição), digite: `12345-abcd-6789`
4. Para `lastDateWatch` (Chave de ordenação), no menu suspenso à esquerda, escolha `Maior que`.
5. Na caixa de texto à direita, digite: `1609477200`
6. Clique em Executar.
7. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

A operação de consulta (Query) no DynamoDB encontra itens com base nos valores da chave primária. Você deve fornecer o nome do atributo da chave de partição e um único valor para esse atributo. A consulta retorna todos os itens com esse valor de chave de partição. Opcionalmente, você pode fornecer um atributo de chave de ordenação e usar um operador de comparação para refinar os resultados da pesquisa.

<figure><img src="../../../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 22</mark>

1. Na seção de itens retornados, revise o registro retornado.
2. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (199).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 23</mark>

1. Para alterar os critérios da consulta, para `userId`, digite: `abd5-zxcg-12385`
2. Clique em Executar.
3. Na seção Itens retornados, revise os resultados.

* Nenhum item é retornado porque não há nenhum registro que corresponda à chave de partição e tenha uma chave de ordenação maior do que a que foi inserida.

4. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

Ao executar uma operação de consulta (Query), a tabela procura por uma correspondência exata para a chave de partição e utiliza a chave de ordenação (se fornecida) como uma maneira de limitar ainda mais os resultados.

<figure><img src="../../../.gitbook/assets/image (200).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Step 24</mark>

1. Clique na aba `Scan`.
2. Clique em `Executar`.
3. Na seção Itens retornados, revise os resultados.

* Todos os itens na sua tabela do DynamoDB devem ser listados.

4. Vá para o próximo passo.

#### <mark style="color:blue;">Concept</mark>

A operação de Scan retorna um ou mais itens e seus atributos acessando cada item em uma tabela ou índice secundário. Se o número total de itens escaneados exceder o limite máximo de tamanho de conjunto de dados de 1 MB, o scan é interrompido e os resultados são retornados ao usuário como um valor `LastEvaluatedKey`, para continuar o scan em uma operação subsequente. Os resultados também incluem o número de itens que excedem o limite. Um scan pode resultar em nenhum dado da tabela que atenda aos critérios de filtro.

<figure><img src="../../../.gitbook/assets/image (201).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">DIY Activite</mark>

* [ ] Crie um novo item de usuário com um ID único.
* [ ] Adicione um novo atributo chamado "rating" com um tipo de dado Número.

<figure><img src="../../../.gitbook/assets/image (203).png" alt=""><figcaption></figcaption></figure>

***
