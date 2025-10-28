## Protocolo HTTP

- O que é?
	- Protocolo de aplicação usado para comunicação web (cliente/servidor) sobre TCP. Transfere representações de recursos (HTML, JSON, etc.).
- Métodos importantes?
	- GET (ler), POST (criar/ação), PUT (substituir), PATCH (atualizar parcialmente), DELETE, OPTIONS, HEAD.
- Códigos de status comuns?
	- 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 422 Unprocessable Entity, 429 Too Many Requests, 500 Internal Server Error.
- Cabeçalhos úteis?
	- Host, Authorization, Content-Type, Accept, Cache-Control, ETag, If-None-Match, Connection, Keep-Alive, Transfer-Encoding.
- HTTP/1.1 vs HTTP/2 vs HTTP/3?
	- HTTP/1.1: texto, conexões keep-alive, cabeçalhos repetidos; HTTP/2: binário, multiplexing, header compression (HPACK); HTTP/3: baseado em QUIC/UDP, reduz latência por conexão e reconexão mais rápida.
- Boas práticas?
	- Usar TLS (HTTPS), controlar caches, usar status codes corretos, cuidar de timeouts, paginar resultados e documentar APIs via OpenAPI.


## TCP, UDP e IP

- O que é IP?
	- Protocolo de rede (camada de rede) responsável pelo roteamento de pacotes entre hosts (endereços IP). Não garante entrega.
- O que é TCP?
	- Protocolo orientado a conexão (camada de transporte) que fornece entrega confiável, ordenada e controle de congestionamento (handshake 3-way, ACKs, retransmissões).
- O que é UDP?
	- Protocolo sem conexão (camada de transporte), entrega simples e sem garantias; baixo overhead e ideal para latência/throughput (ex.: DNS, VoIP, streaming em tempo real quando tolerância a perda existe).
- Quando usar TCP vs UDP?
	- TCP para transferência confiável (HTTP, bancos de dados, transferências de arquivo). UDP quando baixa latência e perda tolerável (VoIP, jogos, QUIC/HTTP3 internamente).
- Como funciona o handshake TCP?
	- SYN -> SYN/ACK -> ACK (3-way handshake) para estabelecer conexão; FIN/ACK para encerramento.
- Conceitos importantes:
	- MTU (tamanho máximo do pacote), fragmentation, reassembly, portas (well-known ports), NAT, TTL, window size e congestion control (slow start).


## Protocolo WebSocket (WS)

- O que é?
	- Protocolo que faz upgrade de uma conexão HTTP para um canal full‑duplex persistente entre cliente e servidor, permitindo troca bidirecional de mensagens.
- Como ocorre o handshake?
	- Cliente envia requisição HTTP com header Upgrade: websocket e Sec-WebSocket-Key; servidor responde com 101 Switching Protocols e Sec-WebSocket-Accept.
- Vantagens sobre polling/long-polling?
	- Menor overhead, latência reduzida e comunicação em tempo real sem reestabelecer conexões repetidamente.
- Quando usar?
	- Aplicações em tempo real: chats, dashboards, jogos, notificações push e streams de eventos.
- Segurança e escala?
	- Usar WSS (WebSocket sobre TLS). Escalar pode exigir brokers/message queues (ex.: Redis Pub/Sub, Kafka) e balanceadores que suportem afinidade ou proxy que faça sticky sessions.


## SSL, TLS e mTLS

- O que é SSL/TLS?
	- SSL (obsoleto) e seu sucessor TLS são protocolos que fornecem criptografia, integridade e autenticação na camada de transporte (TLS 1.2/1.3 são os padrões atuais).
- Como funciona o handshake TLS (resumido)?
	- Cliente hello (cipher suites, nonce) -> Servidor hello + certificado -> (opcional) server key exchange -> troca de chaves (RSA/ECDHE) -> verify -> sessão segura estabelecida. TLS 1.3 simplificou e acelerou o handshake (0-RTT suporte).
- O que é mTLS (mutual TLS)?
	- Variedade de TLS onde cliente e servidor trocam certificados e validam ambos os lados (autenticação mútua). Útil para autenticar serviços entre si (service-to-service) sem apenas tokens.
- Certificados e PKI?
	- CA (Certificate Authority) emite certificados; cadeia de confiança até raiz; revogação via CRL/OCSP e rotação de chaves periódica.
- Diferenças entre TLS 1.2 e 1.3?
	- TLS 1.3 elimina algoritmos fracos, reduz números de mensagens no handshake (mais rápido), remove renegociação insegura e melhora privacidade (menos metadata exposta).
- Boas práticas de segurança TLS?
	- Usar TLS 1.2+ (preferir 1.3), configurar cipher suites fortes (AEAD como AES-GCM/ChaCha20-Poly1305), HSTS, certs com rotação e revogação, proteger chaves privadas e usar OCSP stapling quando possível.
- Quando usar mTLS?
	- Comunicações de backend/serviços confiáveis (microservices, APIs internas, bancos) onde autenticação forte sem depender de tokens é desejada.


### Perguntas de entrevista sugeridas (curtas)
- Explique a diferença entre HTTP/1.1 e HTTP/2.
- Quando escolher UDP ao invés de TCP?
- Como funciona o handshake de WebSocket e por que usamos Upgrade?
- O que é TLS 1.3 e quais benefícios traz sobre 1.2?
- Quando você usaria mTLS em vez de OAuth2/JWT?

---

Notas finais:
- Escolha protocolos e configurações com base em requisitos de latência, confiabilidade e segurança.
- Sempre habilite TLS para tráfego sensível e monitore métricas de rede (latência, retransmissões, erros).

