# Ingress Controller Manager

É o componente responsável por gerenciar os recursos de **Ingress** no Kubernetes. Ele age como um intermediário, configurando automaticamente proxies reversos (como NGINX, Traefik ou HAProxy) para rotear o tráfego de entrada com base nas regras definidas nos recursos de Ingress.

* **Função:**
  * Detecta objetos **Ingress** criados no cluster.
  * Configura e gerencia o proxy reverso para rotear o tráfego externo para os serviços correspondentes.
*   **Exemplo de Implementação:**

    * **NGINX Ingress Controller:** Um dos mais usados.
    * Requer a instalação no cluster para que o Ingress funcione.\


    #### **Ingress**

    É um recurso do Kubernetes que define regras para expor serviços internamente no cluster para o tráfego externo, como HTTP e HTTPS.

    * **Função:**
      * Define rotas baseadas em regras de URL, domínio, porta, etc.
      * Permite SSL/TLS, balanceamento de carga e manipulação de cabeçalhos HTTP.

**Resumo:**

* **Ingress Controller:** O "gerente" que implementa as regras.
* **Ingress:** O "roteiro" que descreve como o tráfego deve ser direcionado para os serviços.\
  Juntos, eles garantem que o tráfego externo chegue corretamente aos Pods do cluster.
