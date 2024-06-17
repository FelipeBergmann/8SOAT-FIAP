# Design Tático

## Como o DDD se adapta em camadas
- No geral são 3 camadas: Interface do usuário, aplicação e Domínio
- Na literatura mais recente, Vernon por exemplo, adiciona uma quarta camada: infraestrutura

## Camada de Interface do Usuário
- GUI, CLI, Apis e etc
- Tudo o que faz interface com algum  usuário

## Camada de Aplicação
- Interface de mediação entre Interface de usuário e Domínio
- Não tem regra de negócio e não altera nenhum estado
- Monitora e reporta as mudanças para a camada superior
- Controle de eventos
- Reportes e etc

## Camada de Domínio
- O Coração do Software
- Onde tem as regras e persistências de negócios
- Não tem a comunicação com banco de dados para guardar/alterar dados

## Camada de Infraestrutura
- Base para todas as outras camadas
- Acesso a base de dados
- Facilita a comunicação entre as camadas superiores

# Como estruturar os componentes

## Objetos de Valor
- Reconhecidos por não possuírem identificadores
- São imutáveis
 - Se tiver que mudar, estamos gerando um novo valor
- Mensuram, quantificam ou descrevem algo no domínio


## Entidades
- Um objeto que é identificado por um ID

## Agregados
- Um conjunto de entidades que compartilham a linguagem ubíqua
Ex: Atividade -> Comentário & Anexos & Notas
- Somente o agregado pode mudar o estado de seu contexto. No exemplo anterior, apenas a entidade Atividade poderia alterar uma nota, comentário ou anexos
- O Agregado tem comandos. Uma entidade externa pode passar um comando para o agregado, mas quem o executa é o próprio agregado.
- Agregados interagem entre eles por meio do identificador. Para um agregado referenciar ao outro, adicionamos uma referência nele ao Id do outro. Semelhante à uma FK de um banco relacional

## Serviços de Domínio
- São objetos tratados em separador que trabalham com diversas entidades e agregados sempre que são necessários cálculos, execuções de rotinas e etc.
- Afetam uma entidade mas não são uma regra dela
- Captura eventos de domínio
