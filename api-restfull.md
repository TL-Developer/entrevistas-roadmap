# API RESTful — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre APIs RESTful: status codes, nomenclatura, paths, métodos HTTP, versionamento, cache, errors e boas práticas.

---

## O que é uma API RESTful?
- Definição:
  - Estilo arquitetural que usa recursos identificados por URIs, operações via métodos HTTP e transferência de representação (JSON/HTTP).
- Principais características:
  - Stateless, recursos, uso de verbos HTTP sem acoplamento ao transporte.

---

## Quais métodos HTTP usar e quando?
- GET: ler recurso(s) — seguro e idempotente.
- POST: criar recurso ou ação não idempotente.
- PUT: substituir recurso completamente — idempotente.
- PATCH: atualizar parcialmente — idempotente (se bem projetado).
- DELETE: remover recurso — idempotente (repetir tem mesmo efeito).
- OPTIONS: descoberta de métodos suportados.

---

## Como nomear endpoints / paths (boas práticas)?
- Use substantivos no plural para recursos: /users, /orders.
- Evite verbs em paths: não usar /getUser ou /createOrder.
- Hierarquia para relações: /users/{userId}/orders.
- Ações que não cabem em CRUD: POST /orders/{id}/cancel ou recursos de controle: /sessions/{id}/refresh.
- Use kebab-case ou snake_case consistentemente (ex.: /user-profiles).

---

## Como versionar API?
- Opções comuns:
  - URI versioning: /v1/users
  - Header versioning: Accept: application/vnd.myapp.v1+json
  - Query param: /users?version=1 (menos recomendado)
- Recomendações:
  - Preferir header ou URI; documentar e suportar coexistência durante migração.

---

## Quais status codes usar (resumo prático)?
- 2xx:
  - 200 OK — leitura/resultado bem-sucedido.
  - 201 Created — recurso criado (incluir Location header).
  - 202 Accepted — aceito para processamento assíncrono.
  - 204 No Content — sucesso sem corpo (DELETE, PUT sem retorno).
- 3xx:
  - 301/302 — redirecionamento (raro em APIs).
- 4xx (cliente):
  - 400 Bad Request — payload inválido/validação.
  - 401 Unauthorized — autenticação requerida/ inválida.
  - 403 Forbidden — autenticado, sem permissão.
  - 404 Not Found — recurso inexistente.
  - 409 Conflict — conflito de estado (ex.: versão).
  - 422 Unprocessable Entity — validação semântica falhou.
  - 429 Too Many Requests — rate limiting.
- 5xx (servidor):
  - 500 Internal Server Error — erro genérico.
  - 502/503/504 — gateway/serviço indisponível/timeout.

---

## Como tratar erros e respostas de erro?
- Formato consistente (ex.: JSON):
  - { "status": 400, "error": "Bad Request", "message": "...", "code": "INVALID_EMAIL", "details": {...} }
- Incluir code legível, message e detalhes úteis para debugging.
- Evitar vazar stack traces ou dados sensíveis.

---

## Idempotência — o que é e por que importa?
- Definição:
  - Reaplicar mesma requisição produz mesmo efeito (PUT, DELETE são idempotentes; POST geralmente não).
- Práticas:
  - Fornecer idempotency-key para POSTs que podem ser re-enviados (pagamentos).

---

## Autenticação e autorização
- Autenticação:
  - Bearer tokens (JWT/opaco), OAuth2, API keys, mTLS.
- Autorização:
  - Checar scopes/roles/ownership no resource server; princípio do menor privilégio.
- Boas práticas:
  - Usar HTTPS, expirar tokens curtos, validar claims e aud/iss.

---

## Paginação, filtro e ordenação
- Paginação:
  - Cursor-based (mais escalável) ou offset-based (simples). Ex.: GET /users?limit=50&cursor=xyz
- Filtros:
  - Query params: /orders?status=paid&from=2025-01-01
- Ordenação:
  - /items?sort=-created_at,name
- Incluir metadados de paginação no response (links rel="next"/"prev" ou meta {total,limit,offset}).

---

## Cache e controle de cache
- Use cabeçalhos HTTP:
  - Cache-Control, ETag, Last-Modified, Vary.
- GET responses devem ser cacheáveis quando seguro.
- Invalidação:
  - Purge em caches CDN ou usar cache-busting (version in path).

---

## Content negotiation e formatos
- Suporte a JSON por padrão.
- Use Accept/Content-Type para negociar formatação (application/json).
- Versões via media type quando necessário.

---

## HATEOAS — quando aplicar?
- HATEOAS (hypermedia) fornece links na resposta para navegação.
- Útil para APIs publicas/hipermidiadas; overhead para APIs internas simples — aplicar conforme necessidade.

---

## Segurança e boas práticas
- Forçar HTTPS; proteção contra CSRF/XSS onde aplicável.
- Limitar tamanho de payloads, validar input e escapar outputs.
- Rate limiting, logging, monitoramento e auditoria.
- Evitar exposição de dados sensíveis em respostas e logs.

---

## Documentação e discoverability
- Documentar com OpenAPI/Swagger e publicar spec.
- Fornecer exemplos de requests/responses, códigos de erro e schemas.
- Usar versioned developer portal e changelog.

---

## Boas práticas operacionais
- Health endpoints: /healthz, /readyz para readiness/liveness.
- Tracing e observabilidade: incluir trace-id em headers e logs.
- Backwards compatibility: adicionar campos opcionais, não remover campos existentes sem versionamento.
- Testes: contract tests (Pact), integração e cenários de erro.

---

## Perguntas de entrevista sugeridas
- Quando usar PUT vs PATCH vs POST?
- Como implementar paginação escalável numa API com milhões de registros?
- O que deve conter um body de erro consistente?
- Como garantir idempotência em operações de escrita?
- Como versionar a API sem interromper clientes?
- Quais headers usar para cache e content negotiation?

--- 

Notas finais:
- Construa APIs previsíveis e consistentes; documente convenções e siga-as.
- Prefira contratos bem definidos (OpenAPI), observabilidade e práticas de segurança por padrão.