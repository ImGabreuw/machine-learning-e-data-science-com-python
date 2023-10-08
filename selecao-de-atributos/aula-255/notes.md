# Seleção com Extra Trees

O algoritmo "Extra Trees," abreviação de "Extremely Randomized Trees," é uma técnica de aprendizado de máquina que pertence à família de algoritmos de árvores de decisão. Ele é uma extensão do algoritmo Random Forest e é usado principalmente para seleção de atributos e classificação ou regressão.

**Funcionamento:**

- O algoritmo Extra Trees é semelhante ao Random Forest no sentido de que ele cria várias árvores de decisão para realizar a tarefa de classificação ou regressão.

- No entanto, a principal diferença entre o Random Forest e o Extra Trees está na forma como as árvores são construídas. Enquanto o Random Forest seleciona aleatoriamente um subconjunto de recursos para cada árvore, o Extra Trees vai um passo além.

- No Extra Trees, as árvores são construídas de forma "extremamente aleatória". Isso significa que, em vez de calcular a melhor divisão para cada nó da árvore com base em algum critério como o Gini ou a entropia, o Extra Trees seleciona divisões aleatórias para os nós.

- Como resultado, as árvores do Extra Trees são ainda mais independentes e mais variadas do que as árvores do Random Forest. Isso pode tornar o Extra Trees robusto contra o overfitting, já que as árvores são menos propensas a se ajustar excessivamente aos dados de treinamento.

**Seleção de atributos:**

- O Extra Trees pode ser usado para selecionar atributos relevantes em um conjunto de dados.

- Durante o treinamento, o algoritmo atribui importâncias a cada atributo com base em quantas vezes um atributo é usado para fazer divisões em todas as árvores da floresta e quão eficazes essas divisões são na classificação.

- A importância de cada atributo é então normalizada de forma que a soma total de importâncias seja igual a 1. Isso fornece uma pontuação de importância relativa para cada atributo.

- Os atributos com pontuações de importância mais altas são considerados mais relevantes e podem ser selecionados para serem usados em modelos subsequentes. Isso é útil para reduzir a dimensionalidade de conjuntos de dados com muitos atributos, mantendo apenas os mais informativos.

- A seleção de atributos com base no Extra Trees é uma técnica poderosa quando você deseja eliminar atributos irrelevantes ou reduzir o custo computacional de treinamento de modelos.

**Vantagens:**

- Efetivo para seleção de atributos, especialmente em conjuntos de dados com muitos atributos.
- Boa capacidade de lidar com dados desbalanceados e variáveis categóricas.
- Reduz o risco de overfitting, pois as árvores são altamente aleatórias.
- É relativamente rápido de treinar.

**Desvantagens:**

- Pode não ser tão preciso quanto outros métodos de seleção de atributos, como a eliminação recursiva de atributos.
- As pontuações de importância podem ser menos interpretáveis do que outras medidas de importância de atributos.

## Biblioteca Sklearn

### Classe ExtraTreesClassifier

A classe `ExtraTreesClassifier` faz parte do módulo `sklearn.ensemble` da biblioteca scikit-learn e é usada para construir modelos de classificação com base no algoritmo "Extremely Randomized Trees" (Extra Trees). Como mencionado anteriormente, o Extra Trees é uma extensão do algoritmo Random Forest e cria árvores de decisão altamente aleatórias para resolver problemas de classificação. Aqui está uma explicação detalhada sobre a classe `ExtraTreesClassifier`:

**Sintaxe:** 

```python
from sklearn.ensemble import ExtraTreesClassifier

selection = ExtraTreesClassifier()
```

**Parâmetros principais:**

- `n_estimators`: Este parâmetro define o número de árvores no conjunto. Quanto mais árvores, mais robusto e preciso o modelo, mas também mais demorado será o treinamento. Um valor típico é 100.

- `criterion`: Define a função para medir a qualidade de uma divisão em cada nó da árvore. As opções comuns são "gini" para o critério de Gini e "entropy" para o critério de entropia.

- `max_depth`: Controla a profundidade máxima das árvores. Limitar a profundidade pode ser útil para evitar overfitting.

- `min_samples_split`: Define o número mínimo de amostras necessárias para dividir um nó interno. Isso pode ajudar a controlar a complexidade das árvores.

- `min_samples_leaf`: Define o número mínimo de amostras em uma folha. Isso pode ser usado para evitar folhas com muito poucas amostras.

**Principais métodos:**

- `fit(X, y)`: Este método é usado para treinar o modelo `ExtraTreesClassifier` com os dados de treinamento `X` e os rótulos de classe correspondentes `y`.

- `predict(X)`: Após o treinamento, você pode usar este método para fazer previsões de classe para um conjunto de dados de entrada `X`.

- `predict_proba(X)`: Este método retorna as probabilidades estimadas para cada classe em vez de apenas as classes previstas. É útil quando você precisa de estimativas de probabilidade.

- `feature_importances_`: Este atributo contém as pontuações de importância atribuídas a cada recurso após o treinamento. Essas pontuações indicam a contribuição de cada recurso para a classificação.

**Exemplo:**

Aqui está um exemplo de uso do `ExtraTreesClassifier`:

```python
from sklearn.ensemble import ExtraTreesClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Carregando o conjunto de dados Iris como exemplo
data = load_iris()
X, y = data.data, data.target

# Dividindo o conjunto de dados em treinamento e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Criando e treinando o modelo ExtraTreesClassifier
model = ExtraTreesClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Fazendo previsões
y_pred = model.predict(X_test)

# Avaliando a precisão do modelo
accuracy = accuracy_score(y_test, y_pred)
print(f'Acurácia do modelo: {accuracy:.2f}')
```

Este exemplo cria um modelo `ExtraTreesClassifier`, treina-o no conjunto de dados Iris e faz previsões de classe. A pontuação de importância dos recursos também pode ser acessada através do atributo `feature_importances_`.
