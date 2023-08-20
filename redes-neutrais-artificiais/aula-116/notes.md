# Redes neurais - base crédito

## Biblioteca Sklearrn

### Classe `MLPClassifier`

A classe `MLPClassifier` do módulo `sklearn.neural_network` é uma implementação do algoritmo de rede neural multilayer perceptron (MLP) para classificação de dados. MLP é uma arquitetura de rede neural artificial que consiste em várias camadas, incluindo uma camada de entrada, uma ou mais camadas ocultas e uma camada de saída. Essa classe é utilizada para criar e treinar redes neurais MLP para tarefas de classificação.

A seguit a explicação dos principais parâmetros da classe `MLPClassifier`:

- `hidden_layer_sizes`: Este é um parâmetro crucial que define a arquitetura da rede neural. Ele especifica o número de neurônios em cada camada oculta. Você pode fornecer uma tupla de inteiros, onde cada número representa o número de neurônios em uma camada oculta. Por exemplo, `(100, 50)` cria uma rede neural com duas camadas ocultas, a primeira com 100 neurônios e a segunda com 50 neurônios.

- `activation`: Este parâmetro define a função de ativação utilizada nos neurônios. Opções comuns são 'relu' (Rectified Linear Unit) para ativação ReLU, 'logistic' para função sigmoid e 'tanh' para tangente hiperbólica.

- `solver`: Este parâmetro define o algoritmo de otimização utilizado para ajustar os pesos da rede. As opções incluem 'adam' (uma versão otimizada do gradiente descendente estocástico), 'sgd' (gradiente descendente estocástico) e 'lbfgs' (um método quase-Newton).

- `alpha`: É o parâmetro de regularização que controla a penalização dos pesos para evitar overfitting. Quanto maior o valor de `alpha`, mais forte é a regularização.

- `learning_rate`: Esse parâmetro controla a taxa de aprendizado para a atualização dos pesos. As opções incluem 'constant' (taxa de aprendizado constante), 'adaptive' (taxa de aprendizado diminui ao longo do tempo) e 'invscaling' (taxa de aprendizado diminui por um fator constante ao longo do tempo).

- `max_iter`: Número máximo de iterações (épocas) durante o treinamento.

- `random_state`: Semente para a geração de números aleatórios, que influencia na inicialização dos pesos da rede.

- `verbose`: Controla a quantidade de informações exibidas durante o treinamento. Se for definido o valor `True`, será exibido a iteração (época) e o valor de perda.

- `tol`: Tolerância para critério de parada do treinamento. O treinamento para quando a diferença entre as atualizações consecutivas dos pesos for menor que o valor especificado no parâmetro `tol`.

Essa classe permite criar redes neurais MLP para tarefas de classificação, permitindo que você ajuste a arquitetura da rede, os hiperparâmetros de treinamento e outras configurações importantes. É uma ferramenta poderosa para resolver problemas de classificação usando redes neurais artificiais de forma eficaz.
