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

```python
from collections import deque

def bfs(inicio, objetivo, vizinhos):
    """
    inicio: estado inicial
    objetivo: função que testa se o estado é objetivo
    vizinhos: função que retorna os vizinhos de um estado
    """
    fronteira = deque([inicio])        # Fila FIFO
    visitados = set([inicio])
    pai = {inicio: None}               # Para reconstruir o caminho

    while fronteira:
        atual = fronteira.popleft()

        if objetivo(atual):
            caminho = []
            while atual is not None:
                caminho.append(atual)
                atual = pai[atual]
            return list(reversed(caminho))

        for viz in vizinhos(atual):
            if viz not in visitados:
                visitados.add(viz)
                fronteira.append(viz)
                pai[viz] = atual

    return None  # Falha
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

```python
def dfs(inicio, objetivo, vizinhos):
    """
    inicio: estado inicial
    objetivo: função que testa se o estado é objetivo
    vizinhos: função que retorna os vizinhos de um estado
    """
    pilha = [inicio]                  # Pilha LIFO
    visitados = set([inicio])
    pai = {inicio: None}

    while pilha:
        atual = pilha.pop()

        if objetivo(atual):
            caminho = []
            while atual is not None:
                caminho.append(atual)
                atual = pai[atual]
            return list(reversed(caminho))

        for viz in vizinhos(atual):
            if viz not in visitados:
                visitados.add(viz)
                pilha.append(viz)
                pai[viz] = atual

    return None  # Falha
```

---
## 4. Comparação de Algoritmos

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
