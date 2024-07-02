# Segurança de Containerês

## Docker hub

### Imagens Confiáveis
Sempre podemos filtrar por:
- Docker Official Image: são imagens oficiais do docker, possuem um alto nível de credibilidade
- Verified Publishers: Empresas que são verificadas pela Docker Hub
- Sponsored OSS: São imagens que são patrocinadas por serem open source

> Sem nenhuma destas 3 flags, ficamos expostos a imagens que podem conter scripts maliciosos

Podemos habilitar em nosso ambiente a configuração a seguir para que só seja feito download de imagens com um dos selos de segurança: ```export DOCKER_CONTANTE_TRUST=1```

### Atualizações de Imagens

A cada novo release de imagens é comum que além de melhorias ela tenha correções de vulnerabilidades. Por isto, é importante manter as versões sempre atualizadas.

### Variáveis de ambiente

Onde podemos salvar nossas variáveis com valores sensíveis para serem recuperadas no momento de montar a imagem, geralmente em um pipeline de CD.

Exemplos: Docker Secrets (docker hub), secret manager (aws), key vault (azure).

As variáveis de ambiente configuradas utilizando as camadas de ARG e ENV potencialmente poderiam ser expostas ao ter acesso ao console do container em execução.

### Usuário/Root

Utilizar o usuário root na imagem para executar a aplicação deixa em aberto o acesso total a todos os componentes do SO.
Podemos resolver isto criando usuários com mais restrições de acesso:

```bash
RUN adduser john

USER john
```

A partir da camada USER todos os comandos serão executados pelo usuário ```john```.

> Quando não configuramos nenhum usuário, todos os comandos serão sempre executados com o usuário root

### Ferramenta de análise de vulnerabilidades

Trivy: é uma plataforma open source para análise de vulnerabilidades de imagens, sistemas de arquivos, repositórios git, VMI, kubernetes e aws
O escaneamento do Trivy pode encontrar: pacotes e dependências de software em uso (SBOM), vulnerabilidades conhecidas, problemas em IaC e configurações incorretas, informações sensíveis e segredos e licenças de software.

[Documentação](https://aquasecurity.github.io/trivy)

Utilização:

Download do binário:
```bash
wget https://github.com/aquasecurity/trivy/releases/download/v0.48.0/trivy_0.48.0_Linux-64bit.tar.gz && tar -xzf trivy_0.48.0_Linux-64bit.tar.gz
```

Movendo para o binário do linux:
```bash
sudo mv trivy  /usr/local/bin/
```

Verificando a instalação:
```bash
trivy version
```

Executando a análise de uma imagem:

```bash
trivy image nome-da-img:tag
```

será retornada uma lista com diversas vulnerabilidades e detecções sobre a imagem, como o SO utilizado.
Desta forma, as vulnerabilidades que são conhecidas podem ser tratadas com a sugestão de correção indicada na URL do relatório.


| Flags | Efeito |
|-------|--------|
|```severity```| filtra por severidade vulnerabilidade|
