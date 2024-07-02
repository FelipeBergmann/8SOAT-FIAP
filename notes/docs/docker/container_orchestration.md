# Orquestração de Contâineres

## Docker Compose file

É um arquivo YAML que define como os contêineres de um aplicativo devem ser configurados e orquestrados, especificando serviços, redes e volumes. Ele facilita a criação e execução de ambientes multi-contêiner de forma simplificada.

- Escrito em YML
  - tomar cuidado com a identação

```yml
version: '3.9'

volumes: 
    mysql_data:{}

services:
  mysql:
    image: mysql:8.0
  volumes:
    - mysql_data:/var/lib/mysql
  restart: always
  environment:
    MYSQL_ROOT_PASSWORD: root
    MYSQL_DATABASE: wordpress
    MYSQL_USER: wordpress
    MYSQL_PASSWORD: wordpress
  
  wordpress:
    depends_on:
      - mysql
    image: wordpress:latest
    port:
      - "80:80"-
    restart: always
    environment:
      WORDPRESS_DB_HOST: mysql:3306
    volumes:
      - ./wordpress:/var/www/html
```

> A exposição de portas no item ```port:``` segue a ordem: portaDockerHost:portaContainer

> No parametro ```restart:``` podemos ter os seguintes valores:
> - no: nunca reinicia
> - on-failure: reinicia quando ocorre alguma falha em um dos serviços
> - always: reinicia sempre
> - unless-stopped: reinicia a menos que seja intencional parar

## Comandos de Partida e Parada
Os comandos a seguir sobem o ambiente descrito no docker compose file e também os param, respectivamente:

```bash
> docker compose up
> docker compose down
```

