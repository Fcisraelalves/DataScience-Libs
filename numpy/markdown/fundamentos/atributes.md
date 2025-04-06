# 🤖 Atributos mais úteis de um `ndarray` para Machine Learning

Ao trabalhar com **dados numéricos e vetores/matrizes** em Machine Learning, utilizamos intensamente arrays do NumPy. Abaixo estão os atributos **mais importantes** para análise, pré-processamento e modelagem.

---

## 🔹 `ndarray.ndim`

Número de **dimensões (ou eixos)** do array.

```python
a = np.array([[1, 2, 3], [4, 5, 6]])
a.ndim  # Saída: 2
```

Útil para verificar se os dados são 1D (vetor), 2D (tabela) ou mais (por exemplo, imagens RGB = 3D).

---

## 🔹 `ndarray.shape`

**Formato** do array: retorna uma tupla com o número de elementos em cada dimensão.

```python
a.shape  # (2, 3) → 2 linhas, 3 colunas
```

Muito usado para:
- Validar entradas e saídas de modelos;
- Redimensionar dados (`reshape`);
- Garantir compatibilidade entre features e labels.

---

## 🔹 `ndarray.size`

Número **total de elementos** no array.

```python
a.size  # 6
```

Importante para verificar se dados foram carregados corretamente ou se a alteração de forma está preservando o total de dados.

---

## 🔹 `ndarray.dtype`

Tipo de dados armazenado nos elementos.

```python
a.dtype  # int64, float32, etc.
```

Crucial ao lidar com:
- Normalização (precisamos de `float`);
- Conversões para tipos compatíveis com modelos (ex: `float32` para TensorFlow).

---

## 🔹 `ndarray.itemsize`

**Tamanho em bytes** de cada item no array.

```python
a.itemsize  # Ex: 8 para float64
```

Importante quando se deseja otimizar o uso de memória, por exemplo, em grandes datasets.

---

## 🔹 `ndarray.nbytes`

**Memória total ocupada** pelo array (em bytes).

```python
a.nbytes  # size * itemsize
```

Essencial para avaliar o custo de carregamento de dados na RAM, especialmente em datasets grandes.

---

## 🔹 `ndarray.T`

Retorna a **transposta** do array (troca linhas por colunas).

```python
a.T
```

Comum em:
- Operações matriciais;
- Ajustes de formato para entrada de modelos;
- Cálculos de produtos internos e correlações.

---
