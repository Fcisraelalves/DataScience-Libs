# 🔗 Concatenar e Dividir Arrays no NumPy

Na prática com dados, é comum precisarmos **juntar arrays (concatenar)** ou **separá-los (dividir)** em subconjuntos para treinar modelos, aplicar validação cruzada ou montar pipelines. O NumPy fornece funções específicas para isso.

---

## 🔗 Concatenar Arrays

### 📌 `np.concatenate()`

Une dois ou mais arrays ao longo de um **eixo especificado**.

```python
import numpy as np

a = np.array([[1, 2],
              [3, 4]])

b = np.array([[5, 6]])

np.concatenate((a, b), axis=0)
# array([[1, 2],
#        [3, 4],
#        [5, 6]])
```

- `axis=0`: concatena **linhas** (verticalmente, mesma quantidade de colunas)
- `axis=1`: concatena **colunas** (horizontalmente, mesma quantidade de linhas)

> ⚠️ Os arrays devem ter **shapes compatíveis**, exceto na direção da concatenação.

---

### 🔽 `np.vstack()`: Vertical Stack

Concatena arrays **verticalmente** (como `axis=0`), mesmo que sejam 1D.

```python
a = np.array([1, 2])
b = np.array([3, 4])

np.vstack((a, b))
# array([[1, 2],
#        [3, 4]])
```

> Útil para empilhar vetores como linhas.

---

### ➡️ `np.hstack()`: Horizontal Stack

Concatena arrays **horizontalmente** (como `axis=1`).

```python
np.hstack((a, b))
# array([1, 2, 3, 4])
```

> Quando usado com arrays 2D, junta colunas.

---

## ✂️ Dividir Arrays

### 🔪 `np.split()`

Divide um array em **subarrays** ao longo de um eixo.

```python
x = np.array([[1, 2, 3, 4],
              [5, 6, 7, 8]])

np.split(x, 2, axis=1)
# [array([[1, 2],
#         [5, 6]]),
#  array([[3, 4],
#         [7, 8]])]
```

- O segundo argumento indica **em quantas partes dividir**
- O número de divisões deve ser **exato**, ou ocorrerá erro

---

### Outras variações úteis

- `np.vsplit()` → divide **verticalmente** (por linhas)
- `np.hsplit()` → divide **horizontalmente** (por colunas)
- `np.array_split()` → permite dividir mesmo que o número de divisões não seja igual

```python
np.array_split(x, 3, axis=1)
# divide em 3 partes desiguais
```

---

## ✅ Aplicações comuns em Machine Learning

- **Dividir conjuntos** em treino/teste/validação
- **Concatenar batches de dados** em pré-processamento
- **Empilhar vetores de características**
- **Juntar previsões** de modelos diferentes (ensemble)

---

Essas operações tornam o código mais modular, dinâmico e escalável, principalmente ao lidar com arrays grandes e pipelines de processamento de dados.

