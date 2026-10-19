# Tipos de Servidores Web — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre os principais servidores web/aplicação do mercado: Apache, Nginx, IIS, LiteSpeed, Caddy, Tomcat, Node.js, Gunicorn, Uvicorn e servidores em nuvem — além dos conceitos que normalmente aparecem junto (web server vs application server, WSGI vs ASGI, reverse proxy).

---

## Apache (HTTP Server)
- O que é?
  - Servidor web de código aberto mais tradicional do mercado, mantido pela Apache Software Foundation.
- Como funciona?
  - Modelo baseado em processos/threads (MPM — Multi-Processing Module: prefork, worker, event) que trata cada conexão com um processo ou thread dedicado.
- Pontos fortes?
  - Maturidade, módulos extensos (`.htaccess`, mod_rewrite, mod_security), grande comunidade e documentação.
- Quando usar?
  - Hospedagem compartilhada, aplicações legadas (PHP clássico), cenários que dependem de configuração por diretório via `.htaccess`.
- Armadilhas?
  - Consome mais memória sob alta concorrência que servidores orientados a eventos (Nginx); cada conexão ociosa ainda ocupa um worker.

---

## Nginx
- O que é?
  - Servidor web/proxy reverso de alto desempenho, criado para resolver o C10k problem (milhares de conexões simultâneas).
- Como funciona?
  - Arquitetura orientada a eventos (event-driven, assíncrona) com poucos processos worker tratando muitas conexões de forma não bloqueante.
- Pontos fortes?
  - Baixo consumo de memória sob alta concorrência, excelente como proxy reverso, load balancer e servidor de arquivos estáticos; termina TLS com eficiência.
- Quando usar?
  - Front de aplicações (proxy reverso para Node.js/Gunicorn/Uvicorn), servir conteúdo estático, load balancing entre instâncias de aplicação, API Gateway simples.
- Armadilhas?
  - Processamento dinâmico (PHP, por exemplo) exige um processo auxiliar (ex.: PHP-FPM) — Nginx sozinho não executa código de aplicação.

---

## IIS (Internet Information Services)
- O que é?
  - Servidor web da Microsoft, integrado ao Windows Server, nativo para hospedar aplicações .NET.
- Como funciona?
  - Application pools isolam aplicações entre si (processo w3wp.exe por pool); integra com o pipeline do ASP.NET/ASP.NET Core via módulo (ASP.NET Core Module — ANCM).
- Pontos fortes?
  - Integração nativa com o ecossistema Windows/.NET, gerenciamento via GUI, autenticação integrada com Active Directory.
- Quando usar?
  - Aplicações .NET hospedadas em infraestrutura Windows, cenários corporativos com AD/SSO integrado.
- Armadilhas?
  - Atrelado ao Windows (custo de licença, menor portabilidade); em .NET moderno, Kestrel é o servidor de fato e o IIS costuma atuar como reverse proxy na frente dele.

---

## LiteSpeed
- O que é?
  - Servidor web comercial (com versão open-source, OpenLiteSpeed) focado em performance, compatível com configurações do Apache.
- Pontos fortes?
  - Suporte nativo a HTTP/3 (QUIC), cache integrado em nível de servidor (LSCache), baixo consumo de recursos sob carga.
- Quando usar?
  - Hospedagem WordPress/PHP de alta performance, migração de Apache sem reescrever `.htaccess`.
- Armadilhas?
  - Versão completa é paga; comunidade menor que Apache/Nginx.

---

## Caddy
- O que é?
  - Servidor web moderno, escrito em Go, com foco em simplicidade de configuração.
- Pontos fortes?
  - **HTTPS automático** — provisiona e renova certificados TLS (via Let's Encrypt) sem configuração manual; arquivo de configuração (Caddyfile) muito mais simples que Nginx/Apache.
- Quando usar?
  - Projetos pequenos/médios onde simplicidade e HTTPS "out of the box" importam mais do que o ecossistema maduro do Nginx.
- Armadilhas?
  - Ecossistema de módulos e comunidade menores; menos battle-tested em cenários de altíssima escala comparado a Nginx.

---

## Tomcat (Apache Tomcat)
- O que é?
  - Servidor de aplicação (application server) para Java, implementa as especificações Servlet, JSP e WebSocket.
- Como funciona?
  - Executa uma JVM e gerencia o ciclo de vida de servlets/aplicações Java empacotadas em `.war`.
- Quando usar?
  - Aplicações Java/Jakarta EE que precisam de um container de servlets (Spring Boot embute o Tomcat por padrão, por exemplo).
- Armadilhas?
  - Não é um servidor de arquivos estáticos de alta performance — comum colocar Nginx/Apache na frente para servir estáticos e fazer proxy reverso para o Tomcat.

---

## Node.js
- O que é?
  - Runtime JavaScript server-side construído sobre a V8 engine; não é "apenas" um servidor web, mas é citado como tal porque o módulo `http` nativo permite criar um servidor diretamente em JS.
- Como funciona?
  - Single-threaded com event loop e I/O não bloqueante — uma thread trata muitas requisições concorrentes delegando operações de I/O (disco, rede, banco) para o sistema operacional.
- Pontos fortes?
  - Mesma linguagem no front e no back (full-stack JS/TypeScript), ecossistema npm gigantesco, ótimo para I/O-bound workloads (APIs, real-time com WebSockets).
- Quando usar?
  - APIs REST/GraphQL, aplicações real-time (chat, notificações), BFFs.
- Armadilhas?
  - Single-threaded: uma operação CPU-bound mal feita (loop pesado síncrono) bloqueia o event loop e trava todas as requisições; para CPU-bound usar `worker_threads` ou escalar horizontalmente.

---

## Gunicorn (Green Unicorn)
- O que é?
  - Servidor **WSGI** (Web Server Gateway Interface) para Python — a interface padrão entre servidor web e aplicações Python síncronas (Flask, Django clássico).
- Como funciona?
  - Modelo pre-fork: um processo master gerencia múltiplos processos worker (síncronos, por padrão), cada um tratando uma requisição por vez.
- Quando usar?
  - Aplicações Python síncronas (Flask, Django sem ASGI) em produção — nunca usar o servidor de desenvolvimento do Flask/Django em produção.
- Armadilhas?
  - Workers síncronos bloqueiam em I/O; para alta concorrência é preciso ajustar o número de workers/threads ou usar workers assíncronos (gevent/eventlet) — mas para workloads assíncronos nativos, o caminho é ASGI (Uvicorn), não Gunicorn puro.

---

## Uvicorn
- O que é?
  - Servidor **ASGI** (Asynchronous Server Gateway Interface) para Python — a evolução do WSGI que suporta `async/await`, WebSockets e HTTP/2.
- Como funciona?
  - Baseado em `uvloop`/`asyncio`, permite que um único worker trate muitas conexões concorrentes de forma não bloqueante (como o event loop do Node.js).
- Quando usar?
  - Frameworks assíncronos modernos em Python: FastAPI, Starlette, Django com suporte ASGI; APIs com WebSockets ou alta concorrência de I/O.
- Armadilhas?
  - Em produção, é comum combinar Uvicorn com Gunicorn como process manager (`gunicorn -k uvicorn.workers.UvicornWorker`) para ter múltiplos processos + event loop assíncrono em cada um.

---

## Cloud Server
- O que é?
  - Não é um software específico, mas o modelo de servidor **hospedado/gerenciado em nuvem** (AWS, Azure, GCP) — pode ser uma VM (EC2, Azure VM), um serviço de container (ECS, AKS) ou uma plataforma serverless (Lambda, Azure Functions) rodando por trás algum dos servidores acima.
- Pontos fortes?
  - Elasticidade (escala sob demanda), gestão de infraestrutura reduzida, alta disponibilidade facilitada por multi-AZ/multi-region.
- Quando usar?
  - Praticamente todo projeto novo em produção, salvo requisitos específicos de compliance/latência que exijam on-premise.
- Ver também:
  - `nuvem.md` (IaaS/PaaS/SaaS, AZ vs Region) e `alta-disponibilidade.md` (redundância, failover) neste repositório.

---

## Conceitos complementares importantes

### Web Server vs Application Server vs Reverse Proxy
- **Web server**: serve conteúdo — principalmente arquivos estáticos (HTML, CSS, JS, imagens) e, via módulos/gateway, delega execução de código dinâmico (ex.: Apache/Nginx + PHP-FPM).
- **Application server**: executa a lógica de aplicação propriamente dita (Tomcat para Java, Gunicorn/Uvicorn para Python, Kestrel para .NET, o processo Node.js para JS).
- **Reverse proxy**: fica na frente de um ou mais servidores de aplicação, recebendo as requisições dos clientes e repassando para o backend correto — faz TLS termination, load balancing, cache, compressão e rate limiting (ex.: Nginx ou Caddy na frente de Gunicorn/Uvicorn/Node.js/Kestrel).
- Na prática, a maioria dos stacks modernos combina os três: Nginx (reverse proxy + estáticos) → Gunicorn/Uvicorn/Node.js/Kestrel (application server) → aplicação.

### WSGI vs ASGI (Python)
- **WSGI**: interface síncrona, um worker trata uma requisição por vez (Gunicorn padrão, Flask, Django clássico).
- **ASGI**: interface assíncrona, suporta `async/await`, WebSockets, Server-Sent Events e HTTP/2 nativamente (Uvicorn, FastAPI, Starlette).
- Quando migrar de WSGI para ASGI?
  - Quando a aplicação precisa de alta concorrência de I/O (muitas chamadas a APIs externas/banco em paralelo) ou de comunicação real-time (WebSockets).

### Modelo de concorrência — por que isso importa na escolha
- **Processo/thread por conexão** (Apache MPM prefork/worker, Tomcat): simples de entender, isolamento forte entre requisições, mas consome mais memória por conexão simultânea.
- **Single-threaded + event loop** (Nginx, Node.js, Uvicorn): baixíssimo overhead por conexão ociosa, ótimo para I/O-bound, mas uma tarefa CPU-bound mal colocada bloqueia tudo.
- Esse é o critério prático mais citado em entrevista para justificar a escolha entre Apache vs Nginx, ou Gunicorn vs Uvicorn.

---

## Perguntas de entrevista sugeridas
- Qual a diferença entre um web server, um application server e um reverse proxy? Dê um exemplo de stack combinando os três.
- Por que o Nginx lida melhor com alta concorrência que o Apache (MPM prefork)?
- Qual a diferença entre WSGI e ASGI? Quando migrar de Gunicorn para Uvicorn?
- Por que uma operação CPU-bound síncrona pode travar um servidor Node.js inteiro?
- O que o IIS/ANCM faz diferente do Kestrel em uma aplicação ASP.NET Core? Por que ainda se usa um na frente do outro?
- Em que cenário o LiteSpeed ou o Caddy trariam vantagem real sobre Nginx?
- O que muda ao rodar sua aplicação em um Cloud Server gerenciado (ex.: Azure App Service) em vez de uma VM com Nginx configurado manualmente?

---

Notas finais:
- Escolha o servidor pela linguagem/runtime da aplicação (Tomcat para Java, Gunicorn/Uvicorn para Python, Kestrel/IIS para .NET, Node.js para JS) e use um reverse proxy (Nginx/Caddy) na frente para TLS, cache e balanceamento — raramente a aplicação fica exposta diretamente à internet.
- Para aprofundar temas relacionados, veja `loadbalancer.md` (estratégias de balanceamento), `cdn.md` (cache na borda), `nuvem.md` (hospedagem em nuvem) e `alta-disponibilidade.md` (redundância e failover) neste repositório.
