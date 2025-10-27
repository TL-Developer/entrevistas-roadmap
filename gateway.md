# API Gateway — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre API Gateway e exemplos (Azure APIM, Apigee, Kong, AWS API Gateway, etc).

---

## O que é um API Gateway?
- O que é?
  - Componente de borda que atua como ponto único de entrada para clientes, agregando, roteando e mediando chamadas a serviços backend.
- Responsabilidades típicas:
  - Autenticação/autorização, TLS termination, roteamento, rate limiting, caching, transformação de payloads, agregação de respostas, logging/tracing, versioning e políticas de segurança.

---

## Quais exemplos populares de API Gateway?
- Azure API Management (APIM):
  - Serviço gerenciado da Microsoft com developer portal, políticas configuráveis, gateway, analytics e integração com Azure.
- Apigee (Google):
  - Plataforma completa com gerenciamento de APIs, monetização, políticas, analytics e gateway gerenciado.
- AWS API Gateway:
  - Gateway gerenciado na AWS, integra com Lambda, VPC links, caching e authorizers.
- Kong:
  - Gateway open-source/empresarial extensível com plugins (auth, rate-limit, logging) e deployment self-hosted/cloud.
- NGINX / Traefik:
  - Gateways HTTP/edge populares para roteamento e TLS (Traefik destaca auto-discovery).
- Ambassador / Gloo:
  - Gateways modernos para Kubernetes integrados com Envoy.
- Outros:
  - Tyk, MuleSoft, IBM API Connect.

---

## Quando usar um API Gateway?
- Use quando:
  - Precisa de ponto único para autenticação, políticas, roteamento por versão, central de observabilidade ou monetização de APIs.
- Evite:
  - Implementar lógica de negócio pesada no gateway — ele deve ser uma camada de mediação, não de domínio.

---

## API Gateway vs Service Mesh
- Diferença principal:
  - API Gateway: ponto de entrada para clientes externos (north-south traffic).
  - Service Mesh: comunicação entre serviços internos (east-west), focado em observabilidade, mTLS e roteamento intra-cluster.
- Complementares:
  - Ambos podem coexistir: gateway para clientes, mesh para tráfego de serviço a serviço.

---

## Políticas e funcionalidades comuns
- Autenticação/autorização (OAuth2, JWT validation)
- Rate limiting / quotas / throttling
- Caching de respostas e cache invalidation
- Request/Response transformation (JSON/XML, header rewrite)
- Aggregation / fan-out
- Circuit breaking / retries (integração a resiliência)
- Monitoring, tracing (OpenTelemetry), logging e analytics
- Developer portal e API catalog (APIM/Apigee)
- Monetization e subscription management (plataformas empresariais)

---

## Considerações de arquitetura e operação
- Escalabilidade:
  - Gateway deve escalar horizontalmente; preferir stateless e usar caches/distributed stores para state.
- Latência:
  - Adicionar uma camada de gateway aumenta latência; tire vantagem de caching e keep-alive para mitigar.
- Segurança:
  - TLS termination, WAF integration, validação de schema, rate limits e proteção contra abuse/hot keys.
- Observabilidade:
  - Trace distribuído, métricas p50/p95/p99, contadores de 429/5xx, logs estruturados.
- Deploy:
  - Managed (Azure APIM, Apigee, AWS) reduz operação; self-hosted (Kong, Envoy) oferece controle e customização.
- Versioning:
  - Versionar APIs por caminho/host/header e usar políticas de canary/traffic-splitting para migração.

---

## Boas práticas
- Não colocar regras de negócio no gateway.
- Centralizar autenticação e políticas reutilizáveis.
- Usar caching e rate-limiting adequadamente.
- Monitorar latências e erros, configurar alerts.
- Testar políticas em staging antes de bloquear em produção.
- Documentar APIs e expor developer portal quando aplicável.

---

## Perguntas de entrevista sugeridas
- O que faz um API Gateway e por que usá-lo?
- Quais diferenças entre Azure APIM, Apigee e Kong?
- Como você implementaria rate limiting e cache em um gateway?
- API Gateway ou Service Mesh — quando usar cada um?
- Como gerenciar versão de APIs no gateway sem quebrar clientes?
- Quais métricas e logs você monitora num API Gateway?
- Quais riscos de segurança ao usar um gateway e como mitigá-los?
- Quando escolher um gateway gerenciado vs self-hosted?
