# Base de dados de crédito

No contexto da biblioteca Python pandas, as funções `head()` e `tail()` são utilizadas para visualizar as primeiras e últimas linhas de um DataFrame, que é uma estrutura de dados tabular bidimensional usada para armazenar e manipular dados.

### **`head()`**

A função `head()` é usada para exibir as primeiras linhas de um DataFrame. Por padrão, ela mostra as primeiras 5 linhas do DataFrame, mas você pode especificar o número de linhas que deseja visualizar passando um argumento inteiro para a função. Por exemplo, `df.head(10)` exibirá as 10 primeiras linhas do DataFrame `df`.

Exemplo:

```python
import pandas as pd

# Criando um DataFrame de exemplo
data = {'Nome': ['Alice', 'Bob', 'Carol', 'David', 'Eva'],
        'Idade': [25, 30, 22, 28, 35],
        'Cidade': ['São Paulo', 'Rio de Janeiro', 'Belo Horizonte', 'Brasília', 'Curitiba']}

df = pd.DataFrame(data)

# Exibindo as primeiras 3 linhas do DataFrame
print(df.head(3))
```

Resultado:

```
    Nome  Idade       Cidade
0  Alice     25    São Paulo
1    Bob     30  Rio de Janeiro
2  Carol     22  Belo Horizonte
```

### **`tail()`**

A função `tail()` é usada para exibir as últimas linhas de um DataFrame. Assim como `head()`, por padrão, ela mostra as últimas 5 linhas do DataFrame, mas você pode especificar o número de linhas que deseja visualizar passando um argumento inteiro para a função. Por exemplo, `df.tail(10)` exibirá as 10 últimas linhas do DataFrame `df`.

Exemplo:

```python
import pandas as pd

# Criando um DataFrame de exemplo
data = {'Nome': ['Alice', 'Bob', 'Carol', 'David', 'Eva'],
        'Idade': [25, 30, 22, 28, 35],
        'Cidade': ['São Paulo', 'Rio de Janeiro', 'Belo Horizonte', 'Brasília', 'Curitiba']}

df = pd.DataFrame(data)

# Exibindo as últimas 2 linhas do DataFrame
print(df.tail(2))
```

Resultado:

```
   Nome  Idade    Cidade
3 David     28  Brasília
4   Eva     35  Curitiba
```

### **`describe()`**

A função `describe()` é uma das funções mais úteis e poderosas da biblioteca Python pandas para análise de dados. Ela é aplicada em um DataFrame e fornece um resumo estatístico das principais informações dos dados numéricos presentes no DataFrame.

Quando você chama a função `describe()` em um DataFrame, ela calcula várias estatísticas descritivas para cada coluna numérica do DataFrame, tais como:

- **count:** Número de valores válidos (não nulos) na coluna.
- **mean:** Média dos valores da coluna.
- **std:** Desvio padrão dos valores da coluna.
- **min:** Valor mínimo presente na coluna.
- **25%:** Primeiro quartil dos valores da coluna (25% dos dados estão abaixo deste valor).
- **50%:** Mediana dos valores da coluna (ou segundo quartil).
- **75%:** Terceiro quartil dos valores da coluna (75% dos dados estão abaixo deste valor).
- **max:** Valor máximo presente na coluna.

Essas estatísticas são úteis para entender a distribuição dos dados e identificar valores discrepantes (outliers) em um DataFrame.

Exemplo:

```python
import pandas as pd

# Criando um DataFrame de exemplo
data = {'Idade': [25, 30, 22, 28, 35, 21, 27, 29, 31, 26],
        'Altura': [1.70, 1.65, 1.80, 1.75, 1.68, 1.72, 1.69, 1.78, 1.73, 1.67],
        'Peso': [68, 75, 60, 70, 63, 68, 72, 69, 77, 66]}

df = pd.DataFrame(data)

# Aplicando a função describe()
descricao = df.describe()

print(descricao)
```

Resultado:

```
           Idade     Altura       Peso
count  10.000000  10.000000  10.000000
mean   27.600000   1.715000  68.000000
std     3.137484   0.043489   5.196152
min    21.000000   1.650000  60.000000
25%    25.250000   1.685000  66.250000
50%    27.500000   1.715000  68.500000
75%    29.750000   1.737500  71.750000
max    35.000000   1.800000  77.000000
```

No exemplo acima, a função `describe()` forneceu informações estatísticas como contagem, média, desvio padrão, valores mínimo e máximo, bem como os quartis para as colunas numéricas "Idade", "Altura" e "Peso" do DataFrame. Essas estatísticas ajudam a ter uma visão geral dos dados e podem ser muito úteis para análises exploratórias iniciais dos dados.

### **Filtro de registros**

O filtro de registros no pandas é uma operação que permite selecionar linhas específicas de um DataFrame com base em determinadas condições. No exemplo que você forneceu, a expressão `base_credit[base_credit["income"] >= 69995.685578]` é um filtro que seleciona as linhas do DataFrame `base_credit` onde o valor da coluna "income" é maior ou igual a 69995.685578.

Vamos entender passo a passo o que está acontecendo:

1. `base_credit["income"]`: Esta parte da expressão acessa a coluna "income" do DataFrame `base_credit`, retornando uma Series que contém todos os valores presentes nessa coluna.

2. `base_credit["income"] >= 69995.685578`: Nesta parte, a comparação é realizada elemento a elemento entre a Series "income" e o valor 69995.685578. O resultado é uma Series booleana com True nas posições em que o valor da coluna "income" é maior ou igual ao valor fornecido e False nas posições em que não é.

3. `base_credit[...]`: Finalmente, essa parte usa a Series booleana resultante da comparação como um filtro para o DataFrame `base_credit`. Ela seleciona apenas as linhas em que o valor correspondente na Series booleana é True, ou seja, as linhas onde a condição `base_credit["income"] >= 69995.685578` é satisfeita.

Portanto, a expressão `base_credit[base_credit["income"] >= 69995.685578]` retorna um novo DataFrame que contém apenas as linhas onde o valor da coluna "income" é maior ou igual a 69995.685578. Isso permite filtrar os registros do DataFrame com base na condição especificada.