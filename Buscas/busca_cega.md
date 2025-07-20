# Busca Cega — Estratégias Não Informadas

> Nesta seção, exploramos as **buscas cegas** (ou não informadas), que não utilizam conhecimento adicional além da definição do problema.

---
## 1. Visão Geral

Busca cega refere-se a algoritmos que exploram o espaço de estados sem orientação heurística.
Elas garantem completude, mas não otimalidade.

Um algoritmo é completo se ele sempre encontra uma solução quando existe uma.
Um algoritmo é ótimo (ou ótimo em custo) se ele sempre encontra a melhor solução, ou seja, a de menor custo.

**Principais algoritmos**:

* Busca em Largura (Breadth-First Search, BFS)
* Busca em Profundidade (Depth-First Search, DFS)

---
## 2. Busca em Largura (BFS)

* **Descrição**: Explora todos os nós a uma distância $d$ do estado inicial antes de avançar para $d+1$.
* **Estrutura de dados**: Fila (FIFO).
* **Propriedades**:

  * *Completa?* Sim, se o espaço de estados é finito.
  * *Ótima?* Sim, se todos os custos de arestas forem iguais.
  * *Complexidade de tempo*: $O(b^{d})$.
  * *Complexidade de espaço*: $O(b^{d})$.

```pseudo
BFS(problem):
  frontier ← Fila contendo o nó inicial
  explored ← ∅
  while frontier não vazio:
    node ← frontier.remover()
    if node.estado é objetivo:
      return solução(node)
    explored.adicionar(node.estado)
    for ação in problem.acoes(node.estado):
      filho ← resultado(node, ação)
      if filho.estado não está em explored ou frontier:
        frontier.adicionar(filho)
  return falha
```

---
## 3. Busca em Profundidade (DFS)

* **Descrição**: Explora um caminho até o fim antes de retroceder (backtracking).
* **Estrutura de dados**: Pilha (LIFO) — recursão implícita.
* **Propriedades**:

  * *Completa?* Não, pode entrar em loops em espaços infinitos.
  * *Ótima?* Não.
  * *Complexidade de tempo*: $O(b^{m})$, onde $m$ é a profundidade máxima.
  * *Complexidade de espaço*: $O(b^{m})$.

### 3.1 Variações

* **DFS Limitada**: Define um limite de profundidade $l$ para evitar loops.

```pseudo
DFS_Limitada(node, limit):
  if node.estado é objetivo:
    return solução(node)
  else if limit = 0:
    return corte
  else:
    algum_corte ← false
    for ação in acoes(node.estado):
      filho ← resultado(node, ação)
      resultado ← DFS_Limitada(filho, limit − 1)
      if resultado não é falha:
        return resultado
      if resultado é corte:
        algum_corte ← true
    return corte se algum_corte senão falha
```

---
## 5. Comparação de Algoritmos

| Algoritmo | Completo? | Ótimo? | Tempo                   | Espaço                  |
| --------- | --------- | ------ | ----------------------- | ----------------------- |
| BFS       | Sim       | Não    | $O(b^{d})$              | $O(b^{d})$              |
| DFS       | Não       | Não    | $O(b^{m})$              | $O(b^{m})$         

> b: Fator de ramificação (número médio de ações por estado)<br>
> d: Profundidade da solução mais rasa (número mínimo de passos até o objetivo)<br>
> m: Profundidade máxima do espaço de busca (pode ser infinita)

---
## Próximos Passos

No próximo capítulo, veremos **buscas informadas**, que utilizam heurísticas para guiar a exploração do espaço de estados.
