# Services

Um objeto Service do Kubernetes é uma camada de abstração que define um conjunto lógico de Pods e habilita a exposição ao tráfego externo, balanceamento de carga e descoberta de serviço para esses Pods.

Embora cada Pod tenha um endereço IP único, estes IPs não são expostos externamente ao cluster sem um objeto Service. Objetos Service permitem que suas aplicações recebam tráfego. Services podem ser expostos de formas diferentes especificando um tipo (campo type) na especificação do serviço (campo spec):

- **ClusterIP (padrão)** - Expõe o serviço sob um endereço IP interno no cluster. Este tipo de serviço é acessível somente dentro do cluster.
- **NodePort** - Expõe o serviço sob a mesma porta em cada nó selecionado no cluster usando NAT. Torna o serviço acessível externamente ao cluster usando o endereço <NodeIP>:<NodePort>. É um superconjunto do tipo ClusterIP.
- **LoadBalancer** - Cria um balanceador de carga externo no provedor de nuvem atual (se suportado) e atribui um endereço IP fixo e externo para o serviço. É um superconjunto do tipo NodePort.
- **ExternalName** - Mapeia o Service para o conteúdo do campo externalName (por exemplo, foo.bar.example.com), retornando um registro DNS do tipo CNAME com o seu valor. Nenhum tipo de proxy é configurado. Este tipo requer a versão 1.7 ou mais recente do kube-dns, ou o CoreDNS versão 0.0.8 ou superior.


[Voltar para Kubernetes](index.md)