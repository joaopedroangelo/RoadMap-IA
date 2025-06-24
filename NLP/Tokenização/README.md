# Tokenização

---
## 1. Definição e Fundamentos

**Tokenização**, no contexto do Processamento de Linguagem Natural (PLN), é o processo de dividir um texto em partes menores chamadas **tokens**. Esses tokens podem ser palavras, caracteres ou unidades intermediárias, dependendo da estratégia utilizada.

Esse processo é essencial porque torna o texto mais estruturado e compreensível para os algoritmos de IA. Assim como uma criança aprende a ler por meio de letras e sílabas antes de entender frases completas, a tokenização ajuda os modelos computacionais a entenderem a linguagem humana em partes menores.

---
## 1.1 Exemplo

Frase:

> "Os chatbots são úteis."

Tokenização por palavras:

```python
["Os", "chatbots", "são", "úteis"]
```

Neste exemplo, os espaços em branco são utilizados como delimitadores para separar as palavras.

---
## 2. Tipos de Tokenização

| Tipo                   | Descrição                                              | Quando Usar                                  | Exemplo com “Chatbots”                       |
| ---------------------- | ------------------------------------------------------ | -------------------------------------------- | -------------------------------------------- |
| **Palavras**           | Divide o texto com base em espaços e pontuação.        | Análises gerais, modelos simples.            | `["Chatbots", "são", "úteis"]`               |
| **Caracteres**         | Quebra o texto em letras individuais.                  | Tarefas detalhadas ou análises ortográficas. | `["C", "h", "a", "t", "b", "o", "t", "s"]`   |
| **Subpalavras**        | Segmenta palavras em unidades menores (subwords).      | Modelos neurais como BERT e GPT.             | `["Chat", "bots"]` ou `["Cha", "tbo", "ts"]` |
| **Baseada em Modelos** | Utiliza regras aprendidas e conhecimento de linguagem. | Textos complexos ou idiomas sem espaços.     | Ex.: spaCy, NLTK, transformers               |

---
## 3. Desafios da Tokenização

- **Ambiguidade**<br>
   A frase “Estou morrendo de fome” pode ser uma expressão figurada ou literal.
   Da mesma forma, o ponto final (.) pode indicar o fim de uma frase ou fazer parte de uma abreviação como “Dr.”.

- **Idiomas Sem Delimitadores Explícitos**<br>
   Em idiomas como chinês, japonês e tailandês, as palavras não são separadas por espaços.
   Isso exige modelos especializados para identificar corretamente os limites entre palavras.


---
## 4. Ferramentas Populares

* **[NLTK](https://www.nltk.org/)**<br>
  Biblioteca em Python amplamente utilizada na área acadêmica. Suporta tokenização de palavras, sentenças e oferece diversos recursos de PLN.

* **[Hugging Face Transformers](https://huggingface.co/transformers/)**<br>
  Inclui tokenizadores otimizados e pré-treinados para modelos como BERT, GPT, RoBERTa e outros. Essencial para aplicações modernas em IA.


---
## 5. Exemplos com NLTK

### 5.1 Tokenização de Palavras com NLTK

```python
from nltk.tokenize import word_tokenize

texto = "Os chatbots são úteis."
tokens = word_tokenize(texto, language='portuguese')
print(tokens)  # ['Os', 'chatbots', 'são', 'úteis', '.']
```

---
### 5.2 Tokenização de Frases com NLTK

```python
from nltk.tokenize import sent_tokenize

texto = "Os chatbots são úteis. Eles ajudam em diversas tarefas."
frases = sent_tokenize(texto, language='portuguese')
print(frases)  # ['Os chatbots são úteis.', 'Eles ajudam em diversas tarefas.']
```

---
### 5.3 Tokenização de Caracteres (Simples)

```python
texto = "Chatbots"
tokens = list(texto)
print(tokens)  # ['C', 'h', 'a', 't', 'b', 'o', 't', 's']
```

---
## 6. Exemplos com Hugging Face

#### GPT-2
```python
from transformers import GPT2Tokenizer

tokenizer = GPT2Tokenizer.from_pretrained("gpt2")

texto = "Chatbots are useful"
tokens = tokenizer.tokenize(texto)
print(tokens)  # ['Chat', 'bots', ' are', ' useful']

```

