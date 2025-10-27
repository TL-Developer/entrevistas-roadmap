# Estruturas de Dados — Perguntas e Respostas

Este documento lista perguntas comuns de entrevistas com respostas objetivas sobre estruturas de dados: list, array, stack, queue, heap, tree, suffix tree, graph, R-tree e hash table.

---

## Lista (List)
- O que é?
  - Coleção ordenada de elementos que permite iteração e inserções/remoções em posições arbitrárias (dependendo da implementação).
- Operações principais e complexidade (lista ligada típica):
  - Acesso por índice: O(n)
  - Inserção/remoção no início: O(1)
  - Inserção/remoção no meio: O(n) (sem referência direta)
  - Iteração: O(n)
- Quando usar?
  - Quando são frequentes inserções/remoções no meio ou início e não é necessário acesso aleatório eficiente.
- Implementação / Dicas:
  - Use lista ligada simples para memória dinâmica; lista duplamente ligada para remoção bidirecional eficiente.
- Armadilhas:
  - Uso inadequado quando acesso por índice frequente é necessário — preferir array/ArrayList.

---

## Array
- O que é?
  - Estrutura contígua de memória com elementos do mesmo tipo e acesso por índice em tempo constante.
- Operações principais e complexidade:
  - Acesso por índice: O(1)
  - Inserção/remoção no fim (amortizado em dinâmica): O(1) amortizado (push/pop)
  - Inserção/remoção no meio: O(n)
  - Busca linear: O(n)
- Quando usar?
  - Quando precisar de acesso aleatório rápido e memória contígua (cache-friendly).
- Implementação / Dicas:
  - Para tamanho variável, use array dinâmico (crescimento exponencial) para manter amortização.
- Armadilhas:
  - Redimensionamento custoso se implementado incorretamente; cuidado com memória e alinhamento.

---

## Pilha (Stack)
- O que é?
  - Coleção LIFO (last in, first out) — empilha e desempilha no topo.
- Operações principais e complexidade:
  - push/pop/peek: O(1)
- Quando usar?
  - Backtracking, avaliação de expressões, chamadas recursivas simuladas.
- Implementação / Dicas:
  - Pode ser implementada por array ou lista ligada; preferir array quando tamanho previsível (mais cache-friendly).
- Armadilhas:
  - Overflow em implementação estática; stack depth em recursão.

---

## Fila (Queue)
- O que é?
  - Coleção FIFO (first in, first out) — enfileira no fim, desenfileira no início.
- Operações principais e complexidade:
  - enqueue/dequeue/peek: O(1)
- Quando usar?
  - Buffering, processamento por ordem de chegada, BFS.
- Implementação / Dicas:
  - Use deque circular para implementar em array; listas ligadas para flexibilidade.
- Armadilhas:
  - Implementação simples de array sem circularidade causa desperdício e necessidade de shift O(n).

---

## Heap (Min-heap / Max-heap)
- O que é?
  - Árvore binária completa representada em array garantindo propriedade de heap (pai ≤ filhos para min-heap).
- Operações principais e complexidade:
  - inserir: O(log n)
  - extrair mínimo/máximo: O(log n)
  - construir heap a partir de array: O(n)
- Quando usar?
  - Filas de prioridade, seleção kth, algoritmos como Dijkstra.
- Implementação / Dicas:
  - Representação em array com índice i: filhos 2i+1, 2i+2.
- Armadilhas:
  - Não fornece busca ou remoção arbitrária eficiente sem índices auxiliares.

---

## Árvore (Tree) — geral (BST, AVL, Red-Black)
- O que é?
  - Estrutura hierárquica de nós com referência para filhos; vários tipos com propriedades diferentes.
- Operações principais e complexidade (BST balanceada):
  - busca/inserção/remoção: O(log n)
  - travessia: O(n)
- Quando usar?
  - Dados hierárquicos, índices de busca, representação de expressões.
- Implementação / Dicas:
  - Para desempenho garantido, usar árvores balanceadas (AVL, Red-Black).
- Armadilhas:
  - BST não balanceada pode degenerar para lista (O(n)).

---

## Suffix Tree (Árvore de sufixos)
- O que é?
  - Estrutura que indexa todos os sufixos de uma string em tempo/espaco quase linear; permite buscas de substring rápidas.
- Operações principais e complexidade:
  - Construção (Ukkonen): O(n)
  - Busca de padrão: O(m) onde m = comprimento do padrão
- Quando usar?
  - Pesquisa de padrões, encontrar substrings repetidas, compressão, bioinformática.
- Implementação / Dicas:
  - Implementação complexa; para muitos casos, suffix array + LCP é mais simples e econômico em memória.
- Armadilhas:
  - Alto custo de implementação e memória; cuidado com alfabetos grandes.

---

## Grafo (Graph)
- O que é?
  - Conjunto de vértices e arestas (dirigidas ou não); pode ser representado por matriz de adjacência ou lista de adjacência.
- Operações principais e complexidade:
  - Iterar adjacências: O(V + E) usando lista de adjacência
  - Checagem de aresta: O(1) em matriz, O(deg(v)) em lista
- Quando usar?
  - Modelagem de redes, dependências, rotas, fluxos.
- Implementação / Dicas:
  - Use lista de adjacência para grafos esparsos, matriz para densidade alta ou verificações O(1).
- Armadilhas:
  - Cuidado com ciclos e componentes conectados; escolha algoritmo (BFS/DFS, Dijkstra, Bellman-Ford, Floyd-Warshall) conforme propriedades (pesos, negativos).

---

## R-tree
- O que é?
  - Índice espacial para objetos multidimensionais (retângulos mínimos); agrupa objetos próximos hierarquicamente.
- Operações principais e complexidade:
  - Busca por região: O(log n) média (dependente de empacotamento)
  - Inserção/remoção: O(log n) média com split heurístico
- Quando usar?
  - Bancos de dados espaciais, GIS, consultas de proximidade e interseção.
- Implementação / Dicas:
  - Várias variantes (R*-Tree melhora heurísticas de split/ reinserção).
- Armadilhas:
  - Sensível à heurística de divisão; desempenho degrade com má distribuição de dados.

---

## Hash Table (Tabela Hash)
- O que é?
  - Estrutura que mapeia chaves para valores usando função hash para acesso médio O(1).
- Operações principais e complexidade:
  - busca/inserção/remoção: O(1) médio, O(n) pior caso (colisões)
- Quando usar?
  - Lookup rápido, contagem, caches.
- Implementação / Dicas:
  - Escolher boa função hash, usar tratamento de colisões (encadeamento ou open addressing) e redimensionamento (load factor).
- Armadilhas:
  - Colisões e ataques por colisão (doS) se hash previsível; iterar em ordem não garantida.

---

Notas finais:
- Sempre explique restrições (memória, padrões de acesso) para justificar a escolha da estrutura.
- Complexidades citadas são típicas; existem variantes com trade-offs diferentes.

# ALGORITMOS

## Busca Binária (Binary Search)
- O que é?
  - Pesquisa eficiente em array ordenado dividindo o espaço de busca ao meio recursiva ou iterativamente.
- Complexidade:
  - Tempo: O(log n), Espaço: O(1) iterativo / O(log n) recursivo.
- Quando usar?
  - Procurar elemento exato ou limites em coleção ordenada.
- Armadilhas:
  - Requer ordenação prévia; cuidado com overflow ao calcular mid (use low + (high-low)/2).

---

## BFS (Busca em Largura)
- O que é?
  - Travessia de grafo/árvore por níveis usando fila.
- Complexidade:
  - Tempo: O(V + E), Espaço: O(V).
- Quando usar?
  - Encontrar caminho mais curto em grafo não ponderado, ordem por nível.
- Armadilhas:
  - Necessidade de marcação de visitados para evitar loops.

---

## DFS (Busca em Profundidade)
- O que é?
  - Travessia que explora profundamente um ramo antes de retroceder (recursiva ou pilha).
- Complexidade:
  - Tempo: O(V + E), Espaço: O(V) (recursão/pilha).
- Quando usar?
  - Detecção de ciclos, ordenação topológica, componentes conectados.
- Armadilhas:
  - Profundidade de recursão pode estourar a stack; use versão iterativa se necessário.

---

## Dijkstra
- O que é?
  - Algoritmo para caminhos mínimos em grafos com arestas de peso não negativo.
- Complexidade:
  - Tempo: O((V + E) log V) com heap binário; Espaço: O(V).
- Quando usar?
  - Roteamento e rotas com pesos não negativos.
- Armadilhas:
  - Não funciona com arestas negativas.

---

## Bellman-Ford
- O que é?
  - Algoritmo para caminhos mínimos que suporta arestas com peso negativo e detecta ciclos negativos.
- Complexidade:
  - Tempo: O(V * E), Espaço: O(V).
- Quando usar?
  - Grafos com arestas negativas ou quando precisa detectar ciclos de peso negativo.
- Armadilhas:
  - Mais lento que Dijkstra em grafos grandes sem pesos negativos.

---

## A* (Busca A*)
- O que é?
  - Busca informada que usa função f(n)=g(n)+h(n) (g=distância já percorrida, h=heurística admissível) para encontrar caminho ótimo.
- Complexidade:
  - Variável: depende da heurística; no pior caso pode degenerar para Dijkstra.
- Quando usar?
  - Planejamento de rota e busca com heurística que aproxima custo restante (ex.: distância euclidiana).
- Armadilhas:
  - Heurística deve ser admissível e preferencialmente consistente; heurística ruim reduz desempenho.

---

## QuickSort
- O que é?
  - Ordenação por divisão (pivot) e partição recursiva.
- Complexidade:
  - Tempo médio: O(n log n), pior: O(n^2) (pivot ruim); Espaço: O(log n) médio.
- Quando usar?
  - Ordenação geral; muito rápido em prática quando bem implementado (random pivot).
- Armadilhas:
  - Escolha do pivot; estabilidade (não estável sem modificações).

---

## MergeSort
- O que é?
  - Ordenação por divisão e fusão (merge) estável.
- Complexidade:
  - Tempo: O(n log n) sempre; Espaço: O(n).
- Quando usar?
  - Quando estabilidade é necessária ou pior caso garantido.
- Armadilhas:
  - Uso de memória adicional; overhead em listas pequenas.

---

## KMP (Knuth-Morris-Pratt)
- O que é?
  - Algoritmo de busca de substring que evita re-comparações usando tabela de prefixos.
- Complexidade:
  - Tempo: O(n + m), Espaço: O(m) para tabela (m = padrão).
- Quando usar?
  - Busca eficiente de padrão em textos grandes.
- Armadilhas:
  - Implementação da tabela de prefixo pode ser fonte de bugs.

---

## Programação Dinâmica — Ex.: Knapsack (0/1)
- O que é?
  - Técnica para resolver problemas com subproblemas sobrepostos e otimização por memoização/tabela.
- Complexidade:
  - Depende do problema; Knapsack 0/1 DP: O(n * W) tempo e espaço (W = capacidade).
- Quando usar?
  - Otimização com subestrutura ótima e sobreposição de subproblemas.
- Armadilhas:
  - Estados e transições mal definidos levam a complexidade explodir; cuidado com memória.

---

## Union-Find (Disjoint Set)
- O que é?
  - Estrutura para gerenciar partições disjuntas com union e find eficientes.
- Complexidade:
  - Operações quase O(α(n)) amortizado com union by rank + path compression (α = inverse Ackermann).
- Quando usar?
  - Algoritmos de MST (Kruskal), componentes conectados dinâmicos.
- Armadilhas:
  - Implementação sem compressão ou rank perde eficiência.

---

## Ordenação Topológica
- O que é?
  - Ordenação linear de vértices de DAG respeitando dependências.
- Complexidade:
  - Tempo: O(V + E), Espaço: O(V).
- Quando usar?
  - Resolução de dependências, build order, schedulers.
- Armadilhas:
  - Só existe em grafos acíclicos; detectar ciclos antes de confiar no resultado.

## Algoritmos de Força Bruta e Outros — Perguntas e Respostas

### Força Bruta (Brute Force)
- O que é?
  - Tentar todas as possibilidades do espaço de busca até encontrar solução válida.
- Complexidade:
  - Geralmente exponencial ou polinomial alto (depende do problema); exemplo: O(n!) ou O(2^n).
- Quando usar?
  - Problemas pequenos, prototipagem, ou quando nenhuma heurística conhecida melhora significativamente.
- Armadilhas:
  - Escala mal; sempre procurar poda, memoização ou formulação melhor.

### Backtracking
- O que é?
  - Explorar recursivamente decisões, revertendo (backtrack) quando caminho inviável.
- Complexidade:
  - Exponencial no pior caso; pode ser muito mais rápido com poda eficaz.
- Quando usar?
  - Problemas de combinatória com restrições (N-Queens, Sudoku, permutações).
- Armadilhas:
  - Falta de poda/heurísticas leva a tempo proibitivo.

### Branch and Bound
- O que é?
  - Explorar espaço de busca usando limites (bounds) para podar ramos que não podem melhorar solução atual.
- Complexidade:
  - Depende da qualidade dos bounds; pior caso exponencial, melhor caso muito reduzido.
- Quando usar?
  - Problemas de otimização (Knapsack exato, TSP exato) quando é possível estimar limites.
- Armadilhas:
  - Bounds fracos -> pouca poda; overhead de manutenção de filas/estados.

### Meet-in-the-Middle
- O que é?
  - Dividir problema em duas metades, computar soluções parciais e combinar — reduz exponencial em metade.
- Complexidade:
  - Ex.: de O(2^n) para O(2^{n/2}) com memória O(2^{n/2}).
- Quando usar?
  - Subconjuntos, soma de subconjuntos, quando n ~ 40 e força bruta direta é inviável.
- Armadilhas:
  - Consome memória; requer boa combinação/ordenação de resultados.

### Algoritmos Gulosos (Greedy)
- O que é?
  - Construir solução escolhendo localmente melhor opção em cada passo.
- Complexidade:
  - Geralmente polinomial, muito eficiente.
- Quando usar?
  - Problemas com propriedade de escolha gulosa (ex.: Huffman, MST com Kruskal/Prim).
- Armadilhas:
  - Nem sempre produz solução ótima; provar corretude é necessário.

### Randomizados (Randomized Algorithms)
- O que é?
  - Usam aleatoriedade para decisões internas; podem ser Monte Carlo (probabilisticamente corretos) ou Las Vegas (sempre corretos, tempo aleatório).
- Complexidade:
  - Expectativa ou probabilidade na análise; muitas vezes mais simples/rápidos na prática.
- Quando usar?
  - Grandes entradas, hashing universal, amostragem, quicksort randomizado.
- Armadilhas:
  - Variância no tempo; necessidades de sementes/repetições para estabilidade.

### Aproximação (Approximation Algorithms)
- O que é?
  - Algoritmos que encontram soluções próximas do ótimo com garantias de fator de aproximação.
- Complexidade:
  - Normalmente polinomial; trade-off entre qualidade e tempo.
- Quando usar?
  - Problemas NP-difíceis onde solução exata é impraticável (ex.: TSP heurístico, Vertex Cover).
- Armadilhas:
  - Garantia de aproximação pode ser fraca; avaliar qualidade prática além do fator teórico.

### Dicas gerais ao escolher abordagem
- Tamanho da entrada e limites práticos definem viabilidade da força bruta.
- Procure poda (pruning), memoização/dinâmica, heurísticas e estruturas auxiliares (hash, heaps).
- Combine técnicas (ex.: backtracking + branch-and-bound, meet-in-the-middle + hashing).
- Teste com instâncias limites e estime uso de memória antes de aplicar método exponencial.


---

Notas rápidas:
- Escolha algoritmo com base em restrições (tempo, espaço, pesos, propriedades do grafo, necessidade de estabilidade).
- Teste com casos de borda (dados ordenados, repetidos, grafos desconexos, pesos extremos).