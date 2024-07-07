# Introdução à arquitetura de software

Fatores a serem considerados na construção de uma AS:
- requisitos de negócio
- restrições de tempo
- restrições de orçamento

Várias abordagens diferentes podem ser utilizadas, como:
- baseada em camadas
- baseada em componentes
- baseada em serviços

Arquitetar para que o software não precise ser reescrito a cada mudança que seja necessária

Primeiro passo: entrevista com os stakeholders
levantar todos os pontos e entender as dores.

## Arquitetura Limpa

Principais pontos:
- Separação de preocupações
- Responsábilidade única
- Abstração
- Depuração fácil
- Simplicidade

## Design Patterns

3 categorias: criacionais, estruturais e padrões de comportamento

### Criacionais
- Factory:  interface para criar objetos em uma classe base sem especificar as classes concretas
- Builder: separa a criação de um objeto complexo da sua representação
- Singleton: permite apenas uma instancia do obj
- Prototype: permite clonagem de objs

### Estruturais
  
Subdivididos em 3 categorias: adaptação, agregação e composição.

#### Adaptação
- Adapter: objs com interfaces incompatíveis trabalhem juntos
- Bridge: separa abstração da implementação
- Proxy: um obj representante controla outro

#### Agregação
- Composite: compoe objs em estrutura de arvores - hierarquia
- Decorator: responsabilidades adicionais dinamicamente
- Façade: interface simplificada para um conjunto de interfaces complexas

#### Composição
- Flyweight: compartilha partes de objs para economizar memória
- Private class Data: protege integridade de dados adicionando eles em uma class privada

### Padrões Comportamentais

#### De Classe
- Template Method: Define esqueleto do algoritmo que pode ser substituído
- Strategy: define uma família de algorítmos que são intercambiaveis
- State: o obj muda de comportamento conforme seu estado interno muda

#### De Objeto
- Observer: Dependencia 1:N, conforme o 1 muda de estado os outros são notificados e atualizados
- Chain of Responsability: Permite que um obj seja processado em cadeia
- Command: Solicitação como obj, habilita desfazer e refazer

#### De interação
- Interpreter: Interpretador de uma linguagem
- Mediator: define um mediador para diminuir o acoplamento entre objs. Todos se comunicam por meio do mediador
- Visitor: adicione novas operações a um  obj sem modificar os objs

### Arquitetura de Camadas

Divide a construção do software em camadas lógicas, geralmente em pilha, onde as inferiores fornecem serviços para as superiores.
Camadas mais comuns:
- Presentation: Camada de UI, interação com o usuário
- Application: Camada onde temos as lógicas de negócio
- Persist Data: Camada que faz a persistencia de dados
