# Boas Práticas

## Imagens
> Buscar utilizar imagens que tem os menores tamanhos e que deêm suporte a todas as funcionalidades que o app precisa
> Desta forma, além de otimizar os downloads e uploads, estamos reduzindo a superfície de vulnerabilidades

## Variáveis de Ambiente

Uma das formas que podemos aumentar a segurança é utilizar a passagem de argumentos durante o docker build.

No Dockerfile:
```bash
ARG MINHA_VARIAVEL
ENV VARIAVEL_DE_AMBIENTE=$MINHA_VARIAVEL
```

Passamos o argumento após a flag ```--build-arg```

```docker build -t node-app:arg --build-arg MINHA_VARIAVEL=valor```

## Logs

Para ajudar na detecção de erros, podemos analisar os logs de saída de um container:

```docker container logs {id_do_container}```

## Limpeza de disco

Por vezes acumulamos muitos containeres em nosso disco, para excluí-las, podemos utilizar o comando ```docker container prune``` que todas os containeres que não estão em execução serão excluídos.

Para remover as imagens, podemos utilizar os comandos:
```docker image ls``` para obter a lista de imagens e seus Ids
```docker image rm {id_da_image}``` ou ```docker image rm -f {id_da_image}``` para forçar a exclusão.

## Artigos
[Boas Práticas - Gaspar Barancelli](https://www.gasparbarancelli.com/post/boas-praticas-para-criar-imagens-docker-eficientes-seguras-e-escalaveis)