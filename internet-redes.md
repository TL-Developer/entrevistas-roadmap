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


## Fundamentos de Redes

- O que é uma rede de computadores?
	- Conjunto de dispositivos interconectados que trocam dados usando protocolos padronizados. Inclui hosts, switches, routers, links e serviços de infraestrutura (DHCP, DNS).
- Conceitos chave?
	- Banda (throughput), latência (RTT), jitter, perda de pacotes, MTU e capacidade de link. Topologias (star, mesh, bus) e camadas de rede.
- Endereçamento e roteamento?
	- Endereços IP (IPv4/IPv6) identificam hosts; roteadores tomam decisões baseadas em tabelas/routing protocols (BGP, OSPF) para encaminhar pacotes entre redes.
- NAT e por que existe?
	- Network Address Translation permite múltiplos hosts privados compartilharem um IP público, resolvendo escassez de endereços e provendo isolamento básico.


## Modelo OSI (visão geral)

- O que é o modelo OSI?
	- Modelo de referência em 7 camadas que ajuda a entender funções de rede: Física, Enlace (Data Link), Rede, Transporte, Sessão, Apresentação e Aplicação.
- Resumo das camadas:
	- 1 Física: meios físicos (cabos, sinais elétricos/ópticos)
	- 2 Enlace: frames, switches, MAC addresses, detecção de erro (Ethernet)
	- 3 Rede: roteamento, IP, encaminhamento entre sub-redes
	- 4 Transporte: TCP/UDP, multiplexação por portas, confiabilidade
	- 5 Sessão: gerenciamento de sessões/conexões (ex.: estabelecimento/fechamento)
	- 6 Apresentação: formatação, criptografia, compressão (ex.: TLS opera aqui/entre camada de apresentação e sessão)
	- 7 Aplicação: protocolos de alto nível (HTTP, DNS, SMTP)
- Por que é útil?
	- Ajudar a isolar problemas, projetar soluções e entender onde aplicar controles (ex.: firewall L4 vs WAF L7).


## Firewall — conceitos e tipos

- O que é um firewall?
	- Dispositivo (hardware/software) que controla o tráfego de rede com base em regras de segurança, filtrando pacotes ou conexões indesejadas.
- Tipos de firewall:
	- Packet-filtering (stateless): regras baseadas em IP/porta/protocolo; simples e rápido.
	- Stateful firewall: acompanha estado da conexão (SYN/ACK), permite regras mais inteligentes.
	- Proxy / Application-level firewall: interpreta protocolos e pode filtrar conteúdo (ex.: proxy HTTP).
- Regras e políticas?
	- Baseadas em listas brancas/ negras, zone-based policies, NAT rules, e inspeção de porta e IP. Princípio do menor privilégio: negar por padrão e permitir explicitamente.
- Onde aplicar?
	- Na borda (perimeter firewall), entre zonas (DMZ, VPC), host-based (firewall local) e em cloud (security groups, NACLs).
- Boas práticas?
	- Segmentar redes, usar regras menos permissivas, registrar logs, revisar regras periodicamente e aplicar defense-in-depth.


## WAF (Web Application Firewall)

- O que é um WAF?
	- Firewall específico para aplicações web que opera na camada HTTP/HTTPS (L7) e protege contra ataques como SQL Injection, XSS, CSRF e outras ameaças ao app.
- Como funciona?
	- Inspeção de requests/responses, regras baseadas em assinaturas, listas, e heurísticas; pode usar aprendizado/ML para detectar padrões anômalos.
- Diferença entre firewall tradicional e WAF?
	- Firewall tradicional filtra pacotes/conexões (L3/L4); WAF compreende o conteúdo HTTP e assemelha-se a um proxy reverso com regras específicas de aplicação.
- Integração com arquitetura?
	- Normalmente colocado na borda (CDN/edge ou antes do API Gateway) ou como plugin no gateway; pode trabalhar com rate limiting, WAF rules e logging para SIEM.
- Limitações e armadilhas?
	- Falsos positivos, necessidade de tuning, não substitui correções no código; desempenho pode ser impactado se inspeção for muito pesada.


## Autenticação Multifator (MFA)

- O que é MFA?
	- Autenticação Multifator exige mais de um fator de verificação antes de conceder acesso: algo que você sabe (senha), algo que você tem (token, dispositivo) e algo que você é (biometria).
- Exemplos de fatores?
	- Conhecimento: senha, PIN.
	- Posse: TOTP (apps como Google Authenticator), SMS (menos seguro), hardware keys (YubiKey, FIDO2/WebAuthn), push notifications.
	- Inerência: impressão digital, reconhecimento facial, voz.
- Por que usar MFA?
	- Reduz significativamente o risco de comprometimento por credenciais roubadas ou senhas fracas; é uma defesa efetiva contra ataques de credential stuffing e phishing (dependendo do fator).
- Formas comuns de implementação?
	- TOTP (Time-based One-Time Password), SMS OTP (não recomendado como único segundo fator), Push-based MFA (aprovação via app), WebAuthn/FIDO2 para autenticação sem senha ou como segundo fator.
- Boas práticas?
	- Preferir fatores resistentes a phishing (FIDO2/WebAuthn), oferecer backup codes e métodos de recuperação seguros, impor MFA para contas privilegiadas, exigir re-authentication para ações sensíveis e monitorar tentativas falhas.
- Riscos e limitações?
	- SMS interceptação/SS7/vulnerabilidades de SIM swap; provisionamento e suporte ao usuário; gestão de dispositivos e recuperação segura (evitar resets inseguros).
- Recomendação para API/serviços?
	- Fornecer endpoints para registrar/desregistrar autenticadores, validar TOTP server-side, suportar WebAuthn, logar eventos de autenticação e forçar MFA em mudanças sensíveis (ex.: alteração de email, saque).

### Perguntas de entrevista sugeridas (curtas)
- O que é MFA e quais são seus fatores?
- Por que SMS não é recomendado como único segundo fator?
- O que é WebAuthn/FIDO2 e por que é preferível em muitos cenários?
- Como desenhar um fluxo de recuperação seguro para usuários que perderam o segundo fator?


