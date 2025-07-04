# Tokenização e Normalização

Toda tarefa de NLP requer normalização textual:<br>
1. Tokenização
2. Normalizar o formato das palavras
3. Segmentar sentenças

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
## Tokenização com spacy

```python
!pip install -U spacy
!python -m spacy download pt_core_news_sm

import spacy
import pandas as pd

# Carregando o modelo de idioma em português
nlp = spacy.load('pt_core_news_sm')

# Texto de exemplo
texto = "Os alunos da faculdade de Engenharia de Software estão ansiosos para o início do curso!"

# Aplicando a tokenização
doc = nlp(texto)

# Extraindo os tokens
tokens = [token.text for token in doc]
print("Tokens:", tokens)

# Coletando informações dos tokens em um único DataFrame
dados_tokens = []
for token in doc:
    dados_tokens.append({
        'Token': token.text,
        'Índice de início': token.idx,
        'É pontuação?': token.is_punct,
        'É espaço em branco?': token.is_space,
        'Parte do discurso': token.pos_,
        'Dependência sintática': token.dep_
    })

# Criando DataFrame com os dados dos tokens
df_tokens = pd.DataFrame(dados_tokens)

# Exibindo o DataFrame
df_tokens
```

Output:<br>
![alt text](../../Imagens/OutputTokenizacaoSpacy.png)

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
## Aprofundamento

Para se aprofundar, veja:<br>
[Tokenização Laboratório](../Labs/TokenizacaoNLTK.ipynb)