# Kubernetes

Kubernetes é um sistema de orquestração de contêineres de código aberto que automatiza a implantação, escalonamento e gerenciamento de aplicações em contêineres. Ele permite que você agrupe contêineres em pods, que podem ser gerenciados e escalados de forma eficiente. Kubernetes lida com a distribuição de cargas de trabalho, gerenciamento de estado e recuperação de falhas. Oferece recursos como balanceamento de carga, armazenamento persistente e gestão de configuração. É amplamente utilizado para manter aplicações altamente disponíveis e escaláveis em ambientes de produção.


## Pods e Nós (Nodes)

Pods são a menor unidade de execução no Kubernetes, consistindo em um ou mais contêineres que compartilham o mesmo ambiente de rede e armazenamento. Eles agrupam processos relacionados para funcionarem juntos de forma coesa e são executados em nós (nodes). Nós são máquinas físicas ou virtuais que compõem o cluster Kubernetes e executam os pods. Cada nó possui um agente chamado Kubelet que gerencia a execução dos pods, além de recursos como CPU, memória e armazenamento. O Kubernetes gerencia a distribuição de pods pelos nós, garantindo alta disponibilidade e escalabilidade das aplicações.

[Apronfundar conhecimento em Pods e Nodes](pods_and_nodes.md)

## O que é um cluster?

Um cluster no contexto do Kubernetes é um conjunto de máquinas (nós) que trabalham juntas para executar e gerenciar aplicações em contêineres de forma distribuída e coordenada. O cluster inclui:

**Nó Mestre (Control Plane):** Gerencia o cluster e coordena todas as operações, como escalonamento, alocação de pods e monitoramento de saúde. Ele é responsável por tomar decisões sobre onde os pods serão executados e por manter o estado desejado do sistema.

**Nós de Trabalho (Worker Nodes):** Executam os contêineres dentro dos pods e fornecem os recursos de CPU, memória e armazenamento para as aplicações. Cada nó de trabalho é gerenciado pelo nó mestre.

O Kubernetes utiliza o cluster para distribuir e balancear a carga de trabalho, garantindo que as aplicações rodem de forma eficiente e escalável, além de oferecer resiliência e alta disponibilidade.

## Próximos Tópicos

### [Pods e Nodes](pods_and_nodes.md)

### [Kubectl](kubectl.md)

### [ConfigMap](configMap.md)

### [Probes](probes.md)

### [ReplicaSet e Deployment](replicaSet_and_deployment.md)

### [Serviços](services.md)

### [Armazenamento](storage.md)

### [Horizontal Pod Autoscaler (HPA)](horizontal_pod_autoscaler_HPA.md)

