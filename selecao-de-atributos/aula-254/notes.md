# Seleção com low variance

A seleção de atributos com baixa variância é uma etapa importante no pré-processamento de dados quando você está lidando com conjuntos de dados para modelagem de machine learning. Essa técnica envolve a identificação e remoção de atributos que têm uma variância muito baixa ou próxima de zero em todo o conjunto de dados. A ideia por trás dessa abordagem é que atributos com baixa variância têm pouca ou nenhuma capacidade discriminativa, ou seja, eles não fornecem informações úteis para o modelo de machine learning.

**Variância de um atributo**:

A variância é uma medida estatística que indica o quão dispersos os valores de um atributo estão em relação à média. A fórmula para calcular a variância é:

$$
\text{Variância} = \frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2
$$

Onde:

- $n$ é o número de observações.
- $x_i$ são os valores do atributo.
- $\bar{x}$ é a média dos valores do atributo.

**Identificação de atributos com baixa variância**:

Para identificar atributos com baixa variância, você pode calcular a variância de cada atributo em seu conjunto de dados. Se a variância de um atributo for muito próxima de zero ou abaixo de um limite específico, ele pode ser considerado como tendo baixa variância o qual implica que são atributos similares.

**Vantagens**:

A remoção de atributos com baixa variância é útil por várias razões:

1. **Redução da Dimensionalidade**: A remoção de atributos com baixa variância reduz a dimensionalidade do conjunto de dados, tornando-o mais gerenciável e economizando recursos computacionais durante o treinamento do modelo.

2. **Evitar Ruído**: Atributos com baixa variância são frequentemente dominados por ruído e não contêm informações significativas. Manter esses atributos pode introduzir ruído no modelo.

3. **Melhorar a Generalização**: Modelos de machine learning podem se beneficiar da remoção de atributos irrelevantes ou redundantes, o que pode melhorar a generalização do modelo.

**Etapas para a seleção de atributos com baixa variância**:

1. **Calcule a variância**: Calcule a variância de cada atributo no conjunto de dados.

2. **Defina um limiar**: Escolha um valor de limite (threshold) que determine quais atributos têm baixa variância. O valor do limite depende do problema e dos dados, mas geralmente está próximo de zero.

3. **Identifique os atributos**: Identifique os atributos cuja variância está abaixo do limite definido.

4. **Remoção dos atributos**: Remova os atributos identificados na etapa anterior do conjunto de dados.

Em resumo, a seleção de atributos com baixa variância é uma técnica útil para melhorar a qualidade e a eficiência dos modelos de machine learning, eliminando atributos que contribuem pouco ou nada para a tarefa de previsão. É importante ajustar o valor do limite de acordo com a natureza dos dados e o problema em questão.

## Biblioteca Sklearn

### Classe VarianceThreshold

A classe `VarianceThreshold` do módulo `sklearn.feature_selection` é uma ferramenta que facilita a seleção de atributos com base na variância. Essa técnica é útil para identificar e remover atributos com baixa variância, ou seja, atributos cujos valores são praticamente constantes em todo o conjunto de dados, o que pode ser um sinal de que eles não são informativos para tarefas de modelagem de machine learning.

**Sintaxe:**

```python
from sklearn.feature_selection import VarianceThreshold

selector = VarianceThreshold(threshold=0.0)
```

**Principais parâmetros:**

- `threshold`: Este é o parâmetro mais importante e determina o limite de variância abaixo do qual os atributos são considerados para remoção. A variância é calculada para cada atributo, e se a variância desse atributo for menor ou igual a `threshold`, ele será removido. O valor padrão é 0, o que significa que qualquer atributo com variação zero (ou seja, valores constantes) será removido.

**Principais métodos :**

- `fit(X, y=None)`: Este método ajusta o seletor aos dados de entrada `X`. Se você fornecer um vetor de rótulos `y`, ele será ignorado, pois a seleção de atributos com base na variância não depende dos rótulos. O método calcula a variância de cada atributo em `X` e determina quais atributos atendem ao critério de variância estabelecido pelo parâmetro `threshold`.

- `transform(X)`: Este método retorna uma nova matriz de dados `X` após a remoção dos atributos com baixa variância. Os atributos que não atendem ao critério são descartados, e a matriz resultante contém apenas os atributos selecionados.

- `fit_transform(X, y=None)`: Este método combina as etapas de ajuste (`fit`) e transformação (`transform`). Ele ajusta o seletor aos dados de entrada `X` e retorna a matriz resultante após a remoção dos atributos com baixa variância.

**Principais atributos:**

- `variances_`: Este atributo fornece as variâncias calculadas para cada atributo no conjunto de dados após o ajuste (`fit`). Você pode usá-lo para verificar as variâncias individuais dos atributos.


**Exemplo:**

```python
from sklearn.preprocessing import MinMaxScaler
from sklearn.feature_selection import VarianceThreshold
import numpy as np

# Criar um conjunto de dados de exemplo (matriz NumPy)
X_temperatures = np.array([
    [25.1, 24.9, 25.0, 24.8],  # Cidade A
    [28.5, 28.4, 28.3, 28.6],  # Cidade B
    [22.0, 22.2, 22.1, 22.3],  # Cidade C
    [30.2, 30.1, 30.0, 30.3]   # Cidade D
])

# Escalonar os dados
scaler = MinMaxScaler()
X_temperatures_scaler = scaler.fit_transform(X_temperatures)

# Criar um objeto VarianceThreshold com um limite específico (por exemplo, 0.1)
selector = VarianceThreshold(threshold=0.15)

# Ajustar o seletor aos dados e obter a matriz resultante
X_low_variance = selector.fit_transform(X_temperatures_scaler)

# Imprimir os atributos selecionados
print(X_low_variance)
```

Saída:

```
[[0.34177215 0.3125    ]
 [0.78481013 0.7875    ]
 [0.         0.        ]
 [1.         1.        ]]
```

Neste exemplo, o seletor `VarianceThreshold` é usado para remover atributos com baixa variância (menos de 0.1) do conjunto de dados de entrada `X`. A matriz resultante `X_low_variance` conterá apenas os atributos selecionados.

A seleção de atributos com base na variância é útil quando você deseja remover atributos que não contribuem significativamente para a tarefa de modelagem, reduzindo assim a dimensionalidade do conjunto de dados e melhorando a eficiência do modelo.