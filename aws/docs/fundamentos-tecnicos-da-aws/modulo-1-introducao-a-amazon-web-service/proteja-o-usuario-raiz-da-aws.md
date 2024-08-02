# Proteja o usuário raiz da AWS

***

## <mark style="color:red;">Qual é o grande problema de autenticação?</mark>

Quando se trata de configurar o acesso a qualquer conta na AWS, é essencial entender completamente dois conceitos fundamentais: autenticação e autorização.

| Autenticação                                                                                                                                                                                                                                                                                                                                                                                    |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| É o processo fundamental de verificação da identidade de um usuário ou sistema que tenta acessar recursos na AWS. Ao criar uma conta na AWS, você estabelece uma combinação de endereço de e-mail e senha para autenticar sua identidade. Quando um usuário fornece corretamente o e-mail e a senha associados à conta, o sistema verifica essas credenciais e concede acesso.                  |
| O objetivo da autenticação é assegurar que o indivíduo ou sistema é realmente quem afirma ser. Nomes de usuário e senhas são os métodos mais comuns de autenticação, mas a AWS suporta também formas mais avançadas, como autenticação baseada em token ou dados biométricos como impressões digitais. Cada forma de autenticação visa responder à pergunta básica: "Você é quem você diz ser?" |
| Essencialmente, a autenticação é o primeiro passo crítico para garantir a segurança dos recursos na nuvem, validando a identidade de quem busca acesso antes de permitir qualquer interação com os serviços da AWS.                                                                                                                                                                             |

| Autorização                                                                                                                                                                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Após a autenticação bem-sucedida e o acesso à conta da AWS, o próximo passo é compreender a autorização, que é fundamental para determinar quais ações um usuário pode realizar nos recursos e serviços da AWS.                                                                                       |
| Autorização, neste contexto, refere-se ao processo de conceder permissões específicas aos usuários para acessar recursos e produtos da AWS. Ela define quais operações um usuário pode executar, como ler, editar, excluir ou criar recursos dentro da conta AWS.                                     |
| Por exemplo, após autenticar-se na sua conta da AWS com sucesso, a autorização define se você pode iniciar, parar ou modificar instâncias EC2, acessar e modificar dados em buckets S3, ou gerenciar configurações em serviços como RDS. “Quais ações você pode executar?”                            |
| Em resumo, enquanto a autenticação valida quem você é, a autorização determina o que você pode fazer uma vez autenticado. Juntos, esses processos garantem que os recursos na AWS sejam acessados e gerenciados de maneira segura e de acordo com as permissões atribuídas a cada usuário ou sistema. |

***

## <mark style="color:red;">Usuário raiz da AWS</mark>

Ao criar uma conta da AWS pela primeira vez, você começa com uma única identidade de login que tem acesso completo a todos os produtos e recursos da AWS na conta. Essa identidade é chamada de usuário da conta da AWS e é acessada pelo login com o endereço de e-mail e a senha que você usou para criar a conta.

***

### <mark style="color:red;">Credenciais de usuário raiz da AWS</mark>

O usuário raiz da AWS possui dois conjuntos de credenciais associados a ele. O primeiro conjunto é composto pelo endereço de e-mail e senha usados para criar a conta, permitindo o acesso ao Console de Gerenciamento da AWS. O segundo conjunto é conhecido como chaves de acesso, que são utilizadas para fazer solicitações programáticas através da AWS Command Line Interface (AWS CLI) ou da API da AWS.

As chaves de acesso consistem em duas partes:

<figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Assim como uma combinação de nome de usuário e senha, o ID da chave de acesso e a chave de acesso secreta são essenciais para autenticar suas solicitações ao utilizar a AWS CLI ou a API da AWS. É crucial que essas chaves sejam gerenciadas com segurança semelhante à aplicada ao endereço de e-mail e senha da conta raiz.

***

### <mark style="color:red;">Práticas recomendadas ao trabalhar com o usuário raiz da AWS</mark>

O usuário raiz da AWS possui acesso completo a todos os produtos e recursos da conta AWS, além de informações pessoais e de faturamento. Por isso, é crucial adotar práticas rigorosas para proteger suas credenciais e minimizar o uso do usuário raiz para operações diárias.

Para garantir a segurança do usuário raiz, siga estas melhores práticas:

#### <mark style="color:blue;">**Escolha uma senha forte**</mark>

Certifique-se de que a senha do usuário raiz seja robusta, contendo uma combinação de letras maiúsculas, minúsculas, números e caracteres especiais.

#### <mark style="color:blue;">**Não compartilhe suas credenciais**</mark>

Nunca divulgue sua senha de usuário raiz ou as chaves de acesso a ninguém. Mantenha essas informações confidenciais e acessíveis apenas para pessoas autorizadas.

#### <mark style="color:blue;">**Desative ou exclua chaves de acesso**</mark>

Se chaves de acesso foram criadas para o usuário raiz, considere desativá-las ou excluí-las se não forem mais necessárias para evitar potenciais comprometimentos de segurança.

> _Quando é OK usar o usuário raiz da AWS? Para algumas tarefas, você desejará usar o usuário raiz da AWS. Confira os links no final desta seção para ler sobre essas exceções._

***

### <mark style="color:red;">Exclua suas chaves para ficar seguro</mark>

Se você ainda não tem uma chave de acesso para seu usuário raiz da AWS, não crie uma chave a menos que seja realmente necessário. Se você tiver uma chave de acesso para o usuário raiz da sua conta da AWS e quiser excluir as chaves, siga estas etapas:

1. No Console de Gerenciamento da AWS, acesse a página **My Security Credentials** (Minhas credenciais de segurança) e faça login com o endereço de e-mail do usuário raiz e a senha.
2. Abra a seção **Access keys** (Chaves de acesso).
3. Em **Actions** (Ações), escolha **Delete** (Excluir).
4. Escolha **Yes** (Sim).

***

### <mark style="color:red;">Multi-factor authentication (MFA)</mark>

Quando você cria uma conta na AWS e faz login pela primeira vez, utiliza autenticação de fator único, que é simples e comum, exigindo apenas um método de autenticação, como um nome de usuário e senha. No entanto, senhas simples podem ser vulneráveis a ataques se forem fáceis de adivinhar ou decifrar por agentes maliciosos, usando engenharia social, bots ou scripts.

Por exemplo, se a senha de um usuário como Bob, "**IloveCats222**", for baseada em informações facilmente acessíveis (Bob ama gatos e seu aniversário é em 22 de fevereiro), ela pode ser comprometida. Isso destaca a importância da autenticação de múltiplos fatores (MFA) para proteger contas contra acesso não autorizado.

A MFA exige dois ou mais métodos de autenticação para verificar a identidade de um usuário:

| Algo que você sabe                                 | Algo que você tem                                                               | Algo que você é                                        |
| -------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------ |
| Como um nome de usuário e senha, ou um número PIN. | Como uma senha única gerada por um dispositivo de hardware ou aplicativo móvel. | Como tecnologia de reconhecimento facial ou biometria. |

Ao combinar esses métodos, a MFA cria uma camada adicional de segurança. Mesmo que a primeira camada, como a senha de Bob, seja comprometida, a segunda camada, como um token gerado por um aplicativo MFA, adiciona proteção extra. Isso é crucial para proteger contas importantes, como a conta raiz da AWS, contra acessos não autorizados.

Portanto, é altamente recomendável habilitar a MFA na sua conta raiz da AWS para fortalecer a segurança e mitigar o risco de comprometimento de credenciais. Isso ajuda a garantir que apenas usuários autorizados possam acessar e gerenciar recursos na nuvem AWS de maneira segura.

***

### <mark style="color:red;">MFA na AWS</mark>

Quando você habilita a autenticação de múltiplos fatores (MFA) no seu usuário raiz da AWS, você está adicionando uma camada extra de segurança ao processo de login. Isso se deve ao fato de que a MFA requer não apenas as credenciais normais de login (como e-mail e senha), mas também um código numérico temporário gerado por um dispositivo MFA compatível.

Ao ativar a MFA, você realiza o seguinte processo:

| Primeira etapa de identificação                                                | Segunda etapa de identificação                                                                                                                                             |
| ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Você insere seu e-mail e senha para autenticar sua identidade como de costume. | Além das credenciais normais, você precisa fornecer um código numérico único que é gerado pelo dispositivo MFA (como um aplicativo de smartphone ou um token de hardware). |

Essa combinação de informações verifica duas categorias de identificação ("algo que você conhece" e "algo que você tem"), fornecendo uma proteção adicional contra acesso não autorizado à sua conta raiz da AWS.

Habilitar a MFA na conta raiz é fortemente recomendado pela AWS como uma prática essencial de segurança. Isso ajuda a proteger suas informações confidenciais e recursos na nuvem contra ameaças como acesso indevido por parte de terceiros, garantindo que apenas usuários autorizados possam acessar e gerenciar sua conta AWS de forma segura.

***

### <mark style="color:red;">Dispositivos MFA compatíveis</mark>

A AWS oferece suporte a uma variedade de mecanismos de MFA, como dispositivos virtuais com MFA, dispositivos de hardware e chaves de segurança Universal 2nd Factor (U2F). Para obter instruções sobre como configurar cada método, confira a seção Resources (Recursos).

<figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">**Recursos**</mark>&#x20;

[Habilitação de dispositivo MFA de hardware (console)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_mfa\_enable\_physical.html)

[H](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_mfa\_enable\_physical.html)[abilitação de uma chave de segurança U2F (console)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_mfa\_enable\_u2f.html)

[H](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_mfa\_enable\_physical.html)[abilitação de um dispositivo virtual de Multi-Factor Authentication (MFA) (console)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_mfa\_enable\_virtual.html)

[Tabela de dispositivos MFA suportados](https://aws.amazon.com/iam/features/mfa/)

***
