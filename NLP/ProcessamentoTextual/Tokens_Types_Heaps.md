# Tokens, Type e Lei de Heaps

> São as etapas feitas antes dos dados serem de fato utilizados.

---
## Token x Type

**Token**: um elemento do vocabulário.

**Type**: uma instância, uma palavra, não conta repetições

---
## Corpus

Um corpus é uma coleção de textos ou áudio, que pode ser usada para treinar e avaliar modelos de PLN. 

Corpora são cruciais para o desenvolvimento de modelos de PLN, pois fornecem dados para aprendizado supervisionado e avaliação de desempenho. 

Corpora podem ser de diversos tipos, como corpora de textos escritos, falados (transcritos) ou ambos, e podem ser especializados em certos temas ou gêneros. 

Um corpus de qualidade geralmente possui um tamanho significativo e é representativo da linguagem que se deseja analisar. 

---
## Quantas palavras em um Corpus?

> Considere palavras = Type, logo sem repetição

**Lei de Heaps**:
A Lei de Heaps descreve a relação entre **N** e **| V |**. Sendo:

**N**: Número de Tokens<br>
**V**: Vocabulário = Conjunto de palavras sem repetição

**| V |**: Tamanho do Vocabulário

Essa lei diz que, à medida que N cresce, o vocabulário | V | também cresce, mas de forma mais lenta. A fórmula está abaixo.

**| V |**: k*N^β

**O que significam o k e o β?**<br>
O *k* é uma constante que depende da língua, do tipo do texto. É ajustada com base nos dados.

O *beta* é um expoente entre 0.67 e 0.75.

**Interpretação**:<br>
Se **N** = 1 milhão de palavras (tokens), o número de tipos (| V |) não será 1 milhão, será bem menor.

Como β < 1, isso significa crescimento sublinear: o vocabulário cresce, mas cada vez mais devagar.

Suponha que temos um corpus com 1 milhão de tokens.

Se k = 10 e Beta = 0.7, então:<br>
**| V |** = 10 x (1000000)^0,7 = 158.490

O vocabulário nesse corpus seria de aproximadamente 158 mil tipos.
