---
description: >-
  Kubernetes (ou K8s) é uma plataforma de orquestração de containers, criado
  pelo Google em 2014, agora mantido pela Cloud Native Computing Foundation
  (CNCF).
---

# Kubernetes

**Objetivo:** Automatizar a implantação, escala e gerenciamento de aplicações em containers.

<figure><img src=".gitbook/assets/image (167).png" alt=""><figcaption><p>Fonte: https://kubernetes.io/pt-br/docs/tutorials/kubernetes-basics</p></figcaption></figure>

***

## <mark style="color:red;">Historia do Kubernetes</mark>

A jornada do Kubernetes começou em 2003 , com o desenvolvimento do **Google Borg** (Container Orchestration System), um sistema interno de orquestração de containers criado pelo Google.&#x20;

O Borg foi projetado para gerenciar a massiva infraestrutura de serviços da empresa, sendo capaz de orquestrar bilhões de workloads mensalmente — um número que ainda hoje ultrapassa 12 bilhões de implantações por mês.

Apesar de sua eficiência, o Google identificou a necessidade de uma solução mais flexível e acessível. Assim, em 2014, o **Kubernetes** foi lançado como uma evolução do Borg, incorporando os aprendizados acumulados ao longo de anos de operação em larga escala.

A partir de 2019, o Kubernetes consolidou-se como a plataforma dominante de orquestração de containers no mercado. Atualmente, ele é mantido pela **Cloud Native Computing Foundation (CNCF)**, garantindo seu desenvolvimento contínuo e suporte à comunidade global.

***

## <mark style="color:red;">O que é o Kubernetes</mark>

Sistema open source utilizado para implantação, automatização de `deployments`, escalonamento e gerenciamento de aplicativos em contêineres, também conhecido pelas abreviaturas `k8s` ou `kube`.

> _O nome **k8s** é uma abreviação de **"Kubernetes"**, sendo `k` + `8 letras` + `s`._

Isso por que nos anos 80 os programadores eram "preguiçosos" e gostavam de abreviar as palavras baseando sempre em primeira letra, ultima letra e o numero de letras entre eles.

{% hint style="info" %}
Seguindo este padrão, surgiu o **k8s**.
{% endhint %}

A palavra "Kubernetes", faz alusão a um navio cargueiro;

* Kubernetes -> "Kuvernetes" (em Grego) -> "Timoneiro" (Aquele que conduz o navio).
* Esse conceito inspira o papel do Kubernetes como orquestrador de containers.

<figure><img src=".gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>



> Muitos dos conceitos e termos do Kubernetes, incluindo o logotipo com **7 Malaguetas**, foram inspirados pelo universo de **Star Trek**. As sete pontas do logotipo fazem referência à personagem **Seven of Nine**, da série _Star Trek_. Além disso, o nome do precursor do Kubernetes, **Borg**, também homenageia a série, sendo uma alusão aos "organismos cibernéticos" conhecidos como Borgs no universo de _Star Trek_.

#### <mark style="color:blue;">Alguns Exemplos de termos abreviados:</mark>

* **Internationalization** `(i18n)`
* **Localization** `(l10n)`
* **Globalization** `(g11n)`
* **Localizability** `(l12y)`

Também vemos alguns termos como `k3s` e `k0s` quando falamos de Kubernetes, estes se referem a distribuições de Kubernetes.

* [K3s](https://k3s.io/) - Distribuição com foco em ter a metade do tamanho em consumo de memória. Kubernetes é uma palavra de 10 letras estilizada como k8s. Portanto, algo com a metade do tamanho do Kubernetes seria uma palavra de 5 letras estilizada como K3s.
* [K0s](https://k0sproject.io/) - Distribuição com foco em facilitação. _**"K0s é para Kubernetes o que Docker é para containers"**_. O nome zero é utilizado para significar zero atrito, zero custo e zero sobrecarga.

O Kubernetes (k8s) facilita a organização e administração de aplicações em ambientes que utilizam dezenas ou até milhares de containers. Ele proporciona flexibilidade ao permitir que as aplicações sejam executadas em diferentes tipos de infraestrutura, como:

* **Infraestrutura local:** Servidores físicos dedicados.
* **Máquinas virtuais:** Ambientes virtualizados.
* **Cloud pública:** Plataformas como AWS, Azure e GCP.
* **Cloud híbrida:** Combinação de ambientes on-premises e nuvem.

Essa versatilidade torna o Kubernetes ideal para cenários modernos de TI, onde escalabilidade e consistência são cruciais.

***

### <mark style="color:red;">O que é um orquestrador de containers</mark>

Um orquestrador de containers é um sistema que automatiza todo o ciclo de vida de containers e das aplicações que eles executam. Seu objetivo é simplificar o gerenciamento de aplicações complexas e garantir eficiência, escalabilidade e alta disponibilidade.

As principais funções de um orquestrador incluem:

* **Implantação:** Automatizar a criação e inicialização dos containers.
* **Provisionamento:** Alocar recursos necessários para os containers (CPU, memória, etc.).
* **Networking:** Configurar a comunicação entre containers e com o mundo externo.
* **Dimensionamento:** Ajustar o número de containers para atender à demanda.
* **Disponibilidade:** Garantir que os serviços estejam sempre ativos e em funcionamento.
* **Gerenciamento do ciclo de vida:** Supervisionar desde a criação até o encerramento dos containers.

#### <mark style="color:blue;">Quais necessidades de uma ferramenta de orquestração de containers?</mark>

* **Migração de aplicações monolíticas para microsserviços:** Facilitar a transição para arquiteturas mais flexíveis e escaláveis.
* **Disponibilidade da aplicação**_:_ Reduzir downtime com replicação e balanceamento de carga.
* **Escalabilidade e alta performance:** Ajustar recursos automaticamente para atender às demandas.
* **Recuperação de desastre&#x20;**_**(Backup/Restore):**_ Implementar backups de dados críticos, como volumes persistentes e configurações de pods e deployments, e garantir sua rápida restauração em caso de falhas no cluster, assegurando a continuidade das operações com mínima perda de dados e tempo de inatividade.

#### _<mark style="color:blue;">**Alguns Orquestradores além do Kubernetes**</mark>_

<figure><img src=".gitbook/assets/image (175).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Características do K8s</mark>

#### <mark style="color:blue;">Imutabilidade Kubernetes</mark>

Segue o princípio de infraestrutura imutável, onde alterações nos objetos (como Pods) são feitas substituindo-os por novas versões, em vez de modificá-los diretamente.

* **Princípios da infraestrutura imutável**
  * Reduz erros humanos e inconsistências.
  * Facilita rollback em caso de falhas.
* **Substituição de Objetos Criados:**
  * Alterações em configurações resultam na recriação automática dos objetos com as atualizações aplicadas.
* **Incremento de segurança contra indisponibilidade:**
  * Ao prevenir mudanças diretas em objetos existentes, o K8s minimiza impactos de falhas e mantém alta disponibilidade dos serviços.

#### <mark style="color:blue;">Disponibilidade do K8s</mark>

* **Configuração Declarativa (Arquivos):** Define o estado desejado da aplicação em arquivos `YAML/JSON`, permitindo recriação automática em caso de falhas.
* **Comandos imperativos (Ações no terminal):** Executa ações pontuais no terminal para ajustes ou diagnósticos rápidos.
* **Self-Healing System:** Detecta e substitui automaticamente componentes com falhas, garantindo continuidade.
* **Autoscale Up/Down:** Ajusta automaticamente a quantidade de recursos (replicas) para cima ou para baixo, conforme a demanda.
* **DevOps Automation Tool:** Automatiza tarefas repetitivas, integrando operações e desenvolvimento.
* **Fault Protection (Ações preventivas):** Implementa ações preventivas para reduzir impactos de falhas e melhorar a confiabilidade.

#### <mark style="color:blue;">Escalabilidade -> Services/Applications</mark>

* **YAML/JSON manifest files:** Definem a configuração declarativa para escalar serviços de forma automatizada.
* **Escala declarativa:** Permite especificar o estado desejado (ex.: número de réplicas, definição de recuso), ajustando automaticamente conforme necessário.
* **Cluster Scale Support:** Garante que clusters possam crescer ou diminuir para atender às demandas de recursos.
* **Service-based decoupling for teams (Desacoplamento Baseado em Serviços):** Promove a independência entre equipes, permitindo que cada serviço seja escalado separadamente.
* **Service-based decoupling for teams (Separação de Responsabilidades):**
  * **Desenvolvedores (Dev):** Foco no desenvolvimento e configuração das aplicações.
  * **Administradores K8s (Ops):** Gerenciam o cluster e a infraestrutura subjacente.



<figure><img src=".gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure>

***

#### <mark style="color:blue;">Abstração de Infraestrutura</mark>

O Kubernetes abstrai a infraestrutura subjacente, permitindo criar clusters em diversos ambientes, como:

* **Cloud Abstraction:** Funciona em qualquer provedor de nuvem pública (AWS, Azure, GCP) ou privada.
* **Bare Metal:** Suporte direto a servidores físicos.
* **Virtual Machines:** Integração com ambientes virtualizados.
* **Kind (Kubernetes IN Docker):** Ideal para testar clusters localmente usando containers Docker.
* **Raspberry Pi:** Permite criar clusters em dispositivos de baixo custo, perfeito para aprendizado ou IoT.

***

### <mark style="color:red;">Glossário</mark>

{% embed url="https://kubernetes.io/pt-br/docs/reference/glossary/?all=true#term-cluster" %}
