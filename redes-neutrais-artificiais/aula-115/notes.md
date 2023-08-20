# Redes multicamada - descida do gradiente estocástico

A descida do gradiente é um método amplamente utilizado para otimizar funções em algoritmos de aprendizado de máquina, incluindo redes neurais. Ela visa ajustar os parâmetros do modelo de forma a minimizar uma função de custo, que quantifica a diferença entre as previsões do modelo e os valores reais dos dados de treinamento.

Existem três variantes principais da descida do gradiente: o batch gradient descent, o stochastic gradient descent (SGD) e o mini-batch gradient descent. Vamos explicar cada um deles:

1. **Batch Gradient Descent:**
   No batch gradient descent, todos os dados de treinamento são usados para calcular o gradiente e atualizar os parâmetros do modelo de uma só vez. Isso significa que a cada iteração, todas as amostras do conjunto de treinamento são processadas antes de ajustar os pesos. Embora possa ser computacionalmente intensivo, o batch gradient descent geralmente converge para uma solução precisa, pois a média das atualizações de peso é considerada.

2. **Stochastic Gradient Descent (SGD):**
   O SGD difere do batch gradient descent ao realizar a atualização dos pesos a cada iteração, utilizando apenas um exemplo de treinamento por vez. Isso torna o SGD mais rápido a cada iteração, mas também torna a convergência mais ruidosa, já que as atualizações são menos estáveis devido à variabilidade dos exemplos individuais.

3. **Mini-Batch Gradient Descent:**
   O mini-batch gradient descent é uma abordagem intermediária entre o batch e o SGD. Nesse caso, o conjunto de treinamento é dividido em pequenos conjuntos chamados de mini-batches. As atualizações dos pesos são calculadas com base na média dos gradientes dos exemplos dentro de cada mini-batch. Essa abordagem combina a eficiência do SGD com a estabilidade do batch gradient descent.

Em resumo, a descida do gradiente estocástico (SGD) é uma técnica importante para otimização de modelos de aprendizado de máquina, incluindo redes neurais. O batch gradient descent utiliza todo o conjunto de treinamento a cada iteração, o SGD atualiza com base em um único exemplo e o mini-batch gradient descent opera com pequenos subconjuntos dos dados. A escolha entre essas abordagens depende da natureza do problema, do tamanho do conjunto de dados e das considerações de eficiência computacional.
