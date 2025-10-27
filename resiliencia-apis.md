# Resiliência em APIs — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre mecanismos de resiliência em APIs: circuit breaker, rate limiting, retry/backoff, bulkhead, timeout, hedging e práticas complementares.

---

## Circuit Breaker
- O que é?
  - Padrão que interrompe chamadas a um serviço degradado para evitar sobrecarga e permitir recuperação.
- Estados e comportamento?
  - Fechado: chamadas normais; Aberto: bloqueia chamadas por um tempo; Meio-aberto: permite chamadas de teste.
- Parâmetros típicos?
  - Threshold de erros, janela de tempo, tempo de rearmamento (reset), número de requisições de teste.
- Quando usar?
  - Serviços dependentes com falhas intermitentes ou latência elevada.
- Armadilhas?
  - Thresholds mal ajustados causam abertura excessiva ou lentidão na detecção de falhas.

---

## Retry + Backoff (com Jitter)
- O que é?
  - Retentar operações falhas com espaçamento progressivo entre tentativas.
- Estratégias comuns?
  - Exponential backoff, linear backoff, exponential backoff + full/partial jitter.
- Parâmetros típicos?
  - Max attempts, base delay, multiplicador, jitter, timeout total.
- Quando usar?
  - Erros transitórios (timeouts, 5xx). Não usar em operações não idempotentes sem cuidado.
- Armadilhas?
  - Retries simultâneos causam stampede; sempre combinar com circuit breaker, caps e jitter.

---

## Rate Limiting (Throttling)
- O que é?
  - Limitar número de requisições por unidade de tempo para proteger recursos.
- Algoritmos populares?
  - Fixed window, Sliding window, Token bucket, Leaky bucket.
- Onde aplicar?
  - Per-user, per-API key, per-IP, por endpoint crítico.
- Resposta padrão?
  - HTTP 429 Too Many Requests; incluir header Retry-After.
- Armadilhas?
  - Janela fixa cria rajadas; escolha token bucket/ sliding window para melhor suavização.

---

## Token Bucket vs Leaky Bucket (breve)
- Token Bucket:
  - Permite rajadas acumulando tokens; bom para throughput variável.
- Leaky Bucket:
  - Saída constante; modela taxa fixa e suaviza rajadas.

---

## Timeouts e Cancelamento
- O que é?
  - Definir prazo máximo para operações externas e cancelar quando excedido.
- Boas práticas?
  - Timeout mais curto que o esperado do serviço dependente, propagar cancelamento, evitar timeouts infinitos.
- Armadilhas?
  - Timeout muito curto gera falsos positivos; muito longo mantém recursos ocupados.

---

## Bulkhead (Casulos)
- O que é?
  - Isolar recursos (threads, conexões, pools) por tipo de trabalho para evitar contágio.
- Quando usar?
  - Serviços multifuncionais onde um fluxo pode sobrecarregar toda a aplicação.
- Armadilhas?
  - Reservas rígidas subutilizadas; dimensionar conforme SLAs.

---

## Fallback e Graceful Degradation
- O que é?
  - Fornecer alternativa quando dependência falha (cache, resposta padrão, degraded feature).
- Quando usar?
  - Funcionalidades não críticas ou quando prioridade é disponibilidade.
- Armadilhas?
  - Fallbacks muito permissivos podem mascarar problemas reais.

---

## Hedging (Request Replication)
- O que é?
  - Enviar requisições paralelas a múltiplos backends e usar a primeira resposta.
- Quando usar?
  - Picos de latência extrema e endpoints críticos.
- Armadilhas?
  - Aumenta carga; aplicar com limites e somente para latências críticas.

---

## Idempotência e Chaves de Idempotência
- O que é?
  - Garantir efeito único de uma operação repetida (POST/PUT).
- Prática?
  - Uso de idempotency-key (UUID) para deduplicar solicitações no servidor.
- Importância?
  - Permite retries seguras e recuperação sem efeitos colaterais.

---

## Backpressure e Controle de Fluxo
- O que é?
  - Sinalizar ao cliente para reduzir taxa quando servidor está saturado.
- Mecanismos?
  - HTTP 429, Retry-After, TCP windowing, gRPC flow control.
- Armadilhas?
  - Clientes que ignoram sinais agravam degradação.

---

## Observabilidade e Métricas
- Métricas essenciais?
  - Latência p50/p95/p99, taxa de erros, success rate, circuit breaker opens, retries, 429 counts, queue depth.
- Logs estruturados e traces?
  - Trace distribuído para identificar fontes de latência/falhas.
- SLA e Alerts?
  - Alertar por aumento de latência, erros e abertura repetida do circuit breaker.

---

## Testes e Chaos Engineering
- O que testar?
  - Timeouts, limites de taxa, comportamento de circuit breaker, fallback, retries em condições reais.
- Chaos?
  - Injetar latência/erros em dependências para validar resiliência e observabilidade.

---

## Client-side vs Server-side
- O que delegar ao cliente?
  - Retries com backoff (respeitando idempotência), hedging limitado, client-side caching.
- O que manter no servidor?
  - Rate limiting centralizado, circuit breakers por dependência, bulkheads de recursos, policies de fallback.

---

## Perguntas de entrevista sugeridas
- Qual a diferença entre token bucket e leaky bucket e quando escolher cada um?
- Como combinar retries, circuit breaker e timeouts de forma segura?
- Quando aplicar bulkhead e como dimensionar pools?
- Como implementar idempotência para endpoints de escrita?
- Como medir se políticas de retry e rate limit estão corretas?
- Quais riscos do hedging e quando usá-lo?

---

Notas finais:
- Combine múltiplas técnicas: timeouts + retries (com backoff/jitter) + circuit breaker + bulkheads.
- Priorizar idempotência, observabilidade e limites bem definidos.
- Testar com cargas reais e práticas de caos para garantir comportamento em produção.