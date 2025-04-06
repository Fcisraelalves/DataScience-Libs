# 📄 Copiar e Visualizar Dados em NumPy: `copy()` vs `view()`

Quando você trabalha com arrays NumPy, é **muito importante** entender a diferença entre **cópias reais** e **visualizações (views)**. Essa diferença determina se **modificações em um array afetarão outro**.

---

## 🧠 Conceito: Arrays são objetos mutáveis

No NumPy, arrays são **estruturas mutáveis**. Isso significa que ao fazer uma atribuição simples, você não está criando um novo array, mas apenas apontando para o mesmo bloco de memória:

```python
import numpy as np

a = np.array([1, 2, 3])
b = a  # não é uma cópia! apenas outra referência
b[0] = 99
print(a)
# array([99, 2, 3])  # a também foi alterado!
```

---

## 📌 `copy()`: cópia **independente**

`copy()` cria uma **nova cópia** do array original. Alterações na cópia **não afetam** o original.

```python
a = np.array([1, 2, 3])
b = a.copy()
b[0] = 100

print(a)  # array([1, 2, 3])
print(b)  # array([100, 2, 3])
```

Essa é a forma mais **segura** quando você quer manipular dados sem alterar o original — muito útil durante:

- Pré-processamento de dados
- Normalização e padronização
- Divisão treino/teste

---

## 👁️ `view()`: visualização (mesma memória)

`view()` cria uma **visualização** do array original. Eles compartilham a **mesma memória**, ou seja, modificar um modifica o outro.

```python
a = np.array([1, 2, 3])
b = a.view()
b[0] = 200

print(a)  # array([200, 2, 3])
```

> A `view()` é útil quando você quer **acessar ou transformar os dados temporariamente** sem duplicar memória.

---

## 🧪 Diferença visual: id e flags

Você pode verificar se dois arrays compartilham dados com:

```python
a.base is None      # True → a é o dono dos dados
b = a.view()
b.base is a         # True → b é uma view de a
```

E usando `.flags`:

```python
a.flags.owndata     # True
b.flags.owndata     # False
```

---

## ✅ Quando usar cada um?

| Situação                            | Use `copy()`       | Use `view()`       |
|------------------------------------|---------------------|--------------------|
| Processar sem afetar o original    | ✅                  | ❌                |
| Ganhar performance sem duplicar    | ❌                  | ✅                |
| Aplicar transformações temporárias | ❌                  | ✅                |
| Criar datasets modificados         | ✅                  | ❌                |

---

## 💡 Em Machine Learning

Durante o pipeline de ML, é comum:

- Fazer `.copy()` para preservar os dados brutos antes da normalização
- Usar `.view()` em slicing para economizar memória
- Evitar bugs por **referência compartilhada involuntária**

---

Entender a diferença entre `copy()` e `view()` te ajuda a evitar **efeitos colaterais** indesejados nos seus arrays, tornando seu código mais **seguro e confiável**.

