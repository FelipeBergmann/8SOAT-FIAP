# Event Storming
- Não pertence à obra original; Foi criada posteriormente para auxiliar
- Atividade lúdica com um grupo de pessoas bem diversas, como:
  - Domain Experts
  - Ouvintes
  - Facilitador
- Quanto ao material: Post-It ou softwares como Miro ou FigJam

## Como Aplicar

Separar os cards por cores e título:
- Eventos
- Comandos
- Políticas
- Modelos de Leitura
- Sistemas Externos
- Ponto De Atenção
- Ator
- Agregados
- Eventos Pivotais

Tudo começa com um brainstorming...

## Eventos
Representam os acontecimentos do contexto e são sempre escritos com o verbo no passado.
Ligações: Entre eventos

## Comandos
Representam os gatilhos de ações e são escritos com o verbo no presente.
Ligações: Antecede um evento

## Políticas
Comandos que são executados por automações do sistema. As políticas podem ter uma condição para serem disparadas.
Ligações: Antes, entre ou após um evento

**Exemplo:**
Professor -> CMD Cria Atividade -> EV Atividade Criada -> Pol Notificar o Aluno de nova Atividade -> CMD Envia Notificação -> Notificação Enviada ao Aluno -> PA como o aluno é notificado?

## Modelos de Leitura
Representa a interface que o usuário irá realizar/ver o comando e/ou tomar uma decisão.
Ligações: Antes de comandos

## Pontos de Atenção
Representam as dúvidas que ainda temos sobre como um evento ocorre
Ligações: Em eventos

## Ator
Pessoa quem realiza um comando
Ligações: Comandos

## Agregados
Representam as entidades agregadoras que irão agrupar os eventos e outras entidades
Ligações: Eventos, Comandos e etc

## Eventos Pivotais
Indicam uma mudança de fase ou de contexto na linha do tempo. São importantes para indicar as limitações dentro de um contexto e ajudam a identificar os agregados
Ligações: Linha do tempo

**Exemplo:**

| Evento Pivotal | Descrição |
|----------------|-----------|
| A | Eventos relacionados à entrega da atividade pelo aluno |
| B | Eventos Relacionados a correção da atividade pelo professor |
| C | Eventos Relacionados aplicar a nota |

## Sistemas Externos

Representa um sistema que está fora do domínio (em outro contexto delimitado)
Ligações: Eventos e comandos

## Como Facilitar o Event Storming

1. Todos criam os cartões com os eventos (brainstorming)
2. Os cartões de eventos são refinados, removendo os duplicados
3. Os cartões de eventos são colocados em ordem sequencial e ligados por flechas, apontando a direção do fluxo
4. [3.1.] Qualquer caminho alternativo é indicado por uma bifurcação. Dica: Alterar a cor/traçado das flechas nos caminhos alternativos para facilitar a leitura
5. Em uma nova leitura dos eventos, adicionar os cartões de pontos de atenção, destacando as dúvidas que ainda temos
6. Separar os contextos com os Eventos Pivotais
7. Escrever os comandos que fazem com que os eventos aconteçam, adicionando-os anteriormente a cada evento
8. Adicione os cartões de Política: eventos que são executados por outros sistemas e não um ator
9. Inclua os cartões de modelo de leitura
10. Inclua os cartões de sistema externo
11. Monte os cartões de agregados, adicionando todos os eventos e comandos aos agregados
