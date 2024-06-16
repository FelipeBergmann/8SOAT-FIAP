# Trabalhando com Contextos Delimitados

## Cooperação

 - Cada contexto é feito por um time;
 - Requer disciplina de comunicação

## Modelo de Parceria

- Os times conversam e combinam as integrações entre eles, tudo de forma negociada.

## Kernel Compartilhado

- Contexto compartilhado, que é o Kernel.
  - Ex: CRM que é mantido pelo mesmo time, onde os dois colaboram no mesmo código.
- Este modelo é a exceção
- :Warning: Tomar cuidado para não criar duplicação de código

## Modelo Cliente Fornecedor
- Contextos dos times desenvolvidos separadamente;
  - Há alguma dependência por conta de algum serviço
  - Os times têm o poder de decidir como querem integrar
- Fornecedor (upstream) é o time que provê o serviço
- Cliente (downstream) é o time que o consome
- Conformista: temos que nos conformar com o formato que o fornecedor disponibiliza e adequar à nossa solução

### Camada Anti Corrupção (ACL)

No DDD pensamos nesta camada como uma barreira para proteger o cliente das alterações do fornecedor. Então, ela fica entre a integração cliente e serviço do fornecedor, fazendo a tradução do que o fornecedor entrega para o cliente. Mantendo um único ponto de alteração caso o fornecedor imponha alguma mudança, assim, o cliente não é afetado.

### Serviço de Host Aberto (OHS)

É uma interface disponibilizada pelo fornecedor de integração para expor os serviços para o cliente não precise se adequar, assim o cliente pode se integrar com uma camada padronizada.
Isto ajuda o fornecedor a separar os seus desenvolvimentos mais internos dos clientes, assim ele pode evoluir os serviços sem se preocupar em quebrar o cliente.

### Linguagem Publicada (PL)

No OHS a linguagem é do fornecedor, neste caso o fornecedor cria instâncias customizadas para o cliente utilizando a linguagem que o cliente usa.

### Caminhos Separados

Para times que não conseguem se entender ou se comunicar, como no modelo parceria, neste cenário os times não se integram. Outros motivos:
- Custo de integração é muito maior que o de criar uma solução interna
- Não tem sentido expor o serviço a outros contextos

## Modelo Grande Bola de Lama (BBM)

Este modelo (Big Ball of Mud) é indicado para sistemas muito grandes e que não tem contextos bem definidos e são inconsistentes. Acontece muito em sistemas legados.
As recomendações são:
- Desenhe uma linha em torno e chame de Grande Bola de Lama;
- Não tente aplicar nenhum método sofisticado de modelagem;
- Cuidado, pois esta bola de lama pode contaminar outros contextos.

## Mapa de Contexto

É um mapa que materializa visualmente todos os nossos contextos delimitados e como eles se integram. Desta forma, temos uma visão estratégica do todo.
O mapa conterá:

- Contextos delimitados
- Times
- Como os contextos se relacionam
- Camadas de: Serviços, ACL, OHS, PL, Fornecedores (upstream) e clientes (downstream)

**Esta documentação é viva, sempre será atualizada.**