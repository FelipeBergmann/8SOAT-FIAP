# Arquitetura Limpa (Clean Architecture)

## Introdução
- **Criador:** Robert C. Martin, também conhecido como "Uncle Bob".
- **Conceito:** O termo "limpo" (clean) significa claro, organizado e objetivo. A ideia não é sugerir que outras arquiteturas são "sujas", mas sim enfatizar a clareza e a objetividade no código.
- **Objetivo:** Aumentar a qualidade do código, facilitando a manutenção e evitando problemas para o desenvolvedor ao resolver os problemas do cliente.
- **Filosofia:** "Nós lemos mais código do que escrevemos", o que reforça a importância de escrever código claro e organizado.

## Princípios Fundamentais

- **Separação de Responsabilidades:** O código deve ser fragmentado em componentes especializados, onde cada componente tem uma única responsabilidade.
- **Hierarquia de Componentes:**
- **Arquitetura:** Define como os componentes são utilizados.
- **Componentes:** Representam como o código é organizado.
- **Código:** Detalha o que realmente é feito.

---

## Princípios S.O.L.I.D

### Single Responsibility Principle (SRP):

Cada componente ou classe deve ter apenas uma única razão para mudar, ou seja, uma única responsabilidade.

### Open/Closed Principle (OCP):

Os componentes devem ser fechados para modificação, mas abertos para extensão.


### Liskov Substitution Principle (LSP):

Os componentes podem ser substituídos por seus subtipos sem afetar a execução correta do programa.


### Interface Segregation Principle (ISP):

As interfaces devem ser específicas e focadas, evitando sobrecarga de responsabilidades e implementações desnecessárias.

### Dependency Inversion Principle (DIP):

Os componentes devem depender de abstrações (interfaces) e não de implementações concretas. Isso permite que eles recebam suas dependências já criadas, sem se preocupar com a instância.

---

## Estrutura das Camadas

![clean architecture layers](images/CleanArchitecture.jpg)


Independência das Camadas: Cada camada deve funcionar de forma independente das outras, seguindo sempre um fluxo de fora para dentro.

> Das camadas de nível mais alto (internas) para as de nível mais baixo (internas) em abstração

### Entidades
**Definição:** Elementos centrais que participam dos casos de uso.
**Função:** Representar as regras de negócio e os dados da aplicação.

### Casos de Uso

**Função:** Coordenar as entidades para realizar cenários específicos de uso. Podem se comunicar entre si.

 **Exemplo:** 
 
 ```
 Caso de uso "Iniciar Venda": 
 Cria o vendedor. 
 Cria a venda associada ao vendedor.
 ```

### Serviços e Camadas Externas

**Controllers, Gateways e Presenters:**

**Controller:** Serve como ponto de entrada, chamado por um serviço externo (API, dispositivo, web). Não é o mesmo "controller" do MVC.

**Gateway:** Atua como intermediário entre o banco de dados e os casos de uso, fornecendo os dados necessários.

**Presenter:** Cuida do formato de saída dos dados, preparando-os para a apresentação.

## Decisões de Arquitetura

**Infraestrutura:** Decisões sobre infraestrutura, como armazenamento de dados e tráfego, devem ser mantidas fora do domínio central da aplicação.