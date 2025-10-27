# DevOps & Pipeline CI/CD — Perguntas e Respostas

Abaixo perguntas comuns de entrevistas com respostas objetivas sobre pipeline CI/CD, DevOps, SRE, canary, blue-green, Terraform, multi-region e on-premise.

---

## O que é DevOps?
- O que é?
  - Cultura e práticas que unem desenvolvimento e operações para entrega contínua, automação e feedback rápido.
- Objetivo?
  - Acelerar entrega de software com qualidade, reduzir silos e melhorar colaboração.
- Métricas comuns (DORA)?
  - Lead time for changes, Deployment frequency, Mean time to restore (MTTR), Change failure rate.

---

## O que é SRE (Site Reliability Engineering)?
- O que é?
  - Abordagem operacional que aplica engenharia para construir e operar serviços confiáveis (prática criada pelo Google).
- Foco principal?
  - SLOs/SLIs, automação, redução de toil e resposta a incidentes.
- Diferença DevOps vs SRE?
  - DevOps é cultura/práticas; SRE é função/implementação focada em confiabilidade com objetivos mensuráveis (SLOs).

---

## O que é um pipeline CI/CD?
- O que é?
  - Conjunto automatizado de etapas que vai do commit ao deploy: build, test, security scans, artefatos, deploy e verificação.
- Fases típicas?
  - CI: checkout → build → unit tests → static analysis → artifact publish.
  - CD: staging deploy → integration/e2e tests → approval → production deploy → smoke tests.
- Ferramentas populares?
  - Jenkins, GitHub Actions, GitLab CI, Azure DevOps, CircleCI, Tekton.
- Boas práticas?
  - Pipelines curtos, testes paralelos, fail fast, promover artefatos imutáveis, infra como código e rollback automático.

---

## O que é Continuous Integration (CI) e Continuous Delivery/Deployment (CD)?
- CI:
  - Merge frequente de mudanças e execução automática de builds/tests.
- Continuous Delivery:
  - Artefatos sempre prontos para deploy manual com um clique.
- Continuous Deployment:
  - Deploy automático para produção após passar as gates.

---

## Como projetar pipelines seguros e eficientes?
- Dicas rápidas:
  - Isolar credenciais (secret store), executar SAST/DAST, usar ambientes efêmeros, cache de dependências, monitorar tempo de pipeline, executar testes críticos primeiro e usar canary/circuit-breakers no deploy.

---

## O que é Canary Deployment?
- O que é?
  - Liberar mudança para pequena porcentagem de tráfego/instâncias e aumentar gradualmente observando métricas.
- Vantagens?
  - Detectar regressões em produção com impacto limitado.
- Requisitos?
  - Feature flags, roteamento por tráfego (LB/Ingress), métricas p95/p99, alerting e rollback automático.
- Quando usar?
  - Releases de alto risco ou mudanças que impactam experiência do usuário.
- Armadilhas?
  - Telemetria insuficiente, stateful changes não compatíveis, limpeza de dados de teste.

---

## O que é Blue-Green Deployment?
- O que é?
  - Manter duas versões (blue/green). Deploy na green, validar e então trocar tráfego para green; blue fica como fallback.
- Vantagens?
  - Switch instantâneo e rollback trivial.
- Desvantagens?
  - Duplica infra (custo), cuidado com migração de schema/state.
- Quando preferir?
  - Deploys que exigem cutover rápido e rollback imediato.

---

## Canary vs Blue-Green — quando escolher?
- Canary:
  - Melhor para mudanças graduais e monitoramento fino.
- Blue-Green:
  - Simples cutover/rollback, preferível quando infra suportar duplicação e mudanças de estado são controladas.

---

## O que é Terraform (IaC)?
- O que é?
  - Ferramenta de Infrastructure as Code para provisionar recursos (multi-cloud) via HCL.
- Conceitos chave?
  - State (arquivo remoto/state backend), providers, resources, modules e plan/apply.
- Boas práticas?
  - Usar state remoto com locking (S3+Dynamo/Backend), modularizar, revisar terraform plan via PR, versionar modules e controlar secrets fora do state.
- Riscos comuns?
  - Drift entre infra e código, gerenciar mudanças destrutivas, state corrompido sem locking.

---

## O que é multi-region e quais são os trade-offs?
- O que é?
  - Distribuir aplicação/infra em múltiplas regiões geográficas para latência, resiliência e conformidade.
- Padrões de dados?
  - Active-passive (failover), active-active (replicação/consistency), read-replicas e sharding por região.
- Considerações?
  - Latência de replicação, consistência (CAP), custo, failover automatizado, DNS/global LB, compliance/região.
- Quando usar?
  - Aplicações globais com requisitos de alta disponibilidade e baixa latência regional.

---

## Considerações On-Premise vs Cloud
- On-Premise desafios?
  - Provisionamento mais lento, capacidade limitada, networking corporativo, compliance e hardware lifecycle.
- Integração híbrida?
  - VPN/Direct Connect, identity federation, replicação de dados e IaC para ambos ambientes.
- Quando optar por on-premise?
  - Requisitos de latência local, regulamentação, controle físico ou custos previsíveis em larga escala.

---

## Deploy em múltiplas regiões/on-premise — práticas
- Estratégias:
  - Automatizar infra com Terraform/Ansible, usar pipelines multi-tenant, provisionar ambientes idempotentes, testar failover, e usar monitoramento global.
- Observabilidade:
  - Collectors regionais, trace distribuído, alertas por região e runbooks para recovery.

---

## Rollback e estratégias de segurança em deploys
- Estratégias:
  - Rollback automático em canary, manter versão anterior pronta (blue-green), feature flags e database migrations backward-compatible.
- Segurança:
  - Gate de aprovação para mudanças sensíveis, escopos mínimos, deploy em janelas controladas e auditoria de deploys.

---

## Perguntas de entrevista sugeridas
- O que é DORA e por que importa?
- Como você implementaria canary com rollback automático?
- Quais trade-offs ao usar multi-region active-active?
- Como gerenciar state do Terraform em equipe?
- Quando preferir blue-green vs canary?
- Como operar pipelines para infra on‑premise e cloud de forma unificada?

```// filepath: c:\Git\entrevistas-roadmap\devops.md
// ...existing code...
{ changed code }
// ...existing code...
# DevOps & Pipeline CI/CD — Perguntas e Respostas

Abaixo perguntas comuns de entrevistas com respostas objetivas sobre pipeline CI/CD, DevOps, SRE, canary, blue-green, Terraform, multi-region e on-premise.

---

## O que é DevOps?
- O que é?
  - Cultura e práticas que unem desenvolvimento e operações para entrega contínua, automação e feedback rápido.
- Objetivo?
  - Acelerar entrega de software com qualidade, reduzir silos e melhorar colaboração.
- Métricas comuns (DORA)?
  - Lead time for changes, Deployment frequency, Mean time to restore (MTTR), Change failure rate.

---

## O que é SRE (Site Reliability Engineering)?
- O que é?
  - Abordagem operacional que aplica engenharia para construir e operar serviços confiáveis (prática criada pelo Google).
- Foco principal?
  - SLOs/SLIs, automação, redução de toil e resposta a incidentes.
- Diferença DevOps vs SRE?
  - DevOps é cultura/práticas; SRE é função/implementação focada em confiabilidade com objetivos mensuráveis (SLOs).

---

## O que é um pipeline CI/CD?
- O que é?
  - Conjunto automatizado de etapas que vai do commit ao deploy: build, test, security scans, artefatos, deploy e verificação.
- Fases típicas?
  - CI: checkout → build → unit tests → static analysis → artifact publish.
  - CD: staging deploy → integration/e2e tests → approval → production deploy → smoke tests.
- Ferramentas populares?
  - Jenkins, GitHub Actions, GitLab CI, Azure DevOps, CircleCI, Tekton.
- Boas práticas?
  - Pipelines curtos, testes paralelos, fail fast, promover artefatos imutáveis, infra como código e rollback automático.

---

## O que é Continuous Integration (CI) e Continuous Delivery/Deployment (CD)?
- CI:
  - Merge frequente de mudanças e execução automática de builds/tests.
- Continuous Delivery:
  - Artefatos sempre prontos para deploy manual com um clique.
- Continuous Deployment:
  - Deploy automático para produção após passar as gates.

---

## Como projetar pipelines seguros e eficientes?
- Dicas rápidas:
  - Isolar credenciais (secret store), executar SAST/DAST, usar ambientes efêmeros, cache de dependências, monitorar tempo de pipeline, executar testes críticos primeiro e usar canary/circuit-breakers no deploy.

---

## O que é Canary Deployment?
- O que é?
  - Liberar mudança para pequena porcentagem de tráfego/instâncias e aumentar gradualmente observando métricas.
- Vantagens?
  - Detectar regressões em produção com impacto limitado.
- Requisitos?
  - Feature flags, roteamento por tráfego (LB/Ingress), métricas p95/p99, alerting e rollback automático.
- Quando usar?
  - Releases de alto risco ou mudanças que impactam experiência do usuário.
- Armadilhas?
  - Telemetria insuficiente, stateful changes não compatíveis, limpeza de dados de teste.

---

## O que é Blue-Green Deployment?
- O que é?
  - Manter duas versões (blue/green). Deploy na green, validar e então trocar tráfego para green; blue fica como fallback.
- Vantagens?
  - Switch instantâneo e rollback trivial.
- Desvantagens?
  - Duplica infra (custo), cuidado com migração de schema/state.
- Quando preferir?
  - Deploys que exigem cutover rápido e rollback imediato.

---

## Canary vs Blue-Green — quando escolher?
- Canary:
  - Melhor para mudanças graduais e monitoramento fino.
- Blue-Green:
  - Simples cutover/rollback, preferível quando infra suportar duplicação e mudanças de estado são controladas.

---

## O que é Terraform (IaC)?
- O que é?
  - Ferramenta de Infrastructure as Code para provisionar recursos (multi-cloud) via HCL.
- Conceitos chave?
  - State (arquivo remoto/state backend), providers, resources, modules e plan/apply.
- Boas práticas?
  - Usar state remoto com locking (S3+Dynamo/Backend), modularizar, revisar terraform plan via PR, versionar modules e controlar secrets fora do state.
- Riscos comuns?
  - Drift entre infra e código, gerenciar mudanças destrutivas, state corrompido sem locking.

---

## O que é multi-region e quais são os trade-offs?
- O que é?
  - Distribuir aplicação/infra em múltiplas regiões geográficas para latência, resiliência e conformidade.
- Padrões de dados?
  - Active-passive (failover), active-active (replicação/consistency), read-replicas e sharding por região.
- Considerações?
  - Latência de replicação, consistência (CAP), custo, failover automatizado, DNS/global LB, compliance/região.
- Quando usar?
  - Aplicações globais com requisitos de alta disponibilidade e baixa latência regional.

---

## Considerações On-Premise vs Cloud
- On-Premise desafios?
  - Provisionamento mais lento, capacidade limitada, networking corporativo, compliance e hardware lifecycle.
- Integração híbrida?
  - VPN/Direct Connect, identity federation, replicação de dados e IaC para ambos ambientes.
- Quando optar por on-premise?
  - Requisitos de latência local, regulamentação, controle físico ou custos previsíveis em larga escala.

---

## Deploy em múltiplas regiões/on-premise — práticas
- Estratégias:
  - Automatizar infra com Terraform/Ansible, usar pipelines multi-tenant, provisionar ambientes idempotentes, testar failover, e usar monitoramento global.
- Observabilidade:
  - Collectors regionais, trace distribuído, alertas por região e runbooks para recovery.

---

## Rollback e estratégias de segurança em deploys
- Estratégias:
  - Rollback automático em canary, manter versão anterior pronta (blue-green), feature flags e database migrations backward-compatible.
- Segurança:
  - Gate de aprovação para mudanças sensíveis, escopos mínimos, deploy em janelas controladas e auditoria de deploys.

---

## Perguntas de entrevista sugeridas
- O que é DORA e por que importa?
- Como você implementaria canary com rollback automático?
- Quais trade-offs ao usar multi-region active-active?
- Como gerenciar state do Terraform em equipe?
- Quando preferir blue-green vs canary?
- Como operar pipelines para infra on‑premise e cloud de forma unificada?
