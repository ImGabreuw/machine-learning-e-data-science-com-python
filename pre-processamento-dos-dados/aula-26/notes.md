# Atributos categóricos - OneHotEncoder

A técnica One-Hot Encoder é um método de transformação utilizado para converter atributos categóricos em valores numéricos, permitindo que esses atributos sejam utilizados em algoritmos de aprendizado de máquina que requerem dados numéricos como entrada.

O processo de One-Hot Encoder envolve três etapas principais:

1. Identificação das categorias únicas: Primeiramente, é feita a identificação de todas as categorias únicas presentes no atributo categórico.

2. Criação de novas variáveis binárias: Para cada categoria única, é criada uma nova variável binária, também chamada de "dummy variable" ou "indicadora". Essa variável assume o valor 1 se a instância pertence à categoria correspondente e 0 caso contrário.

3. Substituição das categorias pelo código one-hot: As categorias originais são substituídas pelas novas variáveis binárias criadas.

Essa técnica é especialmente útil quando os atributos categóricos não têm uma ordem específica e quando não se deseja impor uma relação de ordem a eles. Além disso, ela permite que algoritmos de aprendizado de máquina processem esses dados de forma adequada, já que muitos desses algoritmos requerem que os atributos sejam numéricos.

Vejamos um exemplo para ilustrar o processo:

Suponha que temos um atributo categórico chamado "cor" com as categorias "vermelho", "azul" e "verde". Após aplicar o One-Hot Encoder, teremos três novas colunas binárias representando essas categorias:

| Cor      | Vermelho | Azul | Verde |
| -------- | -------- | ---- | ----- |
| Vermelho | 1        | 0    | 0     |
| Azul     | 0        | 1    | 0     |
| Verde    | 0        | 0    | 1     |

Neste exemplo, cada instância possui apenas uma das novas variáveis com valor 1, indicando a categoria à qual pertence.

A codificação One-Hot Encoder é amplamente utilizada em tarefas de pré-processamento de dados em ciência de dados e aprendizado de máquina, sendo uma das abordagens mais comuns para lidar com atributos categóricos em modelos preditivos. No entanto, é importante considerar o possível aumento na dimensionalidade dos dados, principalmente quando há muitas categorias únicas, o que pode levar a problemas de desempenho em algoritmos de machine learning.

Na literatura de pré processamento de dados, a maneira mais utilizada para o conversão de atributos categóricos é primeiro aplicar o LabelEncoder para converter o atributo categórico em uma valor inteiro simples e em seguida aplicar o OneHotEncoder.

> ## **Biblioteca Sklearn**

### Função `OneHotEncoder.fit_transform`

O método `ColumnTransformer.fit_transform` é uma função do módulo `sklearn.compose` que permite realizar transformações específicas em colunas selecionadas de um conjunto de dados. Quando aplicado em conjunto com o One Hot Encoder, ele possibilita a conversão de atributos categóricos em valores numéricos binários.

**Sintaxe:**

```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder

ct = ColumnTransformer(
    transformers=[('encoder', OneHotEncoder(), lista_colunas_categoricas)],
    remainder='passthrough'
)

X_transformed = ct.fit_transform(X)
```

**Parâmetros:**

- `transformers`: Recebe uma lista de tuplas, onde cada tupla contém um nome para a transformação ('encoder' neste caso) e o objeto do transformador (`OneHotEncoder`). A lista especifica quais colunas devem passar pela transformação.

- `remainder`: Determina como as colunas não especificadas na transformação serão tratadas. Neste caso, 'passthrough' significa que essas colunas não serão alteradas e serão mantidas no conjunto de dados resultante.

**Exemplo:**

```python
import pandas as pd
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder

# Cria um DataFrame de exemplo
data = {
    'cor': ['vermelho', 'verde', 'azul', 'vermelho', 'azul'],
    'tamanho': ['grande', 'médio', 'médio', 'pequeno', 'grande'],
    'preco': [100, 50, 75, 30, 90]
}
df = pd.DataFrame(data)

# Seleciona as colunas categóricas para transformação
lista_colunas_categoricas = ['cor', 'tamanho']

# Cria o ColumnTransformer e aplica o One Hot Encoder nas colunas categóricas
ct = ColumnTransformer(
    transformers=[('encoder', OneHotEncoder(), lista_colunas_categoricas)],
    remainder='passthrough'
)

X_transformed = ct.fit_transform(df)

# Exibe o resultado
print(X_transformed)
```

**Saída:**

```
[[1. 0. 0. 1. 0. 0. 0. 0. 0. 0. 100]
 [0. 1. 0. 0. 1. 0. 0. 0. 0. 0. 50]
 [0. 0. 1. 0. 1. 0. 1. 0. 0. 0. 75]
 [1. 0. 0. 0. 0. 1. 0. 0. 1. 0. 30]
 [0. 0. 1. 0. 0. 0. 0. 1. 0. 1. 90]]
```

**Explicação:**

No exemplo acima, temos um DataFrame com três colunas: 'cor', 'tamanho' e 'preco'. Utilizamos o `ColumnTransformer` em conjunto com o One Hot Encoder para transformar as colunas categóricas 'cor' e 'tamanho' em valores numéricos binários, enquanto mantemos a coluna 'preco' sem alterações.

O One Hot Encoder criou novas colunas binárias para cada categoria única nas colunas 'cor' e 'tamanho', resultando em uma matriz numérica com a representação das categorias em formato binário. Essa abordagem é útil para que modelos de aprendizado de máquina possam trabalhar com atributos categóricos de forma adequada.
