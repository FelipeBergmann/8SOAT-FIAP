# Introdução ao Docker

3 processos do linux que fazem toda a diferença:
Kernel, CGroup e Namespaces

- no windows o docker precisa do wsl na versão 2

- docker hub: repositório de imagens docker
- docker file: onde escrevemos os comandos que serão executados automaticamente assim que o container for iniciado

| cmds | ação |
|---|------|
| docker version | |
| docker | mostra um help de comandos |
| docker container run [nome da imagem] | baixa e executa a img |
| docker pull [nome da imagem] | baixa a img |
| docker container ls | lista os containeres em execução |
| docker container ls -la | lista os containeres já executados |
| docker image ls | lista as imagens que existem localmente (já baixadas) |
| docker container run -it node:18-slim | Roda o container em modo interativo, assim ele não finaliza e abre o console no container |
| docker container kill [id do container] | finalizar execução do container |
| docker container run -d [nome da imagem] | roda em modo daemon, em segundo plano, sem travar o console atual |
| docker container stats [id do container] | mostra os status do container |
| docker container attach [id do container] | entra no container em execução (console) |
| docker container start [id do container] | |
| docker container restart [id do container] | |
| docker container stop [id do container] | |
| docker container pause [id do container] | |
| docker container unpause [id do container] | |
| docker container rm [id do container] | Remove um container que não está em execução |
| docker container rm -f [id do container] | Remove um container de forma forçada |
| docker container top [id do container] | Mostra uma lista de processos rodando atualmente no container |
