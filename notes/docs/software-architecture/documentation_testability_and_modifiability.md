# Documentação, Testabilidade e Modificabilidade

## Documentação

A documentação de como utilizar o sistema diminui a quantidade de dúvidas do usuário. Deve ser feita da forma que melhor se aplicar ao sistema, por exemplo: texto, imagens, slides ou videos.

Tão importante quanto a documentação para o usuário final, é a documentação do desenvolvimento e arquitetura. Ela fornece ao desenvolvedor o caminho e conceitos que foram considerados para as tomadas de decisões arquiteturais.
Esta documentação é feita em conjunto pelo time e envolve decisões até o mais baixo nível. Neste momento procuramos responder as seguintes perguntas: 
- Qual o problema a ser resolvido
- Qual é a solução proposta
- Qual é o modelo de negócio

Avançamos então para a documentação de infraestrutura, onde iremos decidir onde o projeto será implantado e etc.

### Swagger e Redoc

São documentações a nível de web API. O documento gerado é baseado na especificação OpenApi 3.0 ([especificação no github](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.3.md])). O Redoc é uma outra ferramenta de especificação que gera uma página baseada na especificação gerada pelo swagger.


## Test Driven Development

O TDD visa escrever o código da aplicação partindo dos testes.
Babysteps: dar sempre pequenos passos em direção à solução, garante que os testes quebrem nos momentos corretos para que você possa validar seu funcionamento (evitar falsos positivos) e ir incrementando a solução conforme necessário.

1. Escrever os testes que irão falhar
2. Faça o código funcionar
3. Elimine as redundâncias



