# Probes

São um recurso do kubernetes para verificar a saúde de um container. Probes são definidas no manifesto kubernetes e é uma boa prática definir os endpoints para os três tipos de probes.

Existem 3 tipos de probes: Liveness, Readiness e Startup.

## Liveness Probe

Probe que verifica de tmepo em tempo se o aplicativo continua funcional por meio de um coamndo. Se um conteiner falhar repetidamente nesta probe o kubelet irá reiniciar o conteiner.
Esta probe não espera pela readiness probe para ser executada. Se você deseja esperar antes de executar o liveness probe, você pode também definir initialDelaySeconds ou usar o startup probe.

### Liveness Meios de Verificação

Pode ser definido por meio de:
- Requisição http: determina se está em execução realizando uma chamada http que deve retornar o status code 200 em caso positivo.
```yml
livenessProbe:
      httpGet:
        path: /healthz
        port: 8080
        httpHeaders:
        - name: Custom-Header
          value: Awesome
      initialDelaySeconds: 3
      periodSeconds: 3
```
- TCP: escuta uma porta para verificar se a aplicação está em execução.
```yml
livenessProbe:
      tcpSocket:
        port: 8080
      initialDelaySeconds: 15
      periodSeconds: 10
```
- Exec: executa um comando no conteiner para verificar se está em execução.
```yml
livenessProbe:
      exec:
        command:
        - cat
        - /tmp/healthy
      initialDelaySeconds: 5
      periodSeconds: 5
```
- gRPC: se a aplicação implementa Health Check Protocol
```yml
livenessProbe:
      grpc:
        port: 2379
      initialDelaySeconds: 10
```

## Readiness Probe 

Determina se um container já está pronto para receber tráfego. É útil quando é necessário esperar que a aplicação termine suas tarefas iniciais como carregamento de arquivos, estabelecer conexões de rede e etc.

Se esta probe retornar um código de falha, o kubernetes remove o pod de todos os services correspondentes, evitando rotear para este pod tráfego que resultará em falha.

Esta probe é executada durante todo o tempo de vida do conteiner.

### Readiness Meios de Verificação

São definidos de forma similar ao livenessProbe, você apenas utiliza readinessProbe no lugar de livenessProbe.

**Exemplo:**

```yml
readinessProbe:
  exec:
    command:
    - cat
    - /tmp/healthy
  initialDelaySeconds: 5
  periodSeconds: 5
```

## Startup Probe

Verifica se a aplicação dentro de um conteiner foi inicializada. Este probe pode ser adotado para evitar que em conteineres de inicialização lenta sejam removidos pelo kubelet através do liveness probe antes dele finalizar sua inicialização. Se esta probe estiver configurada desativa outras probes (liveness e readiness) temporáriamente até que esta seja concluída.

Este tipo de probe é executada apenas no startup do conteiner, ao contrário das outras que são executadas periodicamente.

### Startup Meio de Verificação

```yml
ports:
- name: liveness-port
  containerPort: 8080

livenessProbe:
  httpGet:
    path: /healthz
    port: liveness-port
  failureThreshold: 1
  periodSeconds: 10

startupProbe:
  httpGet:
    path: /healthz
    port: liveness-port
  failureThreshold: 30
  periodSeconds: 10
```


## Exemplo Final
```yml
apiVersion: v1
kind: Pod
metadata:
  labels:
    test: liveness
  name: liveness-http
spec:
  containers:
  - name: liveness
    image: registry.k8s.io/e2e-test-images/agnhost:2.40
    args:
    - liveness
    livenessProbe:
      httpGet:
        path: /healthz
        port: 8080
        httpHeaders:
        - name: Custom-Header
          value: Awesome
      initialDelaySeconds: 3
      periodSeconds: 3
```

[Voltar para Kubernetes](index.md)