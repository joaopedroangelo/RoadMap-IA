# Exercícios

---
### 1ª Qual das estratégias de busca cega a seguir tem menores custos computacionais na resolução de um problema de busca em um espaço de estados finito: busca em profundidade com aprofundamento iterativo ou busca em largura? Justificar sua resposta.

> A busca em profundidade com aprofundamento iterativo tem menores custos computacionais do que a busca em largura porque evita explorar todos os nós de uma mesma profundidade antes de avançar, concentrando o esforço nos caminhos mais promissores primeiro.

---
### 2ª Qual a diferença entre uma estratégia de busca cega e uma estratégia de busca informada?

> A busca cega não utiliza nenhuma informação adicional sobre o problema além da definição dos estados e das ações disponíveis.

> Já a busca informada usa uma heurística, ou seja, uma estimativa do custo ou da distância até o objetivo, guiando a busca de forma mais eficiente ao priorizar os caminhos que têm maior chance de levar à solução rapidamente.

---
### 3ª Quais as diferenças entre estratégia de busca heurística gulosa e busca heurística A*?

> A busca heurística gulosa utiliza apenas a função heurística h(n), que estima a distância do estado atual até o objetivo, escolhendo sempre o nó que parece estar mais próximo da meta.

> Já a busca A* usa uma combinação entre o custo do caminho já percorrido (g(n)) e a estimativa do custo restante (h(n)), através da função f(n) = g(n) + h(n), analisando assim o custo acumulado. 

---
### 4ª Numa busca heurística A* é indispensável utilizar heurísticas admissíveis? se sim, o que isto significa?

> Sim, numa busca heurística A* é indispensável utilizar heurísticas admissíveis se quisermos garantir que o algoritmo encontre a solução ótima.

> Uma heurística é admissível quando nunca superestima o custo real para se alcançar o objetivo a partir de um determinado estado, ou seja, ela é sempre otimista. Isso significa que a estimativa fornecida pela heurística (h(n)) é menor ou igual ao custo real do caminho mais barato até a meta. Essa propriedade é essencial para que o A* explore primeiro os caminhos com menor custo total real e não descarte prematuramente a melhor solução.

---
### 5ª É possível implementar a busca heurística A* como uma adaptação da busca em Largura. Como fazer a adaptação? 

> Substituindo a fila simples usada na busca em largura por uma fila de prioridade ordenada pelo valor da função f(n) = g(n) + h(n). Enquanto a busca em largura expande os nós em ordem de profundidade, a busca A* expande primeiro os nós que têm menor custo estimado total até o objetivo.

---
### 6ª A função f(n) que uma busca heurística A* utiliza para guiar o processo de busca em cada nó n do espaço de estados deve ser expressa em termos de uma soma. Quais seriam as parcelas desta soma?

> A função f(n) na busca heurística A* é expressa como a soma de duas parcelas: f(n) = g(n) + h(n), em que:

> g(n) é o custo acumulado do caminho desde o estado inicial até o nó n

> h(n) é a estimativa heurística do custo restante para alcançar o objetivo a partir do nó n.

---
### 7ª Defina formalmente heurística consistente.

> Uma heurística h(n) é dita consistente (ou monótona) se, para todo nó n e para todo sucessor n' de n, o valor estimado pela heurística satisfaz a desigualdade:

> h(n) ≤ c(n,n′) + h(n′)

> onde c(n, n') é o custo real para ir de n até n'.

---
### 8ª Explique o conceito de fator de ramificação efetiva e qual a sua relação com estratégias de busca em espaços de estados. 

> O fator de ramificação efetiva é uma medida que indica o número médio de sucessores gerados por nó durante a busca em um espaço de estados.

> Quanto menor o fator de ramificação efetiva, mais eficiente é a estratégia de busca, pois o agente expande menos nós para encontrar a solução.

---
### 9ª Uma heurística admissível domina outra heurística admissível em qual situação? 

> Uma heurística admissível domina outra heurística admissível quando, para todo nó do espaço de estados, sua estimativa de custo até o objetivo é igual ou maior, mas nunca supera o custo real.

---
### 10ª Explique, em linhas gerais, como se dá a solução de um problema adversarial fazendo-se uso do algoritmo MIN-MAX.

> A solução de um problema adversarial usando o algoritmo MIN-MAX envolve modelar a situação como um jogo entre dois jogadores com objetivos opostos: um que busca maximizar seu ganho (MAX) e outro que tenta minimizar esse ganho (MIN).

> O algoritmo constrói uma árvore de decisões que representa todos os possíveis movimentos dos jogadores, alternando entre níveis MAX e MIN.

> A partir das folhas da árvore, que representam estados finais do jogo com valores associados (vantagens ou desvantagens), o algoritmo propaga esses valores para cima, assumindo que o jogador MAX escolhe sempre a jogada que maximiza o valor e o jogador MIN escolhe a que minimiza. Dessa forma, o MIN-MAX determina a melhor jogada para o jogador MAX, antecipando as respostas ótimas do adversário.

---
### 11ª O que você entende por poda alpha-beta no contexto do algoritmo MIN-MAX?

> A poda alpha-beta é uma técnica usada para otimizar o algoritmo MIN-MAX, reduzindo o número de nós que precisam ser avaliados na árvore de busca. Ela funciona mantendo dois valores, alpha (o melhor valor já garantido para o jogador MAX) e beta (o melhor valor já garantido para o jogador MIN), e descartando (podando) ramos da árvore que não podem influenciar a decisão final porque existem alternativas melhores já conhecidas.

---
### 12ª Explique a inspiração biológica e as etapas de mais alto nível de funcionamento de um algoritmo genético (AG). Faça uma figura com os módulos funcionais do AG.

> Um algoritmo genético (AG) é inspirado no processo de evolução biológica, onde populações de indivíduos passam por seleção natural, reprodução e mutação para gerar novas gerações cada vez mais adaptadas ao ambiente. No AG, cada indivíduo representa uma solução possível para o problema, codificada geralmente como uma sequência (cromossomo). As etapas principais são:

> 1. Inicialização: cria-se uma população inicial de soluções aleatórias;
> 2. Avaliação: cada indivíduo é avaliado por uma função fitness que mede sua qualidade;
> 3. Seleção: indivíduos mais aptos são selecionados para reprodução;
> 4. Crossover (recombinação): combina partes de dois ou mais indivíduos para gerar descendentes;
> 5. Mutação: altera aleatoriamente partes dos descendentes para manter diversidade genética;
> 6. Substituição: a nova geração substitui a antiga;

```pseudo
+-----------------+
| Inicialização   |
+--------+--------+
         |
         v
+-----------------+
| Avaliação (Fitness) |
+--------+--------+
         |
         v
+-----------------+
| Seleção        |
+--------+--------+
         |
         v
+-----------------+
| Crossover      |
+--------+--------+
         |
         v
+-----------------+
| Mutação        |
+--------+--------+
         |
         v
+-----------------+
| Substituição   |
+--------+--------+
         |
         v
    Repetir ciclo
```

---
### 13ª De que forma um AG poderia ser utilizado como técnica de Aprendizagem supervisionada?

> Um algoritmo genético pode ser usado para otimizar os parâmetros ou a estrutura de um modelo preditivo, avaliando o desempenho de cada configuração com base em dados rotulados. A partir dessa avaliação, ele evolui a população de soluções para melhorar a precisão do modelo, encontrando configurações que aprendem padrões nos dados de treinamento.

---
### 14ª Espaços de estados amplos e potencialmente não discretizados são adequados para solução de problemas via AGs? Justifique sua resposta

> Sim, porque algoritmos genéticos exploram soluções usando populações e operadores genéticos que funcionam bem em espaços grandes e contínuos, permitindo encontrar boas soluções mesmo quando métodos exatos são inviáveis.

---
### 15ª Na maioria dos casos, AGs irão ajudar a encontrar soluções ótimas para problemas de busca e otimização? Justifique sua resposta

> Na maioria dos casos, algoritmos genéticos ajudam a encontrar **boas soluções aproximadas**, mas não garantem a solução ótima, porque dependem de operações estocásticas e podem ficar presos em ótimos locais. Eles são eficientes para explorar espaços grandes e complexos, mas a garantia de otimalidade geralmente requer métodos exatos ou heurísticas específicas.
