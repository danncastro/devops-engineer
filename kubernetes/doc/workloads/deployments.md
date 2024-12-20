---
description: >-
  Deployment é uma abstração que gerencia um conjunto de réplicas de um
  aplicativo, garantindo que o número desejado de réplicas esteja sempre em
  execução e gerenciando a atualização dessas réplicas.
---

# Deployments

{% embed url="https://kubernetes.io/docs/concepts/workloads/controllers/deployment/" %}

***

## <mark style="color:red;">About Deployment</mark>

Um dos aspectos mais interessantes de um Deployment é que ele trabalha diretamente com o **ReplicaSet.** Ou seja, mesmo que os pods sejam deletados, o **ReplicaSet** se encarregará de garantir o que a quantidade especificada dentro do deployment seja mantida.

Essa é uma das grandes "magias" do kubernetes, e é uma das maiores "pegadinhas" para aqueles que não conhecem o funcionamento e tentam apagar os pods, e eles continuam reaparecendo.

{% hint style="info" %}
Para remover nossos pods precisamos remover o deployment.
{% endhint %}

#### <mark style="color:blue;">Responsável pela implantação da aplicação</mark>

Por default o Kubernetes utiliza a estratégia Rolling Updates (Rolling Release), que executa uma atualização baseada em um percentual de indisponibilidade de pods, que por padrão é ter no máximo 25% de indisponibilidade do total de pods em execução. Oque isso significa?

Quando você atualiza um **Deployment** no Kubernetes, (por exemplo, atualizando a imagem de um container), a atualização não acontece de uma vez só. Em vez disso, o Kubernetes realiza a atualização **gradualmente**:

1. **Substituição Sequencial:** O Kubernetes começa criando novos Pods com a nova configuração (por exemplo, com a nova imagem do container) enquanto mantém os Pods antigos em execução.
2. **Verificação de Saúde:** Após iniciar os novos Pods, o Kubernetes verifica se eles estão funcionando corretamente, e aí que acontece o trabalho em conjunto com o controlador de replicas, o **ReplicaSet** fica ali monitorando a saúde dos Pods para garantir que a quantidade de replicas funcionando estejam provisionadas.
3. **Atualização Gradual:** Assim que o Kubernetes garante que os novos Pods estão funcionando, ele **removerá gradualmente os Pods antigos**, substituindo-os pelos novos até que todos os Pods sejam atualizados.

***

### <mark style="color:red;">RollingUpdateStrategy</mark>

**Max Unavailable (Máximo Indisponível)**: Isso define o número máximo de pods da aplicação que podem estar indisponíveis durante a atualização. Por exemplo, se você definir `max unavailable` como 1, isso significa que durante a atualização, apenas um pod do aplicativo pode ser removido de cada vez. Os outros continuam funcionando normalmente, garantindo que o aplicativo permaneça disponível, mesmo durante a atualização.

**Max Surge (Máximo de Excesso)**: Este é o número máximo de pods extras que podem ser criados além do número original durante a atualização. Por exemplo, se você definir `max surge` como 1 em um aplicativo com 5 pods, durante a atualização, o Kubernetes pode temporariamente criar um sexto pod antes de remover os antigos. Isso ajuda a garantir que haja capacidade suficiente para lidar com qualquer aumento repentino na carga de trabalho durante a atualização.

<figure><img src="../.gitbook/assets/image (185).png" alt=""><figcaption><p>Estrategia Rolling Updates</p></figcaption></figure>

Uma outra forma de implantação é a estratégia Recreate Deployment, mas não é recomendada pois isso pode causar uma indisponibilidade total da aplicação.&#x20;

Porém em ambas as estratégias utilizadas a sempre a possibilidade da utilização do Rollback, que retorna a aplicação ao estado anterior.

***

{% hint style="info" %}
**Todos os recursos utilizados nesses exemplos, estarão disponibilizados no Github:**&#x20;

[**https://github.com/danncastro/k8s-hands-on-testing/tree/main/k8s-cka-exemples/deployments**](https://github.com/danncastro/k8s-hands-on-testing/tree/main/k8s-cka-exemples/deployments)
{% endhint %}

## <mark style="color:red;">Criando Deployments</mark>

{% tabs %}
{% tab title="Deployment" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver created

***

1. Vamos visualizar as informações dos recursos criados.

```bash
kubectl get deploy
```

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl get rs
```

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

***

<pre class="language-bash"><code class="lang-bash"><strong>kubectl get po -owide
</strong></code></pre>

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Rollout" %}
```bash
kubectl rollout status deployment.apps/deployment-webserver
```

deployment "deployment-webserver" successfully rolled out
{% endtab %}

{% tab title="Decribe" %}
```bash
kubectl describe deploy deployment-webserver
```

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Deleted" %}
```
kubectl delete -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps "deployment-webserver" deleted
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Rollout History</mark>

Refere-se ao histórico de versões anteriores de um **Deployment**, permitindo que você retorne a uma versão anterior de um recurso caso a atualização atual cause problemas. O Kubernetes mantém um histórico de alterações feitas no Deployment, e você pode usar o comando `kubectl rollout undo` para reverter para uma versão anterior, garantindo recuperação rápida em caso de falhas.

Em resumo, o **rollback history** é um mecanismo de segurança que permite desfazer atualizações e voltar a um estado estável anterior de uma aplicação.

{% tabs %}
{% tab title="Create" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver created

***

<pre class="language-bash"><code class="lang-bash"><strong>kubectl get po -owide
</strong></code></pre>

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Rollout" %}
```bash
kubectl rollout status deployment.apps/deployment-webserver
```

deployment "deployment-webserver" successfully rolled out
{% endtab %}

{% tab title="History" %}
```bash
kubectl rollout history deployment.apps/deployment-webserver
```

<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Manifest" %}
Alteraremos o número de replicas no manifesto para 4

***

```bash
vim k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

```yaml
  replicas: 4
```

***

```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver configured
{% endtab %}

{% tab title="History" %}
Note que apenas alterar o número de replicas não altera o valor de revisão, isso acontece apenas quando a mudanças significativas, então por exemplo:&#x20;

* Atualização da imagem do contêiner (`image`);
* Alteração de argumentos ou comandos do contêiner;
* Modificação de variáveis de ambiente diretamente definidas no Deploymen

***

```bash
kubectl rollout history deployment.apps/frontend-deploy
```

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Manifest" %}
Alteraremos a versão da imagem do container

***

```yaml
...
image: nginx:1.18.0
```
{% endtab %}

{% tab title="Apply" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver configured

***

Podemos verificar tudo que foi criado pelo nosso deployment através do comando:

```bash
kubectl get all -l app=frontend
```

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

***

```
kubectl describe po deployment-webserver-58d9dc6bdd-mff9j
```

<figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

***
{% endtab %}

{% tab title="Rollout" %}
```bash
kubectl rollout status deployment.apps/deployment-webserver
```

deployment "deployment-webserver" successfully rolled out
{% endtab %}

{% tab title="History" %}
Podemos ver que uma nova versão de revisão foi criada devido a alteração feita na imagem

***

```bash
kubectl rollout history deployment.apps/frontend-deploy
```

<figure><img src="../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Old image" %}
Voltaremos a imagem a versão anterior

```yaml
...
image: nginx
```

```
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver configured
{% endtab %}

{% tab title="History" %}
Note que a versão 1 de revisão sumiu, isso acontece por que o Kubernetes entende que nova revisão feita é exatamente igual a da versão 1 então ela cria a revisão 3 e recomeça a contagem a partir da revisão 3 que é exatamente igual a revisão 1

***

```bash
kubectl rollout history deployment.apps/deployment-webserver
```

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Manifest" %}
Alteraremos novamente a versão da imagem

```bash
vi k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

```yaml
...
image: nginx:1.14.2
```
{% endtab %}

{% tab title="Apply" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver configured
{% endtab %}

{% tab title="History" %}
1. Note que uma nova versão de revisão foi novamente criada seguindo a última revisão

***

```bash
kubectl rollout history deployment.apps/deployment-webserver
```

deployment.apps/deployment-webserver

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

***

2. É possível também analisar uma versão de revisão especifica

```bash
kubectl rollout history deployment.apps/deployment-webserver --revision=2
```

deployment.apps/deployment-webserver with revision #2

<figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

***
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Rollback</mark>

{% tabs %}
{% tab title="Manifest" %}
```bash
vi k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-webserver
  labels:
    app: frontend

spec:
  template:
    metadata:
      name: pod-nginx
      labels:
        env: production
    spec:
      containers:
      - name: container-nginx
        image: nginx:1.21.4

  selector:
    matchLabels:
      env: production
  replicas: 4
```
{% endtab %}

{% tab title="Apply" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml --record
```

Flag --record has been deprecated, --record will be removed in the future

deployment.apps/deployment-webserver configured
{% endtab %}

{% tab title="History" %}
```bash
kubectl rollout history deployment.apps/frontend-deploy
```

<figure><img src="../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Rollback" %}
```bash
kubectl rollout undo deployment.apps/deployment-webserver
```

deployment.apps/deployment-webserver rolled back
{% endtab %}

{% tab title="History" %}
Note que a versão 4 sumiu, isso por que o Rollback foi feito na versão 5 para uma anterior,  fazendo com que a versão 4 se tornasse a versão 6.

***

```bash
kubectl rollout history deployment.apps/frontend-deploy
```

<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Rollback" %}
Podemos também fazer Rollback para versões especificas, e do mesmo modo a versão escolhida para o Rollback é deletada, dando origem a uma nova versão, de forma simplória ela renomeia a versão para a próxima depois da ultima.

***

```bash
kubectl rollout undo deployment.apps/deployment-webserver --to-revision=2
```

deployment.apps/deployment-webserver rolled back

***

```bash
kubectl rollout history deployment.apps/deployment-webserver
```

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

***

```bash
kubectl rollout history deployment.apps/frontend-deploy --revision=7
```

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

***
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Rollout Pause</mark>

{% tabs %}
{% tab title="Deleted" %}
```bash
kubectl delete -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps "deployment-webserver" deleted
{% endtab %}

{% tab title="Manifest" %}
```bash
vi k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-webserver
  labels:
    app: frontend

spec:
  template:
    metadata:
      name: pod-nginx
      labels:
        env: production
    spec:
      containers:
      - name: container-nginx
        image: nginx:1.21.4

  selector:
    matchLabels:
      env: production
  replicas: 5
```
{% endtab %}

{% tab title="Apply" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver created

***

Em outro terminal deixe em execução o comando abaixo:

<pre class="language-bash"><code class="lang-bash"><strong>watch kubectl get po 
</strong></code></pre>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Manifest" %}
Vamos alterar a versão da imagem para gerar uma nova revisão

***

```bash
vim k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-webserver
  labels:
    app: frontend

spec:
  template:
    metadata:
      name: pod-nginx
      labels:
        env: production
    spec:
      containers:
      - name: container-nginx
        image: nginx:1.16.1

  selector:
    matchLabels:
      env: production
  replicas: 5
```
{% endtab %}

{% tab title="Pause" %}
> Deixe um terminal aberto com o comando `watch kubectl get pod` e outro com o comando de `pause` já preparados, pois como estamos utilizando um contexto de testes, existem poucas pods em execução, então a alteração das versões pode ocorrer de forma instantânea, sendo assim já dê o pause assim que executar o apply

```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver configured

***

```bash
kubectl rollout pause deployment.apps/deployment-webserver
```

deployment.apps/deployment-webserver paused
{% endtab %}

{% tab title="Output" %}
Podemos ver que 3 das pods foram atualizadas

***

<pre class="language-bash"><code class="lang-bash"><strong>kubectl get po
</strong></code></pre>

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Rollout Resume</mark>

{% tabs %}
{% tab title="Resume" %}
Após fazer as validações e ter certeza de que a aplicação está pronta para ser executada podemos utilizar o resume para voltar a atualização de versão das pods que não atualizaram

***

```bash
kubectl rollout resume deployment.apps/deployment-webserver
```

deployment.apps/deployment-webserver resumed
{% endtab %}

{% tab title="Output" %}
Agora todas as pods tiveram suas versões atualizadas

***

<pre class="language-bash"><code class="lang-bash"><strong>kubectl get po
</strong></code></pre>

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Deployment Scale - Manifest File/Imperative form</mark>

{% tabs %}
{% tab title="Manifest" %}
Vamos escalar mais 2 pods no arquivo de manifesto ou o que chamamos de **scale up**

***

```bash
vim k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-webserver
  labels:
    app: frontend

spec:
  template:
    metadata:
      name: pod-nginx
      labels:
        env: production
    spec:
      containers:
      - name: container-nginx
        image: nginx:1.16.1

  selector:
    matchLabels:
      env: production
  replicas: 7
```
{% endtab %}

{% tab title="Apply" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver configured
{% endtab %}

{% tab title="Output" %}
<pre class="language-bash"><code class="lang-bash"><strong>kubectl get po
</strong></code></pre>

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Scale down" %}
Faremos a redução de pods mas dessa vez diretamente pelo terminal de forma imperativa

***

```bash
kubectl scale deployment.apps/frontend-deploy --replicas=2
```

deployment.apps/deployment-webserver scaled
{% endtab %}

{% tab title="Output" %}
<pre class="language-bash"><code class="lang-bash"><strong>kubectl get po
</strong></code></pre>

&#x20;

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Recreate Strategy Type</mark>

Como dito anteriormente o Strategy type padrão do Kubernetes é o Rolling Updates (Rolling Release) isso por que ele faz as atualizações baseado na disponibilidade da aplicação, ao qual é diferente do Strategy Type Recreate, que deleta todas as pods em execução e sobem novas não visando sua disponibilidade&#x20;

{% tabs %}
{% tab title="Output" %}
Vamos descrever as pods em execução e ver que o Strategy Type padrão estará setado.

***

```bash
kubectl describe deployment.apps/deployment-webserver | grep StrategyType
```

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Manifest" %}
Vamos novamente alterar a versão da imagem para gerar um novo valor de revisão, e também alteraremos o StrategyType do manifesto.

***

```bash
vim k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-webserver
  labels:
    app: frontend

spec:
  template:
    metadata:
      name: pod-nginx
      labels:
        env: production
    spec:
      containers:
      - name: container-nginx
        image: nginx:1.19.3
  selector:
    matchLabels:
      env: production
  strategy:
    type: Recreate
  replicas: 2
```
{% endtab %}

{% tab title="Apply" %}
```bash
kubectl apply -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps/deployment-webserver configured

***

```bash
watch kubectl get po
```

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Output" %}
Vamos descrever as pods em execução novamente e ver que o Strategy Type foi alterado

***

```bash
kubectl describe deployment.apps/deployment-webserver | grep StrategyType
```

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### <mark style="color:red;">Deletando os recursos criados</mark>

{% tabs %}
{% tab title="Deleted" %}
```bash
kubectl delete -f k8s-hands-on-testing/k8s-cka-exemples/deployments/deployment-webserver.yml
```

deployment.apps "deployment-webserver" deleted

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Output" %}
```bash
kubectl get po -owide
```

No resources found in default namespace.

***

```bash
kubectl get deploy -owide
```

No resources found in default namespace.
{% endtab %}
{% endtabs %}

***
