# 📊 Funções de Agregação no NumPy

Funções de agregação são usadas para **resumir dados** e obter **informações estatísticas** de arrays. São extremamente úteis em pré-processamento, análise exploratória e avaliação de modelos.

---

## 🔢 Principais funções de agregação

Suponha um array `a`:

```python
import numpy as np

a = np.array([[1, 2, 3],
              [4, 5, 6]])
```

---

### 🔼 `sum()`: Soma dos elementos

```python
np.sum(a)        # 21
np.sum(a, axis=0)  # Soma por colunas: [5, 7, 9]
np.sum(a, axis=1)  # Soma por linhas:  [6, 15]
```

---

### 📏 `mean()`: Média dos elementos

```python
np.mean(a)         # 3.5
np.mean(a, axis=0) # [2.5, 3.5, 4.5]
```

---

### 📉 `std()`: Desvio padrão

Avalia a dispersão dos dados.

```python
np.std(a)           # 1.7078...
np.std(a, axis=1)   # Desvio por linha
```

---

### 🔽 `min()` e 🔼 `max()`: Valor mínimo e máximo

```python
np.min(a)           # 1
np.max(a)           # 6
np.min(a, axis=1)   # [1, 4]
np.max(a, axis=0)   # [4, 5, 6]
```

---

### 📍 `argmin()` e `argmax()`: Índices do menor e maior valor

Retornam o **índice linear (1D)** do menor/maior valor no array.

```python
np.argmin(a)  # 0 → posição do valor 1
np.argmax(a)  # 5 → posição do valor 6
```

### Para encontrar a posição 2D:

```python
idx = np.unravel_index(np.argmax(a), a.shape)
# (1, 2) → linha 1, coluna 2 (onde está o valor 6)
```

---

## 🧠 Eixos (`axis`) — Como funcionam?

A maioria dessas funções aceita o argumento `axis`, que controla **a direção da agregação**:

- `axis=0`: agrega por colunas (compara valores **linha a linha**)
- `axis=1`: agrega por linhas (compara valores **coluna a coluna**)

### Exemplo visual:

```python
a = np.array([[1, 2, 3],
              [4, 5, 6]])
```

| `np.sum(a, axis=0)` | Soma por coluna → `[5, 7, 9]` |
|---------------------|------------------------------|
| `np.sum(a, axis=1)` | Soma por linha  → `[6, 15]`  |

---

## ✅ Aplicações práticas em ML

- **Normalização de dados**: usar média e desvio para padronizar entradas
- **Análise estatística**: entender distribuição dos dados
- **Escolha de amostras**: localizar valores máximos/mínimos
- **Avaliação de modelos**: calcular métricas agregadas de desempenho

---

Essas funções tornam possível **resumir e interpretar grandes quantidades de dados** com poucas linhas de código, sendo essenciais no seu toolkit de Machine Learning.
