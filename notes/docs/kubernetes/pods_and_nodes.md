# Pods e Nodes aprofundando o conhecimento

## Componentes do Cluster

### Master Node

É um node que é reponsável por gerenciar os outros nodes, ele conta com módulos como: controller manager, scheduler e etcd.
Este node tem controle dos outros nodes - conhecidos como workers, e consegue escalá-los de modo que libere ou aumente recursos para que os pods possam trabalhar corretamente.

### Worker Node

São nodes que executam os pods e outros recursos

### Etcd

É um banco de dados distribuído que armazena as configurações do cluster e estados dos objetos

### kubelet

É um agente que é executado em cada node do cluster, que gerencia os pods contidos nele.

### Kube-proxy

É responsável por estabelecer a comunicação de rede entre os pods no cluster

### Comunicação e rede

Os pods contidos em um node podem se comunicar com todos os pods no mesmo cluster (mesmo que em outros nodes) por meio de endereços de ip internos.

## O que são pods?

É uma abstração do kubernetes para a execução de um único processo. Executando dentro de um pod podemos ter um ou mais conteineres.
São criados e excluídos conforme a necessidade, o que permite um alto gerenciamento de recursos.

Os Pods são criados a partir de definições YAML ou JSON, que especificam quais containers devem ser executados dentro do Pod, suas imagens e as portas em que cada container deve ouvir. Quando ele é criado, recebe um endereço IP interno dentro do cluster, permitindo que outros Pods se comuniquem com ele.

### Rótulos

Os  rótulos  são  pares  de  chave-valor  que  são  atribuídos  aos  objetos  no Kubernetes,  como  Pods,  Serviços,  Application  Controllers,  entre  outros.  Eles  são usados   para   identificar,   categorizar   e   selecionar   objetos   para   operações   de gerenciamento, como escalonamento e exclusão

Usabilidade:

- Designar objetos para desenvolvimento, teste e produção
- Adicionar tags de versão
- Classificar um objeto usando tags

### Anotações

As anotações, por outro lado, são pares de chave-valor opcionais que podem ser adicionadas a objetos no Kubernetes. Eles são usados para adicionar metadados adicionais aos objetos, como informações de depuração, documentação e políticas de segurança.


Quais são as principais diferenças entre pods e nodes? Por que separar em dois níveis?

**1. Separação de Responsabilidades:**

Pods agrupam contêineres que têm uma relação estreita e precisam compartilhar recursos (como volumes e rede). 
Esses contêineres são geralmente interdependentes e, por isso, precisam estar no mesmo ambiente de execução. Por exemplo, um pod pode conter uma aplicação e um contêiner auxiliar que faz logging ou monitoramento dessa aplicação.

**Nós são unidades de infraestrutura (máquinas físicas ou virtuais)** que fornecem os **recursos computacionais** (CPU, memória, armazenamento) para executar os pods. Um nó pode hospedar vários pods, cada um com diferentes funções, de diferentes partes do sistema.


**2. Escalabilidade e Flexibilidade:**

Se você colocar todos os contêineres em um único pod, você perde a **granularidade** no controle de escala. 
Pods são pensados para serem pequenos, encapsulando um ou poucos contêineres interdependentes. Ao escalar um pod, você replica exatamente o que há dentro dele.

>**Exemplo:** Se você tem uma API e um banco de dados no mesmo pod, ao escalar esse pod, você não pode escalar a API separadamente do banco de dados, mesmo que a API precise de mais replicas,  enquanto o banco não.
**Escalando pods separados:** Ao ter pods separados (ex.: um para a API, outro para o banco de dados), você pode escalar a API independente do banco. Isso te dá flexibilidade para adaptar cada parte da sua aplicação conforme a demanda.


**3. Gerenciamento de Recursos:**

Nós permitem a otimização do uso de recursos. Em um cluster, Kubernetes distribui automaticamente os pods entre diferentes nós, garantindo um balanceamento eficiente da carga. 
Se todos os seus pods estivessem em um único nó, você estaria limitado pela capacidade de CPU, memória e armazenamento desse nó específico.
**Se esse nó falhar, todos os pods falhariam juntos.** Com múltiplos nós, o Kubernetes pode distribuir a carga e garantir alta disponibilidade.


**4. Resiliência e Isolamento:**

Ao separar seus contêineres em pods menores e independentes, você garante melhor isolamento entre diferentes componentes da sua aplicação. 
Se um contêiner dentro de um pod falha, o Kubernetes pode reiniciar apenas esse pod, sem impactar os outros pods no nó.

Se você colocar todos os contêineres em um único pod, qualquer falha em um dos contêineres pode potencialmente afetar outros, já que eles compartilham o mesmo ciclo de vida. Isso também prejudicaria a capacidade de isolar falhas e limitar danos.


**5. Alta Disponibilidade:**

Distribuir pods entre nós é uma prática essencial para garantir a alta disponibilidade. 
Ao espalhar seus pods entre diferentes nós, você minimiza o risco de falhas catastróficas. Se um nó cair, apenas os pods nele são afetados, e o Kubernetes pode rapidamente realocar os pods em outros nós disponíveis.

Se você tiver apenas um nó e ele falhar, todas as suas aplicações caem, independente de quantos pods você tem.


**6. Otimização de Carga e Uso de Recursos:**

Nó é a unidade de infraestrutura física/virtual que provê CPU, memória e armazenamento. 
Kubernetes gerencia os recursos dentro dos nós de forma eficiente, colocando mais pods em nós subutilizados e garantindo que a carga seja bem distribuída no cluster.

Escalar nós inteiros faz sentido quando os nós estão sobrecarregados ou sem recursos suficientes para hospedar mais pods. 
Mas você ainda quer o controle granular para escalar individualmente os pods que realmente precisam de mais instâncias, ao invés de escalar todos os contêineres dentro de um nó ou pod.

### Resumo

Pods permitem agrupar contêineres interdependentes que precisam ser escalados juntos e compartilhar recursos.
Nós são unidades de infraestrutura que suportam a execução de vários pods e permitem a distribuição de carga.
A escalabilidade de pods separados te dá flexibilidade para ajustar recursos e desempenho por serviço, enquanto escalar nós te permite aumentar a capacidade de todo o cluster.
Distribuir pods em vários nós melhora a resiliência e alta disponibilidade.

Portanto, ter um pod por nó ou todos os contêineres em um único pod eliminaria muitos dos benefícios do Kubernetes, como gerenciamento de recursos, resiliência e escalabilidade granular.

[Voltar para Kubernetes](index.md)