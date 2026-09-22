# .NET — Perguntas de Entrevista por Senioridade (Júnior, Pleno, Sênior, Staff)

Checklist de perguntas técnicas de .NET organizadas por nível de senioridade, para orientar estudo e condução de entrevistas. Baseado no cheat sheet "[.NET Interview Cheat Sheet](https://antondevtips.com/)" de Anton Martyniuk, com uma seção adicional de nível **Staff**.

---

## Júnior

- Como lidar com requisições POST, PUT e DELETE em Minimal APIs?
- Como tratar exceções globalmente para todos os controllers?
- Como implementar validação em actions de controller? Como tratar models inválidos?
- Escreva uma action de controller que recebe um DTO como entrada, valida e retorna um erro customizado se for inválido.
- Como retornar diferentes status codes HTTP a partir de uma action de controller?
- Qual a diferença entre `ControllerBase` e `Controller`? Quando usar cada um?
- O que é logging estruturado e por que usá-lo?
- Como escrever logs em arquivo usando providers nativos ou de terceiros?
- Como interromper (short-circuit) o pipeline de requisição em um middleware?
- Como passar dados entre componentes de middleware no pipeline de requisição?
- Como ler um valor de configuração (ex.: connection string) no `Program.cs` ou em um controller?
- Como acessar variáveis de ambiente no ASP.NET Core?
- Como recarregar valores de configuração sem reiniciar a aplicação?
- Descreva a diferença entre `IOptions<T>`, `IOptionsSnapshot<T>` e `IOptionsMonitor<T>`.
- Explique as abordagens "Code First" vs. "Database First" no EF Core.
- Como definir um relacionamento One-to-Many entre duas classes no EF Core?

---

## Pleno

- O que é Method Injection em um Controller e como ele difere de constructor injection?
- Explique o ciclo de vida de um controller no ASP.NET Core. Quando ele é instanciado e descartado (disposed)?
- Explique action filters e como você os usaria com controllers.
- Como logar dados de request e response para requisições HTTP recebidas?
- Explique a diferença entre os atributos `[FromBody]`, `[FromQuery]`, `[FromRoute]` e `[FromForm]`.
- Qual é a ordem de execução dos middlewares e por que ela importa?
- Você pode injetar dependências em uma classe de middleware customizada?
- Quando uma API REST deve retornar `404 Not Found` vs. `204 No Content`?
- É permitido introduzir breaking changes em APIs já existentes? Como evitar isso?
- Quais são as formas mais comuns de versionar uma API?
- O que é mapeamento manual entre objetos e quando usá-lo (em vez de AutoMapper/Mapster)?
- O que é o Richardson Maturity Model e quais são seus níveis?
- Qual a diferença entre monolito, monolito modular e arquitetura de microsserviços?
- O que é um API Gateway e quais problemas ele resolve?
- O que é normalização de banco de dados e quando desnormalizar intencionalmente?
- Como um índice de banco de dados acelera queries e qual a desvantagem de adicionar índices demais?

---

## Sênior

- O que é o Teorema CAP e o que cada letra representa?
- Qual a diferença entre consistência forte (strong consistency) e consistência eventual (eventual consistency)?
- Qual a diferença entre escalabilidade horizontal e vertical?
- Quando escolher um banco NoSQL em vez de um SQL e quais fatores devem guiar essa decisão?
- O que é um distributed lock e quais são os riscos de usá-lo?
- Qual a diferença entre locking otimista e pessimista e quando usar cada um?
- Como você projetaria um schema de banco de dados que suporta multi-tenancy?
- Qual a diferença entre write-through cache e write-back cache?
- Qual a diferença entre REST, gRPC e GraphQL e quando escolher cada um?
- Quando usar uma fila de mensagens em vez de chamadas diretas entre serviços?
- Quais as diferenças entre entrega de mensagens at-most-once, at-least-once e exactly-once?
- Quais bibliotecas .NET você usa para mensageria orientada a eventos e como implementa idempotência e retries?
- O que é Clean Architecture e o que significa, na prática, a Dependency Rule?
- Você usa os padrões Repository e Unit of Work com EF Core? Em que cenários fazem sentido?
- O que é Vertical Slice Architecture e como organizar por feature reduz acoplamento?
- Como você organizaria projetos .NET usando Vertical Slice Architecture?
- Como lidar com duplicação de código em projetos .NET com Vertical Slice Architecture?
- Como você implementaria CQRS em .NET, no nível macro (arquitetural) e micro (código)?

---

## Staff

- Como você decide entre construir uma solução internamente (build) ou adotar uma ferramenta/serviço de terceiros (buy)?
- Como definir e evoluir os padrões arquiteturais (ex.: guidelines de microsserviços, comunicação entre times) em uma organização com múltiplos times .NET?
- Como você conduz uma migração de larga escala (ex.: .NET Framework para .NET moderno, monolito para microsserviços) minimizando risco e downtime?
- Como avaliar e reduzir dívida técnica em um portfólio de vários serviços, equilibrando isso com entrega de novas features?
- Como projetar uma estratégia de observabilidade (logging, métricas, tracing distribuído) que funcione entre times e serviços diferentes?
- Como você define e garante SLIs/SLOs/SLAs para serviços críticos e o que fazer quando eles não são atingidos?
- Como projetar uma arquitetura multi-region para alta disponibilidade e disaster recovery?
- Como você aborda versionamento e compatibilidade de contratos (schemas de eventos, APIs) entre dezenas de serviços mantidos por times diferentes?
- Como você influencia decisões técnicas entre times sem autoridade direta de gestão sobre eles?
- Como você equilibra padronização (golden paths, templates, plataforma interna) com autonomia dos times?
- Como você conduz um post-mortem de um incidente crítico em produção e transforma isso em melhorias sistêmicas?
- Como você avalia o trade-off entre performance, custo de infraestrutura e complexidade ao propor uma mudança arquitetural?
- Como você mentora engenheiros sênior e pleno em decisões de design e arquitetura, sem centralizar todas as decisões em você?
- Como você estrutura uma proposta de arquitetura (RFC/ADR) para obter buy-in de múltiplos stakeholders técnicos e de negócio?

---
