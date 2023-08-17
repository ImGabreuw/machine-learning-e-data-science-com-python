# Redes multicamada - backpropagation, taxa de aprendizagem e momento

O **backpropagation** é uma técnica crucial no treinamento de redes neurais de múltiplas camadas, como o Perceptron Multicamadas (MLP), que visa ajustar os pesos das conexões entre as unidades da rede para minimizar o erro de saída e melhorar a capacidade de generalização. É um algoritmo iterativo que utiliza o gradiente descendente para atualizar os pesos de forma a reduzir o erro de previsão.

**Processo do Backpropagation:**

O processo do backpropagation envolve duas etapas principais: **propagação para frente** e **propagação para trás**.

1. **Propagação para Frente:**

   - A entrada é fornecida à camada de entrada da rede.
   - Os valores de entrada são propagados através das camadas ocultas até a camada de saída, com cada unidade de cada camada calculando uma soma ponderada das entradas e aplicando uma função de ativação.
   - A saída da rede é obtida na camada de saída e é comparada com os valores de saída desejados para calcular o erro.

2. **Propagação para Trás (Backpropagation):**

   - O erro é propagado de volta através da rede, começando pela camada de saída.
   - Os deltas de erro são calculados para cada unidade na camada de saída usando a diferença entre a saída desejada e a saída real da rede.
   - Os deltas são então propagados de volta para as camadas ocultas, calculando os deltas para cada unidade nessas camadas usando o erro propagado das camadas seguintes e os pesos das conexões.
   - Os deltas nas camadas ocultas são usados para ajustar os pesos das conexões, com o objetivo de reduzir o erro de previsão. O ajuste dos pesos é realizado iterativamente usando o gradiente descendente.

**Gradiente Descendente:**

O gradiente descendente é usado para ajustar os pesos de forma a minimizar o erro global da rede. Ele envolve a computação do gradiente da função de custo em relação aos pesos da rede. O gradiente indica a direção e a magnitude do maior aumento da função de custo. No entanto, queremos minimizar a função de custo, portanto, seguimos na direção oposta ao gradiente.

**Atualização dos Pesos:**

Para cada peso $w_{ij}$ na rede, a atualização é feita da seguinte forma:

$$
w_{ij} = w_{ij - 1} \times \text{momentum}  + \eta \times \delta_j \times a_i
$$

- $w_{ij}$: O novo peso da conexão entre a unidade $i$ na camada anterior e a unidade $j$ na camada atual.

- $w_{ij - 1}$: O peso anterior da conexão. Este termo é usado no cálculo do termo de momento.

- $\text{momentum}$: O termo de momento é uma técnica para evitar as mínimas locais, entretanto por ser uma técnica simples pode não funcionar. Além disso, define o quão confiável é a última alteração.

  - Valor alto: aumenta a velocidade de convergência.

  - Valor baixo: diminui a velocidade de convergência, porém aumenta as chances de evitar os mínimos locais.

- $\eta$: A taxa de aprendizado controla o tamanho dos ajustes nos pesos de uma rede neural durante o treinamento.

  - Valor alto: convergência é rápida, porém pode pular o mínimo global.

  - Valor baixo: convergência é lenta mas tem mais chances de atingir o mínimo global.

- $\delta_j$: O delta de erro da unidade $j$ na camada atual.

- $a_i$: A ativação da unidade $i$ na camada anterior.

O processo de propagação para frente e para trás, juntamente com a atualização dos pesos usando o gradiente descendente, é repetido para cada exemplo de treinamento na base de dados várias vezes (épocas), até que o erro global seja reduzido a um nível satisfatório ou o número máximo de épocas seja alcançado.

Em resumo, o backpropagation é uma técnica fundamental no treinamento de redes neurais MLP. Ele permite que a rede ajuste seus pesos iterativamente para minimizar o erro de saída, melhorando assim sua capacidade de fazer previsões precisas e generalizadas. O algoritmo utiliza o gradiente descendente para encontrar a direção na qual os pesos devem ser ajustados para reduzir o erro e é repetido várias vezes até que a rede alcance um bom nível de desempenho.
