# PCA - base census

## Biblioteca Sklearn

### Classe PCA

A classe `PCA` do módulo `sklearn.decomposition` do Scikit-Learn implementa a técnica de Análise de Componentes Principais, ou PCA (Principal Component Analysis). O PCA é uma técnica de redução de dimensionalidade amplamente utilizada que tem como objetivo identificar e capturar as principais variações em um conjunto de dados, reduzindo a quantidade de características (dimensões) enquanto tenta manter a maior quantidade possível de informações.

**Sintaxe:**

```python
from sklearn.decomposition import PCA

pca = PCA(n_components=8)
```

**Principais parâmetros**:

- `n_components`: Este parâmetro define o número de componentes principais a serem mantidos após a redução de dimensionalidade. Pode ser especificado como um número inteiro, um valor decimal entre 0 e 1 para indicar a porcentagem de variância explicada desejada, ou "mle" (Maximum Likelihood Estimation) para estimar automaticamente o número de componentes principais com base na análise de verossimilhança. A escolha do número adequado de componentes principais é importante e depende da natureza dos dados e do problema.

- `whiten`: Quando definido como `True`, este parâmetro normaliza as componentes principais para terem variância unitária. Isso pode ser útil em algumas situações, especialmente quando as escalas das características são diferentes.

- `svd_solver`: Este parâmetro determina qual algoritmo será usado para a decomposição SVD (Singular Value Decomposition) para encontrar os componentes principais. As opções incluem "auto", "full", "arpack" e "randomized". A escolha do solucionador pode afetar o desempenho e a eficiência do PCA.

**Principais atributos**:

- `explained_variance_ratio_`: Fornece uma matriz de valores que indicam a proporção da variância total mantida em cada componente principal. Cada valor na matriz corresponde a um componente principal e representa a fração da variância total explicada por esse componente. Esses valores são classificados em ordem decrescente de importância, com o primeiro valor sendo o mais significativo.

**Principais métodos**:

- `fit(X)`: Este método é usado para ajustar o modelo PCA aos dados de entrada `X`. Os dados devem ser fornecidos como uma matriz, onde cada linha representa uma amostra e cada coluna representa uma característica.

- `fit_transform(X)`: Este método ajusta o modelo PCA aos dados e, em seguida, transforma os dados originais em um novo conjunto de dados com a redução de dimensionalidade aplicada.

- `transform(X)`: Este método aplica a transformação PCA a um conjunto de dados sem ajustar novamente o modelo. É útil quando você já ajustou um modelo PCA a um conjunto de treinamento e deseja aplicar a mesma transformação a um conjunto de teste.

- `inverse_transform(X)`: Este método reverte a transformação PCA para que os dados transformados voltem ao espaço original de alta dimensão.

**Exemplo**:

```python
from sklearn.decomposition import PCA
import numpy as np

# Criar uma matriz de dados de exemplo (m amostras, n características)
X = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# Criar um objeto PCA com 2 componentes principais
pca = PCA(n_components=2)

# Ajustar o modelo PCA aos dados e transformar os dados
X_transformed = pca.fit_transform(X)

# As novas características estão em X_transformed
print(X_transformed)
```

Saída:

```
[[-5.19615242e+00  2.56395025e-16]
 [ 0.00000000e+00  0.00000000e+00]
 [ 5.19615242e+00  2.56395025e-16]]
```

Neste exemplo, a classe `PCA` é usada para reduzir a dimensionalidade de um conjunto de dados de exemplo de 3 características para 2 componentes principais. O método `fit_transform` ajusta o modelo PCA aos dados e, em seguida, transforma os dados originais em um novo conjunto de dados com a redução de dimensionalidade aplicada. Isso é útil para visualização, compressão de dados ou pré-processamento antes de aplicar algoritmos de aprendizado de máquina.