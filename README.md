# 8SOAT-FIAP

## O que é isto?
Este é uma espécie de bucket para infos do curso de arquitetura de software na fiap

## Notes
## Comandos

O projeto de notes roda usando mkdocs. 

Para rodar o projeto é necessário ter instalado o mkdocs. O método de instalação recomendado é via python, rodando o comando:

`pip install mkdocs`

por hora, para realizar o deploy de uma nova versão é necessário rodar:
`mkdocs build` para gerar os arquivos estáticos do site que serão publicados.

Para outros comandos
* `mkdocs serve` - Inicia o serviço localmente (com live-reloading).
* 
* `mkdocs build` - Constrói o site.
* `mkdocs -h` - Escreve os comandos de ajuda.

## Layout do Projeto

    mkdocs.yml    # Arquivo de configuração
    docs/
        index.md  # Página Inicial
        ...       # Outras páginas