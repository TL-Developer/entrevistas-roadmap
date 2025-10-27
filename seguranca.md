# Segurança — Perguntas e Respostas

 ## GitHub Advanced Security (GHAS)
- O que é?
  - Conjunto de funcionalidades de segurança integradas ao GitHub (Code Scanning, Secret Scanning, Dependabot Alerts, etc.).
- Quais recursos principais?
  - CodeQL/code scanning (SAST), secret scanning, Dependabot security updates, supply chain protections.
- Como ativar?
  - Habilitar GHAS no repositório/organização e configurar workflows/codeql e políticas de branch.
- Benefícios?
  - Integração CI/CD, detecção precoce, correções automáticas (Dependabot), visibilidade consolidada.
- Limitações/armadilhas?
  - Ruídos de falso-positivos, custo em organizações grandes, necessidade de tuning e regras personalizadas.

## Dependabot
- O que é?
  - Ferramenta que abre PRs automáticos para atualizar dependências (security + version).
- Tipos de atualizações?
  - Security updates (vulnerabilidades), version updates, lockfile updates e alertas.
- Boas práticas?
  - Configurar automerge com testes verdes, agrupar PRs por pacote/ecosistema, avaliar breaking changes.
- Riscos?
  - PRs quebrando build; atenção a atualizações transicionais e revisar changelogs.

## Ferramenta de Análise Estática (SAST)
- O que é?
  - Análise do código sem execução para encontrar vulnerabilidades, bugs e padrões inseguros.
- Exemplos?
  - CodeQL, SonarQube, SpotBugs, Fortify, Semgrep.
- Onde integrar?
  - CI/CD (pull request checks), IDE (feedback precoce), gate de qualidade.
- Limitações?
  - Falsos positivos, cobertura limitada para runtime issues e configurações; complemento com DAST/IAST/pen tests.

## Credencial Hard-coded
- O que é o problema?
  - Chaves, senhas ou tokens embutidos no código-fonte que podem vazar nos repositórios.
- Riscos?
  - Comprometimento imediato de serviços, acesso não autorizado e exposição em forks/public repos.
- Como detectar?
  - Secret scanning (GHAS), SAST com regras para padrões de credenciais, varredura de histórico git.
- Como mitigar?
  - Remover do histórico, rotacionar credenciais, usar secret manager (AWS Secrets Manager, HashiCorp Vault), variáveis de ambiente e policies de revisão.
- Boas práticas?
  - Scans automáticos, CI bloqueando commits com secrets, políticas de least privilege e rotação periódica.

## OWASP (Top 10 e Outras Iniciativas)
- O que é?
  - Comunidade que publica guias de segurança web (ex.: OWASP Top 10, ASVS, Cheat Sheets).
- Principais itens do Top 10?
  - Injeção, autenticação quebrada, exposição de dados sensíveis, XXE, controle de acesso inadequado, etc.
- Como usar?
  - Referência para revisão de requisitos, testes de segurança, checklist em code reviews e pen tests.
- Benefícios?
  - Padroniza risco, facilita comunicação com times e requisitos de compliance.

## WAF (Web Application Firewall)
- O que é?
  - Firewall que monitora/filtra tráfego HTTP(S) para bloquear ataques na camada de aplicação (injeção, XSS, botnets).
- Onde aplicar?
  - Na borda (CDN/edge), load balancer ou inline antes da aplicação.
- Tipos de regras?
  - Assinaturas conhecidas, rate limiting, regras customizadas por aplicação, bot mitigation.
- Limitações/armadilhas?
  - Falsos positivos, manutenção de regras, não substitui correção de vulnerabilidades no código.
- Boas práticas?
  - Usar WAF + correção de vulnerabilidades, logs e tuning contínuo, teste de regras em modo de monitor antes do blocking.

## Perguntas de entrevista sugeridas (curtas)
- O que é GHAS e quais recursos ele oferece?
- Como o Dependabot ajuda na segurança e quais cuidados tomar ao usar automerge?
- Quais são limitações de SAST e como complementá-lo?
- Como identificar e mitigar credenciais hard-coded num repositório?
- O que é o OWASP Top 10 e como aplicá-lo no ciclo de desenvolvimento?
- Quando e onde inserir um WAF na arquitetura e quais são seus trade-offs?
