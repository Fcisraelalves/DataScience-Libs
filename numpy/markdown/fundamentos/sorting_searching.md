# 🔍 Ordenação e Pesquisa com NumPy

Em muitos problemas de Machine Learning, é necessário **ordenar dados** (por exemplo, notas, probabilidades, distâncias), ou **localizar a posição ideal** para inserir valores em um array ordenado. O NumPy fornece funções otimizadas para isso.

---

## 🔢 `np.sort()`: Ordenar elementos

Retorna uma **cópia ordenada** do array.

```python
import numpy as np

a = np.array([3, 1, 4, 1, 5])
np.sort(a)
# array([1, 1, 3, 4, 5])
```

### Ordenando arrays multidimensionais

Use o argumento `axis`:

```python
b = np.array([[3, 1, 2],
              [6, 5, 4]])

np.sort(b, axis=1)  # ordena linhas
# array([[1, 2, 3],
#        [4, 5, 6]])
```

- `axis=0`: ordena **por coluna**
- `axis=1`: ordena **por linha**
- por padrão, `kind='quicksort'`, mas também aceita `'mergesort'`, `'heapsort'`, etc.

> ⚠️ `np.sort()` retorna **uma cópia**. Se quiser ordenar **in-place**, use `a.sort()`.

---

## 🧮 `np.argsort()`: Índices da ordenação

Retorna os **índices que ordenariam** o array.

```python
a = np.array([10, 5, 3])
np.argsort(a)
# array([2, 1, 0])
```

> Isso é útil quando você quer ordenar um array **e manter a referência original**, como índices de amostras ou IDs.

### Exemplo prático:

```python
nomes = np.array(['img3', 'img1', 'img2'])
confianças = np.array([0.75, 0.92, 0.60])

idx = np.argsort(confianças)[::-1]  # índices em ordem decrescente
nomes[idx]
# array(['img1', 'img3', 'img2'])
```

---

## 🔎 `np.searchsorted()`: Inserção em array ordenado

Retorna o índice onde **um novo valor deveria ser inserido** para manter a ordem.

```python
arr = np.array([1, 3, 5, 7])
np.searchsorted(arr, 4)
# 2 → o valor 4 deve ser inserido na posição 2
```

### Mais exemplos:

```python
np.searchsorted(arr, [0, 6, 8])
# array([0, 3, 4])
```

### Argumento `side`

- `side='left'`: insere **antes** de elementos iguais
- `side='right'`: insere **depois** de elementos iguais

```python
arr = np.array([1, 3, 3, 3, 5])
np.searchsorted(arr, 3, side='left')  # 1
np.searchsorted(arr, 3, side='right') # 4
```

---

## ✅ Aplicações práticas em Machine Learning

- **Ordenar previsões** ou scores de modelos
- **Selecionar top-N amostras**
- **Encontrar posições** para discretização de dados
- **Construir rankings**
- **Agrupar elementos similares**

---

Essas funções são essenciais para **pré-processamento, análise estatística e pós-processamento de resultados** em ML, especialmente quando se trabalha com ordenações, rankings e thresholds.

