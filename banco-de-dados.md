# Banco de Dados — Perguntas e Respostas

Perguntas comuns de entrevistas com respostas objetivas sobre bancos de dados SQL e NoSQL, índices, comandos SQL, funções, triggers, CDC e tópicos relacionados.

---

## SQL vs NoSQL — quando usar?
- O que é SQL (relacional)?
  - Sistemas ACID com esquema fixo, bom para integridade relacional e consultas complexas (joins, analytics).
- O que é NoSQL?
  - Família: key-value, document, column-family, graph. Flexível, escalável horizontalmente, bom para grandes volumes e modelos sem esquema rígido.
- Quando escolher?
  - SQL: transações fortes, integridade, queries ad-hoc. NoSQL: alta escala, modelagem por acesso, baixa latência, requisitos schemaless.

---

## ACID vs BASE e CAP
- ACID:
  - Atomicidade, Consistência, Isolamento, Durabilidade — típico de RDBMS.
- BASE:
  - Basically Available, Soft state, Eventual consistency — comum em NoSQL distribuído.
- CAP:
  - Consistency, Availability, Partition tolerance — trade-offs ao distribuir dados; escolha depende do problema.

---

## Índices — tipos e quando usar
- O que faz um índice?
  - Acelera buscas/ordenações reduzindo leituras, ao custo de escrita e espaço.
- Tipos comuns:
  - B-tree (padrão para range/ordenação), Hash (lookup exato), GiST / GIN (Postgres — full-text, arrays), inverted index (search engines).
- Conceitos:
  - Índice composto, índice cobridor (covering), índice parcial, índice por expressão, unique index.
- Armadilhas:
  - Over-indexing degrada escrita; índices pouco seletivos são inúteis; manter estatísticas atualizadas (ANALYZE).

---

## Particionamento e Sharding
- O que é particionamento (partitioning)?
  - Dividir tabela por range/hash/list para melhorar performance e manutenção.
- O que é sharding?
  - Particionar dados entre nós independentes (horizontal scale).
- Trade-offs:
  - Simplifica consultas locais, mas complica joins e transações cross-shard.

---

## Comandos SQL mais usados (resumo)
- DQL/Consulta:
  - SELECT ... FROM ... [WHERE] [JOIN] [GROUP BY] [HAVING] [ORDER BY] [LIMIT/OFFSET]
- DML:
  - INSERT INTO ... VALUES / SELECT
  - UPDATE ... SET ... WHERE
  - DELETE FROM ... WHERE
- DDL:
  - CREATE TABLE/INDEX, ALTER TABLE, DROP TABLE/INDEX
- Transações:
  - BEGIN / COMMIT / ROLLBACK
- Controle:
  - GRANT / REVOKE (permissions)
- Utilitários:
  - EXPLAIN / EXPLAIN ANALYZE, VACUUM (Postgres), ANALYZE (estatísticas)

---

## Funções SQL úteis (exemplos)
- Agregação:
  - COUNT(), SUM(), AVG(), MIN(), MAX()
- Window:
  - ROW_NUMBER(), RANK(), DENSE_RANK(), LEAD(), LAG(), SUM() OVER(...)
- Strings e datas:
  - CONCAT(), SUBSTRING(), TRIM(), LOWER()/UPPER(), NOW(), DATE_TRUNC(), DATE_ADD/DATE_SUB
- Nulos e valores:
  - COALESCE(), NULLIF()
- JSON / XML:
  - JSON_EXTRACT / -> / ->> (Postgres/MySQL), JSONB ops, JSON_AGG
- Conversões:
  - CAST(expr AS type), PARSE/FORMAT functions

---

## JOINs — tipos e uso
- INNER JOIN:
  - Apenas linhas que batem em ambas tabelas.
- LEFT/RIGHT OUTER JOIN:
  - Mantém linhas da esquerda/direita mesmo sem correspondência.
- FULL OUTER JOIN:
  - Combina todos, com NULLs onde não há match.
- CROSS JOIN:
  - Produto cartesiano (use com cuidado).
- Recomendações:
  - Indexar colunas de join; evitar joins desnecessários em grandes datasets sem sharding.

---

## Transações e níveis de isolamento
- Níveis:
  - Read Uncommitted, Read Committed, Repeatable Read, Serializable.
- Anomalias:
  - Dirty read, Non-repeatable read, Phantom read.
- Escolha:
  - Trade-off entre performance e consistência; serializable é mais seguro, mais custoso.

---

## Triggers — o que são e quando usar
- O que é?
  - Código executado automaticamente em resposta a eventos (INSERT/UPDATE/DELETE).
- Tipos:
  - BEFORE, AFTER, INSTEAD OF (views).
- Usos:
  - Auditoria, validações complexas, atualização de materialized views, propagation.
- Armadilhas:
  - Hard to debug, impacto em performance, ciclos recursivos; prefira lógica na aplicação se possível.

---

## Change Data Capture (CDC)
- O que é?
  - Captura de mudanças (inserts/updates/deletes) de um banco para replicação/ETL/event sourcing.
- Técnicas:
  - Binlog (MySQL), WAL/logical decoding (Postgres), Debezium (Kafka connector), CDC nativo de fornecedores cloud.
- Usos:
  - Replicação, sincronização entre sistemas, auditing, pipelines de dados em tempo real.
- Considerações:
  - Ordem de eventos, idempotência, performance do log, retenção.

---

## Backup, recuperação e PITR
- Tipos:
  - Backup lógico (dump SQL) vs físico (snapshots).
- Point-in-time recovery (PITR):
  - Restaurar até um momento usando logs de transação/WAL.
- Boas práticas:
  - Testar restores, retenção adequada, automatizar, criptografar backups.

---

## Observabilidade e tuning
- Ferramentas:
  - EXPLAIN ANALYZE, pg_stat_statements, slow query logs, performance schema.
- O que medir?
  - Latência de query, CPU IO waits, locks, contagem de conexões, cache hit ratio.
- Otimizações:
  - Indexes corretos, refatorar queries, materialized views, cache apropriado, connection pooling.

---

## Replicação e alta disponibilidade
- Modelos:
  - Master-slave (primary-replica), multi-primary, consensus (Raft/etcd).
- Failover:
  - Automático via orchestrators ou manual com runbooks.
- Consistência:
  - Síncrona vs assíncrona — latência vs durabilidade.

---

## NoSQL — tipos e exemplos de uso
- Key-Value:
  - Redis, DynamoDB — sessões, caches, counters.
- Document:
  - MongoDB, Couchbase — dados semi-estruturados, APIs rápidas.
- Column-family:
  - Cassandra, HBase — grandes escrituras, timeseries.
- Graph:
  - Neo4j — relacionamentos complexos (social, recomendações).
- Search / inverted index:
  - Elasticsearch — busca full-text, analytics.

---

## Boas práticas gerais
- Modelar por padrões de acesso; evitar transformar RDBMS em NoSQL sem pensar.
- Medir antes de otimizar; otimizar queries antes de escalar hardware.
- Automatizar migrations, usar feature flags para alterações de schema complexas.
- Isolar secrets, usar role-based access, auditar queries sensíveis.

---

## Perguntas de entrevista sugeridas
- Quando criar um índice e quais impactos ele tem?
- Qual a diferença entre particionamento e sharding?
- Como funciona CDC em Postgres/MySQL e quando usar Debezium?
- Quando usar um banco NoSQL em vez de relacional?
- Explique níveis de isolamento e anomalias que previnem.
- Como investigar e otimizar uma query lenta?

--- 

Notas finais:
- Escolha banco e modelagem conforme requisitos de consistência, escala e padrões de acesso.
- Teste backups e restores; monitore métricas e revise índices/estatísticas periodicamente.