# Naïve bayes - base risco de crédito

> ## **Gaussian Naive Bayes (GaussianNB)**

GaussianNB é um algoritmo de classificação baseado no teorema de Bayes com a suposição de que os atributos (features) seguem uma distribuição normal (gaussiana). O "NB" em GaussianNB representa "Naive Bayes", indicando que o algoritmo faz uso da abordagem ingênua (naive) de supor independência condicional entre os atributos.

O algoritmo GaussianNB é uma variante do algoritmo Naive Bayes, que é amplamente utilizado em tarefas de classificação em aprendizado de máquina. Ele é particularmente eficaz em cenários com poucos dados disponíveis para treinamento e também é computacionalmente eficiente.

**Funcionamento do GaussianNB:**

O GaussianNB estima as probabilidades condicionais para cada classe, assumindo que os valores dos atributos para cada classe seguem uma distribuição normal. Ele calcula as médias e os desvios padrão dos atributos para cada classe durante a fase de treinamento.

Para fazer a classificação, o algoritmo utiliza o teorema de Bayes para calcular as probabilidades de pertencer a cada classe dada a observação dos atributos. É importante destacar que a suposição de normalidade dos atributos pode ser uma simplificação exagerada em alguns casos, mas, na prática, o GaussianNB pode apresentar bons resultados em muitos problemas.

**Vantagens do GaussianNB:**

- Simplicidade: É fácil de implementar e entender, especialmente quando se trabalha com um grande número de atributos.

- Eficiência computacional: O algoritmo é rápido e requer poucos recursos computacionais para treinamento e classificação.

- Boa performance com poucos dados: O GaussianNB pode funcionar bem mesmo com poucos exemplos de treinamento, tornando-o útil em cenários de dados limitados.

- Lida com atributos numéricos e categóricos: O algoritmo pode lidar tanto com atributos numéricos quanto categóricos, embora o GaussianNB seja mais adequado para atributos numéricos devido à suposição de normalidade.

**Desvantagens do GaussianNB:**

- Suposição de normalidade: A suposição de que os atributos seguem uma distribuição normal pode não ser verdadeira para todos os conjuntos de dados, o que pode levar a resultados imprecisos em alguns casos.

- Independência condicional: A suposição de independência condicional entre os atributos pode não ser válida para alguns problemas, resultando em previsões menos precisas.

- Dados desbalanceados: O GaussianNB pode ser afetado por desequilíbrios na distribuição de classes, resultando em viés na previsão das classes minoritárias.

Apesar de suas suposições simplificadas, o GaussianNB é um algoritmo de classificação útil e amplamente utilizado em várias aplicações, especialmente quando as suposições de normalidade e independência condicional são razoavelmente atendidas no conjunto de dados.

> ## **Distribuição normal**

A distribuição normal, também conhecida como distribuição gaussiana, é uma das distribuições de probabilidade mais importantes e amplamente encontradas na natureza. Ela é caracterizada por sua forma de sino e é completamente determinada por seus dois parâmetros: a média (µ) e o desvio padrão (σ).

A curva de distribuição normal é simétrica em torno da média, e a maioria dos valores se concentra próximo à média, com uma diminuição gradual em direção às caudas da distribuição. A média representa o centro da distribuição, enquanto o desvio padrão mede a dispersão dos valores em relação à média.

A distribuição normal é fundamental em estatística e análise de dados devido ao Teorema Central do Limite, que afirma que, para um grande número de amostras aleatórias de uma população, a média das amostras segue uma distribuição normal, independentemente da distribuição original da população. Essa propriedade torna a distribuição normal especialmente útil para modelar muitos fenômenos naturais e artificiais em uma variedade de campos, incluindo ciências, engenharias, finanças e aprendizado de máquina.

> ## **Biblioteca Sklean**

### **Função `fit`**

A função `GaussianNB.fit()` faz parte do módulo `sklearn.naive_bayes` do scikit-learn e é usada para ajustar um modelo de classificação Naive Bayes Gaussiano aos dados de treinamento. O algoritmo Naive Bayes Gaussiano é apropriado para dados contínuos e assume que as características seguem uma distribuição normal (distribuição gaussiana).

**Sintaxe:**

```python
model.fit(X_train, y_train)
```

**Parâmetros:**

- `X_train`: Array-like ou matriz esparsa de formato (n_samples, n_features) que representa as características de treinamento.

- `y_train`: Array-like de formato (n_samples,) que representa os rótulos de classe de treinamento.

**Exemplo:**

```python
from sklearn.naive_bayes import GaussianNB
import numpy as np

# Dados de treinamento
X_train = np.array([[1.0, 2.0], [2.0, 3.0], [3.0, 4.0], [4.0, 5.0]])
y_train = np.array([0, 1, 0, 1])

# Criando e ajustando o modelo Naive Bayes Gaussiano
model = GaussianNB()
model.fit(X_train, y_train)
```

**Saída:**

Nenhum valor de saída é retornado explicitamente. O método `fit()` ajusta o modelo aos dados de treinamento para que ele esteja pronto para fazer previsões.

**Conclusão**

Durante o processo de ajuste, o modelo estima as médias e os desvios padrão das distribuições normais para cada classe e cada atributo dos dados de treinamento. Essas estimativas são usadas posteriormente para calcular as probabilidades de classificação no momento da previsão. Após o ajuste, o modelo está pronto para ser usado para fazer previsões em novos dados não vistos.

### **Função `predict`**

A função `GaussianNB.predict()` faz parte do módulo `sklearn.naive_bayes` do scikit-learn e é usada para fazer previsões de classe em novos dados usando um modelo de classificação Naive Bayes Gaussiano previamente ajustado.

**Sintaxe:**

```python
y_pred = model.predict(X_new)
```

**Parâmetros:**

- `X_new`: Array-like ou matriz esparsa de formato (n_samples, n_features) que representa os novos dados de entrada para os quais queremos fazer as previsões.

**Retorno:**

- `y_pred`: Array de formato (n_samples,) contendo as previsões de classe para os dados de entrada fornecidos.

**Exemplo:**

```python
from sklearn.naive_bayes import GaussianNB
import numpy as np

# Dados de treinamento
X_train = np.array([[1.0, 2.0], [2.0, 3.0], [3.0, 4.0], [4.0, 5.0]])
y_train = np.array([0, 1, 0, 1])

# Dados de teste
X_test = np.array([[1.5, 3.5], [3.5, 6.0]])

# Criando e ajustando o modelo Naive Bayes Gaussiano
model = GaussianNB()
model.fit(X_train, y_train)

# Fazendo previsões nos dados de teste
y_pred = model.predict(X_test)
print(y_pred)  # Saída: [0 1]
```

No exemplo acima, criamos um modelo Naive Bayes Gaussiano e o ajustamos aos dados de treinamento `X_train` e `y_train`. Em seguida, usamos o modelo ajustado para fazer previsões nas novas amostras `X_test`. A função `predict()` retorna um array contendo as previsões de classe para as amostras de teste fornecidas.

**Conclusão**

O algoritmo Naive Bayes Gaussiano calcula as probabilidades de classificação para cada classe com base nas estimativas das médias e desvios padrão das distribuições normais ajustadas aos dados de treinamento. Em seguida, ele atribui a classe com a maior probabilidade como a previsão para cada amostra de teste.

Vale ressaltar que a implementação do algoritmo Naive Bayes Gaussiano no Python não disponibiliza a visualização da tabela de probabilidade, entretanto a linguagem R, por exemplo, têm suporte para isso.

### **Atributos da classe GaussianNB**

A classe `GaussianNB` do módulo `sklearn.naive_bayes` têm os seguintes atributos:

1. `classes_`: É um array que armazena as classes únicas do problema de classificação. As classes representam os diferentes rótulos ou categorias das amostras presentes nos dados de treinamento. Essas classes são determinadas durante o ajuste do modelo usando o método `fit()`. Cada valor único no array `classes_` representa uma classe específica do problema.

2. `class_count_`: É um array que armazena o número de amostras de cada classe presente nos dados de treinamento. O array possui o mesmo tamanho que o número de classes únicas e é determinado durante o ajuste do modelo usando o método `fit()`. Os valores do array `class_count_` indicam quantas amostras pertencem a cada classe.

3. `class_prior_`: É um array que armazena as probabilidades a priori de cada classe no problema de classificação. As probabilidades a priori representam a probabilidade de uma amostra ser classificada em uma determinada classe antes de observar as características específicas da amostra. Essas probabilidades são calculadas durante o ajuste do modelo usando o método `fit()` e são baseadas no número de amostras em cada classe. O array `class_prior_` possui o mesmo tamanho que o número de classes únicas e seus valores representam as probabilidades a priori de cada classe.

Esses atributos são úteis para entender a distribuição de classes nos dados de treinamento e podem ser acessados após o ajuste do modelo para obter informações relevantes sobre as classes e suas probabilidades. Por exemplo, podemos usar o array `classes_` para obter os nomes das classes, o array `class_count_` para obter o número de amostras em cada classe e o array `class_prior_` para obter as probabilidades a priori de cada classe. Isso pode ser útil para fazer análises e tomada de decisões com base nas previsões do modelo.
