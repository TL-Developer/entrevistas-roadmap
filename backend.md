# Perguntas Técnicas – BFF (Backend for Frontend)

## Conceitos Fundamentais
- O que é BFF (Backend for Frontend) e qual problema esse padrão de arquitetura resolve?
- Qual a diferença entre BFF e uma API tradicional REST ou GraphQL?
- Em quais situações faz sentido usar BFF em uma arquitetura de software?

## Benefícios e Desvantagens
- Quais são os principais benefícios de implementar um BFF?
  - (Ex.: Redução de overfetching, otimização de payloads, adaptação para diferentes frontends, segurança)
- Quais são os principais desafios ou desvantagens de manter múltiplos BFFs?
- BFF pode gerar acoplamento excessivo? Como mitigar isso?

## Arquitetura e Implementação
- Como você organiza a arquitetura de um BFF?
- Quais são as responsabilidades que pertencem ao BFF e quais devem permanecer nos serviços de backend?
- O BFF deve conter regras de negócio? Por quê?
- Você já implementou BFF usando quais tecnologias ou linguagens? (ex.: Node.js, NestJS, .NET, Go, Python)

## Performance e Escalabilidade
- Quais práticas você adota para garantir que o BFF tenha boa performance?
- Como você gerencia o cache em um BFF? (HTTP Cache, Redis, CDN, etc.)
- O que fazer quando o BFF se torna um gargalo de performance?

## Comunicação e Integrações
- Quais padrões de comunicação entre o BFF e os microserviços você já utilizou? (REST, gRPC, GraphQL, Event-driven)
- Como o BFF pode ser utilizado para **orquestrar** chamadas a múltiplos microserviços?
- Como você lida com erros em chamadas paralelas feitas pelo BFF?

## Segurança e Autenticação
- Como o BFF pode ajudar na centralização de autenticação e autorização?
- Qual sua abordagem para gerenciamento de tokens (JWT, OAuth) no contexto do BFF?
- Quais práticas de segurança você considera essenciais na cons


# Perguntas Técnicas – .NET e Ciclo de Vida

## Conceitos Fundamentais do .NET
- O que é a plataforma .NET e quais são suas principais características?
- Qual a diferença entre .NET Framework, .NET Core e .NET (atual)?
- Quais linguagens são suportadas pela plataforma .NET? Qual você mais utiliza?
- O que é o Common Language Runtime (CLR) e qual seu papel?

## Ciclo de Vida de uma Aplicação .NET
- Como funciona o ciclo de vida de uma aplicação ASP.NET (startup, request pipeline, shutdown)?
- Quais são os métodos principais do ciclo de vida no `Startup.cs`? Para que servem `ConfigureServices()` e `Configure()`?
- Como funciona o ciclo de vida de uma aplicação console .NET?
- O que é o **Middleware Pipeline** no ASP.NET e como ele funciona durante o ciclo de uma requisição?

## Gerenciamento de Memória e Garbage Collector
- Como o .NET gerencia a memória de objetos durante o ciclo de vida de uma aplicação?
- Explique como funciona o **Garbage Collector (GC)** no .NET. Quais são suas gerações?
- O que são objetos gerenciados e não gerenciados no .NET?
- Como evitar vazamentos de memória em aplicações .NET?

## Dependency Injection e Ciclo de Vida dos Serviços
- Quais são os ciclos de vida disponíveis no container de injeção de dependência no .NET? (Singleton, Scoped, Transient)
- Dê um exemplo prático de quando utilizar `Scoped` e quando utilizar `Singleton`.
- Como funciona a injeção de dependências no ASP.NET?

## Pipeline de Request no ASP.NET
- O que acontece internamente quando uma requisição HTTP chega no ASP.NET?
- O que são Middlewares e como a ordem


# Perguntas Técnicas – Injeção de Dependência vs Inversão de Dependências

## Conceitos Fundamentais
- O que é o princípio de **Inversão de Dependências (DIP)** no contexto dos princípios SOLID?
- O que é **Injeção de Dependência (DI)**? Ela é um padrão ou um princípio?
- Qual a relação entre **DIP** e **DI**? São a mesma coisa? Explique.

## Diferenças Conceituais
- Inversão de Dependências é um princípio arquitetural. Injeção de Dependências é um meio de aplicá-lo. Você concorda? Justifique.
- É possível aplicar o princípio de **Inversão de Dependências (DIP)** sem usar um contêiner de Injeção de Dependências? Como seria?
- A Injeção de Dependência resolve quais problemas comuns na arquitetura de software?

## Tipos de Injeção de Dependência
- Quais são os tipos de Injeção de Dependência? (Ex.: via construtor, via setter, via interface, via método)
- Em quais cenários você escolheria injeção via construtor e quando preferiria via setter?

## Exemplos e Aplicações
- Dê um exemplo prático de aplicação do princípio de Inversão de Dependências (DIP).
- Como um framework como ASP.NET implementa o padrão de Injeção de Dependência na prática?
- Como a aplicação incorreta de DI pode gerar um **Service Locator antipattern**?

## Boas Práticas e Armadilhas
- Quais os riscos ou malefícios de um uso exagerado ou incorreto de Injeção de Dependência?
- Como garantir que o uso de DI não gere acoplamento excessivo ao container?
- Já enfrentou problemas de performance, ciclo de vida ou complexidade por uso inadequado de DI? Como resolveu?

## Avançado
- Como o DIP ajuda a criar código mais testável e desacoplado?
- Explique como o DIP permite que **módulos de alto nível não dependam de módulos de baixo nível, mas ambos dependam de abstrações**.
- Você consegue citar algum exemplo prático em que a falta de DIP dificultou a manutenção de um projeto?


# Perguntas Técnicas – Banco de Dados (SQL, NoSQL e Grafos)

## Banco de Dados Relacional (SQL)
- O que é um banco de dados relacional? Cite alguns exemplos.
- O que é normalização e quais são suas vantagens e desvantagens?
- Quando é recomendável desnormalizar uma base de dados?
- Explique a diferença entre **INNER JOIN**, **LEFT JOIN**, **RIGHT JOIN** e **FULL JOIN**.
- O que são índices? Como eles impactam na performance das consultas?
- Quais as diferenças entre **PRIMARY KEY**, **FOREIGN KEY** e **UNIQUE**?
- O que são transações ACID? Por que são importantes?
- Como funciona o mecanismo de **lock** em bancos relacionais? Já teve problemas de deadlock?
- O que são **views** e **stored procedures**? Quais os prós e contras de utilizá-los?
- Como funciona um **EXPLAIN PLAN** (ou **EXPLAIN ANALYZE**) e como você o utiliza para otimizar queries?

## Banco de Dados Não Relacional (NoSQL)
- O que é NoSQL e quais são suas principais categorias? (Documentos, Chave-Valor, Colunar e Grafos)
- Qual a diferença entre bancos relacionais e bancos NoSQL?
- Em quais cenários você optaria por um banco NoSQL em vez de um SQL?
- O que é a consistência eventual e como ela se aplica em bancos NoSQL distribuídos?
- Explique como funciona a modelagem de dados em bancos de documentos como MongoDB.
- Quais são as vantagens de bancos chave-valor como Redis ou DynamoDB?
- Como bancos NoSQL lidam com escalabilidade horizontal?
- Quais as limitações ou riscos de utilizar bancos NoSQL?

## Banco de Dados de Grafos
- O que é um banco de dados de grafos? Cite alguns exemplos (ex.: Neo4j, ArangoDB, Amazon Neptune).
- Quais são os componentes básicos de um grafo? (Nodos, Arestas, Propriedades)
- Em que situações um banco de grafos é mais adequado do que SQL ou NoSQL de documentos?
- Como funcionam as consultas em grafos? Já utilizou linguagens como **Cypher** ou **Gremlin**?
- Quais são os desafios em termos de performance e escalabilidade em bancos de grafos?
- Cite exemplos de aplicações reais que se beneficiam fortemente de banco de grafos. (Ex.: redes sociais, motores de recomendação, detecção de fraudes)

## Modelagem e Arquitetura de Dados
- Quais são os principais critérios que você considera na escolha entre SQL, NoSQL e Grafos para um projeto?
- Como você lida com migração de dados entre diferentes modelos (relacional para NoSQL, por exemplo)?
- Quais são os impactos de uma modelagem incorreta no desempenho de um sistema?
- Como você lida com versionamento de esquemas em bases SQL e NoSQL?

## Performance, Escalabilidade e Observabilidade
- Quais técnicas você usa para melhorar a performance de consultas SQL? (ex.: índices, particionamento, caching)
- Já trabalhou com sharding? Como ele funciona?
- Quais são os riscos de hotspots em bancos NoSQL e como mitigá-los?
- Como você monitora performance, latência e integridade de um banco de dados em produção?

## Segurança e Backup
- Quais são as melhores práticas para segurança em bancos de dados? (ex.: criptografia, roles, autenticação)
- Como você implementa estratégias de backup e recuperação de desastres?
- Quais são os impactos de alta disponibilidade (HA) e replicação no design de bancos de dados?


# Perguntas Técnicas – Ferramentas de Testes no .NET

## Testes Unitários
- Quais frameworks você costuma utilizar para testes unitários em .NET? (Ex.: xUnit, NUnit, MSTest)
- Qual a diferença entre xUnit, NUnit e MSTest? Por que você escolheria um em vez de outro?
- Quais ferramentas ou bibliotecas você utiliza para mocks, stubs e fakes? (Ex.: Moq, NSubstitute, FakeItEasy)
- Como você testa exceções, validações e cenários negativos em testes unitários?
- Quais práticas você adota para garantir que seus testes unitários sejam confiáveis e não frágeis?

## Testes Funcionais (Integração e E2E)
- Que ferramentas você utiliza para testes de integração no .NET? (Ex.: TestServer, WebApplicationFactory)
- Você já realizou testes de integração com bancos de dados? Como isola o ambiente?
- Já utilizou ferramentas para testes end-to-end (E2E) como Selenium, Playwright ou Cypress? Como elas se integram com aplicações .NET?
- Como garantir que os testes de integração não sejam flakey e sejam reproduzíveis?

## Testes de Carga e Performance
- Quais ferramentas você utiliza para realizar testes de carga em aplicações .NET? (Ex.: Apache JMeter, k6, Gatling, Azure Load Testing)
- Já utilizou ferramentas específicas do ecossistema .NET, como **NBomber**, para simular carga? Como foi a experiência?
- Quais métricas você observa durante um teste de carga? (ex.: throughput, latency, error rate)
- Como você define o que é um SLA (Service Level Agreement) aceitável após testes de carga?
- Como você detecta gargalos de performance? Que ferramentas utiliza junto aos testes? (ex.: Application Insights, PerfView, dotTrace, JetBrains Rider Profiler)

## Testes Não Funcionais
- Que tipos de testes não funcionais você costuma aplicar em aplicações .NET? (ex.: segurança, escalabilidade, stress, recuperação)
- Que ferramentas você utiliza para testes de segurança? (ex.: OWASP ZAP, Burp Suite, SonarQube, Snyk)
- Como realiza testes de resiliência, como simular falhas de rede, banco ou serviços externos?
- Você já trabalhou com chaos engineering no contexto .NET? Quais ferramentas foram utilizadas? (ex.: Chaos Studio, Gremlin)

## Estratégia e Pipeline
- Como você organiza os testes dentro de um pipeline CI/CD no .NET? (ex.: Azure DevOps, GitHub Actions, GitLab CI)
- Em que fase do pipeline você executa testes unitários, integração e carga? Todos no mesmo pipeline ou separado?
- Já utilizou testes baseados em contrato (Contract Testing)? Com quais ferramentas? (ex.: Pact.NET)

## Boas Práticas
- Quais são, na sua visão, os maiores desafios para manter uma boa cobertura de testes em projetos .NET?
- Como você decide o que testar em unitário, integração e E2E?
- Você tem práticas específicas para garantir que testes de carga e stress sejam parte recorrente dos ciclos de desenvolvimento?



# Perguntas Técnicas – CQRS (Command Query Responsibility Segregation)

## Conceitos Fundamentais
- O que é CQRS e qual problema esse padrão busca resolver?
- Qual a diferença entre CQRS e CRUD tradicional?
- CQRS é um padrão arquitetural ou um padrão de design? Explique.
- CQRS sempre deve ser usado com Event Sourcing? Por quê?

## Separação de Responsabilidades
- Explique a diferença entre **Command** e **Query** no CQRS.
- Como funciona a separação entre os modelos de leitura e escrita?
- Quais são os benefícios práticos de separar leitura e escrita em um sistema?

## Benefícios e Vantagens
- Quais são os principais benefícios de adotar CQRS?
  - (Ex.: escalabilidade, performance, clareza de responsabilidades, modelos otimizados)
- Em que cenários a adoção de CQRS traz ganhos claros?
- Como o CQRS melhora a escalabilidade e a performance de uma aplicação?

## Desvantagens e Desafios
- Quais são os principais desafios ou desvantagens de implementar CQRS?
- Como lidar com a **consistência eventual** que pode surgir com CQRS?
- Quando **não** faz sentido aplicar CQRS?

## Implementação Técnica
- Como você implementaria CQRS em uma aplicação .NET ou Node.js?
- Como é feita a comunicação entre o modelo de escrita e o modelo de leitura?
- Como garantir que as mudanças feitas no Command estejam refletidas na Query (ex.: eventos, sincronização, polling)?
- Quais ferramentas ou frameworks você já utilizou para auxiliar na implementação de CQRS? (ex.: MediatR, Axon, MassTransit, Kafka)

## Integração com Event Sourcing e Mensageria
- Como o CQRS se integra com padrões como Event Sourcing?
- É obrigatório usar mensageria (RabbitMQ, Kafka, etc.) em CQRS? Por quê?
- Como você lida com a orquestração de eventos e a sincronização dos dados entre os modelos?

## Consistência e Performance
- Como você lida com consistência eventual no modelo de leitura?
- Quais técnicas você usa para garantir alta disponibilidade no modelo de Query?
- Como funciona o fallback em caso de falha na propagação dos dados entre Command e Query?

## Escalabilidade e Observabilidade
- Como CQRS ajuda na escalabilidade horizontal de sistemas?
- Quais métricas ou logs são críticos para monitorar uma arquitetura baseada em CQRS?
- Já enfrentou problemas de latência na propagação entre Command e Query? Como resolveu?

## Casos Reais e Boas Práticas
- Já implementou CQRS em algum projeto? Quais desafios enfrentou na prática?
- Em projetos reais, como você decide se implementa CQRS total ou parcial?
- Quais boas práticas você recomenda para quem está começando com CQRS?



# Perguntas Técnicas – Autenticação no .NET e Funcionamento do Token JWT

## Conceitos Fundamentais de Autenticação no .NET
- Quais são os principais métodos de autenticação disponíveis no .NET? (ex.: Cookie, JWT, OAuth, OpenID Connect)
- Como funciona a autenticação baseada em tokens no ASP.NET?
- Quais são os principais componentes envolvidos no pipeline de autenticação do ASP.NET?
- O que são e qual a diferença entre **Authentication** e **Authorization** no .NET?

## Implementação Prática no .NET
- Como configurar a autenticação com JWT no ASP.NET Core?
- Como funciona o middleware `AddAuthentication()` e `AddJwtBearer()` no .NET?
- Quais são os principais claims que você costuma incluir no token?
- Onde e como armazenar os tokens JWT no front-end de forma segura? (ex.: LocalStorage, SessionStorage, HttpOnly Cookies)

## Funcionamento de um Token JWT
- O que é um JWT (JSON Web Token) e como ele é estruturado?
- Explique os três componentes de um token JWT: **Header**, **Payload** e **Signature**.
- Como o JWT garante que o payload não foi alterado?
- O JWT é criptografado? Explique a diferença entre assinatura e criptografia no contexto do JWT.

## Segurança e Boas Práticas
- Quais são os principais riscos de segurança ao trabalhar com JWT? (ex.: token leakage, replay attacks)
- O que é e para que serve o campo **exp (expiration)** dentro do payload?
- Como você faz a renovação de tokens JWT? Utiliza **Refresh Tokens**? Explique como funciona.
- Quais são as boas práticas para proteger APIs que usam JWT?

## Validação e Fluxo
- Como o .NET valida um token JWT recebido em uma requisição?
- Onde é definida a chave de assinatura (HMAC ou RSA) na configuração do backend?
- O que acontece quando um token JWT é inválido ou expirado? Como o middleware lida com isso?

## Integrações e Cenários Avançados
- Como implementar Single Sign-On (SSO) com OpenID Connect e OAuth no .NET?
- Quais são as diferenças práticas entre usar JWT e utilizar IdentityServer, Auth0, Azure AD ou AWS Cognito?
- Como funciona o fluxo OAuth 2.0 no contexto do .NET?

## Casos Práticos e Desafios
- Já enfrentou problemas relacionados a revogação de JWT? Como resolveu?
- Como implementar logout efetivo em uma arquitetura baseada em JWT?
- Como lidar com múltiplos públicos (audiences) e escopos no mesmo token JWT?



# Perguntas Técnicas – API Gateway e Rate Limiting

## Conceitos Fundamentais de API Gateway
- O que é um **API Gateway** e qual seu papel em uma arquitetura de microsserviços?
- Qual a diferença entre um API Gateway e um Load Balancer?
- Quais são as responsabilidades típicas de um API Gateway?
  - (Ex.: roteamento, autenticação, autorização, rate limiting, transformação de payloads)
- Quais as vantagens de utilizar um API Gateway em comparação com a comunicação direta com microserviços?

## Benefícios e Desvantagens
- Quais são os principais benefícios de usar um API Gateway?
- Quais são os riscos ou desvantagens de centralizar a entrada da aplicação em um API Gateway?
- Já trabalhou com algum problema de gargalo ou ponto único de falha (single point of failure) no API Gateway? Como resolveu?

## Rate Limiting – Conceitos e Benefícios
- O que é **Rate Limiting** e qual problema ele resolve?
- Quais os principais benefícios de aplicar Rate Limiting em APIs?
  - (Ex.: proteção contra DDoS, prevenção de abuso, controle de custos, estabilização dos serviços)
- Qual a diferença entre **Rate Limiting**, **Throttling** e **Quota**?
- Em quais camadas você pode aplicar Rate Limiting? (API Gateway, Service Mesh, Backend)

## Implementação e Estratégias de Rate Limiting
- Quais são os principais algoritmos utilizados para Rate Limiting?
  - (Ex.: Token Bucket, Leaky Bucket, Fixed Window, Sliding Window)
- Como você define as políticas de Rate Limiting? Por IP, por API Key, por usuário, por tenant?
- Como o Rate Limiting lida com ambientes distribuídos e múltiplas instâncias do API Gateway?
- Como comunicar ao cliente que ele foi limitado? (ex.: códigos HTTP 429 e headers como `Retry-After`)

## Ferramentas e Práticas
- Quais ferramentas ou soluções de API Gateway você já utilizou? (Ex.: Kong, NGINX, Amazon API Gateway, Azure API Management, Apigee, Traefik, YARP)
- Como essas ferramentas implementam Rate Limiting e outros controles?
- Já utilizou alguma solução baseada em API Gateway + Service Mesh? (Ex.: Istio, Linkerd)
- Como monitorar e observar a aplicação das regras de Rate Limiting?

## Segurança e Escalabilidade
- Como Rate Limiting contribui para a segurança contra ataques de negação de serviço (DDoS)?
- Quais práticas você adota para garantir que Rate Limiting não impacte negativamente usuários legítimos?
- Como escalar um API Gateway horizontalmente mantendo as políticas de Rate Limiting consistentes?

## Casos Práticos e Desafios
- Já precisou criar exceções em políticas de Rate Limiting? Como implementou isso?
- Como garantir que clientes premium ou internos tenham limites diferentes?
- Quais foram os maiores desafios que você já enfrentou na implementação de Rate Limiting?

# Perguntas Técnicas – Memória (Heap vs Stack) e Garbage Collector no .NET

## Conceitos de Memória: Heap vs Stack
- Qual a diferença entre memória **Heap** e **Stack** no .NET?
- Quais tipos de dados são alocados na Stack e quais vão para a Heap?
- O que é mais rápido, acesso na Stack ou na Heap? Por quê?
- O que acontece quando uma variável local (na Stack) referencia um objeto alocado na Heap?
- Como funciona o ciclo de vida dos dados na Stack? E na Heap?
- Explique o que é um **Stack Overflow** e como ele ocorre.
- É possível otimizar o uso de memória escolhendo entre tipos de valor (**value types**) e tipos de referência (**reference types**)?

## Garbage Collector no .NET – Fundamentos
- O que é o **Garbage Collector (GC)** no .NET e qual sua função?
- Como o GC identifica objetos que podem ser removidos da memória?
- Explique o conceito de **Root Objects** na análise do Garbage Collector.
- O que são os conceitos de **Managed Memory** e **Unmanaged Memory** no .NET?

## Funcionamento do GC no .NET
- Como funciona o modelo de gerações no GC do .NET? O que são **Geração 0**, **Geração 1** e **Geração 2**?
- Por que o .NET utiliza um modelo de gerações para o GC? Quais são os benefícios?
- O que é um **Full Garbage Collection** e quais impactos ele pode ter na performance?
- Como funciona o **Large Object Heap (LOH)** e quando ele é utilizado?

## Impacto na Performance e Otimização
- Como o Garbage Collector pode impactar na performance de uma aplicação .NET?
- Quais práticas ajudam a reduzir o impacto do GC? (Ex.: pooling, span, uso correto de structs)
- O que são objetos **pinned** e como eles afetam o Garbage Collector?
- Como utilizar o `IDisposable` e o padrão **Dispose Pattern** para liberar recursos não gerenciados?

## Diagnóstico e Monitoramento
- Quais ferramentas você usa para analisar consumo de memória e atuação do GC? (Ex.: dotMemory, PerfView, Visual Studio Diagnostic Tools, Application Insights)
- Como interpretar gráficos de alocação de memória e pausas do GC?
- Já lidou com memory leaks em .NET? Como os identificou e solucionou?

## Avançado – Controle Fino de Memória
- O que é o **Server Garbage Collector** e como ele difere do **Workstation GC**?
- Como funciona o **Background GC** no .NET?
- Já utilizou estruturas como **Span<T>**, **Memory<T>** ou **ref struct**? Como elas ajudam a otimizar alocação e reduzir GC?
- Quando faz sentido usar **ValueTask** para otimizar alocação de memória em operações assíncronas?


# Perguntas Técnicas – Pilares da Programação Orientada a Objetos (POO)

## Conceito Geral de POO
- O que é Programação Orientada a Objetos e quais são seus principais benefícios?
- Quais são os quatro pilares da orientação a objetos?
- Na sua opinião, POO é mais sobre código ou sobre modelagem de domínio? Justifique.

## Abstração
- O que é **abstração** em orientação a objetos?
- Como você aplica abstração no seu dia a dia? Dê um exemplo prático.
- Qual a diferença entre abstração e encapsulamento?
- Quando a abstração pode ser levada ao excesso e se tornar prejudicial?

## Encapsulamento
- O que é **encapsulamento** e qual sua importância na POO?
- Como o encapsulamento ajuda na segurança e manutenção do código?
- Explique o uso de modificadores de acesso (`public`, `private`, `protected`, `internal`) no contexto do encapsulamento.
- Você já se deparou com código que não respeita o princípio de encapsulamento? Quais foram as consequências?

## Herança
- O que é **herança** em POO?
- Qual a diferença entre herança e composição? Quando preferir uma sobre a outra?
- Explique os problemas do uso excessivo de herança em arquiteturas complexas.
- O que é herança múltipla? Ela é permitida em C#? Como contornar sua ausência?
- Como a herança se relaciona com o princípio do **aberto/fechado (Open/Closed)** do SOLID?

## Polimorfismo
- O que é **polimorfismo**? E quais os dois tipos principais de polimorfismo?
- Explique a diferença entre **polimorfismo de sobrecarga** (compile-time) e **polimorfismo de sobrescrita** (runtime).
- Como o polimorfismo contribui para a extensibilidade e manutenibilidade do código?
- Dê um exemplo prático de uso de polimorfismo na sua experiência.

## Boas Práticas e Arquitetura
- Quais são os maiores desafios ao aplicar POO em sistemas reais?
- Você já trabalhou em projetos que sofreram com problemas causados por excesso de herança ou má abstração? Como resolveu?
- Como os conceitos de orientação a objetos se alinham com padrões de projeto (ex.: Factory, Strategy, Decorator)?
- Como você equilibra os princípios da POO com abordagens funcionais e imutabilidade, comuns em arquiteturas modernas?


# Perguntas Técnicas – Diferença entre Classe Abstrata e Interface

## Conceitos Básicos
- O que é uma **classe abstrata**? O que ela pode conter?
- O que é uma **interface**? Quais são suas características principais?
- Qual a principal diferença conceitual entre uma interface e uma classe abstrata?


# Perguntas Técnicas – Domain-Driven Design (DDD), Entidades e Value Objects

## Conceitos Básicos de DDD
- O que é Domain-Driven Design (DDD) e qual o seu objetivo principal?
- Quais são os conceitos centrais do DDD?
- O que são **Bounded Contexts** e qual a importância deles no DDD?
- Como o DDD ajuda a resolver problemas em sistemas complexos?

## Entidades (Entities)
- O que define uma **Entidade** em DDD?
- Qual é a característica principal que diferencia uma entidade de outros objetos?
- Como a identidade de uma entidade é mantida ao longo do tempo?
- Quais exemplos de entidades você já implementou em projetos reais?

## Value Objects
- O que é um **Value Object** em DDD?
- Qual a diferença entre Value Object e Entidade?
- Quais características são essenciais para um Value Object?
- Quando faz sentido usar Value Objects em vez de Entidades?

## Comparações e Aplicações Práticas
- Como você decide se um objeto deve ser uma entidade ou um value object?
- Explique a importância da imutabilidade em Value Objects.
- Pode um Value Object conter referências para outras entidades ou value objects? Quais cuidados tomar?
- Como o uso correto de entidades e value objects melhora a clareza do modelo de domínio?

## Boas Práticas e Design
- Como você implementa a igualdade (equals/hashcode) para entidades e para value objects?
- Quais padrões de design costumam ser usados junto com entidades e value objects? (ex.: Factory, Aggregate)
- Como o DDD orienta o tratamento de mudanças e evolução das entidades?
- Como o uso de Value Objects pode ajudar a evitar erros comuns no código?

## Avançado
- O que são Aggregates e como eles relacionam entidades e value objects?
- Como garantir a consistência dentro de um Aggregate no DDD?
- Você já enfrentou dificuldades em aplicar DDD em um projeto? Quais foram os principais desafios?


# Perguntas Técnicas – Microserviços, Event-Driven Architecture, Monolito, Clean Architecture e Onion Architecture

## Conceitos Gerais
- O que é um monolito e quais suas principais vantagens e desvantagens?
- O que são microserviços e como eles se diferenciam do monolito?
- Explique o conceito de arquitetura orientada a eventos (Event-Driven Architecture - EDA).
- O que é Clean Architecture? Quais seus princípios fundamentais?
- O que é Onion Architecture e como ela se relaciona com Clean Architecture?

## Comparações e Diferenças
- Quais são as principais diferenças entre um monolito e uma arquitetura de microserviços?
- Como a Event-Driven Architecture complementa ou substitui arquiteturas baseadas em microsserviços?
- Quais os benefícios de aplicar Clean Architecture em projetos monolíticos ou de microsserviços?
- Como Onion Architecture promove o desacoplamento do domínio em relação a frameworks e infraestruturas?

## Implementação e Desafios
- Quais os principais desafios de migrar um monolito para microserviços?
- Como gerenciar a complexidade da comunicação entre microserviços?
- Como garantir consistência de dados em arquiteturas event-driven e microserviços?
- Quais são os padrões comuns para implementar Event-Driven Architecture (ex.: pub/sub, event sourcing, CQRS)?
- Como a separação de camadas em Clean Architecture melhora a testabilidade e manutenção do código?
- Quais práticas você recomenda para definir os limites de contexto (Bounded Context) em Onion Architecture?

## Benefícios e Quando Usar
- Em que cenários você recomendaria manter um monolito em vez de migrar para microserviços?
- Quais são os sinais de que uma aplicação pode se beneficiar de Event-Driven Architecture?
- Quais vantagens Clean Architecture traz para equipes que trabalham em sistemas complexos?
- Como Onion Architecture ajuda no isolamento do domínio frente a mudanças tecnológicas?

## Padrões e Ferramentas
- Que ferramentas ou frameworks você já usou para suportar microserviços e comunicação assíncrona?
- Como você monitora e depura sistemas baseados em Event-Driven Architecture?
- Quais frameworks facilitam a implementação dos princípios de Clean e Onion Architecture?

## Exemplos Práticos
- Pode dar um exemplo prático onde implementou uma solução com microserviços?
- Já aplicou Clean Architecture em algum projeto? Quais os ganhos percebidos?
- Como você lidou com versionamento e evolução em sistemas baseados em eventos?


# Perguntas Técnicas – Diferenças entre Cancellation Token e Circuit Breaker

## Conceitos Básicos
- O que é um **Cancellation Token** e qual o seu propósito em aplicações .NET?
- O que é um **Circuit Breaker** e para que serve em sistemas distribuídos?
- Qual a principal diferença conceitual entre Cancellation Token e Circuit Breaker?

## Funcionamento e Uso
- Como funciona o fluxo de cancelamento utilizando Cancellation Token em operações assíncronas?
- Em quais cenários você usaria Cancellation Token?
- Como o Circuit Breaker atua para proteger sistemas de falhas em cascata?
- Quais estados um Circuit Breaker geralmente possui? (ex.: Closed, Open, Half-Open)

## Aplicações Práticas
- Explique um exemplo prático onde você implementou Cancellation Token para melhorar a responsividade da aplicação.
- Cite um cenário típico onde o Circuit Breaker é fundamental para manter a resiliência do sistema.
- Como o uso de Circuit Breaker ajuda em arquiteturas de microsserviços?

## Integração com Outras Tecnologias
- Quais bibliotecas populares você conhece para implementar Circuit Breaker no .NET? (ex.: Polly)
- Como você combinaria Cancellation Token e Circuit Breaker em uma mesma aplicação?

## Tratamento de Falhas e Cancelamentos
- O que acontece quando uma operação é cancelada via Cancellation Token?
- Como o Circuit Breaker responde a falhas repetidas? O que acontece quando ele está “Open”?
- Quais são as implicações para o usuário final em cada caso?

## Performance e Monitoramento
- O uso de Cancellation Token impacta na performance da aplicação? Como gerenciar isso?
- Como você monitora e loga eventos relacionados ao Circuit Breaker?
- Já enfrentou situações em que o Circuit Breaker foi acionado erroneamente? Como evitou?

## Boas Práticas
- Quais cuidados você recomenda ao utilizar Cancellation Token em APIs públicas?
- Quais estratégias você adotaria para configurar um Circuit Breaker eficiente (thresholds, timeout, retries)?
- Como garantir que o uso combinado desses dois padrões não cause efeitos colaterais inesperados?


# Perguntas Técnicas – Monitoramento de Aplicações .NET

## Conceitos e Importância
- Por que o monitoramento é crucial em aplicações .NET, especialmente em produção?
- Quais são os principais tipos de monitoramento que você considera essenciais? (ex.: métricas, logs, tracing, alertas)
- Como você define indicadores chave de performance (KPIs) para monitorar uma aplicação .NET?

## Ferramentas de Monitoramento
- Quais ferramentas de monitoramento você já utilizou para aplicações .NET? (ex.: Application Insights, New Relic, Dynatrace, ELK Stack)
- Como o Application Insights se integra com o ecossistema .NET e quais são seus principais benefícios?
- Você já utilizou ferramentas de logging estruturado como Serilog, NLog ou log4net? Quais vantagens oferecem?
- Como integrar logs com sistemas centralizados de monitoramento?

## Monitoramento de Performance e Diagnóstico
- Quais métricas de performance você monitora regularmente em aplicações .NET? (ex.: tempo de resposta, uso de CPU, memória)
- Como você identifica gargalos de performance utilizando ferramentas .NET?
- Já utilizou ferramentas de profiling como dotTrace, PerfView ou Visual Studio Diagnostic Tools? Como foi sua experiência?
- Como você monitora o Garbage Collector e o uso de memória?

## Monitoramento Distribuído e Tracing
- O que é tracing distribuído (distributed tracing) e por que ele é importante?
- Quais frameworks ou padrões você conhece para tracing distribuído no .NET? (ex.: OpenTelemetry, Jaeger)
- Como você implementa correlação de logs e traces em sistemas distribuídos?

## Alertas e Automação
- Como você define e configura alertas eficazes para aplicações .NET em produção?
- Já integrou monitoramento com ferramentas de incident management (ex.: PagerDuty, Opsgenie)?
- Que práticas você recomenda para evitar alertas falsos positivos?

## Boas Práticas e Cultura
- Como incentivar a cultura de observabilidade dentro de equipes de desenvolvimento .NET?
- Qual a importância do monitoramento contínuo para o ciclo de vida de uma aplicação?
- Já participou da implementação de dashboards para monitoramento? Que métricas considerou prioritárias?

## Casos Práticos e Desafios
- Pode descrever um problema complexo que você diagnosticou graças ao monitoramento em uma aplicação .NET?
- Quais foram os maiores desafios que enfrentou na implantação de monitoramento?
- Como você mede o impacto das melhorias feitas a partir de dados coletados no monitoramento?

# Perguntas Técnicas – Saga Pattern

## Conceitos Básicos
- O que é o Saga Pattern e qual problema ele busca resolver?
- Como o Saga Pattern se relaciona com transações distribuídas?
- Qual a diferença entre uma transação tradicional e uma saga?

## Tipos de Saga
- Quais são os dois principais tipos de saga? Explique cada um.
- Em quais situações você usaria uma **saga coreografada** versus uma **saga orquestrada**?

## Implementação
- Como você implementaria uma saga em um sistema de microserviços?
- Quais ferramentas ou frameworks você já utilizou para implementar sagas? (ex.: MassTransit, NServiceBus, Camunda)
- Como garantir que as compensações ocorram corretamente em caso de falhas?

## Benefícios e Desafios
- Quais são as vantagens do Saga Pattern em sistemas distribuídos?
- Quais desafios comuns surgem ao implementar sagas?
- Como lidar com inconsistências temporárias e garantir a eventual consistência?

## Monitoramento e Resiliência
- Como monitorar e depurar fluxos de saga em produção?
- Que estratégias você usa para garantir resiliência e recuperação em sagas longas?

## Casos Práticos
- Pode descrever um cenário onde você aplicou o Saga Pattern?
- Como o Saga Pattern impactou a escalabilidade e a manutenção do sistema?

# Perguntas Técnicas – RabbitMQ e Kafka

## Conceitos Básicos
- O que são sistemas de mensageria e para que servem?
- Quais as principais diferenças conceituais entre RabbitMQ e Kafka?
- O que é um broker de mensagens?

## RabbitMQ
- Como funciona o modelo de filas no RabbitMQ?
- O que são exchanges, filas (queues) e bindings no RabbitMQ?
- Quais tipos de exchange existem no RabbitMQ e quando usar cada um? (direct, fanout, topic, headers)
- Como o RabbitMQ garante a entrega de mensagens? O que é **acknowledgment**?
- Como lidar com mensagens duplicadas e garantias de entrega no RabbitMQ?
- Quais são as limitações do RabbitMQ em sistemas de alta escala?
- O que é TTL (Time To Live) para mensagens e filas no RabbitMQ?
- Como implementar retry e dead-letter queues no RabbitMQ?

## Kafka
- O que é o Apache Kafka e qual seu foco principal?
- Explique os conceitos de **topics**, **partitions**, **producers** e **consumers** no Kafka.
- Como o Kafka garante durabilidade e alta disponibilidade das mensagens?
- O que é **offset** em Kafka e como ele é utilizado no consumo das mensagens?
- Qual a diferença entre consumo **at-least-once**, **at-most-once** e **exactly-once**?
- Como o Kafka suporta processamento em tempo real (streaming)?
- Quais são os benefícios de usar Kafka em arquiteturas event-driven?

## Comparações e Casos de Uso
- Quando você recomendaria usar RabbitMQ em vez de Kafka, e vice-versa?
- Quais tipos de sistemas e cargas cada um deles atende melhor?
- Como você integra RabbitMQ ou Kafka com microsserviços?
- Pode citar um cenário prático onde implementou RabbitMQ e outro onde usou Kafka? Quais foram os desafios?

## Performance e Escalabilidade
- Como escalar RabbitMQ e Kafka para suportar alto throughput?
- Quais são os principais gargalos que você já enfrentou com essas tecnologias?
- Como monitorar a saúde e o desempenho de RabbitMQ e Kafka?

## Segurança e Operação
- Quais são as práticas recomendadas para garantir segurança na comunicação com RabbitMQ e Kafka?
- Como você gerencia autenticação e autorização nesses sistemas?
- Já trabalhou com configuração de replicação e failover em RabbitMQ ou Kafka?
