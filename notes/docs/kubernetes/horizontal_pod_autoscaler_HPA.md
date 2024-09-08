# Horizontal Pod Autoscaler (HPA)

Responsável por aumentar ou diminuir automaticamente o número de pods (carga de trabalho) por meio de métricas como utilização de CPU, memória, input/output, métricas customizadas ou métricas de softwares terceiros como Prometheus.

A verificação de escala automática é implementada em formato de loop, podendo configurar o intervalo de verificação pela chave ```--horizontal-pod-autoscaler-sync-period``` configurada no kube-controller-manager

[Voltar para Kubernetes](index.md)