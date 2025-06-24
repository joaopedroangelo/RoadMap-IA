# Definição - Tokenização

Tokenização, no contexto do Processamento de Linguagem Natural (PLN), é o processo de dividir um texto em partes menores chamadas tokens, que podem ser palavras, caracteres ou unidades intermediárias.

Esse processo é essencial porque torna o texto mais estruturado e compreensível para as máquinas. Assim como ensinamos uma criança a ler começando por letras e sílabas antes de chegar a frases, a tokenização "ensina" os computadores a entender a linguagem humana de forma incremental.

#### Exemplo

> Frase: "Os chatbots são úteis.

```python
["Os", "chatbots", "são", "úteis"]
```

Esse é um exemplo de tokenização por palavras, onde os espaços servem como delimitadores.

No entanto, existem outras formas de tokenizar um texto, como por caracteres ou subpalavras, dependendo do idioma e do objetivo da tarefa.


---
# Tipos de Tokenização

| Tipo                         | Descrição | Quando Usar | Exemplo com “Chatbots” |
|-----------------------------|-----------|-------------|-------------------------|
| **Tokenização de Palavras** | Divide o texto com base em espaços e pontuação. Funciona bem em idiomas com separações claras. | Análises gerais, modelos simples | `["Chatbots", "são", "úteis"]` |
| **Tokenização de Caracteres** | Quebra o texto em caracteres individuais. | Análise ortográfica, tarefas muito detalhadas | `["C", "h", "a", "t", "b", "o", "t", "s"]` |
| **Tokenização de Subpalavras** | Divide em unidades menores que palavras completas. Usada para reduzir o vocabulário e tratar palavras desconhecidas. | Modelos neurais como BERT, GPT | `["Chat", "bots"]` ou `["Cha", "tbo", "ts"]` |
| **Baseada em Modelos de Linguagem** | Usa regras e aprendizado prévio para tokenizar de forma mais precisa. | Textos complexos, idiomas sem espaços claros | spaCy, NLTK, transformers (BERT, GPT) |


---
# Desafios da Tokenização

1. **Ambiguidade**

    A frase "Estou morrendo de fome" pode ser interpretada literalmente ou como uma hipérbole.

    Outro exemplo: O ponto final (.) pode indicar fim de frase ou fazer parte de uma abreviação como "Dr.".

2. **Idiomas Sem Delimitadores Claros**

    Idiomas como chinês, japonês e tailandês não usam espaços para separar palavras, dificultando a tokenização.

    Existem modelos de Linguagem adequados para tokenizar essas línguas.


---
# Ferramentas

1. **NLTK**
    
    Uma biblioteca popular em Python, oferece suporte à tokenização de palavras e frases.
    É bastante utilizada em ambientes acadêmicos e em protótipos.

2. **Hugging Face Transformers**

    Inclui tokenizadores avançados usados em modelos como BERT, GPT, RoBERTa.
