# Edit Distance (Distância de Edição)

> Similaridade entre duas Strings

---
## Definição

Distância de edição , também conhecida como distância de Levenshtein , é uma métrica usada para quantificar a similaridade entre duas strings. Ela mede o número mínimo de edições de um único caractere (inserções, exclusões ou substituições) necessárias para transformar uma string na outra. 

Considere as palavras **Sábado** e **Domingo**.

Para encontrar a distância de edição entre essas duas sequências de caracteres, precisamos determinar o número mínimo de edições de caracteres únicos (inserções, exclusões, substituições) necessárias para transformar "sábado" em "domingo".

---
## Tipos de Edição

**1. Inserção**:<br>
Adicionar um único caractere a uma das strings.

**2. Exclusão**:<br>
Remoção de um único caractere de uma das strings.

**3. Substituição**:<br>
Substituir um caractere em uma das strings por outro caractere.

---
## Exemplo

**Sábado** --> **Domingo**

#### Primeiro Caractere

S --> SUBSTITUÍDO --> D

#### Segundo Caractere

á --> SUBSTITUIDO --> o

#### Terceiro Caractere

b --> SUBSTITUIDO --> m

#### Quarto Caractere

a --> SUBSTITUIDO --> i

#### Quinto Caractere

d --> SUBSTITUIDO --> n

#### Sexto Caractere

o --> SUBSTITUIDO --> g

#### Sétimo Caractere

ADIÇÃO --> o

---
## Onde aplicar a Distância de Edição?

É amplamente utilizado em verificação ortográfica , comparação de sequências de DNA , detecção de plágio e comparação de similaridade de strings em geral. Ao calcular a distância de edição entre duas strings, podemos entender o quão semelhantes ou diferentes elas são com base no número de operações necessárias para transformar uma string na outra.

