# Docker & Kubernetes — Perguntas e Respostas

Documenta perguntas comuns de entrevistas com respostas objetivas sobre Docker e Kubernetes.

---

## Docker

- O que é Docker?
  - Plataforma para empacotar aplicações em containers isolados. Images → Containers.

- O que é uma image vs container?
  - Image: artefato imutável (snapshot de filesystem + metadata). Container: instância em execução da image.

- Como reduzir o tamanho de uma image?
  - Usar imagens base enxutas (alpine/distroless), multi-stage builds e remover arquivos temporários.

- O que é Dockerfile e instruções importantes?
  - Arquivo que descreve build de image. Instruções comuns: FROM, RUN, COPY, ADD, CMD, ENTRYPOINT, EXPOSE, ENV.

- Como persistir dados em containers?
  - Volumes (managed by Docker) ou bind mounts. Volumes para dados persistentes e portáveis.

- Como funciona networking em Docker?
  - Drivers: bridge (padrão), host, overlay (swarm), macvlan. Containers no mesmo network resolvem por nome.

- O que é Docker Compose?
  - Ferramenta para definir e executar multi-containers via arquivo docker-compose.yml (desenvolvimento/stack local).

- Como inspecionar logs e o estado de um container?
  - docker logs <container>, docker ps, docker inspect <container>.

- Como garantir segurança de images?
  - Scans (Trivy, Clair), minimizar privilégios, não rodar como root, assinar images (notary), usar runtime de container seguro.

- Quando usar containers em vez de VMs?
  - Quando precisar de boot rápido, densidade maior e isolamento leve; VMs para isolamento de hardware/hipervisor.

---

## Kubernetes (K8s)

- O que é Kubernetes?
  - Orquestrador de containers para deploy, escala e gerenciamento de aplicações em cluster.

- Conceitos básicos: Pod, Deployment, Service?
  - Pod: unidade mínima executando um ou mais containers. Deployment: gerencia réplicas e atualizações. Service: abstração de acesso (ClusterIP/NodePort/LoadBalancer).

- O que é Namespace?
  - Segmentação lógica no cluster para isolamento de recursos e quotas.

- Como expor uma aplicação externamente?
  - Service tipo LoadBalancer (cloud), Ingress (HTTP routing + TLS) com Ingress Controller.

- O que são ConfigMap e Secret?
  - ConfigMap: configurações não sensíveis. Secret: dados sensíveis (base64), evitar expor em plaintext e usar KMS quando possível.

- Quando usar StatefulSet vs Deployment?
  - StatefulSet para workloads com identidade estável, storage persistente e ordenação (bancos, Kafka). Deployment para stateless.

- O que é DaemonSet?
  - Garante um pod por nó (ex.: log/monitoring agents).

- O que é Job e CronJob?
  - Job: tarefa batch que roda até conclusão. CronJob: Job agendado periodicamente.

- Como funciona armazenamento persistente (PV/PVC, StorageClass)?
  - PV: recurso de storage no cluster. PVC: pedido de armazenamento por um pod. StorageClass: provisionamento dinâmico e parâmetros do provedor.

- O que são Liveness e Readiness Probes?
  - Liveness: determina se pod deve ser reiniciado. Readiness: indica se pod aceita tráfego; controla inclusão no Service.

- Como realizar rolling update e rollback?
  - Deployments suportam rolling updates via estrategia (maxUnavailable/maxSurge). kubectl rollout undo para rollback.

- Como controlar recursos (requests/limits)?
  - Definir requests (garantia) e limits (cap) de CPU/mem. Usar QoS classes e ResourceQuota em namespaces.

- O que é Horizontal Pod Autoscaler (HPA)?
  - Escala réplicas de pod horizontalmente com base em métricas (CPU, custom metrics).

- O que é Cluster Autoscaler?
  - Ajusta número de nós no provedor cloud conforme necessidade de pods pendentes.

- O que é RBAC em K8s?
  - Role-Based Access Control: Roles/ClusterRoles + RoleBindings para controlar permissões.

- O que é Helm?
  - Gerenciador de pacotes para Kubernetes (charts) que parametriza e versiona deploys.

- O que são Operators?
  - Extensão que implementa lógica específica do domínio (CRDs + controllers) para gerenciar aplicativos complexos.

- Como depurar pods com problemas?
  - kubectl describe pod, kubectl logs, kubectl exec -it, events, examinar nodes, revisar quotas e probes.

- Segurança: como minimizar riscos no cluster?
  - Policies: NetworkPolicy, PodSecurity (PSP/PSA), usar namespaces, RBAC mínimo, imagens assinadas, node hardening e secrets gerenciados.

- O que é NetworkPolicy?
  - Regras L3/L4 que controlam tráfego entre pods/namespaces; depende do CNI provider.

- O que é CRI/CNI/CPI?
  - CRI: Container Runtime Interface (docker/containerd). CNI: Container Network Interface (rede). CPI: Cloud Provider Interface (integração cloud).

- Boas práticas para produção?
  - Health checks, readiness probes, resource requests/limits, liveness, logging/monitoring/tracing, secure defaults, usar declarative GitOps, backups de etcd.

---

## Perguntas de entrevista sugeridas (curtas)
- Qual diferença entre container orchestration e container runtime?
- O que é um Pod e por que pode conter múltiplos containers?
- Como funcionam rolling updates em um Deployment?
- Quando usar StatefulSet em vez de Deployment?
- Como configurar persistência de dados em K8s (PV/PVC)?
- Como o K8s decide reiniciar um pod com liveness probe?
- O que faz o Ingress Controller e por que é necessário?
- Explique RBAC e como restringir acesso a um namespace.
- O que é um ServiceAccount e para que serve?
- Quais métricas você monitora para autoscaling?

--- 

Notas finais:
- Diferencie conceitos operacionais (Docker local, Compose) de produção (Kubernetes, CI/CD).
- Priorize pequenas imagens, testes de probes e limites de recursos antes de escalar.
- Use ferramentas de observabilidade e politicas de segurança para ambientes de produção.
// ...existing code...