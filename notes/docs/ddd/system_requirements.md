# Levantamento de Requisitos

## Os Quatro Grandes Riscos
Frentes que precisamos analisar antes de lançar um produto. Os quatro listados são:
- Risco de Valor
- Risco de Negócio
- Risco de Usabilidade
- Risco Técnico

## Risco de Valor

Risco do usuário não precisar de fato do seu produto. Se questione:
- O produto gera valor o suficiente a ponto do usuário pagar por ele?
- Quais outras formas que o usuário tem para resolver o mesmo problema?

## Risco de Negócio
Está ligado ao ponto de que se o produto faz sentido no planjeamento estratégico da empresa. Se o produto pode gerar algum desgaste na empresa na esfera reputacional, legal ou financeiro.

## Risco de Usabilidade
Está ligado com a dificuldade do usuário em utilizar o sistema (alô analistas de UX).

## Risco Técnico
Está ligado ao risco de não ter recursos de profissionais ou tecnologias para implementar o produto

## Como Mitigar os Riscos

Antes de começar a implementar o produto, passamos pela etapa de descobrimento, que fará o estudo de mercado da solução.

Podemos então criar uma esteira de desenvolvimento inicialmente dividida por duas áreas: Upstream e Downstream - Planjamento e Desenvolvimento de demandas, respectivamente.
Sugestão de colunas:
Planejamento:
- backlog
- levantamento de requisitos
- refinamento técnico
- quebras técnicas e estimativas
- pronto para desenvolvimento
- prioridades (esta coluna é divida entre as duas áreas, pois é a passagem de área)

Desenvolvimento:
- em andamento
- code review
- testing
- fixing uat
- Pronto para deploy
- done

O objetivo do levantamento de requisitos é mitigar problemas como:

- Demanda incompreendida pelo profissional que a desenvolverá
- Imprevisibilidade no desenvolvimento
- Mitigar bugs, débitos técnicos e alto grau de dependência de outros sistemas

## Especificação do Board

| Coluna | Área | Descrição |
|--------|------|-----------|
| backlog | Planejamento | Onde ficam todas as idéias que ainda não estão maduras |
| levantamento de requisitos | Planejamento | Explorar e detalhar o que deve ser entregue. Personas e etc |
| refinamento técnico | Planejamento | Explorar soluções tecnológicas para cumprir o objetivo  |
| quebras técnicas e estimativas | Planejamento | Separar as demandas para que elas sejam simples de executar e sem depender umas das outras |
| pronto para desenvolvimento  | Planejamento | Onde estamos preparados para desenvolver |
| prioridades | Planejamento | |
| em andamento | Desenvolvimento | |
| code review | Desenvolvimento | |
| testing | Desenvolvimento | |
| fixing uat | Desenvolvimento | |
| Pronto para deploy | Desenvolvimento | |
| done | Desenvolvimento | |

## Documentação dos Requisitos

### Persona
Qualquer usuário de um produto.
É importante entender o perfil da persona para poder projetar de forma correta o comportamento do produto.

### Problema
A dor do usuário que será resolvida. Deve ser bem claro quanto ao fluxo atual do usuário e como ele resolve ele atualmente.

### Mapeamento do fluxo
É importante mapear o fluxo atual, apontando por etapas as personas que a executam e qual o sistema. Desta forma, podemos propor soluções às etapas mais exaustivas.

### Objetivo
Descrever os objetivos que possam ser medidos

### Requisitos da solução
Aqui mapeamos os requisitos funcionais.

### Requisitos não funcionais
Aqui mapeamos os requisitos que não são funcionalidades mas que são essenciais para o sucesso do produto. Ex: Segurança.

## Upstream

É o conceito da etapa de mapeamento e descoberta do produto.

## Downstream

Consiste do desenvolvimento (implementação) própriamente dita até a entrega (done)
