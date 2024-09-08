# Kubectl

- CLI que permite interagir com um cluster kubernetes
- Se conecta com o cluster via api RESTful
- Kubeconfig: variáveis para configurar a conexão com o cluster

## Mapa de comandos

Digite o comando abaixo para obter um mapa de todos os comandos suportados pelo CLI

>kubectl

## Gerenciando PODs

Cria um pod usando o comando run, com o nome nginx, configurando a imagem e a porta como flags

> kubectl run nginx --image=nginx:latest --port=80

Obter uma lista de pods do cluster

> kubectl get pods

Deletar o pod

> kubectl delete pod nginx


[Voltar para Kubernetes](index.md)