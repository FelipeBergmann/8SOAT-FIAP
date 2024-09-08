# ReplicaSets e Deployments

## ReplicaSets

O propósito de um ReplicaSet é gerenciar um conjunto de réplicas de Pods em execução a qualquer momento. Por isso, é geralmente utilizado para garantir a disponibilidade de um certo número de Pods idênticos.

Um ReplicaSet é definido por campos, incluindo um seletor que identifica quais Pods podem ser adquiridos, um número de réplicas indicando quantos Pods devem ser mantidos, e um pod template especificando as definições para novos Pods que devem ser criados para atender ao número de réplicas estipuladas. Um ReplicaSet cumpre seu propósito criando e deletando Pods conforme for preciso para atingir o número desejado. Quando um ReplicaSet precisa criar novos Pods, ele usa o seu podTemplate.

## Quando usar um ReplicaSet 

Um ReplicaSet garante que um número de réplicas de um Pod estão executando em qualquer momento. Entretanto, um Deployment é um conceito de nível superior que gerencia ReplicaSets e fornece atualizações declarativas aos Pods assim como várias outras funções úteis. Portanto, nós recomendamos a utilização de Deployments ao invés do uso direto de ReplicaSets, exceto se for preciso uma orquestração de atualização customizada ou que nenhuma atualização seja necessária.

Isso na realidade significa que você pode nunca precisar manipular objetos ReplicaSet: prefira usar um Deployment, e defina sua aplicação na seção spec.

### Exemplo

```yml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: frontend
  labels:
    app: guestbook
    tier: frontend
spec:
  # modifique o número de replicas de acordo com o seu caso
  replicas: 3
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: php-redis
        image: gcr.io/google_samples/gb-frontend:v3
```

## Deployment (recomendado) 

Deployment é um objeto o qual pode possuir ReplicaSets, atualizá-los e por consequência seus Pods via atualizações declarativas, gradativas do lado do servidor. Enquanto ReplicaSets conseguem ser usados independentemente, hoje eles são principalmente usados por Deployments como um mecanismo para orquestrar a criação, deleção e atualização de um Pod. Quando você usa Deployments você não precisa se preocupar com o gerenciamento de ReplicaSets que são criados por ele. Deployments controlam e gerenciam seus ReplicaSets. Por isso, é recomendado o uso de Deployments quando você deseja ReplicaSets.

Além  disso, o  Deployment permite  que os usuários  atualizem o aplicativo  de forma controlada e automática. Quando uma atualização é implantada, o Kubernetes cria  um  novo  conjunto  de  réplicas  com  a  nova  versão  do  aplicativo  e,  em  seguida, gradualmente substitui as réplicas antigas pelas novas. Esse processo é chamado de “Rolling Update”,e permite que os usuários atualizem o aplicativo sem interromper o serviço.

Se ocorrer algum problema durante uma atualização, o Kubernetes oferece a possibilidade  de  reverter  para  a  versão  anterior  do  aplicativo.  Isso  é  chamado  de rollback e é uma funcionalidade importante para garantir a disponibilidade contínua do serviço.

### Exemplo

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

## Job
Use um Job no lugar de um ReplicaSet para Pods que tem por objetivo sua terminação no final da execução (como batch jobs).

## DaemonSet 

Use um DaemonSet no lugar de um ReplicaSet para Pods que precisam prover funções no nível de sistema, como monitoramento do sistema ou logs do sistema. Esses Pods tem um tempo de vida ligado à vida útil do sistema: os Pods precisam estar executando na máquina antes de outros Pods inicializarem, e são seguros de terminarem quando a máquina esta preparada para reiniciar/desligar.



[Voltar para Kubernetes](index.md)