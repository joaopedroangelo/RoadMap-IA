# EXERCÍCIOS - Capítulo 2 - Norvig e Russel

## 2.1
Suponha que a medida de desempenho preocupa-se apenas com os T primeiros passos de tempo do ambiente e ignora tudo a partir de então.  
**Mostre que a ação de um agente racional depende não apenas do estado do ambiente, mas também do passo de tempo que ele alcançou.**

---

## 2.2
Vamos examinar a racionalidade de várias funções do agente aspirador de pó.

**a.** Mostre que a função do agente aspirador de pó simples descrito na Figura 2.3 é realmente racional, conforme as suposições listadas na página 38.  
**b.** Descreva uma função de agente racional para o caso em que cada movimento custa um ponto. O programa de agente correspondente exige estado interno?  
**c.** Descreva possíveis projetos de agentes para os casos em que quadrados limpos podem ficar sujos e a geografia do ambiente é desconhecida. Faz sentido para o agente aprender a partir de sua experiência nessas situações? Em caso afirmativo, o que ele deve aprender? Se não, por quê?

---

## 2.3
Para cada uma das seguintes afirmações, diga se é verdadeiro ou falso e justifique com exemplos a sua resposta ou com contraexemplos se for o caso.

a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.  
b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.  
c. Existe um ambiente de tarefa em que todo agente é racional.  
d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.  
e. Toda função de agente é implementável por uma combinação de programa/máquina.  
f. Suponha que um agente selecione sua ação uniformemente ao acaso do conjunto de ações possíveis. Existe um ambiente de tarefa determinista em que esse agente é racional.  
g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.  
h. Todo agente é racional em um ambiente não observável.  
i. Um agente jogador de pôquer perfeitamente racional nunca perde.

---

## 2.4
Para cada uma das seguintes atividades, forneça uma descrição PEAS do ambiente da tarefa e caracterize-o em termos das propriedades listadas na Seção 2.3.2.

- Jogar futebol  
- Explorar os oceanos subterrâneos de Titã  
- Comprar livros usados de IA na Internet  
- Jogar uma partida de tênis  
- Praticar tênis contra uma parede  
- Realizar um salto de altura  
- Licitações de um item em um leilão  

---

## 2.5
Defina com suas próprias palavras os termos a seguir:

- Agente  
- Função de agente  
- Programa de agente  
- Racionalidade  
- Autonomia  
- Agente reativo  
- Agente baseado em modelo  
- Agente baseado em objetivos  
- Agente baseado em utilidade  
- Agente com aprendizagem  

---

## 2.6
Este exercício explora as diferenças entre funções de agentes e programas de agentes.

**a.** Pode haver mais de um programa de agente que implemente uma dada função de agente? Dê um exemplo ou mostre por que não é possível.  
**b.** Existem funções de agente que não podem ser implementadas por qualquer programa de agente?  
**c.** Dada uma arquitetura de máquina fixa, cada programa de agente implementa exatamente uma função de agente?  
**d.** Dada uma arquitetura com *n* bits de armazenamento, quantos programas de agentes distintos são possíveis nessa arquitetura?  
**e.** Suponha manter fixo o programa de agente, mas aumentamos a velocidade da máquina por um fator de dois. Isso muda a função de agente?

---

## 2.7
Escreva programas de agente de pseudocódigo para os agentes baseados em:

- Objetivos  
- Utilidade  

---

## 2.8
Implemente um simulador de ambiente de medição de desempenho para o mundo de aspirador de pó representado na Figura 2.2 e especificado na página 38.  
Sua implementação deve ser modular, de forma que os sensores, os atuadores e as características do ambiente (tamanho, forma, localização da sujeira etc.) possam ser alterados com facilidade.

---

## 2.9
Implemente um único agente reflexo para o ambiente de vácuo do Exercício 2.8.  
Execute o ambiente com esse agente para todas as configurações iniciais sujas e localizações do agente possíveis.  
Registre a nota de desempenho de cada configuração e a nota média global.

---

## 2.10
Considere uma versão modificada do ambiente de aspirador de pó do Exercício 2.8, na qual o agente é penalizado com um ponto para cada movimento.

**a.** Um agente reativo simples pode ser perfeitamente racional para esse ambiente? Explique.  
**b.** E um agente reativo com estado? Projete tal agente.  
**c.** Como suas respostas para os itens a e b mudarão se as percepções do agente fornecerem o status limpo/sujo de cada quadrado no ambiente?

---

## 2.11
Considere uma versão modificada do ambiente de aspirador de pó do Exercício 2.8, na qual a geografia do ambiente — extensão, limites e obstáculos — é desconhecida, como também a configuração inicial de sujeira.  
(O agente também pode se mover Acima e Abaixo, além de Esquerda e Direita.)

**a.** Um agente reativo simples pode ser perfeitamente racional para esse ambiente? Explique.  
**b.** Um agente reativo simples com uma função de agente aleatório pode superar um agente reativo simples? Projete tal agente e faça a medição de seu desempenho em vários ambientes.  
**c.** Você poderia projetar um ambiente no qual seu agente aleatório tenha um desempenho muito ruim? Mostre seus resultados.  
**d.** Um agente reativo com estado pode superar um agente reativo simples? Projete tal agente e faça a medição de seu desempenho em vários ambientes. Você pode projetar um agente racional desse tipo?

---

## 2.12
Repita o Exercício 2.11 para o caso em que o sensor de posição é substituído por um sensor de “impacto” que detecta as tentativas realizadas pelo agente para se mover para um obstáculo ou cruzar os limites do ambiente.  
Suponha que o sensor de impacto pare de funcionar; como o agente deverá se comportar?

---

## 2.13
Os ambientes de aspiradores de pó de todos os exercícios anteriores eram determinísticos.  
Descreva possíveis programas de agentes para cada uma das versões estocásticas listadas a seguir:

**a. Lei de Murphy:** durante 25% do tempo, a ação de Aspirar falha ao limpar o chão se ele está sujo e deposita sujeira no chão se ele está limpo.  
De que maneira seu programa de agente é afetado se o sensor de sujeira fornece a resposta errada durante 10% do tempo?

**b. Crianças pequenas:** em cada período de tempo, cada quadrado limpo tem uma chance de 10% de se tornar sujo.  
Você poderia apresentar um projeto de agente racional para esse caso?
