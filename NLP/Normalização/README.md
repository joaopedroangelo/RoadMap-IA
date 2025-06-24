# 1. Normalização — Preparando o Texto para a Tokenização

**Normalização** é a etapa do pré-processamento que visa **padronizar e limpar o texto bruto**, tornando-o mais adequado para as próximas etapas, especialmente a **tokenização** e o **processamento por modelos de linguagem**.

---
## 1.1 Por que Normalizar?

Antes que um texto seja tokenizado, ele pode conter variações, ruídos ou formatos inconsistentes que atrapalham a interpretação por modelos. A normalização reduz essa variabilidade, ajudando a tornar o texto:

- Mais padronizado (ex: tudo em minúsculas)
- Livre de ruídos (ex: emojis, URLs, HTML)
- Mais fácil de tokenizar e processar

---
## 1.2 Etapas Comuns de Normalização

| Etapa                            | Descrição                                                             | Exemplo                                                  |
|----------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------|
| **Remoção de Ruído**            | Elimina HTML, emojis, URLs, símbolos não textuais                    | `"Olá! :) <b>Bem-vindo</b>"` → `"Olá! Bem-vindo"`        |
| **Conversão para Minúsculas**   | Padroniza as letras para minúsculas                                  | `"ChatBots São Úteis"` → `"chatbots são úteis"`          |
| **Remoção de Acentos**          | Torna o texto mais neutro se o modelo não for sensível a acentos     | `"úteis"` → `"uteis"`                                     |
| **Remoção de Pontuação**        | Opcional, dependendo do objetivo                                     | `"Olá, mundo!"` → `"Olá mundo"`                          |
| **Expansão de Contrações**      | Deixa o texto mais explícito para análise posterior                  | `"não é"` → `"nao e"`                                     |
| **Espaços Extras**              | Remove múltiplos espaços, que podem interferir na tokenização        | `"isto   é   um teste"` → `"isto é um teste"`            |

---
## 1.3 Normalização vem **antes** da Tokenização

A normalização prepara o texto para que a **tokenização** produza resultados mais consistentes e úteis.

```text
Texto Bruto
   ↓
1. Normalização
   ↓
2. Tokenização
   ↓
3. Processamento (modelo)
```

> Sem normalização, a tokenização pode gerar tokens inconsistentes, como "Olá!" sendo tratado diferente de "olá"

---
## 1.4 Exemplo em Python (normalização básica)

```python
import re
import unicodedata

def normalizar_texto(texto):
    texto = texto.lower()  # minúsculas
    texto = unicodedata.normalize('NFKD', texto).encode('ASCII', 'ignore').decode('utf-8')  # sem acento
    texto = re.sub(r'https?://\S+|www\.\S+', '', texto)  # remove URLs
    texto = re.sub(r'<.*?>', '', texto)  # remove HTML
    texto = re.sub(r'[^a-zA-Z0-9\s]', '', texto)  # remove pontuação
    texto = re.sub(r'\s+', ' ', texto).strip()  # remove espaços extras
    return texto

exemplo = "Olá! Visite nosso site: https://exemplo.com :)"
print(normalizar_texto(exemplo))  # 'ola visite nosso site'
```

---
## 1.5 Observações

A normalização deve ser adaptada à tarefa e ao idioma.

Alguns modelos (como BERT) esperam o texto original, então nem toda normalização é necessária em pipelines modernas.

