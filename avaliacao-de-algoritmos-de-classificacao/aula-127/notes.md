# Ajuste dos parâmetros dos algoritmos 1

## Tuning de oarâmetros

**Tuning de parâmetros** é o processo de ajustar os hiperparâmetros de um modelo de aprendizado de máquina para encontrar a melhor combinação que otimize o desempenho do modelo. Os hiperparâmetros são configurações que não são aprendidas pelo modelo durante o treinamento, mas afetam como o modelo é treinado e como faz previsões. O tuning de parâmetros visa melhorar o desempenho do modelo em termos de métricas de avaliação, como precisão, recall, F1-score, etc.

## GridSearch

**GridSearch** é uma técnica comum de tuning de parâmetros que envolve a criação de uma "grade" de todas as combinações possíveis de valores de hiperparâmetros que você deseja testar. Para cada combinação de parâmetros na grade, o algoritmo é treinado e avaliado usando validação cruzada ou outro método de avaliação. O GridSearch, então, retorna as melhores combinações de parâmetros com base em uma métrica de avaliação específica.

O processo do GridSearch é geralmente o seguinte:

1. Especifique um conjunto de hiperparâmetros que você deseja ajustar e os possíveis valores para cada hiperparâmetro.
2. Crie todas as combinações possíveis desses hiperparâmetros, formando uma "grade".
3. Para cada combinação de hiperparâmetros, treine o modelo usando validação cruzada ou uma divisão de treinamento/teste.
4. Avalie o desempenho do modelo usando uma métrica de avaliação, como precisão, F1-score, etc.
5. Selecione a combinação de hiperparâmetros que resulta no melhor desempenho com base na métrica de avaliação escolhida.

O GridSearch automatiza o processo de teste de várias combinações de hiperparâmetros, economizando tempo e esforço manual. No entanto, pode ser computacionalmente intensivo, especialmente quando há muitos hiperparâmetros e valores possíveis para testar. Portanto, é importante equilibrar a exploração exaustiva com a eficiência computacional.

## Biblioteca Sklearn

### Classe GridSearchCV

A classe `GridSearchCV` faz parte do módulo `sklearn.model_selection` e é uma ferramenta poderosa para realizar a busca exaustiva por combinações ótimas de hiperparâmetros para um modelo de aprendizado de máquina. O "CV" em `GridSearchCV` se refere à validação cruzada, que é uma técnica utilizada para avaliar o desempenho do modelo de forma mais robusta.

**Funcionamento do GridSearchCV:**

1. Você especifica um modelo que deseja ajustar e os hiperparâmetros que deseja sintonizar.
2. Define uma grade de combinações possíveis de hiperparâmetros que deseja testar.
3. O `GridSearchCV` realiza uma busca exaustiva por todas as combinações da grade, treinando e avaliando o modelo para cada uma delas.
4. Utiliza validação cruzada para avaliar o desempenho de cada combinação.
5. Retorna os melhores hiperparâmetros com base na métrica de avaliação especificada.

**Principais parâmetros:**

- `estimator`: O modelo de aprendizado de máquina que você deseja ajustar.
- `param_grid`: Dicionário contendo os hiperparâmetros que você deseja ajustar e suas possíveis combinações.
- `scoring`: A métrica de avaliação que você deseja otimizar (por exemplo, 'accuracy', 'f1', 'roc_auc', etc.).
- `cv`: Número de dobras da validação cruzada a serem usadas durante a avaliação.

**Exemplo:**

```python
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier

# Definindo o modelo e os hiperparâmetros a serem ajustados
model = RandomForestClassifier()
param_grid = {
    'n_estimators': [50, 100, 200],
    'max_depth': [None, 10, 20],
    'min_samples_split': [2, 5, 10]
}

# Criando o objeto GridSearchCV
grid_search = GridSearchCV(model, param_grid, scoring='accuracy', cv=5)

# Realizando a busca exaustiva
grid_search.fit(X_train, y_train)

# Obtendo os melhores hiperparâmetros e o melhor modelo
best_params = grid_search.best_params_
best_model = grid_search.best_estimator_
```

O `GridSearchCV` é uma abordagem eficiente para encontrar a combinação ideal de hiperparâmetros para um modelo, melhorando seu desempenho e evitando o ajuste excessivo (overfitting).
