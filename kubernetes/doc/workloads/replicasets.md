---
description: >-
  Um ReplicaSet no Kubernetes (k8s) é um controlador que garante que um número
  especificado de réplicas de um pod esteja em execução a qualquer momento no
  cluster.
---

# ReplicaSets

`ReplicaSets` no kubernetes funcionam como `Replicas` do Docker Swarm



{% embed url="https://kubernetes.io/pt-br/docs/concepts/workloads/controllers/replicaset/" %}

***

## <mark style="color:red;">Overview</mark>

O **ReplicaSet** é um componente do Kubernetes responsável por garantir a alta disponibilidade e escalabilidade de uma aplicação, monitorando continuamente o estado dos pods e mantendo o número desejado de réplicas.

Se um pod falhar ou for removido por qualquer motivo, o ReplicaSet iniciará automaticamente uma nova réplica para substituí-lo, garantindo que o número desejado de réplicas seja mantido em execução.

> _Por isso, é geralmente utilizado para garantir a disponibilidade de um certo número de Pods idênticos._

{% hint style="info" %}
Uma das desvantagens da utilização de ReplicasSet, é que ele não faz a alteração dos recursos automaticamente, então toda vez que uma alteração é feita, um novo deploy deve ser aplicado.
{% endhint %}

> Em resumo, o ReplicaSet assegura que a quantidade de réplicas do pod seja mantida conforme o desejado, mas não lida com atualizações automáticas de recursos.

***

## <mark style="color:red;">Criando ReplicaSets</mark>

{% hint style="info" %}
**Todos os recursos utilizados nesses exemplos, estarão disponibilizados no Github:**\


[https://github.com/danncastro/k8s-hands-on-testing/tree/main/k8s-cka-exemples/replicasets](https://github.com/danncastro/k8s-hands-on-testing/tree/main/k8s-cka-exemples/replicasets)
{% endhint %}

{% tabs %}
{% tab title="ReplicaSet" %}
1. Vamos validar os recursos disponíveis antes de deployar o projeto

```bash
kubectl get po -owide
```

No resources found in default namespace.

```bash
kubectl get rs -owide
```

No resources found in default namespace.

***

```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/replicasets/replicaset-webserver.yml
```

replicaset.apps/pods-replicaset created

***

2. Vamos novamente validar, após o deploy

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get rs -owide
```

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Deleted" %}
1. Vamos deletar uma das pods para testar a escalabilidade dos recursos

```bash
kubectl delete po pods-replicaset-4wd4g
```

pod "pods-replicaset-4wd4g" deleted

***

2. Após a deleção, outro recurso será aplicado automaticamente para manter as quantidades de replicas indicadas no manifesto.

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">ReplicaSet Scale - Manifest File</mark>

{% tabs %}
{% tab title="Scale Up" %}
1. Vamos aumentar o valor de replicas dentro do manifesto

```bash
vi k8s-hands-on-testing/k8s-cka-exemples/replicasets/replicaset-webserver.yml
```

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/replicasets/replicaset-webserver.yml
```

replicaset.apps/pods-replicaset configured

***

2. Podemos visualizar que a quantidade de pods aumentaram.

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get rs -owide
```

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Scale Down" %}
1. Vamos novamente ajustar o manifesto, e diminuir a quantidade de replicas.

```bash
vi k8s-hands-on-testing/k8s-cka-exemples/replicasets/replicaset-webserver.yml
```

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/replicasets/replicaset-webserver.yml
```

replicaset.apps/pods-replicaset configured

***

2. Visualizando novamente os recursos, podemos notar que agora a quantidade em execução é de 2 pods.

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get rs -owide
```

<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Deleted" %}
```bash
kubectl delete rs pods-replicaset
```

replicaset.apps "pods-replicaset" deleted

***

```bash
kubectl get po -owide
```

No resources found in default namespace.

```bash
kubectl get rs -owide
```

No resources found in default namespace.
{% endtab %}
{% endtabs %}

***

### &#x20;<mark style="color:red;">ReplicaSet Scale - Imperative Form</mark>

{% tabs %}
{% tab title="ReplicaSet" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/replicasets/replicaset-webserver.yml
```

replicaset.apps/pods-replicaset created

***

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get rs -owide
```

<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title=" Scale Down" %}
```bash
kubectl scale rs pods-replicaset --replicas=1
```

replicaset.apps/pods-replicaset scaled

***

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get rs -owide
```

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Scale Up" %}
```bash
kubectl scale rs pods-replicaset --replicas=3
```

replicaset.apps/pods-replicaset scaled

***

```bash
kubectl get po -owide
```

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get rs -owide
```

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Deleted" %}
```bash
kubectl delete rs pods-replicaset
```

replicaset.apps "pods-replicaset" deleted

***

```bash
kubectl get po -owide
```

No resources found in default namespace.

```bash
kubectl get rs -owide
```

No resources found in default namespace.
{% endtab %}
{% endtabs %}

***
