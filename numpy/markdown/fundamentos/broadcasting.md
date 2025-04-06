# ➕➖✖️➗ Operações Matemáticas Elementares e Broadcasting

O NumPy permite fazer **operações matemáticas elementares** diretamente entre arrays ou entre arrays e escalares, de forma rápida e eficiente. Essas operações são **vetorizadas**, ou seja, aplicadas a todos os elementos automaticamente.

Além disso, o conceito de **broadcasting** permite realizar operações entre arrays de formas diferentes, sem precisar duplicar dados manualmente.

---

## 🔢 Operações Elementares com Arrays

Dado dois arrays:

```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
```

### ➕ Adição

```python
a + b        # array([5, 7, 9])
a + 10       # array([11, 12, 13])
```

### ➖ Subtração

```python
b - a        # array([3, 3, 3])
a - 1        # array([0, 1, 2])
```

### ✖️ Multiplicação (elemento a elemento)

```python
a * b        # array([4, 10, 18])
a * 2        # array([2, 4, 6])
```

### ➗ Divisão

```python
b / a        # array([4.0, 2.5, 2.0])
a / 2        # array([0.5, 1.0, 1.5])
```

- Todas essas operações funcionam **elemento a elemento**, desde que os arrays tenham **shapes compatíveis**.

---

## 🧠 Broadcasting

O **broadcasting** é uma regra que permite realizar operações matemáticas entre arrays de **formas diferentes**, desde que uma das formas possa ser ajustada automaticamente.

### 🔹 Exemplo 1: Escalar + Array

```python
a = np.array([1, 2, 3])
a + 10  # array([11, 12, 13])
```

→ O escalar `10` é "expandido" para o shape do array `a`.

### 🔹 Exemplo 2: Array 2D + 1D

```python
A = np.array([[1, 2, 3],
              [4, 5, 6]])
v = np.array([10, 20, 30])

A + v
# array([[11, 22, 33],
#        [14, 25, 36]])
```

→ O vetor `v` é **broadcasted** para cada linha da matriz `A`.

---

## 🧮 Regras de Broadcasting

1. **Compare as formas dos arrays da direita para a esquerda**
2. Os tamanhos devem ser **iguais** ou **um dos dois deve ser 1**
3. O NumPy automaticamente **"repete"** o array de tamanho 1 para igualar as dimensões

### Exemplo prático:

```python
A.shape = (3, 1)
B.shape = (1, 4)
C = A + B
C.shape → (3, 4)
```

---

## ✅ Por que isso importa em ML?

- Permite aplicar operações em **batches de dados** sem loops
- Facilita a **normalização de colunas**:
  ```python
  X = (X - X.mean(axis=0)) / X.std(axis=0)
  ```
- Otimiza performance com código mais simples e vetorizado

---

### ⚠️ Dica importante:
Se os shapes forem incompatíveis para broadcasting, o NumPy lançará um erro como:

```
ValueError: operands could not be broadcast together with shapes ...
```

---

Dominar essas operações e entender o broadcasting é **essencial para manipular dados eficientemente** e preparar inputs para os algoritmos de Machine Learning.
