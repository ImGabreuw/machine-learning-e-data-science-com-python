# Árvores de decisão - mais conceitos

### **Parametrização de árvores de decisão**

A parametrização, também conhecida como "split" (divisão), é um dos principais conceitos na construção de árvores de decisão. O objetivo das árvores de decisão é dividir o conjunto de dados em subconjuntos cada vez mais homogêneos com relação à variável de resposta (classe ou rótulo). Para isso, o algoritmo de árvore de decisão realiza uma série de divisões recursivas com base em atributos (características) dos dados.

O processo de parametrização funciona da seguinte forma:

1. O algoritmo de árvore de decisão avalia todos os atributos do conjunto de dados e seleciona aquele que melhor separa as classes com base em alguma métrica de impureza, como a entropia ou o índice Gini. Esse atributo é escolhido como o atributo de divisão na raiz da árvore.

2. Em seguida, o conjunto de dados é dividido em subconjuntos com base nos valores do atributo selecionado na raiz. Cada subconjunto corresponde a um ramo da árvore, e o processo de parametrização é aplicado a cada um desses subconjuntos recursivamente.

3. A cada nível da árvore, o algoritmo seleciona o melhor atributo de divisão para cada subconjunto com base nas observações específicas contidas nele. Esse processo continua até que um critério de parada seja atingido, como um número máximo de níveis da árvore ou um número mínimo de observações por folha.

4. Cada folha da árvore representa uma decisão final de classificação. Uma vez que a árvore está construída, novos dados podem ser classificados seguindo o caminho da raiz até a folha correspondente, com base nos valores de seus atributos.

A escolha adequada dos parâmetros de parametrização é essencial para obter uma árvore de decisão que generalize bem para novos dados e evite problemas de ajuste exagerados (_overfitting_) aos dados de treinamento. Parâmetros como a profundidade máxima da árvore, o número mínimo de amostras por folha e o critério de divisão podem ser ajustados para controlar o equilíbrio entre a complexidade da árvore e a capacidade de generalização. O ajuste desses parâmetros é uma parte importante do processo de treinamento de um modelo de árvore de decisão.

### Poda em árvores de decisão

**Poda em Árvores de Decisão:**

A poda, também conhecida como "pruning" em inglês, é uma técnica utilizada para evitar o sobreajuste (overfitting) em árvores de decisão. O sobreajuste ocorre quando a árvore é muito complexa e se ajusta em excesso aos dados de treinamento, capturando ruídos e detalhes irrelevantes, o que pode prejudicar sua capacidade de generalização para novos dados.

O processo de poda envolve a remoção de ramos ou subárvores da árvore que não contribuem significativamente para a melhoria da precisão das previsões em dados de teste. Isso é feito através de uma técnica chamada "validação cruzada" ou "cross-validation", em que uma parte do conjunto de treinamento é reservada como conjunto de validação para avaliar o desempenho da árvore em dados não vistos.

O procedimento básico de poda é o seguinte:

1. Treina-se inicialmente a árvore de decisão usando todo o conjunto de treinamento.

2. Em seguida, para cada nó da árvore, calcula-se a acurácia da subárvore resultante caso aquele nó e seus descendentes sejam removidos. Essa acurácia é avaliada usando o conjunto de validação.

3. Com base nos resultados da validação cruzada, decide-se se o nó deve ser podado (removido) ou não. A poda é realizada quando a remoção do nó não prejudica significativamente a precisão da árvore em dados de validação.

4. O processo de poda é repetido para outros nós da árvore até que não haja mais nós a serem podados ou a remoção de nós não melhore mais a acurácia da árvore.

A poda é uma estratégia eficaz para evitar o sobreajuste em árvores de decisão e melhorar sua capacidade de generalização. Ela ajuda a criar árvores mais simples e interpretáveis, que ainda conseguem fazer previsões precisas em novos dados. Ao equilibrar a complexidade da árvore e sua precisão, a poda aumenta a confiabilidade do modelo em aplicações do mundo real.

**Bias (Viés) e Variância:**

Em termos gerais, o bias (viés) e a variância são dois componentes do erro de previsão em modelos de aprendizado de máquina.

- **Bias (Viés):** Representa o erro sistemático do modelo, ou seja, a diferença média entre as previsões do modelo e os valores reais do conjunto de dados. Um modelo com alto viés tende a simplificar demais o problema e não consegue capturar a complexidade dos dados. Isso pode levar a um modelo subajustado (underfitting), que não se ajusta bem aos dados de treinamento.

- **Variância:** Representa a sensibilidade do modelo a variações nos dados de treinamento. Um modelo com alta variância é muito sensível aos dados de treinamento e pode se ajustar muito bem a eles, mas não consegue generalizar para novos dados. Isso pode levar a um modelo sobreajustado (overfitting), que se ajusta muito bem aos dados de treinamento, mas tem um desempenho ruim em dados não vistos.

O objetivo é encontrar um equilíbrio entre bias e variância para obter um modelo que generalize bem para novos dados. A poda é uma técnica que ajuda a reduzir a variância, permitindo que a árvore se ajuste melhor aos dados de validação e evite o sobreajuste. Ao controlar a complexidade da árvore, é possível obter um modelo com menor variância e, ao mesmo tempo, evitar um viés muito alto, resultando em um modelo mais equilibrado e melhor desempenho geral.

### Vantagens e Desvantagens

**Vantagens:**

1. **Fácil interpretação:** As árvores de decisão são fáceis de entender e interpretar, pois se assemelham a diagramas de fluxo que refletem a lógica de decisão. Isso torna a árvore uma ferramenta valiosa para analisar e explicar o processo de tomada de decisão do modelo.

2. **Não precisa de normalização ou padronização:** As árvores de decisão não são sensíveis à escala dos atributos, o que significa que não é necessário normalizar ou padronizar os dados antes de usá-los como entrada para o algoritmo. Isso simplifica o processo de preparação de dados.

3. **Rápido para classificar novos registros:** Uma vez que a árvore é construída, a classificação de novos registros é rápida, pois envolve apenas a navegação pela estrutura da árvore para chegar a uma decisão.

**Desvantagens:**

1. **Geração de árvores muito complexas:** Árvores de decisão podem crescer muito e se tornar excessivamente complexas, especialmente quando há muitos atributos ou classes no conjunto de dados. Árvores muito complexas tendem a se sobreajustar (problema do _overfitting_) aos dados de treinamento, resultando em baixa capacidade de generalização para novos dados.

2. **Pequenas mudanças nos dados podem mudar a árvore:** Árvores de decisão são sensíveis a pequenas mudanças nos dados de treinamento, o que pode levar a diferentes árvores sendo geradas em diferentes execuções do algoritmo. Essa variabilidade pode tornar o modelo menos confiável e mais difícil de interpretar.

3. **Problema NP-completo para construir a árvore:** O processo de construção de uma árvore de decisão ótima é um problema NP-completo, o que significa que encontrar a melhor árvore possível requer um tempo computacional exponencial à medida que o tamanho do conjunto de dados aumenta. Portanto, algoritmos de construção de árvores geralmente usam abordagens heurísticas que podem não garantir a melhor árvore possível, mas produzem uma solução razoável em tempo viável.

### Outras informações sobre árvore de decisão

- Eram muito populares em meados dos anos 90

- Melhorias como _random forest_ (floresta randômica) melhoram o desempenho.

- Também conhecido pelo termo CART (Classification and Regression Tree)

- Usado pelo Kinect da Microsoft