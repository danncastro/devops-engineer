---
description: >-
  Composta pelos componentes executados em cada nó do cluster, que são
  responsáveis por manter os Pods em execução e fornecer o ambiente de execução
  necessário para as aplicações.
---

# Camada de trabalho

**Função dos Componentes:**

* **Executar Pods:** Os componentes da camada de trabalho garantem que os Pods estejam sempre funcionando, monitorando e corrigindo falhas, se necessário.
* **Ambiente de Execução:** Proporcionam o ambiente necessário para os containers dentro dos Pods, incluindo a execução de containers e o gerenciamento de redes e armazenamento.

***

## <mark style="color:red;">kubelet</mark>&#x20;

{% embed url="https://kubernetes.io/pt-br/docs/concepts/overview/components/#node-components" %}

O **kubelet** é o agente de execução presente em cada nó do cluster. responsável por garantir que os **Pods** e **Containers** sejam executados corretamente nos nós, gerenciando e fornecendo informações sobre a saúde dos nós de volta ao `kube-apiserver`.

> _Componente que executa em todas as máquinas do cluster e gerencia tarefas como a inicialização de pods e contêineres._  Em cada worker-node deverá existir um agente Kubelet em execução.&#x20;

{% hint style="info" %}
O kubelet só entra em cena quando o kube-scheduler já decidiu onde agendar um pod e precisa garantir que o pod esteja em execução no nó correspondente.
{% endhint %}

{% hint style="warning" %}
O kubelet é executado em todos os **worker nodes** e não gerencia containers fora do Kubernetes, ou seja, ele só supervisiona containers que foram criados e estão sob o controle do Kubernetes.
{% endhint %}

* O **kubelet** pode ser visto como o **agente do k8s** que é executado nos `workers-nodes`.

***

* O kubelet assegura que os Pods, alocados pelo **kube-scheduler**, estejam em execução nos nós correspondentes. Ele pode iniciar, parar e manter os containers funcionando conforme as instruções do controlador do cluster.

***

## <mark style="color:red;">kube-proxy</mark>&#x20;

O **kube-proxy** é um componente do Kubernetes que atua como um **proxy de rede** em cada nó do cluster, facilitando a comunicação entre os Pods e entre os Pods e o mundo externo.

**Função do kube-proxy:**

* **Roteamento de Requisições:** O kube-proxy é responsável por **rotear as requisições de rede** para os Pods corretos, garantindo que as comunicações dentro e fora do cluster sejam dirigidas corretamente.
* **Balanceamento de Carga:** O [kube-proxy](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy/) também gerencia o **balanceamento de carga** para os serviços, distribuindo o tráfego de forma equilibrada entre os Pods disponíveis.
* **Regras de Rede:** O kube-proxy mantém **regras de rede** nos nós, cuidando da configuração e gerenciamento de conexões para os serviços e Pods.

> Essencialmente, o **kube-proxy** facilita a conectividade e o balanceamento de tráfego dentro do cluster, viabilizando o conceito de **Serviços** no Kubernetes.

***

## <mark style="color:red;">Container Runtime</mark>&#x20;

O **Container Runtime** é o ambiente de execução de contêineres responsável por executar e gerenciar os containers dentro de um cluster Kubernetes.&#x20;

{% hint style="info" %}
**Observação:** O Kubernetes em si **não executa containers**; essa função é desempenhada pelo **Container Runtime**.
{% endhint %}

<figure><img src="../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

> _O Kubernetes suporta diversos agentes de execução de contêineres:_ [_Docker_](https://docs.docker.com/engine/)_,_ [_containerd_](https://containerd.io/docs/)_,_ [_CRI-O_](https://cri-o.io/#what-is-cri-o)_, e qualquer implementação do_ [_Kubernetes CRI (Container Runtime Interface)_](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-node/container-runtime-interface.md)_._

* Desde a **versão v1.24** o k8s requer que você utilize um container runtime compatível com o `CRI (Container Runtime Interface)` que foi apresentado em 2016 como uma interface capaz de criar um padrão de comunicação entre o container runtime e k8s.

***

* Versões anteriores à v1.24 ofereciam integração direta com o `Docker Engine` usando um componente chamado `dockershim` porém essa integração direta não está mais disponível.

***

* A documentação oficial do Kubernetes **(v1.24)** apresenta alguns ambientes de execução e suas respectivas configurações como o `containerd` um projeto avaliado com o nível graduado pela `CNCF(Cloud Native Computing Foundation)` e o **CRI-0** projeto incubado pela **CNCF**.

***

## <mark style="color:red;">kubectl</mark>&#x20;

{% embed url="https://kubectl.docs.kubernetes.io/" %}

Ferramenta de linha de comando do Kubernetes, permite executar comandos em clusters do Kubernetes, podendo ser usado para **implantar aplicativos, inspecionar e gerenciar recursos de cluster e visualização de logs**.

* É uma sigla para `Kubernetes Control`, muitas das vezes podemos ouvir seu nome pronunciado como `"Kube C T L"`, `"Kube Control"` e `"Kube Cuttle/Cuddle"`, esse ultimo surgiu como um apelido, devido ao seu "Mascote" ser o Cuttle fish (Em português Choco, sibas ou sépia) que é uma espécie de molusco parecido com o polvo

Os comandos do `kubectl` seguem a seguinte semântica:

```bash
kubectl + VERBO + recurso + OPÇÕES
```

Alguns exemplos de verbos:

> &#x20;_get, list, describe, create, update, patch, delete ..._

* O comando `kubectl patch` no Kubernetes é usado para modificar ou atualizar recursos existentes no cluster de forma parcial. Em vez de substituir o recurso inteiro, como acontece com o `kubectl apply` ou `kubectl create`, o `kubectl patch` permite que você altere apenas uma parte específica de um recurso, sem afetar as configurações não modificadas.

Alguns exemplos de recursos:

> _nodes, pods, namespaces, services, deployment, replicaset, pv(persistent volume), pvc(persistent volume claim) ..._

* No Kubernetes podemos utilizar o termo `all` como recurso para trabalhar com todos os recursos.

***

#### <mark style="color:blue;">Kubernetes: Principais Comandos</mark> <a href="#firstheading" id="firstheading"></a>

{% embed url="https://ebasso.net/wiki/index.php?title=Kubernetes:_Principais_Comandos" %}

***

## <mark style="color:red;">Kubeadm</mark>&#x20;

{% embed url="https://kubernetes.io/docs/tasks/tools/" %}

Uma ferramenta para instalar rapidamente o Kubernetes e configurar um cluster seguro.

Você pode usar o kubeadm para instalar a [camada de gerenciamento](https://kubernetes.io/pt-br/docs/reference/glossary/?all=true#term-control-plane) e os componentes dos [nós de processamento](https://kubernetes.io/pt-br/docs/concepts/architecture/nodes/).

***

## <mark style="color:red;">Complementos (</mark>_<mark style="color:red;">addons</mark>_<mark style="color:red;">)</mark> <a href="#addons" id="addons"></a>

{% embed url="https://kubernetes.io/pt-br/docs/concepts/overview/components/#addons" %}

***
