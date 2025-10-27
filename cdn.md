# CDN — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre Content Delivery Networks (CDN): estratégias, provedores (Akamai, Cloudflare, Fastly), cache, invalidação, streaming, segurança e multi-CDN.

---

## O que é uma CDN?
- O que é?
  - Rede distribuída de servidores (POPs) que entrega conteúdo estático/dinâmico a partir da borda para reduzir latência e carga no origin.
- Benefício principal?
  - Menor TTFB, maior throughput, redução de custo de banda no origin e maior disponibilidade global.

---

## Exemplos de provedores populares
- Akamai:
  - Grande cobertura global, recursos empresariais (security, media), bom para grandes volumes e compliance.
- Cloudflare:
  - Rápido deploy, WAF integrado, serviços edge e plano gratuito; forte em proteção DDoS.
- Fastly:
  - Alta performance, VCL para customização de cache-key, bom para streaming e experiências dinâmicas.
- Outros:
  - AWS CloudFront, Azure CDN, Google Cloud CDN, Limelight, KeyCDN.

---

## Quais estratégias de cache usar?
- Origin Pull vs Push:
  - Pull: CDN busca do origin on-demand (mais comum). Push: upload pre-popula POPs (uso em mídia/DRM).
- Cache-Control / Expires:
  - Controlar TTLs com headers (max-age, s-maxage, public/private) e usar stale-while-revalidate/stale-if-error quando suportado.
- Cache Key:
  - Definir chave (host, path, query, headers, cookies) para evitar cache pollution; usar normalização e hashing.

---

## Como invalidar/atualizar conteúdo?
- Purge / Invalidation:
  - Purge por URL, regex, surrogate keys; purges imediatos custam e podem ser rate-limited.
- Surrogate Keys / Tagging:
  - Taggear conteúdo por recurso para limpeza em lote (ex.: todos assets de versão X).
- Cache revalidation:
  - Use ETag/If-None-Match e Last-Modified para validar com origin sem transferir body.

---

## Estratégias para conteúdo dinâmico
- Edge caching com stale:
  - Cachear respostas dinâmicas por curto período + stale-while-revalidate para reduzir latência.
- Edge compute:
  - Executar lógica leve no edge (workers) para personalização, A/B tests ou autenticação antes de chegar ao origin.
- Origin shield:
  - Camada entre POPs e origin para reduzir carga no origin em cache misses.

---

## Streaming e mídia (video / large files)
- Range requests:
  - Suportar byte-range para streaming/seek. Cache de chunks e uso de HLS/DASH com TTL por manifest.
- Segmentação e CDN:
  - Distribuir segmentos pequenos, pré-carregar/manifest caching e usar origin primário para manifests dinâmicos.
- DRM e signed URLs:
  - Usar signed URLs/tokens e expiração curta para proteção de conteúdo.

---

## Performance e protocolos
- HTTP/2, HTTP/3 (QUIC) e TLS:
  - Usar HTTP/2 multiplexing e HTTP/3 para reduzir latência em redes móveis; TLS termination na borda para performance.
- Compressão e formatos:
  - Brotli/ gzip em texto; WebP/AVIF para imagens; adaptar conforme Accept headers (content negotiation).
- Image & asset optimization:
  - Resize/transform no edge, responsive images e cache de variantes otimizadas.

---

## Segurança na CDN
- WAF e DDoS:
  - WAF na borda e mitigação DDoS para proteger origin. Rate limiting para endpoints sensíveis.
- Signed URLs / Token Auth:
  - Controlar acesso a assets privados por assinatura e TTL.
- CORS e headers:
  - Configurar CORS corretamente e headers de segurança (HSTS, CSP, X-Frame-Options) no edge.

---

## Multi-CDN e failover
- Quando usar?
  - Alta disponibilidade global, redução de vendor lock-in e melhor roteamento regional.
- Estratégia:
  - DNS-based failover, load balancing por latency, e monitoramento/health checks; lidar com cache warm-up entre CDNs.
- Trade-offs:
  - Mais complexidade operacional, logging dividido e necessidade de sincronizar purges/keys.

---

## Logs, métricas e monitoramento
- Métricas essenciais:
  - Cache hit ratio, origin offload, TTFB, egress bandwidth, 4xx/5xx por POP, latência p50/p95/p99.
- Logs:
  - Acesso por POP, payload, geo, edge decisions; enviar para SIEM/analytics para troubleshooting e billing.

---

## Custos e trade-offs
- Modelos de cobrança:
  - Bandwidth e requests; custos extras por purge/immediate invalidation e edge compute.
- Otimização de custos:
  - Cache agressivo onde seguro, usar compressão, reduzir purges e usar origin shielding.

---

## Compliance e localização de dados
- Data residency:
  - Alguns provedores e planos permitem controle de região; considerar GDPR e leis locais de dados.
- Logs sensíveis:
  - Reduzir exposição de PII em logs e aplicar retenção/anonimização.

---

## Boas práticas resumidas
- Definir cache keys e TTLs por tipo de conteúdo.
- Usar surrogate-keys para invalidação eficiente.
- Habilitar compressão e formatos modernos.
- Monitorar cache hit ratio e ajustar políticas.
- Proteger origin com WAF, origin shield e rate limits.
- Testar purges e comportamento em failover antes de produção.

---

## Perguntas de entrevista sugeridas
- O que é origin pull vs origin push e quando usar cada um?
- Como você desenharia uma estratégia de purge eficiente para milhões de assets?
- Quais headers HTTP controlam o comportamento de cache em CDNs?
- Quando usar multi-CDN e quais desafios opera‑cionais surgem?
- Como proteger conteúdo estático sensível (signed URLs, token auth)?
- Explique origin shielding e por que ele reduz custos no origin.
- Quais métricas você monitora para decidir TTLs e cache-key?
- Como CDN e HTTP/3 ajudam em conexões móveis de alta latência?

--- 

Notas finais:
- Escolha provedores e políticas conforme requisitos de latência, compliance e custos.
- Teste cenários reais (miss storm, purge, failover) e monitore continuamente.