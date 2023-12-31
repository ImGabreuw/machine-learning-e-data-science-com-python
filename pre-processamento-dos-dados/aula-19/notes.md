# Tratamento de valores faltantes

> ## **Biblioteca Pandas**

### **Função `isnull`**

A função `isnull()` é um método da biblioteca Pandas em Python, utilizado para verificar se há valores nulos (faltantes) em um DataFrame ou em uma Series. Ela retorna um DataFrame ou Series booleano, onde cada elemento é `True` se o valor for nulo (`NaN`) e `False` se o valor for não nulo.

**Sintaxe:**

```python
DataFrame.isnull()
```

**Principais características:**

- Retorna `True` para cada elemento que é nulo (NaN) e `False` para cada elemento que não é nulo.

- Pode ser aplicado tanto em um DataFrame completo quanto em colunas individuais (Series).

- Os valores nulos são frequentemente representados por `NaN` em conjuntos de dados do Pandas.

**Exemplo:**

```python
import pandas as pd

# Exemplo do DataFrame com valores nulos (NaN) na coluna 'age'
data = {'clientid': [28, 30, 31],
        'income': [59417.805406, 48528.852796, 23526.302555],
        'age': [None, None, None],
        'loan': [2082.625938, 6155.784670, 2862.010139],
        'default': [0, 0, 0]}

df = pd.DataFrame(data)

# Verificando quais valores da coluna 'age' são nulos (faltantes)
valores_nulos_age = df['age'].isnull()
print(valores_nulos_age)
```

**Saída:**

```
0    True
1    True
2    True
Name: age, dtype: bool
```

Neste exemplo, a função `isnull()` foi aplicada à coluna 'age' do DataFrame, retornando uma Series booleana indicando quais valores da coluna 'age' são nulos (True) e quais não são (False). Note que os valores nulos são representados por `True`.

### **Função `fillna`**

A função `fillna()` é um método da biblioteca Pandas em Python, utilizada para preencher valores nulos (NaN - Not a Number) em um DataFrame ou em uma Series com valores específicos. Dados faltantes são comuns em conjuntos de dados, e preencher esses valores é uma etapa importante no tratamento de dados ausentes antes de realizar análises ou modelagens.

**Sintaxe:**

```python
DataFrame.fillna(value, inplace=False)
```

**Principais parâmetros:**

- **value:** Obrigatório. O valor que será usado para preencher os valores nulos.

- **inplace:** Opcional. Se True, a modificação é realizada no próprio DataFrame (ou Series), e a função não retorna nada (None). Se False (padrão), a função retorna um novo DataFrame (ou Series) com os valores nulos preenchidos.

**Exemplo:**

```python
import pandas as pd

# Exemplo do DataFrame com valores nulos (NaN) na coluna 'age'
data = {'clientid': [28, 30, 31],
        'income': [59417.805406, 48528.852796, 23526.302555],
        'age': [None, None, None],
        'loan': [2082.625938, 6155.784670, 2862.010139],
        'default': [0, 0, 0]}

df = pd.DataFrame(data)

# Preenchendo os valores nulos da coluna 'age' com o valor 0
df['age'].fillna(0, inplace=True)

print(df)
```

**Saída:**

| clientid |       income | age |        loan | default |
| -------: | -----------: | --: | ----------: | ------: |
|       28 | 59417.805406 | 0.0 | 2082.625938 |       0 |
|       30 | 48528.852796 | 0.0 | 6155.784670 |       0 |
|       31 | 23526.302555 | 0.0 | 2862.010139 |       0 |

Neste exemplo, usamos a função `fillna()` para preencher os valores nulos da coluna 'age' com o valor 0. Ao definir `inplace=True`, a modificação é realizada diretamente no DataFrame original. Agora, a coluna 'age' não contém mais valores nulos e os dados estão prontos para serem utilizados em análises ou modelagens. É importante escolher um valor adequado para preencher os dados faltantes, considerando o contexto e o impacto dessa decisão na análise dos dados.
