# Load Balancer — Perguntas e Respostas

Documento com perguntas comuns de entrevistas e respostas objetivas sobre estratégias de balanceamento de carga.

---

## Round Robin
- O que é?
  - Distribui requisições de forma circular entre servidores.
- Vantagens?
  - Simples, fácil de implementar.
- Desvantagens?
  - Ignora capacidade e estado das instâncias; pode sobrecarregar servidores desiguais.
- Quando usar?
  - Pools homogêneos com carga uniforme.

---

## Weighted Round Robin
- O que é?
  - Variante do Round Robin que atribui pesos a servidores.
- Vantagens?
  - Ajusta distribuição conforme capacidade.
- Desvantagens?
  - Peso estático; não reage a variações dinâmicas de carga.
- Quando usar?
  - Mistura de máquinas com diferentes recursos.

---

## Least Connections
- O que é?
  - Direciona nova conexão ao servidor com menos conexões ativas.
- Vantagens?
  - Bom para cargas com conexões longas/variáveis.
- Desvantagens?
  - Requer contagem precisa de conexões; não considera custo por conexão.
- Quando usar?
  - Serviços com sessões persistentes (ex.: WebSockets).

---

## Weighted Least Connections
- O que é?
  - Combina pesos com menos conexões ativas.
- Vantagens?
  - Balanceia capacidade e número de conexões.
- Desvantagens?
  - Complexidade operacional maior.
- Quando usar?
  - Ambientes heterogêneos com conexões longas.

---

## IP Hash (Source IP Hash)
- O que é?
  - Usa hash do IP do cliente para escolher servidor (afinidade).
- Vantagens?
  - Simples forma de sticky sem session state no servidor.
- Desvantagens?
  - Não tolera mudanças de topologia; proxies/NAT podem quebrar afinidade.
- Quando usar?
  - Quando precisa afinidade simples e clientes com IPs estáveis.

---

## Consistent Hashing
- O que é?
  - Mapeia chaves para servidores minimizando remapeamento quando nós mudam.
- Vantagens?
  - Excelente para caches/distribuição de estado (ex.: memcached).
- Desvantagens?
  - Mais complexo de implementar; requer manejo de hotspots.
- Quando usar?
  - Sistemas distribuídos com sharding e necessidade de elasticidade.

---

## Random
- O que é?
  - Seleção aleatória de servidor (poder ser ponderado).
- Vantagens?
  - Simples; com grande número de servidores tende a balancear.
- Desvantagens?
  - Variância; não ideal para pools pequenos.
- Quando usar?
  - Cenários simples ou como fallback.

---

## Least Response Time
- O que é?
  - Escolhe servidor com menor tempo de resposta recente.
- Vantagens?
  - Reflete performance real.
- Desvantagens?
  - Requer métricas em tempo real; ruído em medições.
- Quando usar?
  - Ambientes com variabilidade de carga e necessidade de SLA.

---

## Sticky Sessions / Session Affinity
- O que é?
  - Mantém cliente ligado sempre ao mesmo backend (cookie, IP).
- Vantagens?
  - Simples para apps com estado por sessão.
- Desvantagens?
  - Reduz elasticidade, pode causar hotspots.
- Quando usar?
  - Apps sem sessão compartilhada; migrar para sessão compartilhada é preferível.

---

## Health Checks e Failover
- O que é?
  - Verificações ativas/passivas para remover instâncias não saudáveis.
- Vantagens?
  - Melhora disponibilidade e roteamento correto.
- Desvantagens?
  - Configuração de checks inadequada pode causar flapping.
- Quando usar?
  - Sempre em produção.

---

## L4 vs L7 Load Balancing
- L4 (TCP/UDP): roteia por IP/porta — baixo overhead, sem visibilidade de HTTP.
- L7 (HTTP/HTTPS): roteia por cabeçalhos/paths/cookies — permite routing avançado, inspeção, TLS termination.

---

## Global Load Balancing (DNS, Anycast)
- O que é?
  - Distribuição entre regiões/datacenters (DNS round-robin, geo-DNS, Anycast).
- Vantagens?
  - Redução de latência geográfica, redundância global.
- Desvantagens?
  - DNS caching dificulta failover rápido; Anycast exige infra de rede.
- Quando usar?
  - Aplicações globais com requisitos de baixa latência.

---

## Connection Draining / Graceful Shutdown
- O que é?
  - Evitar aceitar novas conexões e permitir finalizar as ativas antes de remover instância.
- Vantagens?
  - Evita erros durante deploys/scale down.
- Quando usar?
  - Deploys, escala automática.

---

## Rate Limiting, Throttling e Circuit Breaker no LB
- O que é?
  - Limitar tráfego por cliente/rota; cortar tráfego para backends degradados.
- Vantagens?
  - Protege backend de sobrecarga e ataques.
- Quando usar?
  - Proteção contra picos e abuso.

---

## Perguntas de entrevista sugeridas
- Qual a diferença entre Round Robin e Least Connections? Quando escolher cada um?
- Como implementar sticky sessions sem degradar escalabilidade?
- O que é consistent hashing e por que é útil em caches distribuídos?
- Como o load balancer deve agir ao detectar uma instância com alta latência?
- Quais trade-offs entre L4 e L7 load balancing?
- Como mitigar failover lento em DNS-based global load balancing?

--- 

Notas finais:
- Escolher estratégia segundo padrão de tráfego, heterogeneidade de servidores, necessidade de afinidade e requisitos de disponibilidade.
- Combine health checks, draining e métricas para operação segura.