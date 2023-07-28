# Bases de treinamento e teste

**train_test_split() - Explicação da Função**

A função `train_test_split()` faz parte do módulo `sklearn.model_selection` da biblioteca Scikit-learn (sklearn) em Python. Essa função é amplamente utilizada na avaliação de algoritmos de aprendizado de máquina e é usada para dividir um conjunto de dados em bases de treinamento e teste.

**Sintaxe:**

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, Y, test_size=0.25, random_state=None)
```

**Parâmetros:**

- `X`: Array ou DataFrame com as features (atributos) do conjunto de dados.

- `Y`: Array ou DataFrame com o target (variável de saída ou classe) correspondente às features.

- `test_size`: Define a proporção do conjunto de teste em relação ao conjunto total. Pode ser um valor entre 0 e 1 ou um inteiro (representando o número absoluto de amostras de teste).

- `random_state`: Parâmetro opcional para controlar a aleatoriedade da divisão. Se um valor inteiro for fornecido, garante que a divisão seja sempre a mesma, útil para reproduzir resultados.

  > O valor `0` indica que a divisão sempre será a mesma.

**Retorno:**

- `X_train`: Conjunto de dados de treinamento contendo as features.

- `X_test`: Conjunto de dados de teste contendo as features.

- `y_train`: Conjunto de dados de treinamento contendo o target correspondente às features.

- `y_test`: Conjunto de dados de teste contendo o target correspondente às features.

**Explicação:**

A função `train_test_split()` divide o conjunto de dados `X` e o target `y` em dois conjuntos distintos: base de treinamento (`X_train` e `y_train`) e base de teste (`X_test` e `y_test`). A proporção entre a base de treinamento e a base de teste é controlada pelo parâmetro `test_size`. É comum utilizar uma proporção como 0.3 ou 0.2 para o conjunto de teste, o que significa que 30% ou 20% dos dados serão utilizados para teste, e o restante será usado para treinamento.

A divisão do conjunto de dados é aleatória, mas pode ser reproduzível fornecendo um valor para o parâmetro `random_state`, o que é útil para obter resultados consistentes em diferentes execuções.

Essa função é especialmente útil para avaliar o desempenho do modelo em dados não vistos durante o treinamento. A base de teste é utilizada para medir o quão bem o modelo generaliza em dados desconhecidos, enquanto a base de treinamento é usada para ajustar os parâmetros do modelo.

**Conclusão:**

A função `train_test_split()` é uma ferramenta importante para a avaliação de modelos de aprendizado de máquina. Ao dividir o conjunto de dados em bases de treinamento e teste, podemos estimar o desempenho do modelo em situações do mundo real e garantir que ele generalize bem para dados não vistos durante o treinamento. Essa função é amplamente utilizada na prática para garantir a eficiência e precisão dos modelos de aprendizado de máquina.
