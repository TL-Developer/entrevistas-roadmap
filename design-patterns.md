# Perguntas Técnicas – Alguns Design Patterns Clássicos e sua Importância

## Padrões Criacionais
- O que é o padrão **Singleton**? Quais são suas vantagens e desvantagens?
- Explique o padrão **Factory Method** e como ele facilita a criação de objetos.
- Qual a diferença entre **Factory Method** e **Abstract Factory**?
- Quando utilizar o padrão **Builder** e qual problema ele resolve?

## Padrões Estruturais
- O que é o padrão **Adapter** e em que situações ele é útil?
- Explique o padrão **Decorator** e como ele pode ajudar a adicionar funcionalidades dinamicamente.
- O que o padrão **Facade** oferece em termos de simplificação de sistemas complexos?
- Como o padrão **Proxy** pode ser utilizado para controlar acesso a objetos?

## Padrões Comportamentais
- O que é o padrão **Observer**? Onde ele é aplicado com frequência?
- Explique o padrão **Strategy** e como ele promove flexibilidade no código.
- Como o padrão **Command** permite desacoplar o emissor e o receptor de uma ação?
- Qual a importância do padrão **Template Method** para definir passos de algoritmos?

## Importância Geral dos Design Patterns
- Por que é importante conhecer e aplicar design patterns no desenvolvimento de software?
- Como os design patterns ajudam a melhorar a manutenção e extensibilidade do código?
- Você já enfrentou problemas que foram resolvidos pela aplicação de algum desses padrões? Pode descrever?
- Como design patterns influenciam a comunicação entre membros de uma equipe de desenvolvimento?

## Aplicação Prática e Desafios
- Quais padrões você utiliza com mais frequência no seu dia a dia? Por quê?
- Quais desafios você já enfrentou ao aplicar design patterns em projetos reais?
- Como evitar o uso excessivo ou incorreto de design patterns, que pode levar a código excessivamente complexo?


# Perguntas Técnicas – Princípios YAGNI, DRY e Lei de Demeter

## YAGNI (You Aren’t Gonna Need It)
- O que significa o princípio YAGNI e qual seu objetivo no desenvolvimento de software?
- Quais os riscos de não seguir o princípio YAGNI em um projeto?
- Como o YAGNI impacta a produtividade e a manutenção do código?
- Pode citar um exemplo onde aplicar YAGNI evitou complexidade desnecessária?
- Como equilibrar YAGNI com a necessidade de um design que permita futuras extensões?

## DRY (Don't Repeat Yourself)
- Explique o princípio DRY e por que ele é importante.
- Quais são as consequências de violar o princípio DRY?
- Como identificar duplicações de código que não são óbvias?
- Você pode citar técnicas ou padrões que ajudam a aplicar DRY?
- Quais cuidados tomar para não exagerar na abstração ao aplicar DRY?

## Lei de Demeter (Principle of Least Knowledge)
- O que é a Lei de Demeter e qual problema ela busca solucionar?
- Como a Lei de Demeter influencia o acoplamento entre classes ou módulos?
- Pode dar um exemplo prático de código que viola a Lei de Demeter?
- Quais estratégias você usa para garantir que seu código respeite a Lei de Demeter?
- Como a aplicação da Lei de Demeter pode melhorar a testabilidade do código?

## Relacionamento entre os Princípios
- Como esses três princípios (YAGNI, DRY, Lei de Demeter) se complementam no desenvolvimento de software?
- Você já enfrentou situações em que esses princípios entraram em conflito? Como resolveu?
- Como esses princípios influenciam a escrita de código limpo e manutenível?


# Perguntas Técnicas – Clean Code

## Conceitos e Importância
- O que significa escrever **clean code** e por que isso é importante?
- Quais são os principais benefícios de manter o código limpo em projetos de software?
- Você conhece o livro “Clean Code” de Robert C. Martin? Quais ensinamentos você aplica no dia a dia?

## Nomenclatura e Legibilidade
- Quais critérios você usa para nomear variáveis, funções e classes?
- Como evitar nomes ambíguos e pouco claros?
- Qual a importância da legibilidade em relação à performance?

## Estrutura e Organização
- Como você organiza funções e classes para manter o código limpo?
- Quais práticas ajudam a reduzir o tamanho de funções e métodos?
- O que você pensa sobre comentários no código? Quando eles são necessários?

## Princípios e Padrões
- Como o princípio **Single Responsibility Principle (SRP)** ajuda a manter o código limpo?
- Você utiliza padrões de design para melhorar a clareza do código? Pode citar alguns exemplos?
- Como evitar código duplicado (DRY) e manter a simplicidade?

## Testabilidade e Refatoração
- Como o clean code impacta a testabilidade do software?
- Com que frequência você pratica refatoração no seu código? Como decide quando refatorar?
- Pode citar um exemplo onde uma refatoração melhorou significativamente a qualidade do código?

## Erros Comuns e Desafios
- Quais são os erros mais comuns que você já viu em código que não é limpo?
- Como lidar com pressão por prazos apertados sem comprometer a qualidade do código?
- Qual foi seu maior desafio em manter o código limpo em projetos grandes?

## Ferramentas e Processos
- Quais ferramentas você usa para ajudar a manter a qualidade do código? (ex.: linters, formatadores, análise estática)
- Como o code review contribui para o clean code?
- Você já utilizou pair programming ou mob programming para melhorar a qualidade do código?


# Perguntas Técnicas – Princípios SOLID

## Conceitos Gerais
- O que significa o acrônimo SOLID e por que esses princípios são importantes?
- Qual a relação dos princípios SOLID com a manutenção e escalabilidade do código?

## Single Responsibility Principle (SRP)
- O que diz o princípio de responsabilidade única?
- Por que é importante que uma classe tenha apenas uma razão para mudar?
- Você pode dar um exemplo prático de violação do SRP e como corrigiu?

## Open/Closed Principle (OCP)
- Explique o princípio aberto/fechado.
- Como garantir que uma classe seja aberta para extensão, mas fechada para modificação?
- Quais padrões de design ajudam a aplicar o OCP?

## Liskov Substitution Principle (LSP)
- O que é o princípio da substituição de Liskov?
- Por que quebrar o LSP pode causar problemas em sistemas orientados a objetos?
- Pode citar um exemplo onde violar o LSP causou bugs ou falhas?

## Interface Segregation Principle (ISP)
- O que significa o princípio da segregação de interfaces?
- Quais são os problemas causados por interfaces “gordas”?
- Como você aplicaria o ISP em uma API pública?

## Dependency Inversion Principle (DIP)
- Explique o princípio da inversão de dependência.
- Qual a diferença entre dependência em abstrações e em implementações concretas?
- Como frameworks de injeção de dependência ajudam a aplicar o DIP?

## Aplicação Prática
- Você já trabalhou em um projeto que melhorou após aplicar SOLID? Conte como.
- Quais são os desafios mais comuns ao tentar aplicar SOLID em projetos legados?
- Como o SOLID se relaciona com testes automatizados?
