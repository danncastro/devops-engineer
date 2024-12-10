---
description: >-
  Cria critérios para definir se a aplicação está saudável através de Probes,
  tornando visível ao Kubernetes que uma aplicação não está se comportando da
  maneira esperada.
---

# Probes

{% embed url="https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/" %}

***

## <mark style="color:red;">livenessProbe</mark>&#x20;

A **Liveness Probe** no Kubernetes verifica a saúde de um contêiner em execução dentro de um pod em intervalos definidos pelo usuário. Essa verificação pode ser feita via HTTP, TCP ou execução de comandos no contêiner. No caso de verificação via HTTP, o Kubernetes faz solicitações regulares para um endpoint específico do contêiner. Se o código de retorno estiver fora do intervalo esperado (geralmente 200-399), o pod é considerado não saudável e pode ser reiniciado.

A Liveness Probe ajuda a identificar problemas em que o contêiner ainda está "rodando", mas o aplicativo dentro dele pode estar travado. Se a verificação falhar repetidamente, o Kubernetes reinicia o contêiner para tentar corrigir o problema, garantindo que o serviço continue funcionando.

***

### <mark style="color:red;">Criando LivenessProbe</mark>

{% hint style="info" %}
**Todos os recursos utilizados nesses exemplos, estarão disponibilizados no Github:** &#x20;

[https://github.com/danncastro/nki-kubernetes-projects/tree/main/k8s-cka-exemples/pods](https://github.com/danncastro/nki-kubernetes-projects/tree/main/k8s-cka-exemples/pods)
{% endhint %}

{% tabs %}
{% tab title="livenessProbe" %}
```bash
kubectl apply -f nki-kubernetes-projects/k8s-cka-exemples/pods/pods_liveness_probe.yml && \
sleep 5 && \
kubectl get po && \
sleep 30 && \
kubectl describe po liveness-pod && \
sleep 35 && \
kubectl describe po liveness-pod && \
sleep 30 &&\
kubectl describe po liveness-pod && \
kubectl get po liveness-pod
```

* Após a execução desse comando podemos validar na aba events do describe, tudo que aconteceu durante a inicialização do container.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Events" %}
1. Vamos acompanhar a execução do container durante um tempo

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

***

2. A aplicação não ficará ativa, até que o livenessProbe retorne Success

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

***
{% endtab %}

{% tab title="Output" %}
1. Vemos que retornou sucesso, então a Pod foi criada, e está em execução

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

***

2. Após uma revalidação do livenessProbe, ele identificou a falta do arquivo de validação de Probe e reinicializou novamente a Pod, e esse processo se repete toda vez que a validação do Probe é refeita.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

***
{% endtab %}

{% tab title="Deleted" %}
```bash
kubectl delete -f nki-kubernetes-projects/k8s-cka-exemples/pods/pods_liveness_probe.yml
```

pod "liveness-pod" deleted
{% endtab %}
{% endtabs %}

***

## <mark style="color:red;">readinessProbe</mark>&#x20;

A **Readiness Probe** no Kubernetes verifica se um contêiner está pronto para receber tráfego de rede. Ao contrário da **Liveness Probe**, que verifica a saúde da aplicação e decide se ela deve ser reiniciada, a **Readiness Probe** foca em garantir que a aplicação tenha atingido um estado estável e esteja pronta para aceitar solicitações.

Ela pode ser configurada para realizar verificações via **HTTP** ou **TCP**. No caso de verificação HTTP, a probe envia solicitações para um endpoint específico da aplicação e verifica a resposta. Já no caso do TCP, a verificação é feita conectando-se a uma porta específica do contêiner.

Configurando adequadamente parâmetros como o tempo entre verificações e o tempo de espera para uma resposta bem-sucedida, a **Readiness Probe** ajuda a garantir que o contêiner só receba tráfego quando estiver de fato pronto para processá-lo, evitando falhas no serviço.

***

## <mark style="color:red;">startupProbe</mark>&#x20;

A **Startup Probe** no Kubernetes é projetada para verificar o estado inicial de um contêiner durante sua inicialização ou reinicialização. Ela difere das probes regulares, como **Liveness** e **Readiness Probes**, que monitoram a saúde do contêiner após eles já estarem inicializados.

Quando um contêiner é iniciado, a **Startup Probe** verifica se o aplicativo está pronto para receber tráfego. Se a verificação falhar, o Kubernetes pode reiniciar o contêiner ou até falhar a inicialização do pod inteiro, dependendo da configuração.

Essa probe é especialmente útil para aplicativos com inicialização demorada ou complexa, garantindo que o Kubernetes não direcione tráfego para contêineres que ainda não estão prontos para processá-lo.

> muito util para aplicações legadasque necessitam tempo adicional para inicializar na primeira vez

***
