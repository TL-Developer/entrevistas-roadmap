# Estratégias de Cache — Perguntas e Respostas

Documento com perguntas comuns de entrevistas e respostas objetivas sobre estratégias de cache (cache-aside, read-through, write-through, write-back, write-around, refresh-ahead e outras).

---

## O que é caching?
- O que é?
  - Armazenar temporariamente dados em camada mais rápida (memória) para reduzir latência e carga no backend.
- Quando usar?
  - Leituras frequentes, dados com custo alto de geração, melhorar throughput e reduzir IOPS/latência.
- Armadilhas?
  - Coerência, invalidação, consumo de memória e efeitos de “cache stampede”.

---

## Cache-Aside (Lazy Loading)
- O que é?
  - Aplicação checa cache; se miss, lê do DB, popula o cache e retorna.
- Vantagens?
  - Simples, controle fino sobre o que cachear, evita escrita duplicada.
- Desvantagens?
  - Código do aplicativo mais complexo; risco de stale data e stampede.
- Quando usar?
  - Cargas com leituras majoritárias e dados que podem ser carregados sob demanda.

---

## Read-Through
- O que é?
  - Cache atua como fachada: ao miss, cache mesmo busca do armazenamento e retorna, abstraindo aplicação.
- Vantagens?
  - Simplicidade no aplicativo; centraliza lógica de cache.
- Desvantagens?
  - Dependência do mecanismo de cache para lógica de recuperação; possível latência adicional.
- Quando usar?
  - Deseja abstrair o backend e centralizar políticas de cache.

---

## Write-Through
- O que é?
  - Escrita vai primeiro ao cache e é imediatamente propagada ao armazenamento permanente.
- Vantagens?
  - Consistência mais simples (cache e storage sincronizados).
- Desvantagens?
  - Latência de escrita maior (síncrona); throughput reduzido.
- Quando usar?
  - Quando consistência entre cache e storage é crítica.

---

## Write-Back / Write-Behind
- O que é?
  - Escritas vão ao cache e são persistidas ao storage posteriormente (assíncrono).
- Vantagens?
  - Melhora latência de gravação e throughput.
- Desvantagens?
  - Risco de perda de dados em falhas; complexidade na durabilidade e ordenação.
- Quando usar?
  - Altas taxas de escrita onde alguma latência de persistência é aceitável.

---

## Write-Around
- O que é?
  - Escritas são direcionadas ao storage, pulando o cache; leitura subsequente pode popular o cache.
- Vantagens?
  - Evita poluir cache com dados escritos raramente lidos.
- Desvantagens?
  - Primeira leitura após escrita sofre latência de armazenamento.
- Quando usar?
  - Escritas que raramente são lidas logo em seguida.

---

## Refresh-Ahead (Proactive Refresh)
- O que é?
  - Cache renova entradas antes de expirarem, evitando misses no pico.
- Vantagens?
  - Reduz latência de miss e cache stampede.
- Desvantagens?
  - Tráfego adicional ao backend; complexidade de previsão.
- Quando usar?
  - Dados acessados frequentemente com TTL previsível.

---

## Cache Warming / Pre-warming
- O que é?
  - Popular o cache antes de tráfego real (boot, deploy, escala).
- Vantagens?
  - Evita cold-starts; melhora performance inicial.
- Desvantagens?
  - Custo de pré-carregamento; decidir o que aquecer.
- Quando usar?
  - Deploys, reinícios, cargas previsíveis.

---

## Negative Caching
- O que é?
  - Cachear respostas negativas (ex.: "não encontrado") por curto período.
- Vantagens?
  - Reduz consultas repetidas para chaves inexistentes.
- Desvantagens?
  - Risco de servir ausência obsoleta; TTL curto recomendado.
- Quando usar?
  - Pesquisas por chaves frequentemente inexistentes.

---

## Near Cache / Multi-level Cache
- O que é?
  - Cache local (in-process) junto a cache distribuído (ex.: Redis) para reduzir latência.
- Vantagens?
  - Latências muito baixas para leituras locais; reduz tráfego ao cache central.
- Desvantagens?
  - Coerência entre níveis é desafio; invalidação mais complexa.
- Quando usar?
  - Latência ultra-baixa e alto volume de leituras pela mesma instância.

---

## Local Cache vs Distributed Cache
- O que é?
  - Local: memória da aplicação; Distribuído: compartilhado entre instâncias.
- Trade-offs?
  - Local = latência mínima, mácoerência; Distribuído = coerência e capacidade escalável.
- Quando escolher?
  - Sessões curtas e dados específicos da instância -> local; estado compartilhado -> distribuído.

---

## Eviction Policies (LRU, LFU, FIFO, TTL)
- O que é?
  - Estratégias para escolher quais entradas remover quando cache cheio.
- Diferenças rápidas?
  - LRU: remove menos recentemente usado; LFU: remove menos frequentemente usado; FIFO: ordem de entrada; TTL: expiração por tempo.
- Quando usar?
  - Depende do padrão de acesso e requisitos de freshenss.

---

## Consistent Hashing / Sharding
- O que é?
  - Distribuir chaves entre nós mantendo mínima realocação ao adicionar/remover nós.
- Vantagens?
  - Escalabilidade e balanceamento estável.
- Desvantagens?
  - Complexidade de implementação; necessidade de re-hash quando nós mudam.
- Quando usar?
  - Caches distribuídos grandes que precisam escalar horizontalmente.

---

## Replicação e Alta Disponibilidade
- O que é?
  - Duplicar dados de cache entre nós para tolerância a falhas.
- Estratégias?
  - Master-replica, multi-master, quorum.
- Trade-offs?
  - Consistência vs latência e custos de rede.

---

## Cache Invalidation (Invalidação)
- O que é?
  - Estratégias para remover ou marcar entradas obsoletas.
- Abordagens?
  - Expiração por TTL, invalidação explícita (on update), versioning (cache key version), pub/sub para invalidar clusters.
- Armadilhas?
  - Invalidação incorreta leva a stale reads; excesso de invalidação causa misses.

---

## Stampede / Hot Key Mitigation
- O que é?
  - Problema quando muitos pedidos causam misses simultâneos sobrecarregando backend.
- Mitigações?
  - Locking/coalescing (singleflight), request collapsing, probabilistic early expiration (jitter), rate-limiting, pre-warm.
- Quando aplicar?
  - Quando existem chaves “quentes” com alto tráfego.

---

## TTL e Expiration Strategies
- O que é?
  - Controle de validade temporal das entradas.
- Boas práticas?
  - Usar TTLs razoáveis; combinar TTL externo e invalidação por versão; aplicar jitter para evitar picos sincronizados.
- Quando ajustar?
  - Conforme volatilidade dos dados e tolerância a stale.

---

## Monitoramento e Métricas
- O que medir?
  - Hit ratio, miss ratio, evictions, latency do cache, throughput, ocupação de memória, taxa de erros.
- Porque importante?
  - Afina políticas de TTL/eviction e detecta problemas de hot keys ou stampedes.

---

## Segurança e Consistência
- O que considerar?
  - Criptografia em trânsito/repouso, controle de acesso, evitar expor dados sensíveis em caches compartilhados.
- Consistência?
  - Definir se o sistema tolera eventual consistency; usar versioning ou transações quando necessário.

---

## Resumo de Perguntas de Entrevista sugeridas
- Qual a diferença entre cache-aside e read-through?
- Quando preferir write-back em vez de write-through?
- Como mitigar cache stampede?
- Quais métricas você monitora em um cache distribuído?
- Como garantir coerência entre cache local e cache distribuído?
- Quando usar consistent hashing vs redis cluster sharding?
- Como lidar com hot keys e throttling?
- Como projetar invalidação segura ao atualizar dados no DB?

--- 

Notas finais:
- Escolha estratégia conforme padrão de leitura/escrita, requisito de consistência, tolerância a stale e escala.
- Combinar abordagens (ex.: cache-aside + refresh-ahead + negative caching) frequentemente produz melhores resultados.
- Testar com cargas reais e monitorar continuamente.