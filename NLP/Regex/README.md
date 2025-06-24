# 1. Expressões Regulares (Regex)

**Regex** (ou **Expressões Regulares**) são padrões utilizados para **buscar, extrair ou substituir partes de texto** com base em regras formais.

No contexto do Processamento de Linguagem Natural (PLN), o uso de regex é muito comum nas etapas de **normalização** e **pré-processamento**, como remover URLs, limpar símbolos, detectar padrões de palavras, etc.

---
## 1.1 Por que usar Regex?

- Identificar padrões de texto de forma eficiente
- Substituir ou remover conteúdo indesejado (ex: links, HTML)
- Extrair dados específicos de grandes blocos de texto

---
## 1.2 Sintaxe Básica de Regex

| Padrão | Significado                                       | Exemplo (em texto)                     |
|--------|---------------------------------------------------|----------------------------------------|
| `.`    | Qualquer caractere (exceto nova linha)            | `a.c` casa com `abc`, `a-c`, `a2c`     |
| `\d`   | Qualquer dígito (equivale a `[0-9]`)              | `\d\d\d` casa com `123`, `999`, etc.   |
| `\w`   | Qualquer caractere alfanumérico ou underscore     | `\w+` casa com `palavra_123`           |
| `\s`   | Qualquer espaço em branco (espaço, tab, quebra)   | `\s+` casa com múltiplos espaços       |
| `^`    | Início da linha                                   | `^Olá` casa com `Olá mundo`, mas não com `Oi, Olá mundo` |
| `$`    | Fim da linha                                      | `fim$` casa com `Esse é o fim`         |
| `*`    | 0 ou mais repetições                              | `a*` casa com ``, `a`, `aaa`           |
| `+`    | 1 ou mais repetições                              | `a+` casa com `a`, `aaaa`              |
| `?`    | 0 ou 1 ocorrência                                 | `colou?r` casa com `color` e `colour`  |
| `[]`   | Conjunto de caracteres                            | `[aeiou]` casa com qualquer vogal      |
| `()`   | Agrupamento                                       | `(ha)+` casa com `ha`, `hahaha`, etc.  |
| `|`    | OU lógico                                          | `gato|cachorro` casa com `gato` ou `cachorro` |

---
## 1.3 Exemplos em Python

### Remover URLs com Regex

```python
import re

texto = "Veja mais em https://site.com e também em www.exemplo.org"
texto_limpo = re.sub(r'https?://\S+|www\.\S+', '', texto)
print(texto_limpo)  # Veja mais em  e também em 
```

### Encontrar todos os números

```python
texto = "O valor é 123, depois 456 e então 7890."
numeros = re.findall(r'\d+', texto)
print(numeros)  # ['123', '456', '7890']
```

### Substituir múltiplos espaços por apenas um

```python
texto = "Este    é  um     texto    com   espaços"
texto_normalizado = re.sub(r'\s+', ' ', texto).strip()
print(texto_normalizado)  # Este é um texto com espaços
```
