# 🧩 Manipulação de Dimensões no NumPy

Em Machine Learning e ciência de dados, é comum precisarmos **reorganizar a forma dos arrays** para alimentar corretamente os algoritmos. O NumPy oferece funções poderosas para isso.

---

## 🔁 `reshape()`

Altera a **forma (shape)** do array, sem mudar seus dados.

```python
a = np.array([1, 2, 3, 4, 5, 6])
b = a.reshape((2, 3))  # 2 linhas, 3 colunas

# array([[1, 2, 3],
#        [4, 5, 6]])
```

- O número total de elementos deve **permanecer o mesmo**.
- É possível usar `-1` para o NumPy calcular automaticamente uma dimensão:

```python
a.reshape((-1, 2))  # 3 linhas, 2 colunas
```

---

## 📏 `flatten()`

Retorna uma **cópia unidimensional** do array, independente da estrutura original.

```python
a = np.array([[1, 2], [3, 4]])
b = a.flatten()

# array([1, 2, 3, 4])
```

- Sempre retorna uma **nova cópia** do array original.

---

## 🪶 `ravel()`

Também retorna o array como **1D**, mas sempre que possível retorna uma **view (visão)** em vez de uma cópia.

```python
b = a.ravel()
```

- Usa menos memória.
- Mudanças no array retornado podem refletir no original (caso seja uma view).

---

## ➕ `expand_dims()`

Adiciona uma **nova dimensão** ao array em uma posição específica (útil para CNNs, LSTMs, etc).

```python
a = np.array([1, 2, 3])
b = np.expand_dims(a, axis=0)  # Adiciona uma dimensão na posição 0

# array([[1, 2, 3]]) → shape (1, 3)
```

```python
np.expand_dims(a, axis=1)
# array([[1],
#        [2],
#        [3]]) → shape (3, 1)
```

- Muito usado para ajustar a forma de dados para modelos que esperam entradas 2D, 3D ou 4D (ex: `Conv2D` no TensorFlow requer `[batch, height, width, channels]`).

---

## ✅ Quando usar cada um?

| Função           | O que faz                            | Cópia ou View?       | Quando usar? |
|------------------|---------------------------------------|----------------------|------------------|
| `reshape()`      | Muda o shape do array                 | View (se possível)   | Redimensionar dados |
| `flatten()`      | Transforma em vetor 1D                | Sempre cópia         | Preparar dados para modelos |
| `ravel()`        | Transforma em vetor 1D                | View (se possível)   | Operações rápidas e leves |
| `expand_dims()`  | Adiciona uma nova dimensão            | Cópia                | Ajustar shape para redes neurais |

---

Essas funções são essenciais para preparar os dados corretamente antes de alimentar modelos de machine learning, garantindo compatibilidade entre formatos de entrada e saída.
