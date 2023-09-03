# Regressão linear simples - base preço casas 1

## Biblioteca Pandas

### Função `corr`

A função `corr()` do Pandas é usada para calcular a correlação entre colunas (variáveis) em um DataFrame. A correlação é uma medida estatística que quantifica a relação entre duas variáveis, indicando se elas tendem a se mover juntas (correlação positiva), se movem em direções opostas (correlação negativa) ou se não há relação aparente (correlação próxima a zero).

**Sintaxe**:

```python
DataFrame.corr(method='pearson', min_periods=1)
```

**Parâmetros**:

- `method` (opcional): O método de cálculo de correlação a ser usado. Os métodos comuns são:

  - `'pearson'` (padrão): Calcula a correlação de Pearson, que mede a correlação linear entre variáveis contínuas.
  - `'kendall'`: Calcula a correlação de Kendall, que é uma medida de correlação não paramétrica adequada para dados classificados ou ordinais.
  - `'spearman'`: Calcula a correlação de Spearman, outra medida não paramétrica que é adequada para dados classificados ou ordinais.

- `min_periods` (opcional): O número mínimo de observações não nulas necessárias para calcular uma correlação. O padrão é 1, o que significa que uma correlação será calculada mesmo se houver apenas uma observação não nula.

**Retorno**:

- Um DataFrame de correlação, onde os índices e as colunas são os nomes das variáveis do DataFrame original, e os valores são os coeficientes de correlação entre essas variáveis. A diagonal principal do DataFrame conterá 1s, pois uma variável sempre tem uma correlação perfeita com ela mesma.

**Exemplo**:

```python
import pandas as pd

# Criando um DataFrame de exemplo
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [2, 3, 4, 5, 6],
    'C': [5, 5, 5, 5, 5]
}

df = pd.DataFrame(data)

# Calculando a correlação de Pearson entre as colunas
correlation_matrix = df.corr()

print(correlation_matrix)
```

Neste exemplo, criamos um DataFrame `df` com três colunas (A, B e C) e calculamos a matriz de correlação usando o método padrão de correlação de Pearson. A matriz resultante, `correlation_matrix`, será:

```
     A    B    C
A  1.0  1.0  0.0
B  1.0  1.0  0.0
C  0.0  0.0  1.0
```

Observe que as variáveis A e B têm uma correlação perfeita de 1.0 entre si, pois são linearmente dependentes, enquanto a variável C não está correlacionada com A ou B, como indicado por uma correlação próxima a zero.

A função `corr()` é amplamente usada na análise de dados para explorar relações entre variáveis e entender como elas estão relacionadas umas com as outras. É útil para identificar dependências ou tendências em um conjunto de dados.

## Biblioteca SeaBorn

### Função `heatmap`

A função `heatmap` do Seaborn é uma ferramenta poderosa para visualizar e explorar matrizes de dados bidimensionais, como uma matriz de correlação. Ela cria uma representação gráfica da matriz de dados, onde as células são codificadas por cores, permitindo que você identifique padrões, tendências e relacionamentos entre os elementos da matriz.

**Sintaxe**:

```python
seaborn.heatmap(data, annot=None, fmt=".2f", cmap="coolwarm", cbar=True, linewidths=0.5, square=True)
```

**Parâmetros**:

- `data`: A matriz de dados bidimensional que você deseja visualizar.

- `annot` (opcional): Um valor booleano ou uma matriz do mesmo tamanho de `data`. Se for `True`, os valores reais da matriz serão exibidos nas células do heatmap. Se for uma matriz, ela deve ter as mesmas dimensões de `data` e será usada para anotar as células do heatmap.

- `fmt` (opcional): O formato dos valores de anotação nas células. É uma string de formatação que segue a sintaxe do método `.format()` do Python. Por exemplo, `".2f"` exibirá os valores com duas casas decimais.

- `cmap` (opcional): A paleta de cores a ser usada no heatmap. O Seaborn oferece várias paletas pré-definidas, como "coolwarm", "viridis", "magma", entre outras.

- `cbar` (opcional): Um valor booleano que indica se você deseja incluir uma barra de cores (colorbar) à direita do heatmap.

- `linewidths` (opcional): A largura das linhas que dividem as células do heatmap.

- `square` (opcional): Um valor booleano que indica se você deseja que as células do heatmap sejam quadradas (True) ou retangulares (False).

**Exemplo**:

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Criando uma matriz de dados de exemplo (matriz de correlação)
data = [
    [1.0, 0.8, 0.3, 0.1],
    [0.8, 1.0, 0.6, 0.2],
    [0.3, 0.6, 1.0, 0.7],
    [0.1, 0.2, 0.7, 1.0]
]

# Criando um heatmap
sns.heatmap(data, annot=True, fmt=".2f", cmap="coolwarm", cbar=True, linewidths=0.5, square=True)

# Exibindo o gráfico
plt.show()
```

Neste exemplo, criamos um heatmap para visualizar uma matriz de correlação fictícia. As configurações usadas incluem a anotação das células com os valores reais (usando `annot=True`), o formato dos valores com duas casas decimais (usando `fmt=".2f"`), a paleta de cores "coolwarm" (usando `cmap="coolwarm"`), a inclusão de uma colorbar (usando `cbar=True`), a largura das linhas de divisão de células (usando `linewidths=0.5`), e células quadradas (usando `square=True`).

O heatmap resultante fornece uma representação visual clara das relações na matriz de dados, destacando áreas com alta ou baixa correlação. É uma ferramenta valiosa para explorar e comunicar insights em análises de dados e estudos estatísticos.
