# AWS Identity and Access Management

***

## <mark style="color:red;">IAM</mark>

O AWS Identity and Access Management (IAM) é um serviço fundamental da AWS projetado para ajudar na gestão de acesso aos recursos da sua conta AWS. Ele proporciona uma visão centralizada sobre quem tem acesso à sua conta (autenticação) e quais permissões eles possuem para interagir com os recursos (autorização).

Com o IAM, você pode controlar e delegar acesso de maneira segura, sem precisar compartilhar suas credenciais principais, como chaves de acesso ou senha. Isso permite que você conceda acesso granular a indivíduos ou serviços específicos dentro da sua organização. Por exemplo, você pode configurar permissões que permitem a um usuário realizar apenas operações de leitura em um serviço específico da AWS, limitando suas ações e recursos acessíveis de maneira precisa.

Ao utilizar o IAM, é possível estabelecer políticas detalhadas que especificam quais ações podem ser realizadas em quais recursos, garantindo que cada usuário ou serviço tenha apenas as permissões necessárias para realizar suas funções específicas. Isso não apenas fortalece a segurança da sua conta AWS, mas também ajuda a manter o princípio do menor privilégio, reduzindo o risco de uso indevido de recursos.

***

### <mark style="color:red;">Recursos do IAM</mark>

O AWS Identity and Access Management (IAM) oferece uma série de recursos projetados para fortalecer o controle de acesso e a gestão de identidades em sua conta AWS:

#### <mark style="color:blue;">**Globalidade**</mark>

O IAM é um serviço global da AWS, não vinculado a uma região específica. Isso significa que você pode acessar e gerenciar suas configurações do IAM de qualquer região usando o Console de Gerenciamento da AWS.

#### <mark style="color:blue;">**Integração com produtos AWS**</mark>

O IAM é integrado por padrão com muitos serviços da AWS, facilitando a configuração e gestão de permissões para esses serviços.

#### <mark style="color:blue;">**Políticas de senha**</mark>

Você pode estabelecer políticas de senha no IAM para impor requisitos de complexidade e períodos de rotação obrigatórios para os usuários. Isso ajuda a fortalecer a segurança das contas ao garantir que senhas robustas sejam usadas e atualizadas regularmente.

#### <mark style="color:blue;">**Suporte a MFA**</mark>&#x20;

O IAM suporta autenticação de múltiplos fatores (MFA), oferecendo uma camada adicional de segurança ao exigir um segundo método de autenticação além da senha, como um código gerado por um dispositivo MFA.

#### <mark style="color:blue;">**Federação de identidades**</mark>

O IAM suporta a federação de identidades, permitindo que usuários que já possuem credenciais em outros sistemas (por exemplo, rede corporativa ou provedor de identidade da Internet) obtenham acesso temporário à sua conta AWS. Isso simplifica o gerenciamento de acesso para usuários externos e facilita a integração com sistemas de identidade existentes.

#### <mark style="color:blue;">**Disponibilidade gratuita para todos os clientes**</mark>

O IAM está disponível para uso por qualquer cliente da AWS sem custos adicionais. Isso permite que todas as contas AWS implementem práticas robustas de gerenciamento de acesso sem custos adicionais.

Esses recursos combinados tornam o IAM uma ferramenta poderosa para a implementação de políticas de segurança, controle de acesso e gestão de identidades na AWS, ajudando a proteger seus recursos contra acessos não autorizados e garantindo conformidade com requisitos de segurança.

***

### <mark style="color:red;">Usuário do IAM</mark>

Um usuário do IAM na AWS representa uma entidade, seja uma pessoa ou um serviço, que interage com os recursos da sua conta AWS. Quando você define um usuário no IAM, qualquer atividade realizada por esse usuário é registrada e cobrada na sua conta AWS.

Após criar um usuário no IAM, esse usuário pode fazer login usando suas próprias credenciais para acessar os recursos autorizados na sua conta AWS. Isso é fundamental para gerenciar e controlar quem pode acessar quais recursos dentro da sua infraestrutura na nuvem.

Você pode adicionar vários usuários à sua conta da AWS conforme necessário. Por exemplo, se você está desenvolvendo uma aplicação de fotos de gatos, pode criar usuários individuais no IAM para cada pessoa que está envolvida no desenvolvimento ou na operação da aplicação. Cada usuário deve ter suas próprias credenciais de login exclusivas.

Fornecer a cada usuário suas próprias credenciais de login ajuda a evitar o compartilhamento de credenciais, o que é uma prática de segurança recomendada. Além disso, ao atribuir permissões específicas a cada usuário por meio de políticas de acesso, você pode garantir que cada um tenha apenas as permissões necessárias para realizar suas funções, seguindo o princípio do menor privilégio.

Portanto, os usuários IAM são fundamentais para controlar o acesso e gerenciar identidades de forma segura na AWS, garantindo que apenas usuários autorizados tenham acesso aos recursos específicos que necessitam para suas tarefas.

***

### <mark style="color:red;">Credenciais de usuário do IAM</mark>

Credenciais de usuário do IAM na AWS consistem em um conjunto de acesso. Ao criar um usuário, você pode fornecer a ele os seguintes tipos de acesso:

#### <mark style="color:blue;">**Acesso ao Console de Gerenciamento da AWS**</mark>

Para acessar o console web da AWS, um usuário do IAM precisa de um nome de usuário e senha. Essas credenciais permitem acesso interativo ao console onde os recursos da AWS podem ser gerenciados de forma gráfica.

#### <mark style="color:blue;">**Acesso programático**</mark>

Para interações automatizadas com a AWS através da AWS CLI ou API da AWS, são fornecidas chaves de acesso, que consistem em um ID da chave de acesso e uma chave secreta. Essas credenciais são utilizadas para autenticar solicitações feitas via linha de comando ou através de código programático.

As credenciais de usuário IAM são consideradas permanentes, permanecendo válidas até que sejam rotacionadas pelos administradores da conta, geralmente como parte das práticas de segurança recomendadas.

Ao gerenciar usuários individuais no IAM, é possível conceder permissões diretamente no nível do usuário. Isso é prático para um número limitado de usuários, mas à medida que o número aumenta, pode se tornar complicado administrar e auditar permissões individualmente. Por exemplo, em uma conta com milhares de usuários, é desafiador manter o controle detalhado de quem pode fazer o quê em quais recursos.

Para simplificar esse gerenciamento, o IAM oferece a capacidade de agrupar usuários em conjuntos lógicos chamados de "grupos" e anexar políticas de permissão a esses grupos. Dessa forma, você pode configurar permissões uma vez em nível de grupo e aplicá-las a vários usuários simultaneamente, o que facilita a administração e garante consistência nas políticas de acesso.

***

### <mark style="color:red;">Grupos do IAM</mark>

Grupos no IAM da AWS são conjuntos lógicos de usuários que simplificam o gerenciamento de permissões, oferecendo benefícios significativos para organizar e controlar o acesso aos recursos da AWS de forma escalável e eficiente. Aqui estão os principais pontos sobre grupos do IAM:

#### <mark style="color:blue;">**Herança de Permissões**</mark>

Todos os usuários pertencentes a um grupo herdam as permissões atribuídas a esse grupo. Isso permite conceder e modificar permissões para vários usuários de uma vez, facilitando a administração.

#### <mark style="color:blue;">**Organização por Função**</mark>

Grupos podem ser organizados de acordo com as funções ou cargos dos usuários. Por exemplo, você pode ter grupos para desenvolvedores, segurança e administradores, facilitando a gestão e o controle de quem tem acesso a quais recursos.

#### <mark style="color:blue;">**Flexibilidade e Escalabilidade**</mark>

Ao adicionar um novo usuário, você simplesmente o coloca no grupo apropriado, evitando a necessidade de configurar permissões individuais. Da mesma forma, quando um usuário muda de função, basta removê-lo de um grupo e adicioná-lo a outro para ajustar suas permissões.

#### <mark style="color:blue;">**Características dos Grupos**</mark>

* Um grupo pode ter muitos usuários, facilitando a gestão em grandes organizações.
* Um usuário pode pertencer a vários grupos, permitindo que diferentes conjuntos de permissões sejam combinados conforme necessário.
* No entanto, os grupos não podem ser aninhados dentro de outros grupos.

#### <mark style="color:blue;">**Permissões Iniciais**</mark>

Por padrão, o usuário raiz da AWS possui acesso total a todos os recursos da conta. Em contraste, novos usuários do IAM, grupos ou funções não têm permissões por padrão. As permissões são concedidas explicitamente por meio de políticas do IAM.

#### <mark style="color:blue;">**Políticas do IAM**</mark>

As políticas do IAM definem as permissões que podem ser aplicadas a usuários, grupos ou funções no IAM. Elas especificam quais ações são permitidas ou negadas em quais recursos da AWS.

O uso de grupos no IAM não apenas simplifica a administração de acesso, mas também fortalece a segurança ao permitir uma gestão mais granular e consistente das permissões dentro de uma organização na AWS.

***

### <mark style="color:red;">Políticas do IAM</mark>

As políticas do IAM são essenciais para controlar e gerenciar o acesso aos recursos da AWS de forma granular. Aqui estão os principais pontos sobre como as políticas do IAM são avaliadas:

#### <mark style="color:blue;">**Hierarquia de Avaliação**</mark>

Quando um usuário, grupo ou função faz uma solicitação para um recurso da AWS, a AWS avalia todas as políticas associadas na seguinte ordem:

| Políticas de Usuário                                                  | Políticas de Grupo                                                                                                                           | Políticas de Função                                                                                     |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Primeiro, as políticas anexadas diretamente ao usuário são avaliadas. | Em seguida, as políticas associadas ao grupo ao qual o usuário pertence são avaliadas. O usuário herda todas as permissões dessas políticas. | Se a solicitação é feita por meio de uma função do IAM, as políticas associadas à função são avaliadas. |

#### <mark style="color:blue;">**Permissões Explícitas**</mark>

A avaliação de políticas do IAM segue o princípio de permissões explícitas, o que significa que se uma política nega explicitamente uma ação, essa ação será negada, independentemente de outras políticas permitirem a ação.

#### <mark style="color:blue;">**Permissões Implícitas**</mark>

Se nenhuma política permitir explicitamente uma ação, a ação será negada por padrão.

#### <mark style="color:blue;">**Agrupamento de Permissões**</mark>

Ao agrupar usuários por funções ou departamentos em grupos do IAM, você pode aplicar políticas de grupo que concedem permissões a todos os membros do grupo de uma só vez. Isso simplifica a administração de permissões, garantindo consistência e facilitando alterações organizacionais.

#### <mark style="color:blue;">**Cascata de Permissões**</mark>

As permissões definidas em várias políticas são combinadas usando uma lógica de "união". Isso significa que se uma política permite uma ação específica e outra política também permite a mesma ação, então a ação será permitida para o usuário.

#### <mark style="color:blue;">**Políticas Anexadas Dinamicamente**</mark>

As políticas podem ser anexadas e removidas dinamicamente à medida que as necessidades de acesso dos usuários mudam. Isso proporciona flexibilidade para ajustar as permissões sem a necessidade de modificar a configuração de cada usuário individualmente.

Ao compreender como as políticas do IAM são avaliadas e aplicadas, você pode implementar um modelo de segurança robusto na AWS, garantindo que apenas as ações necessárias sejam permitidas, seguindo o princípio do menor privilégio e melhorando a segurança geral da sua infraestrutura na nuvem.

***

### <mark style="color:red;">Exemplos de políticas do IAM</mark>

A maioria das políticas no IAM da AWS é definida como documentos JSON que especificam permissões detalhadas. Vamos explorar mais sobre os elementos principais de uma política do IAM:

#### <mark style="color:blue;">**Version (Versão)**</mark>

Define a versão da linguagem da política. Para garantir compatibilidade e utilizar todos os recursos disponíveis, é recomendado incluir "Version": "2012-10-17" antes do elemento "Statement"

#### <mark style="color:blue;">**Statement (Declaração)**</mark>

Representa uma ou mais declarações que definem as permissões. Cada declaração possui os seguintes elementos:

| Effect (Efeito)                                                            | Action (Ação)                                                                                                                                   | Resource (Recurso)                                                                                                                                                   |
| -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Especifica se a ação definida será permitida ("Allow") ou negada ("Deny"). | Descreve as ações que são permitidas ou negadas. Pode ser uma ação específica, uma lista de ações ou até mesmo "\*", que indica todas as ações. | Indica quais recursos a declaração afeta. Pode ser um recurso específico identificado pelo seu Amazon Resource Name (ARN) ou "\*", que representa todos os recursos. |

#### <mark style="color:blue;">Exemplo de Política de Administrador</mark>

Aqui está um exemplo de uma política de administrador que permite todas as ações em todos os recursos na conta da AWS:

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "*",
    "Resource": "*"
  }]
}
```

#### <mark style="color:blue;">Exemplo de Política Mais Granular</mark>

Aqui está um exemplo de uma política mais granular que permite que um usuário do IAM altere sua própria senha e obtenha informações sobre seu próprio usuário:

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": [
      "iam:ChangePassword",
      "iam:GetUser"
    ],
    "Resource": "arn:aws:iam::123456789012:user/${aws:username}"
  }]
}
```

Neste exemplo, o uso de `${aws:username}` no ARN do recurso permite que o usuário do IAM acesse apenas suas próprias credenciais. Isso demonstra como você pode definir políticas específicas para controlar o acesso de forma mais granular dentro da sua conta da AWS.

As políticas do IAM permitem que você aplique o princípio do menor privilégio, concedendo apenas as permissões necessárias para cada usuário, grupo ou função, aumentando assim a segurança e o controle sobre seus recursos na nuvem.

***

### <mark style="color:red;">Estrutura da política</mark>

Ao criar uma política, cada um dos elementos mostrados na tabela é necessário na declaração de política.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">**Recursos**</mark>&#x20;

[O que é o IAM?](https://docs.amazonaws.cn/en\_us/IAM/latest/UserGuide/introduction.html)

[Identidades do AWS IAM](https://docs.amazonaws.cn/en\_us/IAM/latest/UserGuide/id.html)

[Gerenciamento de acesso com o AWS IAM](https://docs.amazonaws.cn/en\_us/IAM/latest/UserGuide/access.html)

***
