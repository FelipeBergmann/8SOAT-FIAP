# ConfigMap

O   ConfigMap   é   um   recurso   do   Kubernetes   que   permite   separar   as configurações de um container de seus artefatos de implantação. Isso significa que é possível  armazenar  as  configurações  em  um  local  centralizado  e  gerenciá-las separadamente do container.As configurações podem ser armazenadas em um ConfigMap em um arquivo YAML. Essas configurações podem ser injetadas em um container de várias maneiras, incluindo como variáveis de ambiente, como arquivos montados ou como argumentos de linha de comando.

Comando para criar um configmap:

> kubectl create configmap <map-name> <data-source>

Obtendo os dados do ConfigMap game-config:

> kubectl describe configmaps game-config

A saída será parecida com esta:

```bash
Name:         game-config
Namespace:    default
Labels:       <none>
Annotations:  <none>

Data
====
game.properties:
----
enemies=aliens
lives=3
enemies.cheat=true
enemies.cheat.level=noGoodRotten
secret.code.passphrase=UUDDLRLRBABAS
secret.code.allowed=true
secret.code.lives=30
ui.properties:
----
color.good=purple
color.bad=yellow
allow.textmode=true
how.nice.to.look=fairlyNice
```

[Voltar para Kubernetes](index.md)