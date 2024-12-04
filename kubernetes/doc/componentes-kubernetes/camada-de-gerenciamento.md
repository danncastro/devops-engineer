---
description: >-
  Os componentes da camada de gerenciamento tomam decisões globais sobre o
  cluster, bem como detectam e respondem aos eventos do cluster.
---

# Camada de Gerenciamento

{% embed url="https://kubernetes.io/pt-br/docs/concepts/overview/components/#componentes-da-camada-de-gerenciamento" %}

**Funções da Camada de Gerenciamento:**

* Coordena as operações e estados do cluster.
* Monitora e reage a eventos, como falhas ou alterações de configuração.

{% hint style="info" %}
**Alta Disponibilidade:**\
Em ambientes de produção, o ambiente de gerenciamento é geralmente executado em múltiplos computadores, provendo tolerância a falhas e alta disponibilidade.
{% endhint %}

> Embora os componentes de gerenciamento possam ser executados em qualquer node do cluster, normalmente são configurados para rodar em uma única máquina, para simplificação na configuração inicial.

***

## <mark style="color:red;">kube-apiserver</mark>&#x20;

É o componente central que expõe a API do Kubernetes e serve como ponto de entrada para o cluster. Ele desempenha um papel fundamental no gerenciamento e na comunicação entre os diferentes componentes do Kubernetes.

* **Ponto de Entrada:** Toda ação no cluster passa pela **kube-apiserver**, que é responsável por aceitar e processar requisições, seja de usuários ou de outros componentes.
* **Banco de Dados (etcd):** Apenas o **kube-apiserver** tem permissão para escrever nas configurações do banco de dados **etcd**, que armazena o estado do cluster.
* **Validação e Configuração:** Valida e configura dados dos objetos no cluster, como **Pods**, **Serviços**, **Controladores de Replicação**, entre outros.
* **Frontend do Cluster:** Fornece a interface de comunicação entre o estado compartilhado do cluster e todos os outros componentes que interagem com ele.

O servidor de **API** do Kubernetes valida e configura dados para os objetos presentes no cluster, que incluem `pods`, `serviços`, `controladores de replicação` e outros.

O **API Server** atende às operações e fornece o **Frontend** para o estado compartilhado do cluster por meio do qual todos os outros componentes interagem.

<figure><img src="../.gitbook/assets/image (171).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">etcd</mark>&#x20;

{% embed url="https://etcd.io/" %}

`etcd` é um banco de dados do tipo "chave -> valor"  distribuído e fortemente consistente que fornece uma maneira confiável de armazenar dados que precisam ser acessados ​​por um sistema distribuído ou cluster de máquinas.&#x20;

**Armazenamento no Kubernetes:**\
O **etcd** é o principal armazenamento de dados do Kubernetes, armazenando o estado e a configuração do cluster. Ele é crucial para viabilizar atualizações automáticas e coordenar a programação de tarefas no cluster.

**Tolerância a Falhas:**\
Ele é resiliente a falhas de máquinas, inclusive no nó líder, e lida com **eleições de líder** durante partições de rede, garantindo a continuidade do funcionamento do cluster.

**Funções no Kubernetes:**

* Facilita a **configuração de redes de sobreposição** para containers.
* Permite a **coordenação de jobs** e garante a consistência do estado do cluster.

> _etcd é um componente importante de vários outros projetos, não apenas do Kubernetes, ou seja ele é um componente externo aplicado a infraestrutura Kubernetes._

***

## <mark style="color:red;">kube-schenduler</mark>&#x20;

O **kube-scheduler** é responsável pelo agendamento de **Pods** nos nós apropriados do cluster, levando em consideração as especificações e restrições definidas, como disponibilidade de recursos.

Ele recebe as requisições vindas do **kube-apiserver**, e gerência da melhor forma onde será instânciado a nova aplicação com base em critérios como recursos e políticas definidas..&#x20;

<figure><img src="../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

> Ele consulta o API Server para obter informações sobre os recursos do cluster e decide onde colocar os pods com base em políticas de agendamento.

É um processo que atribui pods as nós (`nodes`). Ele determina quais são os posicionamentos válidos para cada pod na fila de agendamento de acordo com as restrições e os recursos disponíveis.&#x20;

> _O **kube-schenduler** classifica cada node válido e vincula o pod a um Node adequado._

***

## <mark style="color:red;">kube-controller-manager</mark>&#x20;

O **kube-controller-manager** é responsável por gerenciar os controladores que mantêm o estado desejado do sistema.&#x20;

No Kubernetes, um controlador é um loop que observa o estado compartilhado do cluster por meio do `kube-apiserver` e faz ajustes para garantir que o sistema esteja sempre no estado configurado.

\
O **kube-controller-manager** coordena diversos controladores, como:

* **Controlador de Replicação:** Garante que o número de réplicas de um pod esteja sempre conforme o especificado.
* **Controlador de Serviço:** No Kubernetes, o **Controlador de Serviço** é responsável por garantir que os serviços estejam corretamente configurados e acessíveis dentro do cluster. Ele gerencia a criação e manutenção de objetos de **Service**, que são usados para expor aplicações em execução nos **Pods** para outros componentes internos ou externos ao cluster. O controlador verifica a saúde e disponibilidade dos Pods associados, fazendo a distribuição do tráfego de rede para os Pods disponíveis, garantindo que o serviço esteja sempre acessível, mesmo que haja falhas ou escalabilidade dinâmica dos Pods.

<figure><img src="../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">Cloud-controller-manager</mark>

***
