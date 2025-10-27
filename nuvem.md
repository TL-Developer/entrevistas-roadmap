# Nuvem — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre modelos de nuvem, camadas de serviço e arquitetura regional.

---

## Modelos de implantação: Nuvem Pública, Privada e Híbrida
- O que é nuvem pública?
  - Serviços oferecidos por provedores externos (AWS, Azure, GCP) acessíveis via internet; escalabilidade e gestão terceirizada.
- Quando usar?
  - Agilidade, escalabilidade elástica e menor overhead operacional.
- O que é nuvem privada?
  - Infraestrutura dedicada a uma organização (on-premise ou hosted) com maior controle e isolamento.
- Quando usar?
  - Requisitos de compliance, latência local, controle físico ou workloads sensíveis.
- O que é nuvem híbrida?
  - Combinação de nuvem pública e privada com integração de rede e gestão; workloads movem-se conforme requisitos.
- Quando usar?
  - Migração incremental, requisitos de dados residenciais ou burst para pública.

---

## Modelos de serviço: IaaS, PaaS, SaaS
- O que é IaaS?
  - Infrastructure as a Service — VMs, storage, redes gerenciadas pelo provedor; cliente gerencia SO e apps.
- Vantagem?
  - Controle granular da infraestrutura; bom para lift-and-shift.
- O que é PaaS?
  - Platform as a Service — plataforma gerenciada (runtime, DB managed, build packs); foca no deploy de apps.
- Vantagem?
  - Menos operação, deploy mais rápido e escalonamento automático.
- O que é SaaS?
  - Software as a Service — aplicação completa consumida via web (ex.: Office 365, Salesforce).
- Vantagem?
  - Zero gestão de infra; foco no uso do produto.

---

## Zona (Availability Zone) vs Região (Region)
- O que é Availability Zone (AZ)?
  - Data center isolado dentro de uma região com redundância de energia/rede; projetada para falhas independentes.
- O que é Region?
  - Conjunto de AZs em uma localização geográfica (ex.: us-east-1); isolamento geográfico e conformidade.
- Por que separar por AZ?
  - Alta disponibilidade: replicação entre AZs reduz risco de falha de datacenter.
- Quando usar múltiplas regiões?
  - Tolerância a desastre geográfica, menor latência para usuários globais e requisitos de residência de dados.

---

## Multi-Region — padrões e trade-offs
- O que é multi-region?
  - Deploy em várias regiões geográficas ativas ou passivas.
- Padrões comuns:
  - Active-passive: replicação e failover para região secundária.
  - Active-active: tráfego roteado para várias regiões com replicação e resolução de consistência.
  - Geo-sharding: particionamento de dados por região/usuário.
- Trade-offs?
  - Consistência de dados (latência de replicação), custo aumentado, complexidade de deploy e observabilidade.
- Quando escolher?
  - Necessidade de baixa latência global, conformidade/regulação ou alta disponibilidade regional.

---

## Rede, Latência e Conectividade
- Como conectar on-premise e cloud?
  - VPN site-to-site, Direct Connect / ExpressRoute para links dedicados e baixa latência.
- O que considerar sobre latência?
  - Proximidade da região ao usuário, uso de CDN e replicação de dados para reduzir RTT.
- Segurança de rede?
  - Segmentar com VPC/VNet, usar peering, firewalls gerenciados, e controle de identidade (IAM).

---

## Dados e Consistência
- Estratégias de replicação de dados?
  - Read replicas, cross-region replication, CDC/streaming para sincronização.
- Escolha entre consistency e latency?
  - Priorize consistência forte para transações críticas; eventual consistency para leitura escalável com baixa latência.

---

## Custo e Operação
- Como otimizar custo na nuvem?
  - Right-sizing, autoscaling, instâncias reservadas/savings plans, tiering de storage e lifecycle policies.
- Observabilidade e SRE?
  - Monitorar custo por serviço, alertas por gasto anômalo e runbooks para failover.

---

## Perguntas de entrevista sugeridas
- Qual a diferença prática entre IaaS e PaaS? Quando escolher cada um?
- Quando optar por nuvem privada vs pública?
- O que é uma Availability Zone e por que ela importa?
- Quais problemas surgem em arquitetura multi-region active-active?
- Como projetar replicação de dados cross-region com latência aceitável?

--- 

Notas finais:
- Escolha modelo e região conforme requisitos de latência, compliance e custo.
- Teste failover e recuperação regularmente e automatize provisão via IaC.