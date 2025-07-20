# Busca Competitiva — Algoritmos Adversariais

> Nesta seção, exploramos as **buscas competitivas**, também chamadas de **buscas adversariais**,
> aplicadas a problemas em que múltiplos agentes (jogadores) competem entre si.

---
## 1. Conceitos Básicos

* **Jogo de Soma Zero**: O ganho de um jogador é a perda do outro. Exemplo: xadrez, jogo da velha.
* **Árvore de Jogo**: Modela estados de jogo como nós; arestas representam movimentos de jogadores alternados.
* **Função de Avaliação**: Estima a qualidade de um estado quando o jogo não está em um nó terminal.

---
## 2. Algoritmo Minimax

Minimax explora a árvore de jogo assumindo que ambos jogadores jogam de forma ótima:

* Jogador MAX tenta **maximizar** o valor.
* Jogador MIN tenta **minimizar** o valor.

### 2.1 Pseudocódigo Minimax

```pseudo
function minimax(no, jogador):
    if no é terminal:
        return valor(no)
    if jogador == MAX:
        melhorValor ← -infinito
        for cada filho em no.sucessores():
            valorFilho ← minimax(filho, MIN)
            melhorValor ← max(melhorValor, valorFilho)
        return melhorValor
    else:  # jogador == MIN
        melhorValor ← +infinito
        for cada filho em no.sucessores():
            valorFilho ← minimax(filho, MAX)
            melhorValor ← min(melhorValor, valorFilho)
        return melhorValor
```

---
## 3. Poda Alfa-Beta

A **poda alfa-beta** otimiza o Minimax, eliminando ramos que não influenciam a decisão final.

* **α (alfa)**: melhor valor (mais alto) encontrado até agora para MAX.
* **β (beta)**: melhor valor (mais baixo) encontrado até agora para MIN.

### 3.1 Pseudocódigo Alfa-Beta

```pseudo
function alphabeta(no, α, β, jogador):
    if no é terminal:
        return valor(no)
    if jogador == MAX:
        v ← -infinito
        for cada filho em no.sucessores():
            v ← max(v, alphabeta(filho, α, β, MIN))
            α ← max(α, v)
            if α ≥ β:
                break  # poda
        return v
    else:  # jogador == MIN
        v ← +infinito
        for cada filho em no.sucessores():
            v ← min(v, alphabeta(filho, α, β, MAX))
            β ← min(β, v)
            if β ≤ α:
                break  # poda
        return v
```

---
## 4. Expectimax (Jogos com Elementos de Chance)

Para jogos que envolvem aleatoriedade (por exemplo, rolamento de dados), usa-se **Expectimax**:

```pseudo
function expectimax(no, tipo):
    if no é terminal:
        return valor(no)
    if tipo == MAX:
        return max(expectimax(filho, CHANCE) for filho em no.sucessores())
    if tipo == MIN:
        return min(expectimax(filho, CHANCE) for filho em no.sucessores())
    if tipo == CHANCE:
        return soma(probabilidade(filho) * expectimax(filho, MAX) for filho em no.sucessores())
```

---
## 5. Exemplo Prático: Jogo da Velha

* Estados: configurações da grade 3×3.
* Função de avaliação: +1 se MAX vence, -1 se MIN vence, 0 empate.
* Aplica Minimax ou Alfa-Beta para escolher o movimento ótimo.
