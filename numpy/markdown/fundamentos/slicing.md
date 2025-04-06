# 🔍 Indexação e Fatiamento (`slicing`) de Arrays no NumPy

Saber **acessar, selecionar e modificar partes específicas de arrays** é essencial em projetos de Machine Learning e ciência de dados. A seguir, veremos como fazer isso de forma eficiente com o NumPy.

---

## 🎯 Indexação Básica

A indexação funciona como em listas do Python: os índices começam em **0**.

```python
import numpy as np
a = np.array([10, 20, 30, 40, 50])
a[0]    # 10
a[-1]   # 50 (último elemento)
```

### Em arrays 2D:

```python
b = np.array([[1, 2, 3],
              [4, 5, 6]])
b[0, 0]  # Linha 0, coluna 0 → 1
b[1, 2]  # Linha 1, coluna 2 → 6
```

---

## ✂️ Fatiamento (Slicing)

Permite selecionar **intervalos** de elementos usando a notação `inicio:fim:passo`.

```python
a[1:4]     # [20, 30, 40]
a[:3]      # [10, 20, 30] (do início até índice 2)
a[::2]     # [10, 30, 50] (de 2 em 2)
a[::-1]    # [50, 40, 30, 20, 10] (ordem reversa)
```

---

## 📐 Fatiamento em Arrays 2D

```python
b = np.array([[ 1,  2,  3],
              [ 4,  5,  6],
              [ 7,  8,  9]])

b[0:2, 1:]  # Linhas 0 e 1, colunas 1 até o fim
# Resultado:
# array([[2, 3],
#        [5, 6]])
```

### Sintaxe geral para 2D:

```python
array[linhas, colunas]
```

- `b[1, :]` → linha 1 inteira
- `b[:, 2]` → coluna 2 inteira
- `b[::2, ::2]` → linhas e colunas de 2 em 2

---

## 🔄 Modificando Partes do Array

Você pode alterar valores diretamente via indexação:

```python
a = np.array([0, 1, 2, 3, 4])
a[1:4] = 99
# array([ 0, 99, 99, 99, 4])
```

---

## 🧠 Dicas úteis

- Fatiamentos não criam cópias por padrão, apenas **"views"** (visões). Alterar uma fatia afeta o array original.
- Para criar uma **cópia independente**, use `.copy()`:

```python
c = a[1:4].copy()
```

---

## ✅ Quando isso é útil em ML?

- Selecionar subconjuntos de dados (ex: primeiras 100 amostras)
- Separar colunas de features e rótulos
- Aplicar máscaras ou filtros personalizados
- Reorganizar dados de entrada para modelos

---
