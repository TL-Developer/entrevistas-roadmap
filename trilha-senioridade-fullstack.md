# Trilha de Senioridade — Engenheiro(a) Full Stack (React + .NET)

Guia consolidado do que é esperado, o que se faz no dia a dia e quais pré-requisitos técnicos cada nível de senioridade (Júnior, Pleno, Sênior e Staff) costuma exigir para uma vaga de engenharia full stack com **front-end em React** e **back-end em .NET**.

Os tópicos aqui resumem e cruzam o conteúdo dos demais arquivos deste repositório (`frontend.md`, `backend.md`, `dotnet-por-senioridade.md`, `banco-de-dados.md`, `arquitetura.md`, `design-patterns.md`, `resiliencia-apis.md`, `alta-disponibilidade.md`, `gateway.md`, `loadbalancer.md`, `estrategias-cache.md`, `estrutura-dados-algoritmos.md`, `nuvem.md`, `devops.md`, `k8s-docker.md`, `autenticacao-auth.md`, `seguranca.md`, `api-restfull.md`, `cdn.md`, `internet-redes.md`, `cultura-carreira-comportamental.md`, `cases.md`) — use-os para aprofundar cada tópico citado.

---

## Como usar este guia

Cada nível traz:
- **O que se espera / dia a dia** — o tipo de trabalho e autonomia esperados.
- **Front-end (React)** — o que é bom/necessário saber.
- **Back-end (.NET)** — o que é bom/necessário saber.
- **Lógica de programação e estrutura de dados** — profundidade esperada.
- **Banco de dados (SQL e NoSQL)** — profundidade esperada.
- **Arquitetura, resiliência e mensageria** — rate limit, circuit breaker, idempotência, API Gateway, mensageria, arquitetura orientada a eventos.
- **Cloud, CI/CD, Docker e Kubernetes** — o que se espera operar/entender.
- **Comportamental** — postura e impacto esperados.

Os níveis são cumulativos: tudo que é esperado de um Júnior também é esperado de um Pleno, e assim por diante.

---

## Júnior

### O que se espera / dia a dia
- Implementa features pequenas e bem definidas com apoio de pares e revisão de código.
- Corrige bugs simples e escreve testes unitários básicos.
- Segue padrões de código e arquitetura já definidos pelo time.
- Pergunta e busca ajuda quando trava; aprende rápido com feedback.

### Front-end (React)
- Diferença entre `props` e `state`; principais Hooks (`useState`, `useEffect`, `useContext`).
- Virtual DOM e por que ele existe.
- Chamadas assíncronas a APIs (`fetch`/`axios`), tratamento de loading e erro na UI.
- Fundamentos de JavaScript/TypeScript: tipos, escopo, `let`/`const`, funções, arrays (`map`/`filter`/`reduce`).
- Organização básica de componentes e estilos (CSS Modules, styled-components ou TailwindCSS).

### Back-end (.NET)
- Criação de endpoints (Minimal API ou Controllers) com os verbos HTTP corretos (GET/POST/PUT/DELETE).
- Validação de entrada e tratamento de exceções global.
- Injeção de dependência e seus ciclos de vida básicos (Singleton, Scoped, Transient).
- Leitura de configuração (`appsettings.json`, variáveis de ambiente, `IOptions<T>`).
- ORM básico (EF Core): Code First, migrations, relacionamentos simples.

### Lógica de programação e estrutura de dados
- Lógica de programação sólida: condicionais, laços, recursão, funções puras.
- Estruturas básicas: array, lista, pilha, fila, hash table — o que são e quando usar cada uma.
- Complexidade (Big O) em nível intuitivo: diferença entre O(1), O(n) e O(n²).

### Banco de dados
- SQL básico: SELECT, JOIN (INNER/LEFT), WHERE, GROUP BY, índices simples.
- Diferença entre PRIMARY KEY, FOREIGN KEY e UNIQUE.
- Noção do que é um banco NoSQL (documento, chave-valor) e quando ele existe no projeto.

### Arquitetura, resiliência e mensageria
- Entende o que é uma API REST e como consumi-la.
- Já ouviu falar de rate limiting e circuit breaker (não precisa implementar sozinho ainda).
- Sabe o que é idempotência em termos simples (reenviar a mesma requisição não deve duplicar efeito).

### Cloud, CI/CD, Docker e Kubernetes
- Sabe rodar a aplicação localmente com Docker (`docker build`, `docker run`, `docker compose up`).
- Entende o que é um pipeline de CI/CD (build → test → deploy) e consegue acompanhar um pipeline existente.
- Conhece o conceito de nuvem (IaaS/PaaS/SaaS) em nível introdutório.

### Comportamental
- Comunica bloqueios cedo, é receptivo a feedback e documenta o que aprende.

---

## Pleno

### O que se espera / dia a dia
- Entrega features de média complexidade com autonomia, do design técnico simples à implementação.
- Revisa código de outros devs e propõe melhorias.
- Investiga e resolve bugs mais complexos, incluindo problemas de performance.
- Participa de decisões técnicas do time (não só executa).

### Front-end (React)
- Gerenciamento de estado além do básico: Context API vs Redux/Zustand, quando usar cada um.
- Performance: `React.memo`, `useMemo`, `useCallback`, listas virtualizadas, evitar re-renders desnecessários.
- Testes: unitários (Jest/Testing Library) e alguma experiência com E2E (Cypress/Playwright).
- TypeScript com profundidade: generics, utility types, narrowing.
- Boas práticas de organização de projeto (Atomic Design ou equivalente), tratamento consistente de erros de API.

### Back-end (.NET)
- Action filters, middlewares customizados, ordem de execução e injeção de dependência em middleware.
- Versionamento de API e cuidado com breaking changes.
- Padrões de projeto aplicados no dia a dia (Factory, Strategy, Decorator, Repository).
- Testes de integração (WebApplicationFactory) além dos unitários.
- Boas práticas de REST: status codes corretos, paginação, cache HTTP (ETag, Cache-Control).

### Lógica de programação e estrutura de dados
- Escolhe a estrutura de dados certa para o problema (heap para prioridade, árvore para hierarquia, grafo para relacionamento).
- Entende e aplica complexidade de tempo/espaço na escolha de algoritmos (busca binária, ordenação, BFS/DFS).
- Resolve problemas de programação dinâmica e backtracking em nível básico/intermediário.

### Banco de dados
- SQL avançado: window functions, subqueries, EXPLAIN/EXPLAIN ANALYZE para otimizar queries.
- Índices: quando criar, impacto em leitura/escrita, índice composto.
- NoSQL com profundidade: quando escolher documento, chave-valor ou colunar; modelagem orientada a padrão de acesso.
- Normalização vs desnormalização intencional.

### Arquitetura, resiliência e mensageria
- **Rate limiting**: algoritmos (token bucket, sliding window) e onde aplicar (gateway, middleware).
- **Circuit breaker**: estados (fechado/aberto/meio-aberto) e bibliotecas (Polly no .NET).
- **Idempotência**: implementação prática com idempotency-key em endpoints de escrita.
- **API Gateway**: o que é, responsabilidades (roteamento, auth, rate limit) e quando usar.
- **Mensageria**: conceitos de fila (RabbitMQ) — exchanges, filas, bindings, dead-letter queue, retry.
- Entende arquitetura monolito vs microsserviços e os trade-offs de cada uma.

### Cloud, CI/CD, Docker e Kubernetes
- Escreve e ajusta `Dockerfile` (multi-stage build, imagem enxuta).
- Configura pipelines de CI/CD (GitHub Actions/Azure DevOps): build, testes, publish de artefato.
- Noções de Kubernetes: Pod, Deployment, Service, ConfigMap/Secret — consegue debugar um pod com problema.
- Diferença entre IaaS, PaaS e SaaS aplicada a decisões reais de projeto.

### Comportamental
- Propõe soluções, não só aponta problemas; equilibra prazos e qualidade; mentora juniores informalmente.

---

## Sênior

### O que se espera / dia a dia
- Projeta soluções técnicas para problemas ambíguos e de média/alta complexidade.
- Define arquitetura de features e serviços, antecipando riscos de escala, consistência e falhas.
- Lidera revisões técnicas e investigações de incidentes (RCA).
- Mentora plenos e juniores; influencia decisões técnicas do time.

### Front-end (React)
- Arquitetura de aplicações React de grande porte: Microfrontends, Module Federation, SSR (Next.js) quando aplicável.
- Performance avançada: entendimento de event loop, heap vs stack, memory leaks, uso de Chrome DevTools (Performance, Memory, Coverage).
- Decide estratégias de cache, code splitting, lazy loading e otimização de Core Web Vitals.

### Back-end (.NET)
- Domain-Driven Design: Entidades, Value Objects, Aggregates, Bounded Contexts.
- CQRS e, quando necessário, Event Sourcing — trade-offs de consistência eventual.
- Saga Pattern (coreografado vs orquestrado) para transações distribuídas.
- Clean/Onion/Hexagonal Architecture e Vertical Slice Architecture — quando cada uma vale a pena.
- Performance e memória: geração do GC, `Span<T>`/`Memory<T>`, profiling (dotTrace, PerfView).

### Lógica de programação e estrutura de dados
- Aplica estruturas avançadas (union-find, R-tree, suffix structures) quando o problema pede.
- Escolhe entre força bruta, guloso, programação dinâmica, branch & bound e aproximação conforme restrições reais do sistema.
- Avalia trade-offs de algoritmos em produção (latência vs uso de memória vs throughput).

### Banco de dados
- **Teorema CAP**: entende os trade-offs entre consistência, disponibilidade e tolerância a partição e aplica isso na escolha de banco/arquitetura.
- Consistência forte vs eventual; locking otimista vs pessimista; distributed locks e seus riscos.
- Sharding, particionamento e multi-tenancy no design do schema.
- Replicação síncrona vs assíncrona; CDC (Debezium, WAL/binlog) para sincronização entre sistemas.

### Arquitetura, resiliência e mensageria
- Combina rate limiting + circuit breaker + timeout + retry/backoff + bulkhead de forma coerente (sem efeitos colaterais entre si).
- **Arquitetura orientada a eventos (EDA)**: pub/sub, event sourcing, outbox pattern, garantias de entrega (at-least-once, at-most-once, exactly-once).
- Kafka vs RabbitMQ: quando usar cada um, partições, offsets, consumer groups.
- Desenha estratégias de alta disponibilidade: redundância, failover, RTO/RPO, split-brain.
- API Gateway vs Service Mesh — quando cada um se aplica.

### Cloud, CI/CD, Docker e Kubernetes
- Projeta arquitetura multi-region (active-passive/active-active) e entende os trade-offs de latência/consistência/custo.
- Kubernetes em produção: HPA, probes de liveness/readiness, resource requests/limits, RBAC, NetworkPolicy.
- Estratégias de deploy seguro: canary, blue-green, rollback automático.
- Infraestrutura como código (Terraform) e GitOps.

### Comportamental
- Comunica decisões técnicas complexas para públicos técnicos e não técnicos; assume responsabilidade por incidentes e pelo resultado do time.

---

## Staff

### O que se espera / dia a dia
- Define padrões arquiteturais e tecnológicos para múltiplos times, não apenas para o próprio.
- Conduz migrações de larga escala (ex.: monolito → microsserviços, .NET Framework → .NET moderno) minimizando risco.
- Avalia e prioriza dívida técnica no nível de portfólio de serviços.
- Influencia decisões técnicas e de produto sem autoridade formal de gestão.

### Front-end e Back-end
- Define *golden paths*, templates e plataforma interna reutilizável entre times (React e .NET).
- Estabelece guidelines de arquitetura (quando usar microsserviços, EDA, BFF, Module Federation) e garante consistência entre squads.
- Avalia build vs buy para ferramentas e serviços de terceiros.

### Arquitetura, resiliência e mensageria
- Projeta estratégia de observabilidade (logs, métricas, tracing distribuído) consistente entre serviços e times.
- Define e acompanha SLIs/SLOs/SLAs de serviços críticos; decide o que fazer quando não são atingidos (error budget).
- Garante compatibilidade de contratos (schemas de eventos, versionamento de API) entre dezenas de serviços de times diferentes.
- Decide estratégias de resiliência e alta disponibilidade em nível de organização (não só de um serviço).

### Cloud, CI/CD, Docker e Kubernetes
- Define estratégia de infraestrutura multi-region/multi-cloud para disaster recovery em nível organizacional.
- Padroniza pipelines de CI/CD e práticas de deploy seguro entre múltiplos times.
- Avalia custo vs performance vs complexidade antes de propor mudanças de infraestrutura em larga escala.

### Comportamental
- Conduz post-mortems de incidentes críticos e transforma aprendizados em melhorias sistêmicas.
- Escreve RFCs/ADRs e obtém buy-in de múltiplos stakeholders técnicos e de negócio.
- Mentora sêniores e plenos em decisões de design sem centralizar todas as decisões em si.

---

## Resumo rápido por tema (onde cada nível entra)

| Tema | Júnior | Pleno | Sênior | Staff |
|---|---|---|---|---|
| Lógica de programação | Fundamentos | Aplica com critério | Trade-offs avançados | Define padrões p/ times |
| Estrutura de dados | Básicas (array, lista, pilha, fila, hash) | Escolhe a certa (heap, árvore, grafo) | Avançadas + trade-offs de produção | — |
| SQL | Básico (SELECT/JOIN) | Avançado (window functions, EXPLAIN) | Modelagem para CAP/sharding | Padrões entre times |
| NoSQL | Noção | Modelagem por acesso | CAP, consistência, CDC | — |
| Cloud | Noção (IaaS/PaaS/SaaS) | Usa pipelines e deploys | Multi-region, HA | Estratégia multi-cloud/org |
| CI/CD | Acompanha pipeline | Configura pipeline | Canary/blue-green, rollback | Padroniza entre times |
| Docker | Roda local | Escreve Dockerfile otimizado | — | — |
| Kubernetes | — | Noções básicas | HPA, probes, RBAC, produção | Estratégia organizacional |
| Rate limiting | Ouviu falar | Implementa | Combina com outros padrões | Define política global |
| Circuit breaker | Ouviu falar | Implementa (Polly) | Combina com retry/timeout/bulkhead | Padrão de resiliência org. |
| Idempotência | Noção | Implementa (idempotency-key) | Garante em sagas/eventos | Padrão entre serviços |
| API Gateway | Consome API | Entende responsabilidades | Decide Gateway vs Service Mesh | Define padrão de borda |
| Mensageria | — | Conceitos de fila | Kafka vs RabbitMQ, garantias de entrega | Compatibilidade de contratos |
| Arquitetura orientada a eventos | — | Noção | Projeta (outbox, event sourcing) | Define padrões organizacionais |
| Teorema CAP | — | — | Aplica na escolha de banco/arquitetura | Decide em nível de plataforma |

---

Notas finais:
- Use este arquivo como checklist de estudo (candidato) ou como referência de calibração de nível (entrevistador).
- Para aprofundar cada tópico, consulte o arquivo específico correspondente neste repositório (ex.: `resiliencia-apis.md` para rate limit/circuit breaker, `banco-de-dados.md` para SQL/NoSQL/CAP, `k8s-docker.md` para Docker/Kubernetes, `devops.md` para CI/CD, `nuvem.md` para cloud, `backend.md` para mensageria/CQRS/Saga).
- Senioridade não é só conhecimento técnico: também é escopo de impacto, autonomia e capacidade de influenciar decisões — por isso cada nível traz também o que se espera no dia a dia e no comportamental.
