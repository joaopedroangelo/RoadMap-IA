# Algoritmo A*

> Nesta seção, apresentamos o **Algoritmo A***, que combina o custo já percorrido e uma heurística para garantir busca ótima e eficiente.

---
## 1. Princípio de Funcionamento

O A* explora nós usando a função de avaliação:

```
f(n) = g(n) + h(n)
```

* **g(n)**: custo do caminho do estado inicial até o nó n.
* **h(n)**: heurística que estima o custo de n até um estado objetivo.

A cada iteração, A* expande o nó com menor f(n) na fronteira.

---
## 2. Propriedades

| Característica | A*                                                  |
| -------------- | --------------------------------------------------- |
| Completo?      | Sim, se existirem custos positivos e espaço finito. |
| Ótimo?         | Sim, se a heurística for admissível.                |
| Tempo          | Exponencial no pior caso: O(b^{C\*/ε})              |
| Espaço         | Exponencial no pior caso: O(b^{C\*/ε})              |

> *C*\* é o custo da solução ótima e ε é o menor incremento de custo.

---
## 3. Heurística Admissível e Consistente

* **Admissível**: Nunca superestima o custo real ao objetivo.
* **Consistente**: Para toda transição (n → n'):

  ```
  h(n) ≤ c(n,n') + h(n')
  ```

Heurísticas consistentes garantem que f(n) não diminua ao longo de um caminho.

---
## 4. Pseudocódigo

```pseudo
A*(problem):
  start ← nó inicial com g(start)=0
  frontier ← PriorityQueue ordenada por f(n)=g(n)+h(n)
  frontier.adicionar(start)
  came_from ← mapa vazio
  cost_so_far ← mapeia nó → custo g(n)
  cost_so_far[start] ← 0

  while frontier não vazio:
    current ← frontier.remover_menor_f()
    if current.estado é objetivo:
      return reconstruir_caminho(came_from, current)

    for ação em problem.acoes(current.estado):
      next ← resultado(current, ação)
      new_cost ← cost_so_far[current] + custo(current, ação, next)
      se next não em cost_so_far ou new_cost < cost_so_far[next]:
        cost_so_far[next] ← new_cost
        priority ← new_cost + h(next)
        frontier.adicionar(next, prioridade=priority)
        came_from[next] ← current

  return falha
```

---
## 5. Exemplo Prático

Considere um problema de caminho em grade com obstáculos:

* **g(n)**: número de passos desde o início.
* **h(n)**: distância de Manhattan até o destino.

A* encontra o caminho mais curto evitando áreas bloqueadas, expandindo menos nós que UCS.

---
## Próximos Passos

No próximo arquivo, abordaremos **estratégias de busca competitiva**.
