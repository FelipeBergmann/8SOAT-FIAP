# Gerenciamento de Contêineres

Podemos criar um arquivo Dockerfile na raiz do nosso projeto, que nos ajudará a rodar a aplicação sem precisar fazer tudo manualmente.
```
Atenção: o padrão do nome do arquivo é Dockerfile, caso seja criado como dockerfile (por exemplo) precisaremos especificar o nome do arquivo durante o build
```

Arquivo exemplo

```Dockerfile
# define uma imagem que existe no dockerhub 
# esta imagem já roda em cima de um linux kernel (debian) e instala o node
# se trocassemos por uma imagem do sistema operacional diretamente, precisaríamos instalar o node
FROM node:18 

# Como estamos executando dentro de um SO, precisamos definir um diretório para que a aplicação seja executada
# caso contrário, ela será executada dentro do diretório Home
WORKDIR /app

# copia o arquivo package.json para o diretório atual
# desta forma, as próximas camadas só serão reconstruidas caso o package.json tenha sofrido alguma alteração
# caso este arquivo (que guarda as dependencias do nosso projeto) não tenha sido alterado
# as próximas camadas serão utilizadas do cache
COPY package.json .

# executa o comando npm install
RUN npm install

# copia todos os arquivos do diretório atual para o diretório app
COPY . .

# expõe uma porta do container
EXPOSE 3000

# executa o comando node app.js
# aqui usamos CMD ao invés do RUN pois o RUN é executado no momento de build da imagem
# já o CMD é executado no momento em que o container é iniciado
# também poderíamos usar o ENTRYPOINT - a diferença é que com o CMD os argumentos podem
# ser substituídos via CLI, já no ENTRYPOINT não
CMD [ "node", "app.js" ]

```

Para executar a nossa aplicação, precisamos criar (build) a imagem. Abrindo o terminal no diretório raíz do nosso app (diretório que se encontra o Dockerfile) e executamos o comando abaixo. A flag -t cria uma tag para a nossa imagem, auxiliando no gerenciamento de versões.

```bash
docker build -t node-app:1 .
```

Desta forma, se executarmos o comando docker image ls, teremos uma imagem chamada node-app (coluna repository) com tag 1

Para utilizar outro nome de arquivo Dockerfile, utilizar a flag ` -f Dockerfile-nome `

## Disponibilizando as imagens

- Docker Hub - FREE
- AWS
- Azure
- Google Container

### Passo a passo

Na primeira vez, precisamos nos conectar ao docker hub: ` docker login `, se autentique com o seu usuário e senha.

Vamos fazer o build da imagem: `docker build -t SeuNomeDeUsuario/node-app:tagname`

para publicar, faça o push para o seu repositório: ` docker push SeuNomeDeUsuario/node-app:tagname `

## Redes

Todo container precisa de uma rede para interagir no ambiente

docker network ls
drivers:
bridge: ponte entre container e nossa máquina com acesso à internet
host: conecta com a máquina local sem acesso à internet
null: sem nenhum driver - isola a comunicação com o mundo externo. Indicado para containeres de dados. Desta forma ele é acessado apenas na rede local do docker.
overlay: para comunicação entre hosts - ex: comunicação entre containeres rodando na máquina local e containeres rodando em uma VM

`docker network inspect driver-id`
conseguimos inspecionar as configurações de cada driver

`docker network create --driver bridge nomeDaRede`

Colocar o container em comunicação utilizando nosso driver criado. O nome da rede também pode ser o id da rede
`docker network connect nomeDaRede idDoContainerRunning` 

Assim, podemos isolar os containeres que estiverem rodando na rede nomeDaRede dos outros que estão rodando no adaptador bridge (criado automáticamente)


## Volumes

São os discos que o container usa
aloca pedaços do nosso disco para utilização do container.  

`docker container run -it --mount type=bind,src=/mnt/meu-disco,dst=/mnt/meu-disco,ro node:3 /bin/bash`

`docker volume create nomeDoVolume`
`docker volume rm nomeDoVolume`
`docker volume inspect nomeDoVolume`
`docker volume prune`
`docker container logs`


