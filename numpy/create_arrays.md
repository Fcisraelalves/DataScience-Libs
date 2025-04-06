# 📚 Fundamentos da Criação de Arrays com NumPy

A biblioteca NumPy fornece diversas funções para criação de arrays. Essas funções são fundamentais para manipulação de dados numéricos de forma eficiente em Python. Abaixo, exploramos algumas das mais utilizadas.

---

## 🔹 `np.array()`

Cria um array NumPy a partir de uma lista, tupla ou outra estrutura de dados semelhante.

```python
import numpy as np
a = np.array([1, 2, 3])
```

**Parâmetros principais:**
- `object`: Sequência ou estrutura de dados que será convertida em array.
- `dtype` (opcional): Tipo de dado do array (`int`, `float`, `str`, etc).
- `ndmin` (opcional): Número mínimo de dimensões.

---

## 🔹 `np.arange()`

Gera um array com valores igualmente espaçados dentro de um intervalo, similar à função `range()` do Python.

```python
np.arange(0, 10, 2)  # array([0, 2, 4, 6, 8])
```

**Parâmetros:**
- `start`: Valor inicial (inclusivo).
- `stop`: Valor final (exclusivo).
- `step`: Incremento entre os valores.

---

## 🔹 `np.linspace()`

Cria um array com um número fixo de valores igualmente espaçados entre dois limites.

```python
np.linspace(0, 1, 5)  # array([0. , 0.25, 0.5 , 0.75, 1. ])
```

**Parâmetros:**
- `start`: Início do intervalo.
- `stop`: Fim do intervalo.
- `num`: Número de elementos gerados.
- `endpoint` (opcional): Inclui o valor final se `True`.

---

## 🔹 `np.zeros()` e `np.ones()`

Cria arrays preenchidos com zeros ou uns.

```python
np.zeros((2, 3))  # matriz 2x3 de zeros
np.ones((2, 3))   # matriz 2x3 de uns
```

**Parâmetros:**
- `shape`: Tupla com as dimensões do array.
- `dtype` (opcional): Tipo de dado dos elementos.

---

## 🔹 `np.full()`

Cria um array preenchido com um valor específico.

```python
np.full((2, 2), 7)  # matriz 2x2 preenchida com 7
```

**Parâmetros:**
- `shape`: Dimensão do array.
- `fill_value`: Valor a ser inserido em cada posição.

---

## 🔹 `np.identity()`

Cria uma matriz identidade (diagonal principal com 1s e zeros no restante).

```python
np.identity(3)
```

**Parâmetros:**
- `n`: Número de linhas (e colunas) da matriz quadrada.

---

## 🔹 `np.random.randint()`

Gera inteiros aleatórios dentro de um intervalo.

```python
np.random.randint(1, 10, size=(2, 3))
```

**Parâmetros:**
- `low`: Limite inferior (inclusivo).
- `high`: Limite superior (exclusivo).
- `size`: Forma do array.

---

## 🔹 `np.random.standard_normal()`

Gera valores aleatórios com distribuição normal padrão (média = 0, desvio padrão = 1).

```python
np.random.standard_normal((2, 2))
```

**Parâmetros:**
- `size`: Forma do array.

---

## 🔹 `np.random.uniform()`

Gera números aleatórios com distribuição uniforme contínua.

```python
np.random.uniform(0, 1, size=(2, 2))
```

**Parâmetros:**
- `low`: Limite inferior (inclusivo).
- `high`: Limite superior (exclusivo).
- `size`: Forma do array.

---

## 🔹 `np.random.integers()` *(versão mais recente do `randint`)*

Gera inteiros aleatórios **inclusive no limite superior** (diferente de `randint`).

```python
np.random.integers(1, 10, size=(2, 2))
```

**Parâmetros:**
- `low`: Mínimo valor (inclusivo).
- `high`: Máximo valor (inclusivo).
- `size`: Forma do array.

---

## 🔹 `np.random.permutation()`

Retorna uma permutação aleatória de uma sequência ou reorganiza aleatoriamente os índices de um array.

```python
np.random.permutation([1, 2, 3, 4])
```

**Parâmetros:**
- `x`: Sequência a ser permutada (array, lista ou número inteiro `n` para permutar `np.arange(n)`).

---
