# Redes multicamada - delta camada oculta

O cálculo do delta na camada oculta é uma parte essencial do processo de treinamento de redes neurais, especialmente em algoritmos de aprendizado supervisionado, como o backpropagation. Assim como o cálculo do delta na camada de saída, o cálculo do delta na camada oculta envolve a medição do erro e a propagação desse erro de volta através da rede neural para atualizar os pesos das conexões.

**Cálculo do Delta na Camada Oculta:**

O cálculo do delta na camada oculta é mais complexo do que na camada de saída, porque as unidades na camada oculta não estão diretamente ligadas ao erro. O delta na camada oculta é calculado usando a propagação do erro da camada seguinte, ou seja, da camada que está mais próxima da camada de saída.

Vamos considerar uma rede neural com uma única camada oculta. Suponha que queremos calcular o delta para a unidade $j$ na camada oculta. O delta $\delta_j$ é calculado da seguinte forma:

$$
\delta_j = f'(z_j) \times \delta_{saída} \times w_{j}
$$

- $f'(z_j)$: Derivada da função de ativação aplicada à entrada ponderada da unidade $j$ na camada oculta ($z_j$).

- $\delta_{saída}$: Delta da camada de saída.

- $w_{j}$: Peso da conexão entre a unidade $j$ na camada oculta e camada de saída.

O cálculo do delta na camada oculta envolve duas etapas principais:

1. Propagação do erro da camada seguinte: O erro da camada de saída, representado pelos deltas $\delta_{saída}$, é propagado de volta para a camada oculta. Isso é feito multiplicando o delta da unidade na camada seguinte pelo peso da conexão entre as duas unidades e somando para todas as unidades na camada de saída.

2. Aplicação da derivada da função de ativação: O valor resultante é multiplicado pela derivada da função de ativação aplicada à entrada ponderada da unidade na camada oculta.

**Importância do Delta na Camada Oculta:**

O cálculo do delta na camada oculta é crucial porque ele informa como os pesos das conexões entre as unidades ocultas e as unidades de saída devem ser ajustados para reduzir o erro na camada de saída. Assim como na camada de saída, a magnitude do delta indica a sensibilidade do erro nas saídas em relação às mudanças nos pesos.

Ao calcular os deltas nas camadas ocultas, o processo de backpropagation continua retrocedendo pela rede neural, atualizando os pesos das conexões em cada camada para minimizar o erro global da rede. Essa propagação do erro e o ajuste dos pesos são realizados iterativamente por meio do gradiente descendente, permitindo que a rede neural aprenda gradualmente a mapear corretamente as entradas para as saídas desejadas.

Em resumo, o cálculo do delta na camada oculta é uma etapa fundamental no processo de treinamento de redes neurais. Ele mede o erro propagado da camada seguinte e é usado para determinar como os pesos das conexões da camada oculta devem ser ajustados para reduzir esse erro. Isso permite que a rede neural aprenda a melhorar suas previsões à medida que os pesos são atualizados iterativamente ao longo do processo de treinamento.
