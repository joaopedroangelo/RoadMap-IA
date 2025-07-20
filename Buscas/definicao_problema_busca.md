# Definição de Problema de Busca

> Neste tópico, vamos apresentar os componentes fundamentais que definem um problema de busca em Inteligência Artificial.

---
## 1. Estado

Um **estado** representa uma configuração possível do sistema em que o agente está operando.
No domínio de um problema, os estados formam um conjunto finito ou infinito, chamado de espaço de estados.

* **Exemplo**: Em um problema de labirinto, cada célula ou posição no labirinto é um estado.
* Notação comum: $s \in S$, onde $S$ é o conjunto de todos os estados.

---
## 2. Ação

Uma **ação** é uma operação que faz a transição de um estado para outro. Nem todas as ações estão disponíveis em todos os estados.

* **Função de Transição**: A partir de uma ação, mapeia um estado para outro.
* **Exemplo**: No labirinto, ações podem ser `Ir para cima`, `Ir para baixo`, `Ir para a esquerda` e `Ir para a direita`.

---
## 3. Estado Inicial e Estado(s) Objetivo(s)

* **Estado Inicial**: É de onde o agente começa a busca.
* **Objetivo**: Um ou mais estados $s_{g} \in G \subseteq S$ que satisfazem o objetivo.

---
## 4. Custo de Caminho

O **custo de caminho** é a soma dos custos das ações realizadas para ir do estado inicial até um estado $s$.

* **Exemplo**: Em um problema de roteamento, o custo pode representar distância, tempo ou outro recurso consumido.

---
## 5. Exemplo Completo

### Problema do Caminho Mínimo em uma Grade

* **Estados**: Células de uma grade.
* **Ações**: Mover-se para células adjacentes (cima, baixo, esquerda, direita).
* **Estado Inicial**: Célula superior esquerda $(0,0)$.
* **Estado Objetivo**: Célula inferior direita $(m-1,n-1)$.
* **Custo**: Cada movimento tem custo 1.

Este problema pode ser resolvido com busca em largura (BFS) para encontrar o menor número de passos.

---
## Próximos Passos

No próximo arquivo, exploraremos em detalhes as **buscas cegas**, que não utilizam informações para guiar a busca.
