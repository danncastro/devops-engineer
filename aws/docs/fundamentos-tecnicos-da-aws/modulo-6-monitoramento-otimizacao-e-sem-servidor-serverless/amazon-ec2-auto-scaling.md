# Amazon EC2 Auto Scaling

***

## <mark style="color:red;">**Problemas de capacidade**</mark>

Para melhorar a disponibilidade e acessibilidade de um sistema, adicionar mais servidores é uma estratégia comum. No entanto, isso não resolve completamente o problema se houver falhas de capacidade. Vamos examinar como o problema de carga afeta sistemas ativo-passivo e ativo-ativo.

#### <mark style="color:blue;">**Sistemas Ativo-Passivo**</mark>

| Descrição                                                                                    | Desafio de Capacidade                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Em sistemas ativo-passivo, apenas uma instância está ativa enquanto a outra fica em standby. | Se a carga aumentar significativamente, o sistema pode enfrentar problemas se a instância ativa não conseguir lidar com a demanda adicional. Nesse caso, a disponibilidade do sistema pode ser comprometida até que a instância de standby seja ativada, o que pode levar tempo. |

#### <mark style="color:blue;">**Sistemas Ativo-Ativo**</mark>

| Descrição                                                                                     | Desafio de Capacidade                                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Em sistemas ativo-ativo, ambas as instâncias estão ativas e compartilham a carga de trabalho. | Apesar de ter maior capacidade de escalar horizontalmente e distribuir a carga, se uma das instâncias não estiver dimensionada adequadamente para suportar picos de tráfego, isso pode afetar o desempenho geral da aplicação. |

#### <mark style="color:blue;">**Casos de Uso e Benefícios**</mark>

| Ativo-Passivo                                                                                                                                                                       | Ativo-Ativo                                                                                                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| É útil para aplicações com necessidades modestas de escalabilidade e onde a recuperação de desastres é crítica. Ideal para cargas de trabalho previsíveis e com demandas variáveis. | Recomendado para aplicações que requerem alta disponibilidade e escalabilidade dinâmica. É eficaz para lidar com picos de tráfego imprevisíveis e manter o desempenho mesmo diante de falhas de um dos servidores. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Ativo-Passivo                                                                                                                 | Ativo-Ativo                                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Oferece segurança adicional em caso de falha total de uma instância, garantindo continuidade dos serviços após a recuperação. | Proporciona melhor desempenho sob cargas de trabalho variáveis e permite escalabilidade instantânea para atender a demandas crescentes, minimizando impactos de falhas individuais. |

Ao considerar problemas de capacidade, é crucial escolher o modelo mais adequado com base nas características da aplicação, necessidades de disponibilidade e capacidade de resposta a picos de tráfego, garantindo assim uma operação contínua e eficiente do sistema.

***

## <mark style="color:red;">Escalabilidade vertical</mark>

A escalabilidade vertical é essencial quando se trata de aumentar a capacidade de um sistema ativo-passivo para lidar com cargas de trabalho crescentes. Neste modelo, você aumenta a capacidade de um servidor existente ao escolher um tipo de instância maior ou diferente no Amazon EC2, por exemplo. Aqui estão os passos típicos envolvidos:

| Interrupção e Alteração da Instância                                                                                          | Ativação e Troca de Tráfego                                                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A instância passiva é interrompida sem afetar a aplicação em execução. Em seguida, o tipo ou tamanho da instância é alterado. | Após a alteração, a instância passiva é reiniciada e assume o tráfego ativo, enquanto a instância anterior é ajustada de acordo para manter a consistência. |

| Limitações da Escalabilidade Vertical                                                                                                                                                         | Transição de Retorno                                                                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Este método pode ser trabalhoso, envolvendo várias etapas manuais. Além disso, há um limite para o quanto um servidor pode ser escalado verticalmente antes de atingir sua capacidade máxima. | Quando a carga diminui, o processo pode ser revertido. No entanto, há limitações práticas quanto ao número de vezes que esse tipo de escalabilidade pode ser aplicado eficientemente. |

#### <mark style="color:blue;">**Casos de Uso e Vantagens**</mark>

| Aplicações Críticas com Estado                                                                                                                                        | Cargas de Trabalho Variáveis                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Ideal para sistemas que exigem alta disponibilidade e integridade de dados, como bancos de dados e sistemas financeiros, onde a consistência dos dados é fundamental. | Útil para aplicações com padrões de tráfego previsíveis, onde picos ocasionais exigem aumento rápido da capacidade. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Manutenção da Integridade e Consistência                                                                                        | Utilização de Recursos Existentes                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| A escalabilidade vertical permite que a aplicação mantenha seu estado e integridade dos dados durante os ajustes de capacidade. | Aproveita ao máximo os recursos do servidor existente antes de considerar outras estratégias de escalabilidade. |

No entanto, quando a demanda por capacidade aumenta constantemente ou quando há a necessidade de maior flexibilidade e distribuição de carga, a escalabilidade horizontal oferecida por sistemas ativo-ativo se torna mais vantajosa. Isso permite adicionar novos servidores conforme necessário, distribuindo a carga de forma eficiente e sem os limites associados à escalabilidade vertical.

***

## <mark style="color:red;">Escalabilidade horizontal</mark>

Escalabilidade horizontal é crucial para sistemas ativo-ativo, especialmente quando se trata de aplicações stateless, que não armazenam sessões de cliente no servidor. Nesse contexto, adicionar mais servidores não requer modificações na aplicação. Apenas aumenta-se o número de instâncias conforme necessário e reduz-se quando o tráfego diminui. O Amazon EC2 Auto Scaling automatiza esse processo, criando e removendo instâncias do EC2 com base em métricas do Amazon CloudWatch.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Flexibilidade de Escalabilidade                                                                                    |
| ------------------------------------------------------------------------------------------------------------------ |
| Ideal para aplicações web modernas e serviços em nuvem que precisam lidar com variações significativas no tráfego. |

| Redundância e Disponibilidade                                                                                       | Eficiência de Recursos                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Garante que a aplicação permaneça disponível mesmo se um dos servidores falhar, mantendo a continuidade do serviço. | Aproveita melhor os recursos disponíveis, distribuindo a carga de trabalho de forma mais equilibrada entre várias instâncias. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Resposta Dinâmica a Demandas                                                                                                                          | Economia de Custos                                                                                                                    |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Capacidade de escalar horizontalmente de forma dinâmica conforme a demanda aumenta ou diminui, proporcionando uma experiência de usuário consistente. | Permite otimizar os custos operacionais ao ajustar automaticamente a capacidade de acordo com as necessidades reais de processamento. |

Ao contrário da escalabilidade vertical, que tem limitações práticas, a escalabilidade horizontal oferece uma abordagem mais flexível e resiliente para lidar com crescimentos imprevisíveis ou picos de tráfego. Isso torna-se essencial para aplicações modernas que precisam lidar com grandes volumes de usuários simultâneos ou variações sazonais na demanda.

***

### <mark style="color:red;">ELB com EC2 Auto Scaling</mark>

O serviço ELB se integra de forma eficaz ao EC2 Auto Scaling, proporcionando uma solução robusta para escalabilidade automática de aplicações na AWS. Quando uma nova instância do EC2 é adicionada ou removida do grupo do EC2 Auto Scaling, o ELB é imediatamente notificado. No entanto, antes de encaminhar tráfego para uma nova instância do EC2, o ELB realiza verificações para garantir que a aplicação esteja operacional.

#### <mark style="color:blue;">**Funcionalidades Principais**</mark>

{% tabs %}
{% tab title="Verificações de Integridade" %}
O ELB utiliza dois métodos para validar a integridade das instâncias do EC2:

* Estabelecimento de conexão TCP com o servidor back-end e marcação da instância como disponível se a conexão for bem-sucedida.
* Realização de solicitação HTTP ou HTTPS para uma página específica e validação do código de resposta HTTP recebido.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Escalabilidade Automática                                                                                                                         | Alta Disponibilidade                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Ideal para aplicações que experimentam variações significativas no tráfego, permitindo ajustes dinâmicos na capacidade do EC2 conforme a demanda. | Garante que o tráfego seja direcionado apenas para instâncias funcionais do EC2, melhorando a disponibilidade e a confiabilidade da aplicação. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Simplicidade Operacional                                                                                   | Monitoramento Contínuo                                                                                                                                         |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Automatiza o gerenciamento de capacidade e disponibilidade, reduzindo a necessidade de intervenção manual. | Oferece uma solução proativa ao monitorar constantemente a saúde das instâncias do EC2, garantindo que apenas instâncias íntegras recebam tráfego de usuários. |

A integração entre ELB e EC2 Auto Scaling é essencial para implementações escaláveis e resilientes na nuvem, permitindo que as aplicações se adaptem rapidamente às mudanças nas condições de uso sem comprometer a performance ou a experiência do usuário.

***

## <mark style="color:red;">Escalonamento tradicional versus autoescalabilidade</mark>

Na abordagem tradicional de escalonamento, os servidores são comprados e provisionados para lidar com o pico máximo de tráfego. Isso resulta em capacidade ociosa durante os períodos de baixo tráfego, desperdiçando recursos e dinheiro. Desligar servidores ociosos pode economizar energia, mas não otimiza completamente os custos.

Na nuvem, com o modelo de pagamento conforme o uso, como o EC2 sob demanda, é crucial desativar recursos não utilizados para evitar gastos desnecessários. Gerenciar manualmente a adição e remoção de servidores é possível, mas pode levar a subprovisionamento ou superprovisionamento dependendo da demanda variável.

#### <mark style="color:blue;">**Benefícios da Autoescalabilidade**</mark>

| Otimização de Custos                                                                                                                                                                 | Resposta a Picos de Tráfego                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A autoescalabilidade ajusta dinamicamente a capacidade dos servidores com base nas necessidades reais de tráfego, evitando tanto o subprovisionamento quanto o superprovisionamento. | Automatiza a adição de novas instâncias do EC2 durante picos inesperados de tráfego, garantindo disponibilidade e performance sem a necessidade de intervenção manual. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| E-commerce                                                                                                                                       | Aplicações Web                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Durante promoções ou eventos sazonais, a autoescalabilidade garante que o site permaneça acessível mesmo com um aumento repentino de visitantes. | Para plataformas que recebem carga variável ao longo do dia, a autoescalabilidade ajusta dinamicamente a capacidade para otimizar custos sem comprometer a disponibilidade. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Eficiência Operacional                                                                                                   | Economia Financeira                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| Reduz a necessidade de gerenciamento manual, permitindo que os recursos sejam alocados conforme a demanda em tempo real. | Maximiza a eficiência dos recursos na nuvem, evitando desperdícios e otimizando os custos operacionais. |

O EC2 Auto Scaling é essencial para empresas que buscam flexibilidade, eficiência e economia na gestão de infraestrutura na nuvem, adaptando-se de forma inteligente às flutuações na demanda de tráfego sem comprometer a performance ou a experiência do usuário.

***

## <mark style="color:red;">Amazon EC2 Auto Scaling</mark>

O Amazon EC2 Auto Scaling é um serviço projetado para ajustar dinamicamente a capacidade da sua infraestrutura de acordo com a demanda, garantindo performance estável e otimização de custos. Ele permite escalar automaticamente a quantidade de instâncias do EC2 com base nos requisitos específicos da sua aplicação. Ao fazer isso, você paga somente pelo uso real, sem desperdícios de recursos.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Otimização de Custos                                                                                            | Garantia de Disponibilidade                                                                                         |
| --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Ajusta a capacidade conforme a demanda em tempo real, evitando custos desnecessários com infraestrutura ociosa. | Substitui automaticamente instâncias com problemas, garantindo que sua aplicação permaneça disponível e resiliente. |

| Escalabilidade Automática                                                                                                                                                          | Gerenciamento de Frotas                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Ideal para aplicações com picos variáveis de tráfego, como e-commerce durante promoções, garantindo que a capacidade seja escalada adequadamente para atender à demanda crescente. | Ajuda na gestão eficiente de grandes conjuntos de instâncias, monitorando e ajustando automaticamente conforme necessário. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Eficiência Operacional                                                                                                       | Confiabilidade                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Automatiza o dimensionamento da infraestrutura, liberando recursos de gerenciamento para focar em outras áreas estratégicas. | Minimiza o tempo de inatividade ao substituir automaticamente instâncias com falhas, mantendo a continuidade dos serviços. |

O Amazon EC2 Auto Scaling é essencial para empresas que precisam de flexibilidade, eficiência e confiabilidade na gestão de recursos de computação na nuvem, adaptando-se dinamicamente às necessidades da aplicação e garantindo uma operação suave e econômica.

***

### <mark style="color:red;">Configurar componentes do EC2 Auto Scaling</mark>

O Amazon EC2 Auto Scaling possui três componentes essenciais para sua configuração:

| Modelo de Lançamento ou Configuração                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Define quais recursos serão escalados automaticamente, como instâncias do EC2 e suas configurações associadas, como tipos de instância, AMIs (Amazon Machine Images) e opções de rede. |

| Grupo do EC2 Auto Scaling                                                                                                                                                                                                                     | Políticas de Escalabilidade                                                                                                                                                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| É o ambiente onde as instâncias do EC2 serão lançadas e gerenciadas pelo EC2 Auto Scaling. Inclui definições como número mínimo e máximo de instâncias, zonas de disponibilidade e outras configurações relacionadas à distribuição e escala. | Estabelecem as condições para adicionar ou remover instâncias automaticamente com base em métricas específicas, como uso da CPU, tráfego de rede ou outras métricas personalizadas. Essas políticas garantem que o sistema se adapte dinamicamente às demandas da aplicação. |

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Escalabilidade Automática                                                                                                                            | Resiliência e Disponibilidade                                                                                                                 | Eficiência Operacional                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Ideal para aplicações que experimentam variações significativas de tráfego, como plataformas de e-commerce durante períodos de alta demanda sazonal. | Garante que a aplicação permaneça operacional mesmo em caso de falha de instâncias, substituindo automaticamente as instâncias com problemas. | Otimiza os custos ao ajustar dinamicamente a capacidade com base na necessidade real, evitando desperdício de recursos. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Automatização                                                                                                                 | Agilidade                                                                                                          | Economia                                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Simplifica o gerenciamento de infraestrutura ao automatizar o dimensionamento de recursos com base em políticas predefinidas. | Permite uma resposta rápida a mudanças na demanda, garantindo que a capacidade seja adequada em todos os momentos. | Reduz os custos operacionais ao alinhar precisamente a capacidade de computação com o uso real da aplicação, sem excessos ou falta de recursos. |

Configurar adequadamente esses componentes no Amazon EC2 Auto Scaling é fundamental para empresas que buscam flexibilidade, eficiência e confiabilidade na gestão de recursos na nuvem, adaptando-se dinamicamente às necessidades da aplicação e garantindo uma operação suave e econômica.

***

### <mark style="color:red;">Modelos de execução</mark>

Os modelos de inicialização são essenciais para definir todas as configurações necessárias ao lançar instâncias do EC2, incluindo AMI, tipo de instância, grupo de segurança e volumes do EBS. Aqui estão os benefícios e maneiras de usar esses modelos:

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Benefícios dos Modelos de Inicialização**</mark>

| Automação de Implantação                                                                                                       | Versionamento                                                                                                                                     | Flexibilidade                                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Permitem lançar instâncias do EC2 de forma consistente e automatizada, tanto manualmente quanto com o Amazon EC2 Auto Scaling. | Suportam versionamento para facilitar a reversão a versões anteriores em caso de problemas ou necessidade de retornar a uma configuração estável. | Podem ser criados de três maneiras: a partir de uma instância existente, de um modelo anterior ou do zero, permitindo ajustes precisos conforme necessário. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Ambientes Escaláveis                                                                                                        | Gestão de Configuração                                                                                      | Desenvolvimento Iterativo                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Ideal para aplicações que requerem escalabilidade automática, como plataformas web que enfrentam picos sazonais de tráfego. | Facilita a padronização e a gestão de configurações em ambientes complexos com múltiplas instâncias do EC2. | Suporta iterações rápidas de desenvolvimento, onde é crucial manter diferentes versões de configurações de instância. |

#### <mark style="color:blue;">**Por que Usar Modelos de Inicialização**</mark>

| Eficiência Operacional                                                                                                         | Controle de Versão                                                                                                                |
| ------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| Automatiza o processo de lançamento de instâncias do EC2, reduzindo erros manuais e garantindo consistência nas configurações. | Permite gerenciar alterações de configuração com facilidade, mantendo um histórico de versões para rápida reversão ou comparação. |

| Adoção de Recursos Atualizados                                                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ao utilizar modelos de inicialização, você garante que esteja sempre utilizando os recursos mais recentes do Amazon EC2, maximizando a eficiência e segurança da sua infraestrutura na nuvem. |

Usar modelos de inicialização é uma prática recomendada pela AWS para otimizar o gerenciamento de recursos no Amazon EC2, proporcionando flexibilidade e controle durante todo o ciclo de vida das instâncias.

***

### <mark style="color:red;">Grupos do EC2 Auto Scaling</mark>

Os grupos do EC2 Auto Scaling são fundamentais para configurar e gerenciar a escalabilidade automática das instâncias do EC2. Aqui estão os principais pontos sobre sua configuração e uso:

#### <mark style="color:blue;">**Componentes Essenciais**</mark>

| Localização e Rede                                                                                                                                                                                                                                             | Modelo de Compra de Instâncias                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Um grupo do Auto Scaling define onde as instâncias do EC2 serão implantadas dentro da Amazon VPC. É crucial selecionar pelo menos duas sub-redes distribuídas em diferentes zonas de disponibilidade para garantir alta disponibilidade e tolerância a falhas. | Você pode configurar o tipo de compra das instâncias do EC2, escolhendo entre sob demanda, spot ou uma combinação dos dois. Isso permite aproveitar instâncias spot com custo reduzido, sem complicação administrativa excessiva. |

| Configuração de Capacidade                                                                                                                                                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;">**Mínimo**</mark>**:** Define o número mínimo de instâncias que devem estar em execução, mesmo que o tráfego seja baixo. Isso garante que haja sempre uma capacidade mínima para lidar com cargas inesperadas.     |
| <mark style="color:red;">**Máximo**</mark>**:** Estabelece o número máximo de instâncias que podem ser escaladas pelo Auto Scaling, limitando os custos e garantindo que não haja escalonamento excessivo.                                     |
| <mark style="color:green;">**Capacidade Desejada**</mark>**:** Define o número ideal de instâncias que devem estar em execução. O Auto Scaling ajusta automaticamente a quantidade de instâncias para corresponder a essa capacidade desejada. |

<figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações com Demanda Variável                                                               |
| --------------------------------------------------------------------------------------------- |
| Ideal para aplicações web que enfrentam flutuações no tráfego ao longo do dia, semana ou ano. |

| Ambientes de Produção                                                                                                                                      | Gerenciamento de Custos                                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Garante que a infraestrutura seja dimensionada automaticamente para atender aos requisitos de carga sem intervenção manual, mantendo alta disponibilidade. | Permite otimizar os custos operacionais usando instâncias spot para cargas de trabalho não críticas, reduzindo assim o orçamento de infraestrutura. |

#### <mark style="color:blue;">**Por que Usar Grupos do EC2 Auto Scaling**</mark>

| Escalabilidade Automática                                                                                                              | Alta Disponibilidade                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Ajusta automaticamente o número de instâncias do EC2 com base na demanda real da aplicação, mantendo a performance e reduzindo custos. | Distribui instâncias em zonas de disponibilidade diferentes para garantir que a falha em uma zona não afete a disponibilidade da aplicação. |

| Gerenciamento de Custo Eficiente                                                                                                              |
| --------------------------------------------------------------------------------------------------------------------------------------------- |
| Permite usar instâncias spot para economizar dinheiro em cargas de trabalho não críticas, sem comprometer a disponibilidade ou a performance. |

Configurar corretamente os grupos do EC2 Auto Scaling é fundamental para otimizar a operação e a eficiência dos recursos na nuvem, proporcionando flexibilidade e controle sobre a infraestrutura da sua aplicação.

***

### <mark style="color:red;">**Disponibilidade com o EC2 Auto Scaling**</mark>

O EC2 Auto Scaling oferece alta disponibilidade configurando dinamicamente a capacidade de instâncias do EC2 com base em três configurações essenciais: mínimo, máximo e desejado. Definir todos os três valores iguais, por exemplo, quatro, garante que o Auto Scaling mantenha constantemente quatro instâncias ativas. Se uma instância falhar, o Auto Scaling automaticamente a substituirá, assegurando que a capacidade mínima seja sempre mantida.

<figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Ambientes Críticos                                                                                                                                                                  | Gerenciamento Simplificado                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Aplicações que requerem disponibilidade contínua, como plataformas de comércio eletrônico durante períodos de alto tráfego ou serviços de streaming que não podem ter interrupções. | Ideal para equipes de operações que buscam automação para manter uma frota de instâncias EC2 com um número específico de instâncias operacionais a qualquer momento. |

#### <mark style="color:blue;">**Por que Usar Disponibilidade com o EC2 Auto Scaling**</mark>

| Alta Disponibilidade Automática                                                                                                                                    | Eficiência Operacional                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Garante que o número especificado de instâncias esteja sempre disponível, substituindo automaticamente qualquer instância que não esteja funcionando corretamente. | Minimiza a necessidade de intervenção manual para lidar com falhas de instâncias, permitindo que a equipe se concentre em tarefas mais estratégicas. |

Configurar o EC2 Auto Scaling para manter uma capacidade estável e resiliente é crucial para garantir que suas aplicações permaneçam disponíveis e respondam eficazmente às demandas variáveis de tráfego.

***

## <mark style="color:red;">Automação com políticas de escalabilidade</mark>

No Amazon EC2 Auto Scaling, as políticas de escalabilidade automatizam o ajuste dinâmico da capacidade com base nas métricas monitoradas pelo Amazon CloudWatch. Isso elimina a necessidade de ajustes manuais frequentes na capacidade desejada do grupo do Auto Scaling.

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Gestão Proativa da Capacidade                                                                                                        | Otimização de Custos                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| Útil para aplicações que enfrentam flutuações de tráfego ao longo do dia, como plataformas de e-commerce durante promoções sazonais. | Ajuste automático da capacidade para minimizar gastos operacionais, adicionando ou removendo instâncias conforme a demanda real. |

#### <mark style="color:blue;">**Por que Usar Automação com Políticas de Escalabilidade**</mark>

| Eficiência Operacional                                                                                                                                    | Resposta Rápida                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Utilização de métricas como CPU, tráfego de rede e outras para acionar ações automatizadas de escalabilidade, garantindo desempenho estável da aplicação. | Implementação de políticas simples, por etapas ou baseadas em metas para responder rapidamente às mudanças nas condições de utilização. |

As políticas de escalabilidade do EC2 Auto Scaling oferecem uma abordagem eficaz para otimizar a capacidade de infraestrutura na nuvem, proporcionando flexibilidade e confiabilidade para aplicações dinâmicas e escaláveis.

***

### <mark style="color:red;">**Política de escalabilidade**</mark>

ChatGPT

A política de escalabilidade simples no Amazon EC2 Auto Scaling permite definir ações com base em alarmes do Amazon CloudWatch. Ela é eficaz para adicionar ou remover várias instâncias do EC2 ou definir um número específico de instâncias para ajustar a capacidade conforme necessário. Você pode usar porcentagens para escalar rapidamente o grupo, em vez de quantidades fixas, facilitando o crescimento ou a redução dinâmica do grupo.

#### <mark style="color:blue;">**Casos de Usos**</mark>

| Aplicações com Flutuações Diárias                                                                                         | Ambientes de Teste e Desenvolvimento                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Ideal para plataformas que experimentam picos de tráfego durante certos horários do dia, como sites de notícias ou blogs. | Automatização do dimensionamento de recursos para ambientes que variam em demanda ao longo do ciclo de desenvolvimento. |

#### <mark style="color:blue;">**Por que Usar Política de Escalabilidade Simples**</mark>

| Simplicidade na Implementação                                                                  | Resposta Rápida a Mudanças                                                                         |
| ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Configuração direta com base em métricas de uso, sem a necessidade de configurações complexas. | Ações imediatas com base em thresholds de CPU, permitindo uma adaptação ágil à demanda do sistema. |

A política de escalabilidade simples é uma ferramenta poderosa para ajustar automaticamente a capacidade do EC2, garantindo que sua aplicação mantenha o desempenho e a disponibilidade conforme necessário, sem necessidade de intervenção manual constante.

***

### <mark style="color:red;">**Política de escalabilidade de etapas**</mark>

A política de escalabilidade de etapas no Amazon EC2 Auto Scaling oferece um método mais sofisticado para ajustar a capacidade com base em métricas do Amazon CloudWatch. Diferente da política simples, a de etapas permite responder a múltiplos alarmes simultaneamente, mesmo durante ações de escalabilidade ou verificações de integridade em andamento. Por exemplo, você pode configurar o sistema para adicionar duas novas instâncias quando a utilização da CPU atingir 85% e mais quatro instâncias quando alcançar 95%.

#### <mark style="color:blue;">**Casos de Usos**</mark>

| Aplicações com Cargas Variáveis                                                                                                                       | Eventos de Picos Previsíveis                                                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Útil para plataformas que experimentam flutuações significativas no tráfego, permitindo um ajuste mais granular conforme a demanda cresce ou diminui. | Empresas que esperam picos sazonais ou eventos específicos podem programar aumentos escalonados na capacidade para lidar com maior tráfego sem interrupções. |

#### <mark style="color:blue;">**Por que Usar Política de Escalabilidade de Etapas**</mark>

| Flexibilidade Avançada                                                                                                    | Gestão Precisa de Recursos                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Responde de maneira escalonada a diferentes níveis de utilização, adaptando-se gradualmente às necessidades da aplicação. | Permite ajustes mais finos e específicos, minimizando o risco de sobrecarga ou subutilização dos recursos. |

A política de escalabilidade de etapas é uma escolha estratégica para operações que requerem um controle mais detalhado sobre a escalabilidade, proporcionando um equilíbrio entre responsividade às mudanças de carga e estabilidade operacional.

***

### <mark style="color:red;">**Política de dimensionamento para monitoramento de targets**</mark>

A política de dimensionamento para monitoramento de targets no Amazon EC2 Auto Scaling é ideal para aplicações que precisam ser escaladas com base em métricas específicas, como utilização média da CPU, da rede (dentro ou fora) ou contagem de solicitações. Neste tipo de política, você define um valor de destino a ser alcançado e o sistema automaticamente configura os alarmes necessários no Amazon CloudWatch.

#### <mark style="color:blue;">**Casos de Usos**</mark>

| Aplicações com Requisitos de Desempenho                                                                                                                                       | Gerenciamento de Carga Previsível                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Útil para plataformas que necessitam ajustar a capacidade com base em métricas de desempenho críticas, como CPU e tráfego de rede, para manter uma resposta rápida e estável. | Ideal para cenários onde a demanda varia previsivelmente ao longo do tempo, permitindo uma adaptação proativa e eficiente da capacidade. |

#### <mark style="color:blue;">**Por que Usar Política de Dimensionamento para Monitoramento de Targets**</mark>

| Automatização Simplificada                                                                                                                                                            | Precisão na Escalabilidade                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Configura automaticamente os alarmes do CloudWatch com base nos seus parâmetros de desempenho, eliminando a necessidade de configuração manual e otimizando o monitoramento contínuo. | Permite ajustar dinamicamente a capacidade com base em métricas específicas de desempenho, garantindo que a infraestrutura responda precisamente às necessidades da aplicação. |

A política de dimensionamento para monitoramento de targets oferece uma abordagem eficiente e direcionada para dimensionar recursos de forma automática, ideal para ambientes onde o desempenho e a eficiência operacional são críticos.

***

## **Recursos**

[Amazon EC2 Auto Scaling(opens in a new tab)](https://aws.amazon.com/ec2/autoscaling/)

[Perguntas frequentes sobre o Amazon EC2 Auto Scaling(opens in a new tab)](https://aws.amazon.com/ec2/autoscaling/faqs/)

[Definição de limites de capacidade para o seu grupo do Auto Scaling(opens in a new tab)](https://docs.aws.amazon.com/autoscaling/ec2/userguide/asg-capacity-limits.html)

[Políticas de escalabilidade simples e de etapas para o Amazon EC2 Auto Scaling(opens in a new tab)](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html)

[Políticas de dimensionamento com monitoramento do target para o Amazon EC2 Auto Scaling(opens in a new tab)](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html)

[Criação de um grupo do Auto Scaling usando um modelo de inicialização](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg-launch-template.html)

***
