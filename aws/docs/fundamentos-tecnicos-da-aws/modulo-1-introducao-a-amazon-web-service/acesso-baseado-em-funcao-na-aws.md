---
description: >-
  Esta seção resume algumas das práticas recomendadas mais importantes do IAM
  com as quais você deve estar familiarizado antes de criar soluções na AWS.
---

# Acesso baseado em função na AWS

***

## <mark style="color:red;">Bloquear o usuário raiz da AWS</mark>

O usuário raiz é uma identidade poderosa em sua conta da AWS, capaz de acessar todos os recursos e informações, incluindo dados pessoais e de faturamento. Para garantir a segurança, é fundamental tomar medidas para proteger o usuário raiz:

#### <mark style="color:blue;">**Não compartilhe as credenciais**</mark>

Evite compartilhar o endereço de e-mail, senha ou chaves de acesso associadas ao usuário raiz com terceiros. Mantenha essas informações confidenciais para evitar acesso não autorizado.

#### <mark style="color:blue;">**Considere excluir chaves de acesso**</mark>

Se o usuário raiz não precisar de acesso programático à AWS, é recomendável excluir as chaves de acesso associadas a ele. Isso reduz o risco de comprometimento por meio de solicitações programáticas não autorizadas.

#### <mark style="color:blue;">**Habilitar MFA na conta raiz**</mark>

Habilitar a autenticação multifatorial (MFA) para o usuário raiz é uma prática crucial de segurança. A MFA adiciona uma camada adicional de proteção, exigindo um segundo fator de autenticação além da senha padrão, como um código gerado por aplicativo ou um dispositivo MFA físico.

Essas medidas ajudam a mitigar os riscos associados ao usuário raiz, reforçando a segurança da conta da AWS contra acesso não autorizado e possíveis comprometimentos de segurança.

***

## <mark style="color:red;">Adote o princípio de privilégio mínimo</mark>

O princípio do menor privilégio é uma prática de segurança fundamental que recomenda conceder apenas as permissões necessárias para realizar uma tarefa específica e nada além disso. Ao implementar o menor privilégio no controle de acesso usando o AWS Identity and Access Management (IAM), você pode aumentar significativamente a segurança de sua conta da AWS.&#x20;

Aqui estão os passos para implementar o menor privilégio:

#### <mark style="color:blue;">**Iniciar com o conjunto mínimo de permissões**</mark>

Ao criar políticas do IAM, comece definindo apenas as permissões essenciais necessárias para realizar uma tarefa específica. Por exemplo, se um usuário precisa apenas de acesso de leitura a um bucket do Amazon S3, conceda apenas permissões de leitura (por exemplo, s3).

#### <mark style="color:blue;">**Concessão de permissões adicionais conforme necessário**</mark>

À medida que as necessidades de acesso evoluem, conceda permissões adicionais de forma granular e apenas quando necessário. Evite conceder permissões excessivas que possam comprometer a segurança da conta.

#### <mark style="color:blue;">**Revisão regular das permissões**</mark>

Periodicamente, revise as permissões atribuídas aos usuários, grupos e funções do IAM. Remova ou ajuste as permissões que não são mais necessárias para reduzir a superfície de ataque.

#### <mark style="color:blue;">**Utilização de grupos do IAM**</mark>

Organize usuários com funções semelhantes em grupos do IAM e atribua políticas de grupo que concedem permissões apropriadas para cada função. Isso simplifica o gerenciamento de permissões em escala e facilita a aplicação do princípio do menor privilégio.

#### <mark style="color:blue;">**Monitoramento e auditoria**</mark>

Implemente monitoramento contínuo e auditoria das permissões do IAM para identificar atividades suspeitas ou permissões excessivas. Utilize os recursos da AWS como AWS CloudTrail e AWS Config para registrar e analisar eventos de acesso.

Ao seguir o princípio do menor privilégio, você reduz o risco de comprometimento da segurança ao limitar o acesso apenas ao necessário para realizar operações específicas, mantendo a integridade e a segurança dos recursos na AWS.

***

## <mark style="color:red;">Usar o IAM adequadamente</mark>

O AWS IAM (Identity and Access Management) é essencial para controlar quem pode acessar seus recursos na AWS. Ele permite criar e gerenciar usuários, grupos e funções para acesso dentro de uma conta da AWS. No entanto, o IAM não deve ser confundido com ferramentas de autenticação e autorização usadas em sites para login de usuários. Ele também não oferece recursos para proteger sistemas operacionais e redes contra ameaças externas. Em resumo, o IAM é focado na gestão de acesso aos serviços e recursos específicos da AWS, não lidando com aspectos como login de usuários em sites ou segurança de sistemas operacionais.

***

## <mark style="color:red;">Usar funções do IAM quando possível</mark>

Manter funções no AWS IAM é mais eficiente do que manter usuários individuais. Quando um usuário assume uma função, o IAM gera credenciais temporárias que têm um tempo de vida definido, geralmente entre 15 minutos e 36 horas, e que expiram automaticamente. Em contraste, os usuários tradicionais têm credenciais de longo prazo, como nomes de usuário e senhas, ou conjuntos de chaves de acesso.

As chaves de acesso de um usuário comum permanecem válidas até que sejam explicitamente rotacionadas pelo usuário ou pelo administrador da conta. Já as credenciais de login de um usuário expiram se uma política de senha é aplicada à conta, obrigando os usuários a alterarem suas senhas periodicamente.

***

## <mark style="color:red;">Considere usar um provedor de identidade</mark>

Se você planeja expandir sua aplicação de fotos de gatos em uma empresa com várias pessoas trabalhando nela, é recomendável considerar o uso de um provedor de identidade (IdP) para gerenciar as informações de identidade dos funcionários. Tanto produtos da AWS, como o AWS Single Sign-On, quanto provedores de identidade de terceiros oferecem uma única fonte centralizada para todas as identidades na organização.

Ao adotar um IdP, você elimina a necessidade de criar usuários separados no AWS IAM para cada funcionário. Em vez disso, você pode usar funções do IAM para conceder permissões às identidades federadas do IdP. Por exemplo, se você tem uma funcionária chamada Marta que precisa acessar várias contas da AWS, ao invés de criar e gerenciar múltiplos usuários do IAM chamados Marta em cada conta AWS, você pode gerenciar Marta centralmente através do IdP da sua empresa. Se Marta for promovida ou deixar a empresa, você pode atualizar suas credenciais no IdP, refletindo automaticamente em todos os acessos que ela tinha nas contas AWS, sem a necessidade de ajustar cada conta individualmente.

***

## <mark style="color:red;">Considere o AWS Single Sign-On</mark>

O AWS SSO (AWS Single Sign-On) é um provedor de identidade (IdP) que simplifica o processo de login para os usuários em uma organização que utiliza várias contas da AWS. Ele permite que os usuários façam login em um único portal com um conjunto de credenciais, e então proporciona acesso centralizado às contas e aplicações designadas.

Comparado ao IAM, o AWS SSO opera de forma semelhante ao fornecer um diretório onde você pode criar usuários, agrupá-los, definir permissões entre grupos e conceder acesso aos recursos da AWS. No entanto, o AWS SSO oferece várias vantagens. Por exemplo, ele facilita a integração com provedores de identidade de terceiros, permitindo a sincronização automática de usuários e grupos já existentes. Isso evita a necessidade de recrear perfis de usuário que já estão configurados em outro lugar e simplifica o gerenciamento de identidades através do IdP escolhido.

Além disso, o AWS SSO separa claramente as responsabilidades entre o IdP e a AWS, garantindo que o gerenciamento de acesso aos recursos na nuvem não esteja diretamente ligado ou dependente do provedor de identidade. Isso ajuda a manter a segurança e a eficiência na gestão de acesso em ambientes corporativos complexos com várias contas e usuários.

***

## <mark style="color:red;">**Recursos**</mark>&#x20;

[Práticas recomendadas de segurança no IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)

[Como criar e gerenciar usuários no AWS Single Sign-On](https://aws.amazon.com/blogs/security/how-to-create-and-manage-users-within-aws-sso/)

***
