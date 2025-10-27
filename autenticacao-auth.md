# Autenticação & Autorização — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre autenticação: JWT, algoritmos, OAuth2/OpenID Connect, Auth0, RBAC, melhores práticas e armadilhas.

---

## O que é JWT (JSON Web Token)?
- O que é?
  - Token compacto e auto-contido que carrega claims em formato JSON, assinado (e opcionalmente criptografado).
- Estrutura?
  - Header.Payload.Signature (base64url).
- Para que serve?
  - Transportar identidade/claims entre partes sem consulta contínua ao servidor.

---

## Quais algoritmos de assinatura são comuns?
- HS256:
  - HMAC com chave simétrica; simples mas chave deve ser compartilhada com verificador.
- RS256:
  - RSA com chave pública/privada; verificação com public key (melhor para serviços distribuídos).
- ES256:
  - ECDSA (curvas elípticas); menor tamanho de token, boa para performance em alguns cenários.

---

## O que validar em um JWT ao recebê-lo?
- Verificações essenciais:
  - Assinatura válida, iss (issuer), aud (audience), exp (expiration) e nbf (not before) quando aplicáveis.
  - Algoritmo esperado (evitar aceitar "alg":"none" ou mudado).
  - Uso de chave pública correta via JWKS quando aplicável.

---

## O que são tokens opacos vs JWT?
- Tokens opacos:
  - Valor aleatório; validação exige introspecção no servidor/authorization server.
- JWT:
  - Auto-contido; permite validação offline (sem consulta) mas exige rotação/validade correta.

---

## Como funciona refresh token?
- Função:
  - Permite obter novos access tokens sem reautenticação do usuário.
- Boas práticas:
  - Armazenar com segurança (HttpOnly cookie), usar refresh token rotation, TTL curto para access token e monitorar uso.
- Riscos:
  - Se leak, permite troca por access tokens; proteger rotacionando e revogando.

---

## Onde armazenar tokens no browser?
- Não recomendado: localStorage/sessionStorage para tokens sensíveis (susceptível a XSS).
- Recomendado:
  - HttpOnly Secure SameSite cookies para access/refresh tokens (mitiga XSS, atentar CSRF).
- Alternativa:
  - Armazenamento em memory + uso de cookies para refresh + proteção CSRF.
s
---

## O que é OAuth2 e quais flows importantes?
- OAuth2 resumo:
  - Protocolo de autorização para conceder acesso delegado a recursos.
- Flows:
  - Authorization Code (com PKCE para apps públicas) — recomendado para SPAs/mobile.
  - Client Credentials — máquina a máquina.
  - Refresh Token — renovar access token.
  - Implicit — obsoleto/ não recomendado.

---

## O que é OpenID Connect (OIDC)?
- OIDC:
  - Camada de identidade sobre OAuth2 que fornece ID Token (JWT) com informações sobre o usuário e endpoints padrão (userinfo, jwks).
- Uso:
  - Autenticação federada e single sign-on.

---

## O que é PKCE e por que usar?
- PKCE:
  - Proof Key for Code Exchange — mitiga interceptação do authorization code em clientes públicos (SPAs/mobile).
- Use:
  - Sempre em flows authorization code para clientes sem segredo.

---

## O que é Auth0 e qual o papel dele?
- Auth0:
  - Serviço de identidade gerenciado (IDaaS) que implementa OAuth2/OIDC, social login, regras, connectors, gerenciamento de usuários e JWKS.
- Vantagens:
  - Rápida integração, segurança e suporte a protocolos.
- Desvantagens:
  - Custo, dependência de terceiro e necessidade de configuração correta.

---

## O que é RBAC vs ABAC?
- RBAC (Role-Based Access Control):
  - Permissões baseado em papéis; simples e amplamente usado.
- ABAC (Attribute-Based Access Control):
  - Decisões baseadas em atributos do sujeito, recurso e contexto; mais flexível fine-grained.
- Quando usar?
  - RBAC para simplicidade; ABAC para regras dinâmicas e contexto complexo.

---

## Como implementar autorização segura em APIs?
- Boas práticas:
  - Separar autenticação (quem é) de autorização (o que pode fazer).
  - Checar scopes/roles/claims no resource server.
  - Princípio do menor privilégio e políticas centralizadas quando possível.

---

## Como revogar tokens?
- Estratégias:
  - Manter lista de revogação (blacklist) ou usar curto TTL e refresh tokens rotativos.
  - Introspection endpoint para tokens opacos.
- Trade-off:
  - JWT sem introspecção é difícil de revogar antes do expirado sem manter estado.

---

## Quais são as principais vulnerabilidades relacionadas a tokens?
- XSS:
  - Roubo de tokens armazenados no client (evitar localStorage).
- CSRF:
  - Cookies sem proteção SameSite/CSRF tokens podem ser abusados.
- Algoritmo/Key Confusion:
  - Não aceitar token com algoritmo inesperado; validar chave correta.
- Replay:
  - Use nonces, jti claim e refresh rotation para mitigar.

---

## O que é JWKS e por que é útil?
- JWKS:
  - JSON Web Key Set — endpoint que expõe chaves públicas usadas para verificar assinaturas (RS256/ES256).
- Benefício:
  - Permite rotação de chaves sem atualizar todos os serviços manualmente.

---

## Quais são práticas de segurança recomendadas?
- Regras rápidas:
  - Usar HTTPS sempre; validar assinatura e claims; short-lived access tokens; refresh rotation; HttpOnly+Secure+SameSite cookies; implementar rate limiting e monitoramento; rotacionar chaves via JWKS.
- Testes:
  - Pen tests focados em XSS, CSRF, token leakage e configurações de CORS.

---

## Perguntas de entrevista sugeridas
- Qual a diferença entre JWT e token opaco? Quando escolher cada um?
- Como funciona o flow Authorization Code com PKCE?
- Por que não guardar access tokens em localStorage?
- Como funciona refresh token rotation e por que é importante?
- Como você revoga um JWT válido antes do expirar?
- Explique RS256 vs HS256 — trade-offs e quando usar.
- O que é JWKS e como ele facilita rotação de chaves?
- Como integrar Auth0 com sua API e quais cuidados de segurança tomar?