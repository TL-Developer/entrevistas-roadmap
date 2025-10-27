# Arquitetura de Software — Perguntas e Respostas

Abaixo perguntas comuns de entrevistas com respostas objetivas sobre arquiteturas: Clean Architecture, MVC, Hexagonal (Ports & Adapters) e Onion Architecture.

---

## Clean Architecture
- O que é?
  - Arquitetura por camadas concêntricas que coloca regras de negócio (entidades, casos de uso) no centro, isolando-as de frameworks, UI e infraestrutura.
- Qual é a responsabilidade de cada camada?
  - Entidades: regras de negócio puras; Use Cases/Interactors: orquestram lógica de aplicação; Interface Adapters: adaptam dados para UI/DB; Frameworks/Drivers: detalhes externos.
- Quais são os benefícios?
  - Independência de UI/DB, testabilidade, facilidade para trocar tecnologias, clareza de dependências (dependência aponta para o centro).
- Quais as desvantagens/trade-offs?
  - Sobreengenharia para projetos simples, mais abstrações e boilerplate, curva de aprendizado.
- Quando aplicar?
  - Sistemas médios/grandes com requisitos de manutenção a longo prazo ou necessidade de trocas tecnológicas.

---

## MVC (Model-View-Controller)
- O que é?
  - Padrão que separa aplicação em Modelo (dados/estado), View (apresentação) e Controller (entrada/coordenação).
- Como as responsabilidades se dividem?
  - Model: domínio/estado; View: renderização; Controller: interpreta eventos, atualiza model e view.
- Onde é mais usado?
  - Aplicações web clássicas e GUIs; frameworks como Rails, ASP.NET MVC, Spring MVC.
- Limitações comuns?
  - Controller pode crescer demais (fat controller), acoplamento entre controller e view se não houver camadas intermediárias.
- Quando preferir MVVM ou Flux em vez de MVC?
  - Interfaces ricas e data-binding intenso -> MVVM; aplicações single-page com fluxo unidirecional -> Flux/Redux.

---

## Hexagonal Architecture (Ports & Adapters)
- O que é?
  - Arquitetura que define um núcleo de aplicação independente e "portas" que descrevem interfaces; "adaptadores" ligam portas a implementações externas (DB, UI, testes).
- Diferença principal para Clean Architecture?
  - Conceitualmente semelhantes; hexagonal enfatiza interação através de portas/adapters e bidirecionalidade, Clean organiza em círculos com foco em dependência dirigida ao centro.
- Benefícios práticos?
  - Facilita testes substituindo adaptadores, isolamento do core, clareza sobre pontos de integração.
- Exemplo de porta/adaptador?
  - Porta: interface de repositório; Adaptador: implementação concreta para PostgreSQL, outra para testes em memória.
- Quando usar?
  - Projetos que precisam de alta testabilidade e trocas frequentes de integrações externas.

---

## Onion Architecture
- O que é?
  - Variante concêntrica onde o domínio (modelos e regras) fica no núcleo e camadas externas dependem apenas de camadas internas; infraestrutura do lado de fora.
- Diferenças para Clean Architecture?
  - Muito próximas; Onion enfatiza explicitamente o Domain Model no centro e políticas de dependência "inside-out".
- Como tratar persistência/transações?
  - Interfaces (repositório) definidas nas camadas internas; implementações colocadas nas camadas externas; unidade de trabalho adaptada por uma camada de infraestrutura.
- Vantagens e trade-offs?
  - Forte proteção do domínio, testabilidade; similar a Clean — adiciona complexidade para sistemas simples.

---

## Perguntas práticas e de projeto
- Onde colocar validação de negócio vs validação de entrada?
  - Validação de entrada (formatos, tipos) na borda (UI/API); validação de negócio (regras, invariantes) no domínio/interactors.
- Em qual camada a lógica de autorização/autenticação fica?
  - Cross-cutting: decisões de autenticação podem ocorrer na borda (middleware), autorização de regras específicas no domínio/casos de uso.
- Banco de dados deve conhecer regras de negócio?
  - Preferir manter regras no domínio; triggers/constraints no DB apenas para invariantes críticas e redundância de segurança.
- Como migrar um monólito legado para Clean/Hexagonal sem grande risco?
  - Extrair funcionalidades uma a uma para componentes com interfaces claras (strangling pattern), criar adaptadores que delegam para código legado até a substituição.
- Como medir que a arquitetura está ajudando (indicadores)?
  - Tempo para adicionar trocar tecnologia, número de bugs regressivos, facilidade de testagem (cobertura unitária), tempo de deploy.

---

Notas finais:
- Escolha arquitetura pelo contexto: equipe, ciclo de vida, complexidade do domínio e necessidades de teste/manutenção.
- Arquiteturas são guias; evite aplicar camadas extras sem necessidade.