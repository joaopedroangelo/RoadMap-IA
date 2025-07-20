# Busca Heurística - Estrategias Informadas

> Nesta seção apresentamos as buscas informadas que usam funções heurísticas para guiar a exploração do espaço de estados.

---
## 1. Função Heurística

Uma heurística h(n) estima o custo para chegar ao objetivo a partir do nó n.

* Admissivel: h(n) menor ou igual ao custo real de n até o objetivo.
* Consistente: para cada transição de n para n', h(n) menor ou igual a custo(n,n') + h(n').

---
## 2. Busca Gulosa (Greedy Best-First Search)

A busca gulosa expande primeiro o nó com menor valor de h(n).

Pseudocódigo:
```
GreedyBestFirst(problem):
    frontier = fila de prioridade ordenada por h(n)
    frontier.adicionar(no_inicial)
    explored = conjunto vazio

    enquanto frontier nao vazio:
        node = frontier.remover_menor_h()
        se node.estado e objetivo:
            retorna solucao(node)
        explored.adicionar(node.estado)
        para cada acao em problem.acoes(node.estado):
            filho = resultado(node, acao)
            se filho.estado nao esta em explored e nao esta em frontier:
                frontier.adicionar(filho)
    retorna falha
```

Propriedades:

* Completo: nao (pode ficar preso em becos sem saida)
* Otimo: nao
* Tempo: O(b^m) no pior caso
* Espaco: O(b^m)

---
## 3. Heurísticas Comuns

* Distância Euclidiana: linha reta ate o objetivo em problemas espaciais.
* Distância de Manhattan: soma das distancias horizontais e verticais em uma grade.
* Conflito Linear: refinamento da distancia de Manhattan para reduzir empates.

---
## 4. Exemplo Prático: 8-puzzle

* Estado: posições dos 8 números e espaço vazio.
* Heurística h1: numero de peças fora do lugar.
* Heurística h2: soma das distâncias de Manhattan de cada peça ate a posição certa.

A busca gulosa com h2 geralmente explora menos nos que com h1, mas nao garante encontrar o melhor caminho.

---
## Próximo Passo

No proximo arquivo veremos o Algoritmo A*, que combina custo real e heuristica para garantir completude e otimalidade.
