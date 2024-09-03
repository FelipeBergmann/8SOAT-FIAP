# Arquitetura Hexagonal

Separação de Conceitos (separation of concerns): modularizar de forma que resolva um único problema

Modularizar em três áreas distintas e isoladas:

Centro do hexagono
Lado superior esquerdo do hexagono
Lado inferior direito do hexagono

Reusabilidade de código
alta coesão
baixo acoplamento
independência de tecnologia

## Centro do Hexagono

Temos o motivo do nosso software existir, chamamos de core.

## Fora do Hexagono

Temos os adaptadores, que permitem que as tecnologias que estão fora do centro cheguem no centro sem contaminá-lo.

## Portas e Adaptadores

Cada lado do hexagono representa o mesmo que uma porta e os objetos entre a porta e o centro são adaptadores.
Porta: Conceito lógico que define um ponto de entrada e saída de uma aplicação.

De acordo com o prof Marco Tulio Valente, no livro Engenharia de Software Moderna, existem 2 tipos de portas:

> Entrada: interfaces para comunicação de fora para dentro. Quando uma classe externa precisa chamar uma classe interna 
> Saída: interfaces para comunicação de dentro para fora. Quando uma classe do core precisa chamar um método de uma classe externa. Estas portas declaram os serviços requeridos pelo sistema - serviços do mundo externo, que são necessários para o funcionamento do interno. Ex: comunicação com um banco de dados.

Estas portas independem de tecnologia, por isto estão do lado interno (mas não no centro).
Já os serviços externos estão ligados a uma tecnologia como: Http, gRPC ou GraphQL, Bancos de dados como SQL ou NoSql...
Os serviços externos conseguem se comunicar com o centro do hexagono por meio dos adaptadores.

Ou seja, a função de um adaptador é implementar uma conexão entre uma porta e serviços externos.

Devemos ter pelo menos 2 adaptadores para uma porta: um para a implementação real e outra para teste. Ex: serviço de cache: um adaptador direciona para o serviço real (redis e etc) e outro para um cache em memória.

## Atores

Fora do hexagono temos qualquer coisa que interaja com o sistema interno. Estas coisas podem ser seres humanos, dispositivo de hardware ou software, estes são os atores.
Os atores podem ser condutores ou conduzidos:

- Condutores: Recebem chamadas vindas de fora do sistema. Ex: requisição HTTP
- Conduzidos: Recebem chamadas vindas de dentro do sistema e a direcionam para um sistema externo. Ex: envio de smtp, comunicação com banco de dados e etc.

Os condutores ficam do lado esquerdo do hexagono, já os conduzidos do lado direito.

## Fluxo de interação

1. Solicitação recebida pelo adaptador externo, este envia a adapta e envia a solicitação para uma porta de entrada
2. a porta executa a lógica de negócio e envia a resposta para outro adaptador externo
3. O adaptador externo adapta e envia a resposta para a interface externa que originou a solicitação
   
Neste cenário temos um problema, o centro depende do ator conduzido.
Para resolver vamos usar o princípio de inversão de controle (IoC)

## Testes

Em algumas abordagens é dificil testar tudo conforme a pirâmide de testes: E2E, integração, unidade (do topo à base respectivamente).
O foco desta arquitetura é isolar toda a lógica da aplicação no centro do hexagono sem dependência de outras tecnologias, tornando-a mais fácil de ser testada


