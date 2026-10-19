# Trilha de Senioridade — Engenheiro(a) Full Stack (React + .NET)

Guia consolidado do que é esperado, o que se faz no dia a dia e quais pré-requisitos técnicos cada nível de senioridade (Júnior, Pleno, Sênior, Staff e Arquiteto) costuma exigir para uma vaga de engenharia full stack com **front-end em React** e **back-end em .NET**.

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
- **Comportamental, cultura e troubleshooting** — postura, impacto e maturidade de resolução de problemas esperados.

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

### Comportamental, cultura e troubleshooting
- Comunica bloqueios cedo, é receptivo a feedback e documenta o que aprende.
- **Troubleshooting**: sabe reproduzir um bug a partir de passos claros, ler stack traces e logs básicos, usar o debugger da IDE; diferencia "não sei resolver" de "não tentei o suficiente" e pede ajuda depois de uma tentativa genuína, não antes nem tarde demais.
- Não tem medo de admitir erro ou de perguntar algo "óbvio" — cultura de time seguro para errar (ver `cultura-carreira-comportamental.md`) começa em como o Júnior é tratado quando erra.

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

### Comportamental, cultura e troubleshooting
- Propõe soluções, não só aponta problemas; equilibra prazos e qualidade; mentora juniores informalmente.
- **Troubleshooting**: debuga de forma independente em código que não escreveu, usando ferramentas de profiling/tracing (Chrome DevTools, dotTrace, Application Insights) além do debugger; investiga problemas de performance com dados (métricas, logs), não achismo; sabe isolar a causa provável antes de sair mudando código.
- Participa de investigações de incidentes contribuindo com dados e hipóteses, mesmo sem liderar a investigação ainda.

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

### Comportamental, cultura e troubleshooting
- Comunica decisões técnicas complexas para públicos técnicos e não técnicos; assume responsabilidade por incidentes e pelo resultado do time.
- **Troubleshooting**: lidera investigação de incidentes cross-service, correlacionando logs, métricas e traces distribuídos (OpenTelemetry/Jaeger); resolve problemas ambíguos sem reprodução clara, formulando e testando hipóteses metodicamente (ex.: eliminação por bisecção, comparação com baseline).
- **Cultura de postmortem sem culpa ("blameless postmortem")**: conduz RCA focado em entender *como* o sistema permitiu a falha (fatores situacionais, decisões no contexto do momento), não em *quem* errar — conceito formalizado por John Allspaw na Etsy, hoje prática padrão em times de alta maturidade (SRE do Google, PagerDuty, etc.). Um time com medo de punição esconde informação e perde a chance real de aprender com o incidente.

---

## Staff

### Referência de mercado: os 3 pilares e os 4 arquétipos do Staff Engineer
Duas obras de referência do mercado formalizam o que é o trabalho de Staff+ e ajudam a calibrar expectativa de forma mais concreta que "senioridade alta":

- **Os 3 pilares** (Tanya Reilly, *The Staff Engineer's Path*):
  1. **Big-picture thinking** — pensar além do ciclo atual: iniciar projetos de um ano, prever o que a empresa vai precisar daqui a 3 anos, construir software fácil de desligar/substituir no futuro.
  2. **Execução** — tocar projetos mais ambíguos e complexos que exigem articulação entre múltiplas pessoas/times, capital político e, às vezes, mudança de cultura — não só código.
  3. **Leveling up** — elevar o nível técnico de quem está ao redor, por influência intencional (mentoria, revisão, ensino) e acidental (ser referência de comportamento/padrão).
- **Os 4 arquétipos de Staff-plus** (Will Larson, *Staff Engineer: Leadership Beyond the Management Track*):
  1. **Tech Lead** — guia abordagem e execução técnica de um time específico, em parceria próxima com o gestor desse time.
  2. **Architect** — dono da direção, qualidade e abordagem técnica de uma área crítica, combinando restrições técnicas, necessidade dos usuários e liderança no nível da organização. *(Importante: no vocabulário de Larson, "Architect" é um dos quatro arquétipos de Staff Engineer, não necessariamente um cargo separado — veja a seção "Arquiteto de Software" abaixo para a visão alternativa, mais comum em empresas maiores, de Arquiteto como papel com autoridade formal distinta.)*
  3. **Solver** — aprofunda em problemas muito complexos e ambíguos; alguns ficam em uma área por muito tempo, outros migram de "incêndio" em "incêndio" conforme a liderança direciona.
  4. **Right Hand** — estende a atenção e o escopo de um executivo em organizações complexas, atuando onde for mais necessário.
- Use os dois frameworks juntos: os 3 pilares descrevem **o tipo de trabalho**; os 4 arquétipos descrevem **onde esse trabalho se concentra**. Um Staff pode, por exemplo, atuar como "Architect" (arquétipo) dentro do pilar de "big-picture thinking".

### O que se espera / dia a dia
- Define padrões arquiteturais e tecnológicos para múltiplos times, não apenas para o próprio.
- Conduz migrações de larga escala (ex.: monolito → microsserviços, .NET Framework → .NET moderno) minimizando risco.
- Avalia e prioriza dívida técnica no nível de portfólio de serviços.
- Influencia decisões técnicas e de produto sem autoridade formal de gestão.

### Front-end e Back-end
- Define *golden paths*, templates e plataforma interna reutilizável entre times (React e .NET).
- Estabelece guidelines de arquitetura (quando usar microsserviços, EDA, BFF, Module Federation) e garante consistência entre squads.
- Avalia build vs buy para ferramentas e serviços de terceiros.

### Visão técnica ampla (Technology Radar)
- Diferente do Sênior (que aprofunda verticalmente), o Staff precisa de **amplitude**: entender o suficiente de áreas fora do seu dia a dia (dados, segurança, mobile, infra, IA/ML, outras stacks) para fazer boas perguntas, avaliar riscos e conversar com especialistas de qualquer área.
- Mantém e revisa periodicamente um **mapa consciente do próprio conhecimento**, no espírito da matriz popularizada por Rumsfeld e usada em contextos de arquitetura/Staff Engineer (ex.: *The Staff Engineer's Path*, de Tanya Reilly):
  - **O que eu sei que sei** (known knowns) — domínio sólido, pode decidir e ensinar.
  - **O que eu sei que não sei** (known unknowns) — lacunas conhecidas; vira item de estudo ou de consulta a um especialista.
  - **O que eu não sei que não sei** (unknown unknowns) — o ponto cego real: tecnologias, práticas ou riscos que nem estão no radar e que podem gerar decisões ruins por ignorância, não por má escolha.
  - Objetivo prático: reduzir o terceiro quadrante continuamente, movendo itens para "sei que não sei" (torná-los visíveis) antes que virem um incidente ou uma decisão arquitetural ruim.
- Ferramentas e hábitos para isso:
  - Manter um radar de tecnologia próprio ou do time, inspirado no [Technology Radar da ThoughtWorks](https://www.thoughtworks.com/radar) (quadrantes Techniques, Tools, Platforms, Languages & Frameworks; anéis Adopt, Trial, Assess, Hold).
  - Ler changelogs, RFCs e post-mortems de outras empresas; participar de comunidades e conferências fora da própria stack.
  - Fazer *spikes*/provas de conceito periódicas em tecnologias fora da zona de conforto, mesmo sem aplicação imediata.
  - Conversar regularmente com especialistas de outras áreas (dados, segurança, SRE, mobile) para expor pontos cegos antes que virem problema.

### Arquitetura, resiliência e mensageria
- Projeta estratégia de observabilidade (logs, métricas, tracing distribuído) consistente entre serviços e times.
- Define e acompanha SLIs/SLOs/SLAs de serviços críticos; decide o que fazer quando não são atingidos (error budget).
- Garante compatibilidade de contratos (schemas de eventos, versionamento de API) entre dezenas de serviços de times diferentes.
- Decide estratégias de resiliência e alta disponibilidade em nível de organização (não só de um serviço).
- **Arquitetura celular (cell-based)**: conhece o padrão (popularizado pela AWS) de particionar o sistema em "células" independentes, cada uma servindo um subconjunto de clientes/tráfego, para limitar o *blast radius* — o impacto máximo de uma falha única. Entende que redundância multi-AZ/multi-region cobre falha de infraestrutura, mas não cobre falha de deploy ruim ou erro operacional; células contêm esse segundo tipo de falha.

### Cloud, CI/CD, Docker e Kubernetes
- Define estratégia de infraestrutura multi-region/multi-cloud para disaster recovery em nível organizacional.
- Padroniza pipelines de CI/CD e práticas de deploy seguro entre múltiplos times.
- Avalia custo vs performance vs complexidade antes de propor mudanças de infraestrutura em larga escala.

### Comportamental, cultura e troubleshooting
- Conduz post-mortems de incidentes críticos e transforma aprendizados em melhorias sistêmicas.
- Escreve RFCs/ADRs e obtém buy-in de múltiplos stakeholders técnicos e de negócio.
- Mentora sêniores e plenos em decisões de design sem centralizar todas as decisões em si.
- Faz **"Glue Work"** (conceito de Tanya Reilly) sem se incomodar com o fato de ser um trabalho pouco visível: integrar novos membros, destravar pessoas travadas, construir consenso entre times, escrever documentação e conduzir design reviews — trabalho que frequentemente decide se um projeto dá certo, mesmo não aparecendo em métricas de código.
- **Troubleshooting em escala**: não resolve incidente sozinho — constrói os sistemas e processos (observabilidade padronizada, runbooks, ferramentas de diagnóstico) que permitem qualquer time investigar problemas sem depender dele. Trata um incidente recorrente como sinal de lacuna sistêmica a corrigir, não como mau desempenho de quem respondeu.
- Reforça ativamente a cultura de **postmortem sem culpa** entre times (não só no próprio) — questiona processos quando percebe que pessoas escondem erros por medo, porque isso destrói a capacidade do time de aprender com falhas.

---

## Arquiteto de Software

### Arquiteto vs. Staff — qual a diferença?
Existem duas visões de mercado que vale conhecer, porque entrevistadores e empresas usam ambas:
- **Visão 1 — Architect como arquétipo de Staff** (Will Larson, *Staff Engineer*): "Architect" é um dos 4 arquétipos de Staff-plus (junto com Tech Lead, Solver e Right Hand), não um cargo à parte. Nessa visão, um Staff Engineer "modo Architect" é dono da direção técnica de uma área crítica, mas segue sem autoridade formal de gestão — convence pelo argumento, não pela posição.
- **Visão 2 — Arquiteto como papel com autoridade formal distinta** (mais comum em empresas maiores/tradicionais, inclusive em vagas de mercado brasileiras de "Arquiteto de Software/Soluções"): o Arquiteto tem a palavra final sobre decisões estruturais — **diz o que deve ser feito**, documenta a arquitetura formalmente, faz a interface entre stakeholders de negócio e técnicos, e é cobrado pela governança dessas decisões ao longo do tempo (não só por propô-las) em comitês de arquitetura.
- Na prática: o título varia por empresa. O que não varia é o tipo de responsabilidade: quanto mais formal o papel de Arquiteto, mais ele é cobrado por decisões estruturais documentadas e por garantir que elas sejam seguidas — e menos por "convencer", como no Staff puro.
- Vale a sobreposição: boa parte do conteúdo do nível Staff acima (observabilidade, SLOs, alta disponibilidade, EDA, radar de tecnologia, os 3 pilares de Reilly) também é esperado de um Arquiteto — a seção abaixo foca no que é **adicional e específico** do papel, com base no livro *Fundamentals of Software Architecture* (Mark Richards e Neal Ford), referência de mercado para a disciplina.

### Fundamentos do papel (Richards & Ford)
- **As duas leis da arquitetura de software**:
  1. **Tudo em arquitetura de software é trade-off** — se parece que algo não é um trade-off, é porque o trade-off ainda não foi identificado. Não existe "melhor solução" isolada, só a mais adequada para o contexto e as restrições dadas.
  2. **O "porquê" é mais importante que o "como"** — documentar a razão de uma decisão (contexto, restrições, alternativas descartadas) importa mais do que os detalhes de implementação, que mudam com o tempo; é exatamente o papel do ADR.
- **Architecture characteristics ("-ilities")**: o termo que o livro usa para o que este guia chama de NFRs — disponibilidade, confiabilidade, escalabilidade, performance, segurança, testabilidade, deployability etc. — e que o Arquiteto precisa identificar explicitamente para cada sistema, priorizá-las (nem toda característica cabe, escolher poucas e relevantes) e verificar se a arquitetura as atende.
- **Fitness functions**: mecanismos automatizados (testes de arquitetura, métricas, regras de CI) que verificam continuamente se a arquitetura continua atendendo às characteristics definidas — evita que a arquitetura "decida" se degradar silenciosamente ao longo do tempo.
- **8 expectativas do arquiteto**, segundo o livro: tomar decisões arquiteturais (não decisões de implementação, que são do time); analisar continuamente a arquitetura e o ambiente técnico; manter-se atualizado com tendências de mercado (conecta com a seção de radar de tecnologia do Staff); garantir que as decisões tomadas estejam sendo seguidas na prática; ter exposição e experiência diversa (múltiplas stacks, plataformas, estilos); ter conhecimento do domínio de negócio, não só de tecnologia; ter habilidades interpessoais (facilitação, negociação, apresentação, mentoria); e entender e navegar a política da organização.

### O que se espera / dia a dia
- Traduz visão de negócio em solução técnica e é o elo formal entre stakeholders de negócio e times técnicos.
- Toma e documenta decisões estruturais ("coisas difíceis de mudar depois", na definição de Martin Fowler) — não apenas sugere, decide e é responsável pelo resultado.
- Analisa alternativas de design contra restrições reais (custo, prazo, confiabilidade, time disponível) e escolhe a opção mais adequada, não a tecnicamente "mais elegante".
- Participa (ou conduz) comitês/fóruns de arquitetura (architecture review board) para aprovar mudanças estruturais propostas por outros times.
- Conduz provas de conceito (PoCs) para validar escolhas antes de comprometer o time com uma tecnologia ou padrão.

### O que é bom saber

**Documentação e modelagem de arquitetura**
- **C4 Model** (Context, Container, Component, Code) — linguagem comum de diagramas para descrever um sistema em diferentes níveis de zoom; ferramentas de mercado: Structurizr, PlantUML, Mermaid (diagram-as-code).
- **ADR (Architecture Decision Record)** — registrar cada decisão relevante com contexto, alternativas consideradas, trade-offs e consequência; é o principal mecanismo de rastreabilidade de decisões cobrado em arquitetura madura.
- **ArchiMate / UML / TOGAF** — notações e frameworks de arquitetura corporativa (enterprise architecture) usados em organizações maiores para conectar arquitetura de negócio, aplicação, dados e tecnologia.
- **ATAM (Architecture Tradeoff Analysis Method)** — método formal para avaliar como uma arquitetura atende (ou não) a múltiplos atributos de qualidade concorrentes entre si (ex.: performance vs segurança vs custo).

**Requisitos não funcionais (NFRs) como responsabilidade central**
- Performance, escalabilidade, confiabilidade, segurança, manutenibilidade e custo são, no mercado, descritos como os requisitos que "nenhum ticket de feature cobre" e que ficam sob responsabilidade do arquiteto — diferente dos requisitos funcionais, que o time de produto prioriza.
- **AWS Well-Architected Framework** — referência de mercado amplamente usada como checklist de NFRs, com 6 pilares: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization e Sustainability.
- **Azure Well-Architected Framework** — equivalente da Microsoft, com 5 pilares: Reliability, Security, Cost Optimization, Operational Excellence e Performance Efficiency.
- Usar um desses frameworks (ou um checklist próprio inspirado neles) como guia de revisão antes de aprovar uma arquitetura evita que decisões sejam tomadas só pensando em requisito funcional.

**Resiliência em escala: Arquitetura Celular (Cell-Based) — e como ela se relaciona com DDD**
- **Arquitetura celular**: padrão (popularizado pela AWS) de particionar o sistema em "células" independentes — cada uma com sua própria capacidade, dados e failure domain — servindo um subconjunto de clientes/tráfego. O objetivo é limitar o **blast radius**: o impacto máximo que uma única falha pode causar.
- Diferente de multi-AZ/multi-region (que protegem contra falha de infraestrutura), células também contêm falhas de **deploy ruim ou erro operacional** — o tipo de falha que uma região saudável não impede, porque o problema está no código/config, não no datacenter.
- **Não é "versus" DDD — é complementar**: DDD (Sênior) define *onde* estão as fronteiras de domínio (bounded contexts); arquitetura celular (Arquiteto/Staff) decide *como particionar infraestrutura e tráfego* para isolar falhas. Bounded contexts mal definidos tendem a virar células mal particionadas, com acoplamento cruzando a fronteira que deveria isolar a falha — por isso o Arquiteto precisa entender ambos para desenhar partições que façam sentido de domínio e de infraestrutura ao mesmo tempo.
- Trade-off conhecido: células menores reduzem blast radius, mas multiplicam rotas, dashboards e pipelines de deploy — exige **shuffle sharding** (distribuir clientes entre células de forma que nenhum cliente fique preso sempre na mesma célula sobrecarregada) e rollout disciplinado (nunca publicar em todas as células de uma vez).

**Governança e processo**
- Define escopo de governança com ferramentas como **RACI** (quem é Responsável, Aprovador, Consultado, Informado em cada decisão) para não virar gargalo nem perder rastreabilidade.
- Garante que decisões arquiteturais relevantes fiquem documentadas (ADRs) e acessíveis, não só na cabeça de quem decidiu.
- Equilibra padronização (reduzir variação técnica entre times) com autonomia (não travar entrega por burocracia arquitetural).

**Certificações e referências de mercado**
Não são pré-requisito, mas funcionam como sinal de mercado e guia de estudo estruturado: **AWS Certified Solutions Architect**, **Microsoft Certified: Azure Solutions Architect Expert (AZ-305)** e certificação **TOGAF**. Para aprofundar a teoria por trás do papel, as referências mais citadas no mercado são os artigos de Martin Fowler sobre arquitetura de software (ex.: *"Who Needs an Architect?"*) e o site [c4model.com](https://c4model.com).

### Comportamental, cultura e troubleshooting
- Assume a responsabilidade pela decisão, não só pela sugestão — inclusive quando a decisão se mostra errada depois.
- Comunica trade-offs de forma que stakeholders de negócio entendam o risco, sem simplificar a ponto de esconder a complexidade real.
- Sabe dizer "não" ou "ainda não" para pedidos que comprometem a arquitetura no médio prazo, justificando com dados e trade-offs — não com autoridade de cargo.
- Projeta **debugabilidade/observabilidade como architecture characteristic desde o início** (não como algo que se adiciona depois de um incidente) — exige que todo serviço novo nasça com logging estruturado, métricas e tracing antes de ir para produção.
- Audita se a cultura de postmortem sem culpa está realmente sendo seguida entre times (não só declarada) — times que punem quem relata erro geram informação de pior qualidade sobre as próprias falhas da arquitetura.

---

## Resumo rápido por tema (onde cada nível entra)

| Tema | Júnior | Pleno | Sênior | Staff | Arquiteto |
|---|---|---|---|---|---|
| Lógica de programação | Fundamentos | Aplica com critério | Trade-offs avançados | Define padrões p/ times | — |
| Estrutura de dados | Básicas (array, lista, pilha, fila, hash) | Escolhe a certa (heap, árvore, grafo) | Avançadas + trade-offs de produção | — | — |
| SQL | Básico (SELECT/JOIN) | Avançado (window functions, EXPLAIN) | Modelagem para CAP/sharding | Padrões entre times | — |
| NoSQL | Noção | Modelagem por acesso | CAP, consistência, CDC | — | — |
| Cloud | Noção (IaaS/PaaS/SaaS) | Usa pipelines e deploys | Multi-region, HA | Estratégia multi-cloud/org | Well-Architected (AWS/Azure) como guia de decisão |
| CI/CD | Acompanha pipeline | Configura pipeline | Canary/blue-green, rollback | Padroniza entre times | Governança de padrões entre portfólios |
| Docker | Roda local | Escreve Dockerfile otimizado | — | — | — |
| Kubernetes | — | Noções básicas | HPA, probes, RBAC, produção | Estratégia organizacional | — |
| Rate limiting | Ouviu falar | Implementa | Combina com outros padrões | Define política global | Aprova como NFR em ADR |
| Circuit breaker | Ouviu falar | Implementa (Polly) | Combina com retry/timeout/bulkhead | Padrão de resiliência org. | Aprova como NFR em ADR |
| Idempotência | Noção | Implementa (idempotency-key) | Garante em sagas/eventos | Padrão entre serviços | Exige como requisito de design |
| API Gateway | Consome API | Entende responsabilidades | Decide Gateway vs Service Mesh | Define padrão de borda | Decide e documenta (ADR) |
| Mensageria | — | Conceitos de fila | Kafka vs RabbitMQ, garantias de entrega | Compatibilidade de contratos | Decide e documenta (ADR) |
| Arquitetura orientada a eventos | — | Noção | Projeta (outbox, event sourcing) | Define padrões organizacionais | Aprova em comitê de arquitetura |
| Teorema CAP | — | — | Aplica na escolha de banco/arquitetura | Decide em nível de plataforma | Formaliza trade-off em ADR |
| Radar de tecnologia / amplitude | — | — | Profundidade na própria stack | Amplitude entre stacks; mapeia known/unknown unknowns | Usa para avaliar build vs buy |
| Modelagem e documentação | — | — | — | RFCs/ADRs pontuais | C4 Model, ADR, TOGAF/ArchiMate, ATAM |
| Governança | — | — | — | Influencia sem autoridade formal | Autoridade formal + RACI + comitê de arquitetura |
| Troubleshooting | Reproduz bug com apoio | Debuga sozinho, usa profiling | Lidera RCA, correlaciona logs/métricas/traces | Postmortem sem culpa; ferramentas de diagnóstico org. | Observabilidade como architecture characteristic desde o design |
| Arquitetura celular (blast radius) | — | — | — | Conhece o padrão | Decide e combina com fronteiras de DDD |

---

Notas finais:
- Use este arquivo como checklist de estudo (candidato) ou como referência de calibração de nível (entrevistador).
- Para aprofundar cada tópico, consulte o arquivo específico correspondente neste repositório (ex.: `resiliencia-apis.md` para rate limit/circuit breaker, `banco-de-dados.md` para SQL/NoSQL/CAP, `k8s-docker.md` para Docker/Kubernetes, `devops.md` para CI/CD, `nuvem.md` para cloud, `backend.md` para mensageria/CQRS/Saga).
- Senioridade não é só conhecimento técnico: também é escopo de impacto, autonomia e capacidade de influenciar decisões — por isso cada nível traz também o que se espera no dia a dia e no comportamental.
- Staff e Arquiteto se sobrepõem bastante no mercado; em muitas empresas são o mesmo cargo. A distinção usada aqui (autoridade formal sobre decisões estruturais vs. influência sem autoridade) é a mais citada em comparações de mercado, mas varia de empresa para empresa.

Referências de mercado usadas nas seções de Staff e Arquiteto:
- [C4 Model](https://c4model.com)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [Azure Well-Architected Framework](https://learn.microsoft.com/azure/well-architected/)
- Martin Fowler, [Who Needs an Architect?](https://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf)
- Mark Richards e Neal Ford, [*Fundamentals of Software Architecture: An Engineering Approach*](https://www.oreilly.com/library/view/fundamentals-of-software/9781492043447/) — leis da arquitetura, architecture characteristics, fitness functions e as 8 expectativas do arquiteto.
- Will Larson, [*Staff Engineer: Leadership Beyond the Management Track*](https://staffeng.com/book) — os 4 arquétipos de Staff-plus (Tech Lead, Architect, Solver, Right Hand).
- Tanya Reilly, [*The Staff Engineer's Path*](https://www.oreilly.com/library/view/the-staff-engineers/9781098118723/) — os 3 pilares (big-picture, execução, leveling up) e o conceito de "Glue Work" ([noidea.dog/glue](https://noidea.dog/glue)).
- John Allspaw, [Blameless PostMortems and a Just Culture](https://www.etsy.com/codeascraft/blameless-postmortems/) (Etsy, 2012) — referência original da cultura de postmortem sem culpa usada nas seções de Sênior, Staff e Arquiteto.
- AWS, [Guidance for Cell-Based Architecture](https://github.com/aws-solutions-library-samples/guidance-for-cell-based-architecture-on-aws) — padrão de particionamento para redução de blast radius usado na seção de Arquiteto.
