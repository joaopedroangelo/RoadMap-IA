# Pré-Processamento

---
## Contexto 

O processamento de linguagem natural (PLN) permite que os computadores interpretem a linguagem humana. Todos os computadores podem entender códigos binários, mas não entendem a linguagem natural, escrita e falada pelas pessoas.

Porém, um computador com Processamento de Linguagem Natural pode ser capaz de entender a frase acima.

Mas antes que o texto seja processado pelos modelos, é preciso que algumas etapas de pré-processamento sejam feitas.

O pré-processamento de PLN é a preparação do texto bruto para análise por um programa ou modelo de aprendizado de máquina. O pré-processamento de PLN é necessário para colocar o texto em um formato que os modelos de aprendizagem profunda possam analisar com mais facilidade.

---
## Ordem de Pré-Processamento Textual

- Eliminar identificadores e URLs usando Expressões Regulares
- Conversão para minúsculas.
- Tokenizar as strings em palavras.
- Remover Stop words e pontuação.
- Stemming vs. Lemmatization.

Abaixo, estão exemplos dessas técnicas de pré-processamento usando a biblioteca NLTK.

Essa biblioteca inclui um conjunto diversificado de corpora que podem ser lidos com nltk.corpus.

**NLTK**: O Natural Language Toolkit é uma plataforma completa
que contém mais de 50 corpora e recursos lexicais. Isso também
fornece as ferramentas, interfaces e métodos necessários para processar
e analisar dados de texto.

---
## Setup

```python
import nltk                                # Biblioteca Python para PLN
from nltk.corpus import twitter_samples    # amostras de tweets da NLTK
import random                              # gerador de número pseudo-aleatório


nltk.download('stopwords')                 # download stopwords - NLTK
import re                                  # biblioteca para expressões regulares
import string                              # operações em string

from nltk.corpus import stopwords          # módulo stopwords que vem no NLTK
from nltk.stem import PorterStemmer        # módulo para stemming
from nltk.tokenize import TweetTokenizer   # módulo para 'tokenizar' strings

# download dataset de amostras do twitter
nltk.download('twitter_samples')

# Amostra selecionada
tweet = all_positive_tweets[102]
print(tweet)
@zaynmalik prince charming on stage :) x https://t.co/OnVFhzt5fZ
```

---
## Eliminar identificadores e URLs

```python
# remove hyperlinks
tweet2 = re.sub(r'https?://[^\s\n\r]+', '', tweet2)

print(tweet)
print(tweet2)
```

---
## Tokenização

A tokenização é um processo fundamental no campo do Processamento de Linguagem Natural, onde o texto é transformado em unidades menores chamadas tokens. Esses tokens podem ser palavras individuais, números, pontuações, símbolos especiais ou até mesmo unidades mais complexas, como emojis.

Um token é uma unidade mínima de texto que pode ser tratada como uma única entidade. 

Uma maneira muito simples de tokenizar um texto, é por meio de espaços em branco.

![alt text](../../Imagens/TokenizacaoEspacoBranco.png)

Mesmo que você não vá usar a tokenização baseada em espaço em branco, ela pode ser um primeiro passo antes da Tokenização de fato.

Antes que qualquer modelo de PLN possa processar o texto, ele precisa ser tokenizado para que as palavras e outros elementos possam ser tratados individualmente.

Em alguns casos, a tokenização também pode envolver a normalização do texto, como a conversão de todas as letras para minúsculas, remoção de pontuações ou símbolos especiais, etc.

---
## Como a Tokenização é realizada?

**1. Tokenização baseada em Espaços em Branco**<br>
    Uma abordagem simples é dividir o texto com base nos espaços em branco. Nesta abordagem, cada palavra é tratada como um token separado.

**2. Tokenização com base em Regras**<br>
    Outra abordagem é usar regras específicas para dividir o texto em tokens. Isso pode envolver o uso de expressões regulares (regex) ou outras técnicas para identificar padrões específicos no texto.

**3. Tokenização com base em Subpalavras**<br>
    O texto é dividido em partes menores que, embora possam ser menores que uma palavra inteira, ainda carregam um significado substancial por si mesmas.

**4. Tokenização com base em Modelos de Linguagem**<br>
    Muitas bibliotecas de PLN, como spaCy e NLTK, fornecem modelos de linguagem pré-treinados que são capazes de realizar a tokenização de forma mais precisa e sofisticada.

---
## Tokenização com NLTK

```python
# Inicializando a classe tokenizer 
tokenizer = TweetTokenizer(preserve_case=True, strip_handles=True,
                               reduce_len=True)

# tokenize tweets
tweet_tokens = tokenizer.tokenize(tweet2)

print()
print('Tweet tokenizado:')
print(tweet_tokens)

Tweet tokenizado:
['prince', 'charming', 'on', 'stage', ':)', 'x']
```

> O método preserve_case indica se você quer manter a capitalização original da entrada e por padrão está definido como True. Como o tweet originalmente está todo escrito com letras minúsculas não será necessário definir como False.

> O método strip_handles, por padrão, é definido como False. Ele especifica se os identificadores de texto do Twitter usados ​​no método tokenize devem ser removidos.

> O método reduce_len, por padrão, é definido como False. Ele especifica se as sequências de caracteres repetidas de comprimento 3 ou superior devem ser substituídas por sequências de comprimento 3.

---
## Tokenização baseada em Sub-Palavras

O o texto é dividido em partes menores que, embora possam ser menores que uma palavra inteira, ainda carregam um significado substancial por si mesmas.

Por exemplo, vamos tokenizar a palavra “incompreensível” em português. A tokenização baseada em subpalavras poderia dividir essa palavra em várias partes, como “in”, “compreens”, “ível”. Cada uma dessas partes, ou tokens, carrega um significado independente.

Agora, vamos considerar a tokenização de um parágrafo. Suponha que temos o seguinte parágrafo em português:

“O cachorro está correndo no parque. Ele parece muito feliz.”

A tokenização desse parágrafo pode resultar em algo assim:

[“O”, “ c”, “ach”, “or”, “ro”, “ est”, “á”, “ cor”, “rend”, “o”, “no” par”, “que”, “.”, “ Ele”, “ p“, “are”, “ce“, “ m”, “uit“, “o”, “ fel”, “iz”, “.”]


---
## Tokenização baseada em Modelos de Linguagem

```python
pip install transformers

from transformers import AutoTokenizer

# Carregando o tokenizer de um modelo multilíngue
tokenizer = AutoTokenizer.from_pretrained("bert-base-multilingual-cased")

# Texto de exemplo
texto = "O cachorro está correndo no parque. Ele parece muito feliz."

# Tokenizando
tokens = tokenizer.tokenize(texto)
print("Tokens:", tokens)

# Convertendo tokens para IDs (como são representados no modelo)
input_ids = tokenizer.convert_tokens_to_ids(tokens)
print("IDs:", input_ids)
```

---
## Stop Words

Stop words, ou palavras de parada, são palavras comuns em um idioma que geralmente são removidas durante o processamento de texto, seja para análise de texto ou para otimização de mecanismos de busca. Elas não são consideradas essenciais para entender o significado central do texto e podem até atrapalhar a análise ao adicionar ruído. 

Exemplos comuns de stop words incluem:
- Artigos definidos e indefinidos: o, a, os, as, um, uma, uns, umas.
- Preposições: de, em, para, com, por, sobre, etc.
- Conjunções: e, ou, mas, se, etc.
- Pronomes: eu, tu, ele, ela, nós, vós, eles, elas, etc.
- Verbos auxiliares: ser, estar, ter, haver, etc. 

```python
print(tweet_tokens)

tweets_clean = []

for word in tweet_tokens: # analisa cada palavra da lista de tokens
    if (word not in stopwords_english and  # remove stopwords
        word not in string.punctuation):  # remove pontuação
        tweets_clean.append(word)

print('stop words e pontuções removidas:')
print(tweets_clean)

['prince', 'charming', 'on', 'stage', ':)', 'x'] # tweet antes

stop words e pontuções removidas:
['prince', 'charming', 'stage', ':)', 'x'] # tweet depois
```

---
## Stemming vs Lemmatization

Stemming é simplesmente transformar qualquer palavra em seu radical base, que você pode definir como o conjunto de caracteres usados ​​para construir a palavra e seus derivados. Stemming ajuda a reduzir o número de palavras no texto e simplificar o vocabulário.

> casinha -> cas<br>
> casebra -> cas

```python
print(tweets_clean)

# Inicializando a classe stemming 
stemmer = PorterStemmer() 

# Lista vazia para armazenar os stems
tweets_stem = [] 

for word in tweets_clean:
    stem_word = stemmer.stem(word)  # palavra com stemming 
    tweets_stem.append(stem_word)  # adiciona a lista

print('Palavras depois de user stemming')
print(tweets_stem)


['prince', 'charming', 'stage', ':)', 'x'] # Tweet antes

stemmed words:
['princ', 'charm', 'stage', ':)', 'x'] # Tweet depois de usar stemming
```

A redução de ‘charming’ para ‘charm’ realmente faz sentido, mas e a de ‘prince’ para ‘princ’? Essa palavra ao menos existe? O contexto pode mudar totalmente.

Com lemmatization, podemos reduzir as palavras para outra que realmente existam e não prejudique o contexto do texto. Assim, teríamos:

> achieve -> achieve

> achieving -> achieve

Apesar de ser uma melhor opção, não é tão rápido e simples como o stemming.

---
## Aprofundamento

Para se aprofundar, veja:<br>
[Tokenização Laboratório](../Labs/TokenizacaoNLTK.ipynb)

[Tutorial NLTK](../Labs/Tutorial_NLTK.ipynb)