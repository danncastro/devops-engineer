---
description: >-
  No Docker, a menor unidade computacional possível é o Container, já no
  Kubernetes a menor unidade computacional possível é o Pod.
---

# Pods

{% embed url="https://kubernetes.io/docs/concepts/workloads/pods/" %}

{% hint style="info" %}
#### Todos os recursos utilizados nesses exemplos, estarão disponibilizados no Github:

[https://github.com/danncastro/k8s-hands-on-testing/tree/main/k8s-cka-exemples/pods](https://github.com/danncastro/k8s-hands-on-testing/tree/main/k8s-cka-exemples/pods)
{% endhint %}

***

## <mark style="color:red;">O que é um pod?</mark> <a href="#what-is-a-pod" id="what-is-a-pod"></a>

{% hint style="info" %}
**Observação:** você precisa instalar um [ambiente de execução de contêiner](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) em cada nó do cluster para que os pods possam ser executados nele.
{% endhint %}

<figure><img src="../.gitbook/assets/image (165).png" alt=""><figcaption></figcaption></figure>

Um **Pod Kubernetes** é um grupo de um ou mais [containers](https://kubernetes.io/docs/concepts/containers/), **(como Docker)** que inclui armazenamento compartilhado (`volumes`), endereços IP e informações sobre como executa-lo

> Os pods são compostos por um container nos casos de uso mais comuns ou por vários containers fortemente acoplados em cenários mais avançados.

<figure><img src="../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>

* Os containers são agrupados nesses pods para que os recursos possam ser compartilhados entre eles, então eles recebem endereços IP's únicos e compartilham o mesmo Namespaces.&#x20;
* Pods além do compartilhamento de rede, também compartilhar recursos de armazenamento entre os containers, **mas não podem compartilhar a mesma porta de acesso** dentro de um mesmo pod.

<figure><img src="../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Containers em um mesmo pod se comunicam através de localhost.
{% endhint %}

> Os Pods são `efêmeros` , ou seja, a menos que você mapei um volume persistente ali para as pods. Quando um Pod é **reiniciado ou removido**, ele é destruído e uma nova Pod é criado no lugar, com **configuração nova**, o que implica que:
>
> * O **IP do Pod** será alterado. Cada vez que um Pod é recriado, ele recebe um novo IP interno.
> * **Dados voláteis** dentro do Pod serão perdidos, a menos que você utilize volumes persistentes.
>
> \
> Para garantir um IP fixo ou estável para acesso, você pode usar um **Service**, que fornece um ponto de acesso estável, independentemente da reinicialização dos Pods."

***

### <mark style="color:red;">Criando Pods -  Imperative Form</mark>

{% tabs %}
{% tab title="Pods" %}
```bash
kubectl get po -owide
```

No resources found in default namespace.

***

```bash
kubectl run pod-apache --image httpd
```

pod/pod-apache created

***

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Deleted" %}
```bash
kubectl delete po pod-apache
```

pod "pod-apache" deleted

***

```bash
kubectl get po -owide
```

No resources found in default namespace.
{% endtab %}

{% tab title="Multi Pods" %}
```bash
kubectl run pod-apache2 --image httpd
```

pod/pod-apache2 created

***

```bash
kubectl run pod-apache3 --image httpd
```

pod/pod-apache3 created

***

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Delete All" %}
```bash
kubectl delete --all pods
```

pod "pod-apache2" deleted

pod "pod-apache3" deleted

***

```bash
kubectl get po -owide
```

No resources found in default namespace.
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Criando Pods - Manifest Files</mark>

{% tabs %}
{% tab title="Pod" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/pods/pod_webserver.yml
```

pod/pod-webserver created

***

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Deleted" %}
```bash
kubectl delete -f k8s-hands-on-testing/k8s-cka-exemples/pods/pod_webserver.yml
```

pod "pod-webserver" deleted

***

```bash
kubectl get po -owide
```

No resources found in default namespace.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">Recursos de carga de trabalho para gerenciar pods</mark> <a href="#workload-resources-for-managing-pods" id="workload-resources-for-managing-pods"></a>

Os pods em um cluster Kubernetes são usados ​​de duas maneiras principais:

* **Pods que executam um único contêiner:** O modelo “um contêiner por pod” é o caso de uso mais comum do Kubernetes;
* **Pods que executam vários contêineres que precisam trabalhar juntos:** Um pod pode encapsular um aplicativo composto de vários contêineres colocados no mesmo local que estão fortemente acoplados e precisam compartilhar recursos.

{% hint style="info" %}
**Observação:** agrupar vários contêineres colocalizados e cogerenciados em um único pod é um caso de uso relativamente avançado. Você deve usar esse padrão apenas em instâncias específicas em que seus contêineres estão fortemente acoplados.
{% endhint %}

Se quiser dimensionar seu aplicativo horizontalmente (para fornecer mais recursos gerais executando mais instâncias), você deverá usar vários pods, um para cada instância.

> No Kubernetes, isso normalmente é chamado de _replicação_

Os pods replicados geralmente são criados e gerenciados como um grupo por um recurso de carga de trabalho e seu [controller](https://kubernetes.io/docs/concepts/architecture/controller/).

Consulte [Pods e controladores](https://kubernetes.io/docs/concepts/workloads/pods/#pods-and-controllers) para obter mais informações sobre como o Kubernetes usa recursos de carga de trabalho e seus controladores para implementar o escalonamento e a recuperação automática de aplicativos

***

## <mark style="color:red;">Pod Multi Contêineres</mark> <a href="#how-pods-manage-multiple-containers" id="how-pods-manage-multiple-containers"></a>

Os contêineres em um pod são automaticamente co-localizados e co-agendados na mesma máquina física ou virtual do cluster. Os contêineres podem compartilhar recursos e dependências, comunicar-se entre si e coordenar quando e como serão encerrados.

{% embed url="https://kubernetes.io/docs/concepts/workloads/pods/#how-pods-manage-multiple-containers" %}

> Habilitar o [feature gate](https://kubernetes.io/docs/reference/command-line-tools-reference/feature-gates/) `SidecarContainers`  permite que você especifique contêineres de inicialização `restartPolicy: Always.` Definir a política de reinicialização `Always`  garante que os contêineres de inicialização onde você a definiu continuem em execução durante toda a vida útil do pod.

{% hint style="info" %}
Consulte [Contêineres Sidecar e restartPolicy](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/#sidecar-containers-and-restartpolicy) para obter mais detalhes.
{% endhint %}

O principal motivo pelo qual os pods podem ter vários contêineres é para oferecer suporte a aplicativos auxiliares que auxiliam um aplicativo primário. Exemplos típicos de aplicativos auxiliares são data pullers, data pushers, and proxies. Aplicativos auxiliares e primários geralmente precisam se comunicar uns com os outros.&#x20;

> Normalmente, isso é feito por meio de um sistema de arquivos compartilhado. ou por meio da interface de rede de loopback, localhost. Um exemplo desse padrão é um servidor web junto com um programa auxiliar que consulta um repositório Git para novas atualizações.

{% hint style="info" %}
Os pods são projetados como entidades descartáveis ​​e relativamente efêmeras.&#x20;
{% endhint %}

Quando um pod é criado (diretamente por você ou indiretamente por um [controlador](https://kubernetes.io/docs/concepts/architecture/controller/)), o novo pod está programado para ser executado em um [Nó](https://kubernetes.io/docs/concepts/architecture/nodes/) em seu cluster. O pod permanece nesse nó até que termine a execução, o objeto Pod seja excluído, o pod seja _removido_ por falta de recursos ou o nó falhe.

{% hint style="info" %}
**Observação:** reiniciar um contêiner em um pod não deve ser confundido com reiniciar um pod. Um pod não é um processo, mas um ambiente para execução de contêineres. Um pod persiste até ser excluído.
{% endhint %}

Podemos ter pods que possuem mais que um único container, fazemos isto quando, por exemplo, precisamos que mais de um container tenha acesso a um mesmo volume.

> No arquivo de configuração, conseguimos ver a existência de um Volume com o nome de `shared-data` que será montado no segundo container no caminho `/pod-data`.

Através desse volume, o container `debian-container` irá popular o arquivo `/pod-data/index.html` que foi montado em ambos os containers, tornando o arquivo acessível pelo primeiro container no caminho `/usr/share/nginx/html`.

{% tabs %}
{% tab title="Pods" %}
```bash
kubectl apply -f nki-kubernetes-projects/k8s-cka-exemples/pods/pods_multi_container.yml
```

pod/pod-multi-container created

***

Veja que agora temos dois containers criados em um pod de nome `multi-containers`.&#x20;

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Stats" %}
Como nosso `debian-container` tinha apenas o propósito de popular o arquivo `index.html` ele está em estado de `terminated`.&#x20;

***

```bash
kubectl get po pod-multi-container -oyaml
```

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

> A opção `--output=yaml` é uma ótima maneira de gerar um arquivo YAML de algum recurso já existente no kubernetes
{% endtab %}

{% tab title="Nginx" %}
Vamos conectar ao container nginx através de um shell e verificar se o nginx está sendo executado

```bash
kubectl exec -it pod-multi-container -c nginx-container -- /bin/bash
```

***

1. Um dos motivos para executarmos estes pods multi containers é oferecer suporte do aplicativo auxiliar ao aplicativo principal.&#x20;

***

2. Este container auxiliar muitas das vezes é chamado de _`sidecar`_, normalmente é um extrator ou fornecedor de dados, ou até mesmo um proxy.

```bash
curl localhost
```

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

***

> Um _sidecar_ é um dispositivo de uma única roda preso na lateral de uma motocicleta, scooter ou bicicleta, fazendo com que se transforme em um veículo de três rodas suportando mais um passageiro.
{% endtab %}

{% tab title="Deleted" %}
Podemos agora remover nossos containers

```bash
kubectl delete -f k8s-cka-exemples/pods/pods_multi_container.yml
```

pod "pod-multi-container" deleted
{% endtab %}
{% endtabs %}

***

## <mark style="color:red;">Pod OS</mark> <a href="#pod-os" id="pod-os"></a>

Podemos definir o campo `.spec.os.name` como   `Windows` ou `Linux`  para indicar o sistema operacional no qual deseja que o pod seja executado. Esses dois são os únicos sistemas operacionais suportados atualmente pelo Kubernetes. Futuramente, esta lista poderá ser ampliada.

A configuração `.spec.os.name` ajuda a identificar o sistema operacional do pod com autoridade e é usada para validação.

> O kubelet se recusa a executar um pod onde você especificou um sistema operacional de pod, se este não for o mesmo sistema operacional do nó onde o kubelet está sendo executado

***

## <mark style="color:red;">Pods and Controllers</mark> <a href="#pods-and-controllers" id="pods-and-controllers"></a>

Você pode usar recursos de carga de trabalho para criar e gerenciar vários pods para você. Um controlador para o recurso cuida da replicação, implementação e recuperação automática em caso de falha do pod.

Por exemplo, se um nó falhar, um controlador perceberá que os pods naquele nó pararam de funcionar e criará um pod substituto. O agendador coloca o pod substituto em um nó íntegro.

> _No caso das Pods, seu controlador é o ReplicaSet_

Aqui estão alguns exemplos de recursos de carga de trabalho que gerenciam um ou mais pods:

* [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
* [StatefulSet](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)
* [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset)
* [ReplicasSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)

***

## <mark style="color:red;">Pod Templates</mark> <a href="#pod-templates" id="pod-templates"></a>

Controllers para  [workload](https://kubernetes.io/docs/concepts/workloads/). Os recursos criam pods a partir de um _modelo de pod_ e gerenciam esses pods em seu nome.

PodTemplates são especificações para criação de pods e estão incluídos em recursos de carga de trabalho como [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) , [Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/) e [DaemonSets](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/) .

Cada controlador de um recurso de carga de trabalho usa o `PodTemplate` interior do objeto de carga de trabalho para criar pods reais.

O exemplo abaixo é um manifesto para um Job simples com um `template` que inicia um contêiner. O contêiner nesse pod imprime uma mensagem e depois faz uma pausa.

{% tabs %}
{% tab title="Pod Templates" %}
```bash
kubectl apply -f kubernetes_projects/k8s_cka_exemples/pods/job_template_pod.yml
```
{% endtab %}
{% endtabs %}

Modificar o modelo de pod ou mudar para um novo modelo de pod não afeta diretamente os pods que já existem

Por exemplo, o controlador `StatefulSet` garante que os pods em execução correspondam ao modelo de pod atual para cada objeto `StatefulSet`. Se você editar o `StatefulSet` para alterar seu modelo de pod, o StatefulSet começará a criar novos pods com base no modelo atualizado.

> Eventualmente, todos os pods antigos serão substituídos por novos pods e a atualização será concluída.

***

### <mark style="color:red;">Atualização e substituição de pod</mark> <a href="#pod-update-and-replacement" id="pod-update-and-replacement"></a>

O Kubernetes não impede que você gerencie pods diretamente. É possível atualizar alguns campos de um Pod em execução, no local. No entanto, operações de atualização de pods como [`patch`](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.28/#patch-pod-v1-core)  e [`replace`](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.28/#replace-pod-v1-core) têm algumas limitações:

* A maioria dos metadados sobre um pod é imutável. Por exemplo, você não pode alterar os campos `namespace`, `name`, `uid` ou `creationTimestamp`; o campo `generation` é único. Aceita apenas atualizações que incrementem o valor atual do campo.

***

* Se `metadata.deletionTimestamp` estiver definido, nenhuma nova entrada poderá ser adicionada à lista `metadata.finalizers`.

***

* As atualizações do pod não podem alterar campos diferentes de `spec.containers[*].image, spec.initContainers[*].image, spec.activeDeadlineSeconds` ou `spec.tolerations` para `spec.tolerations`, você só pode adicionar novas entradas.

***

* Ao atualizar o campo `spec.activeDeadlineSeconds`, são permitidos dois tipos de atualizações:

1. definir o campo não atribuído para um número positivo;
2. atualizando o campo de um número positivo para um número menor e não negativo

***

## <mark style="color:red;">Armazenamento em pods</mark>

Um pod pode especificar um conjunto de armazenamento compartilhado [volumes](https://kubernetes.io/docs/concepts/storage/volumes/). Todos os contêineres no pod podem acessar os volumes compartilhados, permitindo que esses contêineres compartilhem dados

Os volumes também permitem que dados persistentes em um pod sobrevivam caso um dos contêineres precise ser reiniciado.

***

## <mark style="color:red;">Rede de pods</mark> <a href="#pod-networking" id="pod-networking"></a>

Cada pod recebe um endereço IP exclusivo para cada família de endereços. Cada contêiner em um pod compartilha o namespace da rede, incluindo o endereço IP e as portas de rede. Dentro de um pod (e **somente** então), os contêineres que pertencem ao pod podem se comunicar entre si usando `localhost`.&#x20;

Os contêineres em um pod também podem se comunicar entre si usando comunicações padrão entre processos, como SystemV semaphores ou memória compartilhada POSIX.

Contêineres em pods diferentes têm endereços IP distintos e não podem se comunicar por IPC no nível do sistema operacional sem configuração especial. Os contêineres que desejam interagir com um contêiner em execução em um pod diferente podem usar a rede IP para se comunicar.

> Os contêineres dentro do pod consideram o nome do host do sistema igual ao configurado `name`  para o pod.

***

## <mark style="color:red;">Pods estáticas</mark>

{% embed url="https://kubernetes.io/pt-br/docs/tasks/configure-pod-container/static-pod/" %}

_Os pods estáticos_ são gerenciados diretamente pelo daemon kubelet em um nó específico, sem o [Servidor API](https://kubernetes.io/docs/concepts/overview/components/#kube-apiserver) observando-os. Considerando que a maioria dos Pods são gerenciados pelo plano de controle (por exemplo, um [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)), para pods estáticos, o kubelet supervisiona diretamente cada pod estático (e o reinicia se falhar).

O principal uso dos pods estáticos é executar um plano de controle auto hospedado: em outras palavras, usar o kubelet para supervisionar os [componentes individuais do plano de controle](https://kubernetes.io/docs/concepts/overview/components/#control-plane-components) .

***

## <mark style="color:red;">Container probes</mark> <a href="#container-probes" id="container-probes"></a>

Um probe é um diagnóstico realizado periodicamente pelo kubelet em um contêiner. Para realizar um diagnóstico, o kubelet pode invocar diferentes ações:

* `ExecAction`(realizado com a ajuda do tempo de execução do contêiner)
* `TCPSocketAction`(verificado diretamente pelo kubelet)
* `HTTPGetAction`(verificado diretamente pelo kubelet)

Você pode ler mais sobre [testes](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/#container-probes) na documentação do Pod Lifecycle

***

## <mark style="color:red;">Init Containers</mark>

{% embed url="https://kubernetes.io/docs/concepts/workloads/pods/init-containers/" %}

Contêineres especializados que são executados antes dos contêineres de aplicativos em um [Pod](https://kubernetes.io/docs/concepts/workloads/pods/).&#x20;

Os contêineres de inicialização podem conter utilitários ou scripts de configuração não presentes em uma imagem de aplicativo.

> Você pode especificar contêineres init na especificação do pod junto com a matriz `containers`  (que descreve contêineres de aplicativos).

Uma [Pod](https://kubernetes.io/docs/concepts/workloads/pods/) pode ter vários contêineres executando aplicativos dentro dele, mas também pode ter um ou mais contêineres init, que são executados antes dos contêineres de aplicativos serem iniciados.

Os contêineres init são exatamente como os contêineres normais, exceto:

* Os contêineres de inicialização sempre são executados até a conclusão.
* Cada contêiner init deve ser concluído com êxito antes que o próximo seja iniciado.

> Se o contêiner init de um pod falhar, o kubelet reinicia repetidamente esse contêiner init até obter êxito. No entanto, se o pod tiver `restartPolicy: never` e um contêiner de inicialização falhar durante a inicialização desse pod, o Kubernetes tratará o pod geral como com falha.

Para especificar um contêiner init para um pod, adicione o campo  `initContainers`  à [especificação do pod](https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/pod-v1/#PodSpec) , como uma matriz de itens `container` (semelhante ao campo `containers` app e seu conteúdo). Consulte [Container](https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/pod-v1/#Container) na referência da API para obter mais detalhes.

Os contêineres init não são compatíveis com `lifecycle`, `livenessProbe`, `readinessProbe` ou `startupProbe`  porque eles devem ser executados até a conclusão antes que o pod possa estar pronto.

> Cada contêiner init deve ser bem-sucedido antes que o próximo possa ser executado.

#### <mark style="color:blue;">Comportamento detalhado</mark> <a href="#detailed-behavior" id="detailed-behavior"></a>

Durante a inicialização do pod, o kubelet atrasa a execução dos contêineres init até que a rede e o armazenamento estejam prontos. Em seguida, o kubelet executa os contêineres init do pod na ordem em que aparecem nas especificações do pod

> Cada contêiner init deve sair com êxito antes do início do próximo contêiner.

Se um contêiner falhar ao iniciar devido ao tempo de execução ou sair com falha, ele será tentado novamente de acordo com o Pod `restartPolicy`.&#x20;

* No entanto, se o pod `restartPolicy` estiver definido como Always, os contêineres de inicialização usarão `restartPolicy OnFailure.`

Um pod não pode existir `Ready`  até que todos os contêineres de inicialização sejam bem-sucedidos.

#### <mark style="color:blue;">Pod Initialization</mark>

Este exemplo demonstra como usar um contêiner de inicialização para inicializar um pod antes da execução de um contêiner de aplicativo.

{% tabs %}
{% tab title="Pods" %}
```bash
kubectl apply -f nki-kubernetes-projects/k8s-cka-exemples/pods/pods_init.yml
```

pod/pods-init created

***

Podemos visualizar que a pod subirá em ordem do init

```bash
kubectl get po --watch
```

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Mensagem" %}
Vamos acessar a Pod e visualizar a mensagem que nos é apresentado no output do terminal.

***

```bash
kubectl exec -it init-pod -- /bin/sh
```

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

***

Podemos sair do TTY do container e visualizar que nosso container ainda estará executando até o tempo definido no arquivo  YAML.

***

```bash
kubectl get po
```

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Deleted" %}
```bash
kubectl delete -f nki-kubernetes-projects/k8s-cka-exemples/pods/pods_init.yml
```

pod "pods-init" deleted

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get po
```

No resources found in default namespace.
{% endtab %}
{% endtabs %}

***

## <mark style="color:red;">Horizontal Pod Autoscaler</mark>&#x20;

O `HPA` visa manter o consumo médio de CPU o mais próximo do valor definido e escalona uma nova pod conforme a necessidade.&#x20;

São responsáveis por definir em quais circunstâncias escalaremos nossa aplicação automaticamente.

***

## <mark style="color:red;">Vertical Pod Autoscaler</mark>&#x20;

O `VerticalPodAutoscaler` remove a necessidade de definir limites e pedidos por recursos do sistema, como cpu e memória.&#x20;

* Quando definido, ele define os consumos de maneira automática baseada na utilização em cada um dos nós, além disso, quanto tem disponível ainda de recurso.

```bash
kubectl scale deployment nome-deploy --replicas x
```

***
