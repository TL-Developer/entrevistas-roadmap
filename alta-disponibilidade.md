# Alta Disponibilidade — Como os Sistemas se Mantêm Disponíveis Durante Falhas

Perguntas e respostas objetivas sobre os padrões que mantêm sistemas distribuídos disponíveis diante de falhas: redundância, replicação, retries, backoff exponencial, failover, health checks, load balancing, circuit breaker e backups/disaster recovery.

---

## Redundância
- O que é?
  - Manter componentes extras (servidores, instâncias, links de rede) prontos para assumir caso um componente falhe, evitando ponto único de falha (SPOF).
- Como funciona na prática?
  - Um servidor primário atende as requisições enquanto um servidor standby fica pronto para entrar em ação (ativo-passivo) ou ambos atendem simultaneamente (ativo-ativo).
- Quando usar?
  - Em qualquer componente crítico do sistema: servidores de aplicação, bancos de dados, load balancers, links de rede.
- Armadilhas?
  - Redundância sem monitoramento/health check não garante disponibilidade; custo de manter recursos ociosos (no modelo ativo-passivo).

---

## Replicação
- O que é?
  - Copiar dados de um banco/nó primário para múltiplas réplicas, permitindo que outra réplica atenda as requisições durante falhas.
- Tipos comuns?
  - Replicação síncrona (consistência forte, maior latência) vs assíncrona (melhor performance, risco de perda de dados recentes).
- Topologias?
  - Master-slave (leader-follower), master-master (multi-leader), leaderless (ex.: Dynamo-style).
- Quando usar?
  - Para escalar leitura, aumentar disponibilidade e permitir recuperação rápida após falha do nó primário.
- Armadilhas?
  - Replication lag pode causar leituras desatualizadas; conflitos de escrita em topologias multi-leader exigem estratégia de resolução.

---

## Retries (Retentativas)
- O que é?
  - Tentar novamente uma requisição que falhou, já que muitas falhas são transitórias e desaparecem sozinhas.
- Quando usar?
  - Erros transitórios (timeouts, 5xx, falhas de rede). Evitar em operações não idempotentes sem cuidado adicional (idempotency key).
- Armadilhas?
  - Retries sem controle podem causar "retry storm" e sobrecarregar um serviço já degradado; combinar sempre com backoff e circuit breaker.

---

## Backoff Exponencial (com Jitter)
- O que é?
  - Estratégia de retry em que o tempo de espera entre tentativas cresce exponencialmente (ex.: 1s, 2s, 4s, 8s...), evitando sobrecarregar um sistema que já está com problemas.
- Por que usar jitter?
  - Adicionar aleatoriedade ao tempo de espera evita que múltiplos clientes retentem exatamente ao mesmo tempo (thundering herd).
- Parâmetros típicos?
  - Número máximo de tentativas, delay base, multiplicador, teto máximo de espera (cap).
- Armadilhas?
  - Sem um número máximo de tentativas ou timeout total, o cliente pode ficar retentando indefinidamente.

---

## Failover
- O que é?
  - Chavear automaticamente o tráfego para um sistema standby saudável quando o primário falha.
- Como funciona?
  - Um mecanismo de detecção de falha (health check) identifica que o primário está fora do ar e redireciona o tráfego para a réplica/standby.
- Tipos?
  - Failover automático vs manual; failover regional (disaster recovery) vs failover local (dentro da mesma zona).
- Métricas importantes?
  - RTO (Recovery Time Objective) — tempo até o sistema voltar a operar; RPO (Recovery Point Objective) — quantidade de dados que pode ser perdida.
- Armadilhas?
  - "Split-brain": primário e standby ambos acham que são o líder e aceitam escritas simultaneamente, gerando inconsistência.

---

## Health Checks & Load Balancing
- O que é?
  - Verificações periódicas (health checks) que determinam se uma instância está saudável; o load balancer usa esse status para enviar tráfego apenas a instâncias saudáveis.
- Tipos de health check?
  - Liveness (o processo está rodando?) vs readiness (o processo está pronto para receber tráfego?).
- Quando remover uma instância do pool?
  - Após N falhas consecutivas de health check, evitando remover por uma falha isolada (flapping).
- Armadilhas?
  - Health checks muito superficiais (ex.: apenas ping TCP) não detectam degradação real da aplicação (ex.: banco de dados fora do ar).

---

## Circuit Breaker
- O que é?
  - Padrão que interrompe temporariamente chamadas a um serviço com falhas recorrentes, evitando sobrecarga e dando tempo para recuperação.
- Estados?
  - Fechado (chamadas normais) → Aberto (bloqueia chamadas por um período) → Meio-aberto (permite requisições de teste para verificar recuperação).
- Quando usar?
  - Chamadas a serviços/dependências externas que podem falhar ou ficar lentas.
- Armadilhas?
  - Threshold mal calibrado: abre cedo demais (falsos positivos) ou tarde demais (não protege o sistema a tempo).

---

## Backups & Disaster Recovery
- O que é?
  - Manter cópias (snapshots) dos dados e um plano para restaurar serviço e dados rapidamente após uma falha grave ou desastre regional.
- Estratégias comuns?
  - Backup completo, incremental e diferencial; backups multi-região para sobreviver à perda de uma região inteira.
- Métricas importantes?
  - RTO e RPO (mesmos conceitos do failover), definidos de acordo com a criticidade do sistema.
- Armadilhas?
  - Ter backup sem testar restauração regularmente; backups armazenados na mesma região do sistema original não protegem contra desastres regionais.

---

## Perguntas de entrevista sugeridas
- Qual a diferença entre alta disponibilidade e tolerância a falhas?
- Como você projetaria failover automático para um banco de dados crítico?
- O que é split-brain e como evitá-lo?
- Qual a diferença entre RTO e RPO? Como eles influenciam a estratégia de backup?
- Como combinar retries, backoff exponencial e circuit breaker de forma segura?
- Qual a diferença entre liveness e readiness probes?
- Quando usar replicação síncrona vs assíncrona?

---

Notas finais:
- Alta disponibilidade é resultado da combinação de múltiplos padrões: redundância + replicação + health checks/load balancing + failover + circuit breaker + retries/backoff + backups/disaster recovery.
- Sempre definir e validar objetivos de RTO/RPO de acordo com a criticidade de cada sistema.
- Testar falhas de forma proativa (chaos engineering) para validar que os mecanismos de resiliência funcionam de verdade.
