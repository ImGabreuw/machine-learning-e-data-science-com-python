# Redes multicamada - descida do gradiente

O gradiente descendente é uma técnica fundamental no treinamento de redes neurais, e sua aplicação está diretamente relacionada à otimização dos pesos para redução de erros e busca do mínimo global na função de perda.

**Gradiente Descendente:**

O gradiente descendente é um algoritmo de otimização usado para ajustar os pesos em uma rede neural (ou em qualquer modelo de aprendizado de máquina) a fim de minimizar a função de perda. A ideia central é iterativamente atualizar os pesos na direção oposta ao gradiente da função de perda, de forma a encontrar um mínimo global na superfície de erro.

**Inicialização Aleatória de Pesos:**

Ao iniciar o treinamento de uma rede neural, os pesos das conexões entre os neurônios são definidos inicialmente de forma aleatória. Essa inicialização é crucial, pois determina o ponto de partida no espaço de busca de pesos. A inicialização aleatória ajuda a evitar que a rede fique presa em mínimos locais indesejados e permite que a otimização explore diferentes regiões da função de perda.

**Busca do Mínimo Global:**

O objetivo do treinamento de uma rede neural é encontrar um conjunto de pesos que leve a um mínimo global ou próximo dele na função de perda. O mínimo global é o ponto na superfície de erro onde o valor da função de perda é o mais baixo possível em relação a todos os outros pontos. No entanto, em redes neurais profundas, a função de perda geralmente é complexa e cheia de muitos mínimos locais, o que pode dificultar a busca pelo mínimo global.

O cálculo da derivada parcial é o responsável por direcionar o gradiente a fim de encontrar a região com menor erro, ou seja, quando atingirmos o menor valor possível da função de custo com base no melhor conjunto de pesos Durante cada iteração é realizado esse cálculo para a descida do gradiente até a região da mínima global.

Para realizar o cálculo da derivada parcial basta seguir os seguintes passos:

1. Calcular o valor da função de ativação:

   $$
   y = \frac{1}{1 + e^{-x}} = \frac{1}{1 + e^{-(-1,43)}} = 0,193
   $$

2. Aplicar o resultado obtido na etapa anterior na fórmula da derivada:

   $$
   d = y \cdot (1 - y) = 0,193 \cdot (1 - 0,193) = 0,156
   $$

**Processo de Treinamento:**

O processo de treinamento consiste em repetir as seguintes etapas:

1. Propagar os dados de treinamento através da rede neural para calcular as previsões.

2. Calcular o valor da função de perda com base nas previsões e nos valores reais.

3. Calcular os gradientes da função de perda em relação aos pesos (Backpropagation).

4. Atualizar os pesos na direção oposta ao gradiente multiplicado por uma taxa de aprendizado.

5. Repetir essas etapas até que a função de perda seja minimizada ou até que um número máximo de iterações seja alcançado.

**Convergência:**

Com a atualização iterativa dos pesos usando o gradiente descendente, a esperança é que o processo eventualmente alcance uma região de mínimo global ou próximo a ele, resultando em pesos que levam a uma rede neural bem ajustada para a tarefa em questão.

Vale ressaltar que o gradiente descendente não garante encontrar o mínimo global em todos os casos, especialmente em funções de perda complexas. Existem variações do gradiente descendente, como:

- "Força bruta": realiza todas as combinações possíveis de pesos sendo a forma que retorna o melhor resultado, embora não é viável computacionalmente hoje em dia

- _Simulated annealing_

- Algoritmos genéticos (algoritmos de otimização)

Cada um desses algoritmos possuem suas próprias características de convergência e eficiência.

Em resumo, o uso do gradiente descendente durante o treinamento de redes neurais é uma abordagem essencial para ajustar os pesos de forma a minimizar o erro e encontrar um conjunto de pesos que leve a um mínimo global ou próximo a ele na função de perda. Tal objetivo é fundado em conceitos matemáticos, essencialmente a multiplicação, de vetores e matrizes.
