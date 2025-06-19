# Perguntas e Respostas – Problemas Reais em Backend e Frontend

## Backend

### 1. Como você resolveu um problema de performance em uma API lenta?
**Resposta:**  
Identifiquei os gargalos usando ferramentas de profiling e logs detalhados. Descobri que consultas ao banco de dados estavam causando lentidão devido a joins complexos e falta de índices. Refatorei as queries para usar índices apropriados, otimizei o acesso aos dados com cache em Redis e implementei paginação para reduzir a quantidade de dados retornados. Também apliquei compressão nas respostas HTTP. Isso reduziu o tempo médio de resposta de 2 segundos para menos de 300ms.

### 2. Como lidou com inconsistência de dados em microserviços?
**Resposta:**  
Implementei o padrão Saga para garantir consistência eventual entre serviços, usando uma orquestração centralizada para controlar o fluxo das transações distribuídas. Também usei eventos de compensação para desfazer operações em caso de falha. Adotei mensagens idempotentes para evitar duplicação e tratei os casos de falhas temporárias com retry exponencial.

### 3. Como você resolveu um problema de alta carga e falhas no backend?
**Resposta:**  
Identifiquei que a aplicação não estava preparada para o volume de requisições. Adotei balanceamento de carga com múltiplas instâncias, implementei caching agressivo com Redis para consultas frequentes e utilizei um API Gateway para aplicar rate limiting e proteger os serviços. Além disso, incluí circuit breakers para isolar serviços falhos e garantir resiliência.

---

## Frontend

### 1. Como você melhorou a performance de uma aplicação React lenta?
**Resposta:**  
Analisei com o React Profiler e Chrome DevTools para identificar componentes que renderizavam desnecessariamente. Utilizei `React.memo` para memorizar componentes puros, apliquei `useMemo` e `useCallback` para evitar recriações de funções e valores, e implementei lazy loading com React.lazy e Suspense para carregar componentes sob demanda. Também adotei listagem virtualizada para renderizar grandes listas, reduzindo o consumo de memória e melhorando a fluidez.

### 2. Como resolveu problemas de memory leak em uma aplicação frontend?
**Resposta:**  
Detectei memory leaks usando o Chrome DevTools Heap Profiler, que indicava listeners e timers não removidos. Refatorei o código para limpar event listeners no `useEffect` return, cancelei timers com `clearTimeout` ou `clearInterval` e garanti que componentes desmontados não atualizassem estado. Isso evitou acúmulo de memória e melhorou a estabilidade.

### 3. Como você lidou com inconsistências visuais e problemas de responsividade?
**Resposta:**  
Adotei um sistema de design consistente com componentes reutilizáveis, utilizando CSS Modules e TailwindCSS para garantir estilos isolados e previsíveis. Usei media queries para adaptar layouts em diferentes tamanhos de tela e testes em múltiplos dispositivos. Além disso, configurei ferramentas como Storybook para validar os componentes em isolamento, garantindo que visual e comportamento permanecessem consistentes.


# Problemas Reais e Soluções – Cache, Filas e Idempotência

## Cache

### Problema 1: Cache desatualizado causando dados inconsistentes para usuários
**Solução:**  
Implementei uma estratégia de invalidação de cache baseada em eventos, onde toda vez que os dados são atualizados na base, uma mensagem é enviada para invalidar ou atualizar o cache correspondente. Usei o padrão Cache Aside para garantir que o cache seja atualizado somente quando necessário, evitando dados stale para os usuários.

### Problema 2: Cache stampede em horários de pico
**Solução:**  
Para evitar que várias requisições simultâneas tentassem popular o cache após expiração, implementei um mecanismo de lock distribuído (com Redis Redlock) para garantir que apenas uma instância atualizasse o cache, enquanto as outras aguardavam ou retornavam dados antigos até a atualização.

---

## Filas

### Problema 3: Perda de mensagens importantes durante falhas temporárias no consumidor
**Solução:**  
Configurei filas com **acknowledgment manual** e implementei retry com backoff exponencial. Mensagens não confirmadas eram reenviadas para a fila, garantindo que nenhuma mensagem fosse perdida mesmo em falhas temporárias. Também usei dead-letter queues para identificar mensagens que falharam repetidamente para análise posterior.

### Problema 4: Processamento fora de ordem causando inconsistência de dados
**Solução:**  
Identifiquei que múltiplos consumidores estavam processando mensagens em paralelo sem controle de ordem. Implementei particionamento baseado em chave, garantindo que mensagens relacionadas fossem processadas na mesma partição e, portanto, em ordem. Isso preservou a consistência dos dados no sistema.

---

## Idempotência

### Problema 5: Operações financeiras duplicadas devido a múltiplas requisições repetidas
**Solução:**  
Introduzi uma chave única de idempotência enviada pelo cliente para cada operação financeira. No servidor, armazenei o status e resultado da operação para aquela chave. Requisições repetidas com a mesma chave retornavam o resultado armazenado, evitando múltiplos débitos ou créditos.

### Problema 6: API exposta recebendo chamadas duplicadas por falha na rede
**Solução:**  
Projetei endpoints REST para serem idempotentes, usando tokens de idempotência e atualizações do tipo upsert no banco de dados. Isso garantiu que reprocessar a mesma requisição não causasse efeitos colaterais, mantendo a integridade dos dados mesmo em situações de retry automático.

---

Quer que eu prepare exemplos de código, arquiteturas ou diagramas para esses casos?
