# Armazenamento

Os arquivos em disco em um contêiner são efêmeros, o que apresenta alguns problemas para aplicações não triviais quando executadas em contêineres. Um problema é a perda de arquivos quando um contêiner quebra. O kubelet reinicia o contêiner, mas em um estado limpo. Um segundo problema ocorre ao compartilhar arquivos entre contêineres que são executados juntos em um Pod. A abstração de volume do Kubernetes resolve ambos os problemas.

## Volumes

O Kubernetes suporta muitos tipos de volumes. Um Pod é capaz de utilizar qualquer quantidade de tipos de volumes simultaneamente. Os tipos de volume efêmeros têm a mesma vida útil do pod, mas os volumes persistentes existem além da vida útil de um pod. Quando um pod deixa de existir, o Kubernetes destrói volumes efêmeros; no entanto, o Kubernetes não destrói volumes persistentes. Para qualquer tipo de volume em um determinado pod, os dados são preservados entre as reinicializações do contêiner.

Em sua essência, um volume é um diretório, eventualmente com alguns dados dentro dele, que é acessível aos contêineres de um Pod. Como esse diretório vem a ser, o meio que o suporta e o conteúdo do mesmo são determinados pelo tipo particular de volume utilizado.

Para utilizar um volume, especifique os volumes que serão disponibilizados para o Pod em .spec.volumes e declare onde montar esses volumes dentro dos contêineres em .spec.containers[*].volumeMounts.

>Volumes não podem ser montados dentro de outros volumes (mas você pode consultar Utilizando subPath para um mecanismo relacionado). Além disso, um volume não pode conter um link físico para qualquer outro dado em um volume diferente.

O  Kubernetessuporta  vários  tipos  de  volumes,  cada  um  com  suas  próprias propriedades e funcionalidades. Alguns dos tipos mais comuns de volumes são:

- **emptyDir:** um volume vazio que é criado quando um Pod é iniciado e é excluído quando o Pod é encerrado. Ele é geralmente usado para compartilhar arquivos temporários entre containers em um Pod.
- **hostPath:** um volume que monta um diretório ou arquivo do nó do cluster no container. É útil quando os containers precisam acessar arquivos ou diretórios no nó do cluster.
- **persistentVolumeClaim:**  um  volume  que  fornece  armazenamento  persistente para os containers em um Pod. É usado quando os dados precisam sobreviver àreinicializações ou redimensionamentos de Pods.

### Tipos de Persistent Volumes

O Kubernetes suporta vários tipos de persistent volumes.Temos uma lista dos tipos mais comuns: 
- **NFS:** um protocolo de compartilhamento de arquivos em rede que permite que vários nós acessem o mesmo armazenamento.
- **iSCSI:**  um  protocolo  de  armazenamento  em  rede  que  permite  que  um sistema de armazenamento remoto seja montado em um nó do cluster.●hostPath: um volume que monta um diretório ou arquivo do nó do cluster no container.  É  útil  quando  os  containers  precisam  acessar  arquivos  ou diretórios no nó do cluster.
- **EBS  (Elastic  Block  Store):**  um serviço  de  armazenamento  em  nuvem oferecido   pela   AWS   que   permite   criar   volumes   de   armazenamento persistente. 

#### Exemplo

```yml
apiVersion: v1
kind: Pod
metadata:
  name: test-ebs
spec:
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  containers:
  - image: registry.k8s.io/test-webserver
    name: test-container
    volumeMounts:
    - mountPath: /test-ebs
      name: test-volume
  volumes:
  - name: test-volume
    nfs:
      server: 192.168.1.100
      path: "/dados"
```


[Voltar para Kubernetes](index.md)