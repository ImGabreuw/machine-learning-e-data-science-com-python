# Tratamento de valores inconsistentes

> ## **Tratamento de dados**

O tratamento de dados em uma base de dados é uma etapa crucial na análise de dados, pois dados inconsistentes podem prejudicar a qualidade e a confiabilidade das análises e modelos construídos. Abaixo, estão listados as três principais abordagens:

1. **Apagar a coluna inteira, caso a maioria dos dados dessa coluna estejam inconsistentes:**

   Nesta abordagem, se a maioria dos valores em uma coluna estiver inconsistente, pode ser uma opção eliminar completamente essa coluna da base de dados, pois ela não fornecerá informações relevantes para a análise. No entanto, é importante avaliar o impacto dessa exclusão na análise geral, pois pode haver informações importantes em outras colunas associadas.

2. **Apagar apenas os registros com dados inconsistentes:**

   Nessa abordagem, os registros (linhas) que contêm valores inconsistentes são removidos da base de dados. Isso pode ser uma solução viável quando apenas uma pequena proporção de registros está com dados inconsistentes. A exclusão dos registros evita que os dados errôneos afetem a análise de outras observações.

3. **Substituir os valores inconsistentes pela média:**

   Essa abordagem é útil quando apenas alguns valores estão inconsistentes na coluna. Nesse caso, podemos calcular a média dos valores válidos da coluna e substituir os valores inconsistentes por essa média. Essa abordagem mantém a quantidade de dados e pode ser uma solução razoável para evitar perda de informações.

### **Exemplo**

Considere a seguinte base de dados com as colunas: 'clientid', 'income', 'age', 'loan' e 'default'. Suponha que a coluna 'age' contenha apenas valores negativos como dados inconsistentes.

| clientid | income | age | loan | default |
| -------- | ------ | --- | ---- | ------- |
| 1        | 50000  | -35 | 2000 | No      |
| 2        | 30000  | -27 | 1000 | Yes     |
| 3        | 25000  | 32  | 1500 | No      |
| 4        | 70000  | -20 | 3000 | Yes     |
| 5        | 40000  | -45 | 1000 | No      |

**Apagar a coluna inteira, caso a maioria dos dados dessa coluna estejam inconsistentes:**

Neste exemplo, se a coluna 'age' contém apenas valores negativos, podemos optar por apagar toda a coluna, já que não possui dados válidos para análise.

```python
treated_base_credit = base_credit.drop("age", axis=1) # axis = 1 <=> coluna
print(treated_base_credit)
```

| clientid | income | loan | default |
| -------- | ------ | ---- | ------- |
| 1        | 50000  | 2000 | No      |
| 2        | 30000  | 1000 | Yes     |
| 3        | 25000  | 1500 | No      |
| 4        | 70000  | 3000 | Yes     |
| 5        | 40000  | 1000 | No      |

**Apagar apenas os registros com dados inconsistentes:**

Nessa abordagem, removeríamos as linhas 1, 2 e 4, pois elas contêm valores negativos na coluna 'age'.

```python
treated_base_credit = base_credit.drop(base_credit[base_credit["age"] < 0].index)
print(treated_base_credit)
```

| clientid | income | age | loan | default |
| -------- | ------ | --- | ---- | ------- |
| 3        | 25000  | 32  | 1500 | No      |
| 5        | 40000  | -45 | 1000 | No      |

**Substituir os valores inconsistentes pela média:**

Nessa abordagem, calcularíamos a média dos valores válidos da coluna 'age' (32 anos) e substituiríamos os valores inconsistentes pela média.

```python
average = base_credit["age"][base_credit["age"] > 0].mean()
base_credit.loc[base_credit["age"] < 0, "age"] = average
```

| clientid | income | age | loan | default |
| -------- | ------ | --- | ---- | ------- |
| 1        | 50000  | 32  | 2000 | No      |
| 2        | 30000  | 32  | 1000 | Yes     |
| 3        | 25000  | 32  | 1500 | No      |
| 4        | 70000  | 32  | 3000 | Yes     |
| 5        | 40000  | 32  | 1000 | No      |

> ## **Biblioteca Pandas**

### **Função `loc`**

A função `loc` é um recurso poderoso da biblioteca Pandas em Python, utilizada para localizar dados em um _DataFrame_ de forma baseada em rótulos (filtros). Com `loc`, é possível realizar operações de indexação baseadas em rótulos de linhas e colunas, tornando a manipulação de dados mais conveniente e intuitiva.

Sintaxe:

```python
dataframe.loc[linhas, colunas]
```

Principais parâmetros:

- **linhas:** Permite selecionar as linhas desejadas com base nos rótulos do índice.

- **colunas:** Permite selecionar as colunas desejadas com base nos rótulos dos cabeçalhos.

Uso e exemplos:

1. Acessar uma célula específica:

   ```python
   import pandas as pd

   data = {'Nome': ['João', 'Maria', 'Pedro'],
           'Idade': [25, 30, 22],
           'Cidade': ['São Paulo', 'Rio de Janeiro', 'Belo Horizonte']}

   df = pd._DataFrame_(data)

   # Acessar a célula da linha 1 e coluna 'Nome'
   valor = df.loc[1, 'Nome']
   print(valor)

   # Saída: 'Maria'
   ```

2. Selecionar um subconjunto de linhas e colunas:

   ```python
   # Selecionar as linhas de índice 0 a 1 e as colunas 'Nome' e 'Idade'
   subset = df.loc[0:1, ['Nome', 'Idade']]
   print(subset)

   # Saída:
   #     Nome  Idade
   # 0   João     25
   # 1  Maria     30
   ```

3. Fazer uma filtragem baseada em condições:

   ```python
   # Filtrar as linhas onde a idade é maior que 25
   filtro = df.loc[df['Idade'] > 25]
   print(filtro)

   # Saída:
   #     Nome  Idade        Cidade
   # 1  Maria     30  Rio de Janeiro
   ```

   Uma alternativa à função `loc`, nesse caso, é utilizar um filtro diretamente, por exemplo:

   ```python
   # Filtrar as linhas onde a idade é maior que 25
   filtro = df[df['Idade'] > 25]
   print(filtro)

   # Saída:
   #     Nome  Idade        Cidade
   # 1  Maria     30  Rio de Janeiro
   ```

A função `loc` permite realizar operações de seleção de forma mais expressiva, usando rótulos em vez de posições numéricas. Isso torna o código mais legível e menos sujeito a erros quando se trabalha com DataFrames complexos. É uma ferramenta essencial para análise e manipulação de dados em Pandas.

### **Função `drop`**

A função `drop()` é uma importante função da biblioteca Pandas em Python, utilizada para remover linhas ou colunas de um _DataFrame_. Essa função permite que você exclua dados indesejados ou realiza modificações em um _DataFrame_ sem a necessidade de criar um novo objeto.

**Sintaxe:**

```python
dataframe.drop(labels, axis=0, inplace=False)
```

**Principais parâmetros:**

- **labels:** Obrigatório. Pode ser um rótulo único ou uma lista de rótulos, representando as linhas ou colunas que você deseja remover.

- **axis:** Opcional. Especifica o eixo ao longo do qual a remoção deve ocorrer. Pode ser 0 para remover linhas (registros) ou 1 para remover colunas. Deve-se passar os índices das linhas que deseja remover, e para isso você pode utilizar o atributo `index` do _DataFrame_.

- **inplace:** Opcional. Se True, a modificação é realizada no próprio _DataFrame_, e a função não retorna nada (None). Se False (padrão), a função retorna um novo _DataFrame_ sem as linhas ou colunas especificadas.

**Exemplos:**

1. Remover linhas de um _DataFrame_:

   ```python
   import pandas as pd

   data = {'Nome': ['João', 'Maria', 'Pedro'],
           'Idade': [25, 30, 22],
           'Cidade': ['São Paulo', 'Rio de Janeiro', 'Belo Horizonte']}

   df = pd._DataFrame_(data)

   # Remover a linha de índice 1
   df_sem_linha = df.drop(1)
   print(df_sem_linha)

   # Saída:
   #    Nome  Idade        Cidade
   # 0  João     25     São Paulo
   # 2 Pedro     22  Belo Horizonte
   ```

2. Remover colunas de um _DataFrame_:

   ```python
   # Remover a coluna 'Cidade'
   df_sem_coluna = df.drop('Cidade', axis=1)
   print(df_sem_coluna)

   # Saída:
   #     Nome  Idade
   # 0   João     25
   # 1  Maria     30
   # 2  Pedro     22
   ```

3. Remover linhas e colunas ao mesmo tempo:

   ```python
   # Remover a linha de índice 1 e a coluna 'Cidade'
   df_sem_linha_coluna = df.drop(df[df["Idade"] >= 30].index).drop('Cidade', axis=1)
   print(df_sem_linha_coluna)
   # Saída:
   #    Nome  Idade
   # 0  João     25
   # 2 Pedro     22
   ```

A função `drop()` é uma ferramenta útil para manipulação e limpeza de dados em DataFrames, permitindo que você realize operações de exclusão de forma eficiente. É importante observar que a função por padrão retorna um novo _DataFrame_ com as modificações, preservando o _DataFrame_ original. Caso você queira modificar o _DataFrame_ original, você pode usar o parâmetro `inplace=True`.
