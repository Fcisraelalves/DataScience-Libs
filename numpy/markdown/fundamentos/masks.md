# 🎭 Máscaras e Filtragem de Dados com Indexação Booleana (Boolean Indexing)

A **indexação booleana** é uma técnica para filtrar dados em arrays NumPy com base em **condições lógicas**. Em vez de acessar os dados por índices numéricos, usamos **máscaras booleanas** (`True` ou `False`) para selecionar os elementos desejados.

Essa abordagem é muito comum em **pré-processamento de dados**, quando precisamos, por exemplo:

- Remover outliers
- Selecionar amostras com uma característica específica
- Separar classes ou faixas de valores
- Criar subconjuntos do conjunto de dados

---

## 🧠 Como funciona

Se aplicarmos uma **condição lógica** sobre um array, o NumPy retorna uma **máscara booleana**:

```python
import numpy as np

dados = np.array([10, 15, 20, 25, 30])
mascara = dados > 20
# array([False, False, False,  True,  True])
```

Para filtrar os valores que satisfazem a condição:

```python
dados[dados > 20]
# array([25, 30])
```

---

## 🔍 Exemplos de condições

```python
dados < 15         # menores que 15
dados == 20        # iguais a 20
(dados >= 15) & (dados <= 25)  # entre 15 e 25
```

> ⚠️ Use parênteses ao combinar condições com `&` (E) ou `|` (OU), pois o Python segue a precedência lógica.

---

## 🧱 Aplicando em arrays 2D

```python
matriz = np.array([[10, 20, 30],
                   [40, 50, 60]])

matriz[matriz > 30]
# array([40, 50, 60])
```

> A filtragem retorna os elementos de forma **achatada (1D)**. Para manter a forma original, usamos técnicas como `np.where()` ou `reshape()` depois da filtragem.

---

## 🛠️ Modificando valores com máscara

Você pode usar máscaras para **alterar** elementos do array:

```python
dados[dados < 20] = 0
# array([ 0,  0, 20, 25, 30])
```

---

## 🧮 `np.where()`: outra forma de aplicar lógica condicional

A função `np.where(condição, valor_se_verdadeiro, valor_se_falso)` é muito útil:

```python
np.where(dados > 20, 1, 0)
# array([0, 0, 0, 1, 1])
```

Isso é frequentemente usado para **criar colunas binárias (one-hot)** ou aplicar rótulos com base em condições.

---

## ✅ Aplicações em Machine Learning

- Selecionar dados por **classe alvo**
- Remover ou marcar **valores ausentes (NaN)** ou inválidos
- Criar colunas auxiliares para **feature engineering**
- Aplicar **estratégias de balanceamento** de classes
- Gerar **máscaras de amostragem** para treino/teste/validação

---

## 🎓 Dica importante

A indexação booleana **preserva o shape relativo dos dados filtrados** e permite operações vetorizadas — muito mais eficientes do que laços `for`.

---

A indexação booleana é uma das ferramentas mais expressivas do NumPy. Dominar bem seu uso melhora tanto a **leitura** quanto a **eficiência** do seu código!

