# Redes multicamada - cálculo do erro

O algoritmo mais simples para o cálculo de erro do modelo é descrito pela seguinte fórmula:

$$
\text{Erro} = \text{Resposta correta} - \text{Resposta calculada}
$$

Com base no exemplo da tabela com os atributos previsores "x1" e "x2" e o atributo meta "Classe":

| x1  | x2  | Classe |
| :-: | :-: | :----: |
|  0  |  0  |   0    |
|  0  |  1  |   1    |
|  1  |  0  |   1    |
|  1  |  1  |   0    |

Calculamos os valores de saída para cada registro e obtivemos os seguintes resultados:

| x1  | x2  | Classe | Calculado |  Erro  |
| :-: | :-: | :----: | :-------: | :----: |
|  0  |  0  |   0    |   0.406   | -0.406 |
|  0  |  1  |   1    |   0.432   | 0.568  |
|  1  |  0  |   1    |   0.437   | 0.563  |
|  1  |  1  |   0    |   0.458   | -0.458 |

Como é possível notar, em alguns registros o valor de erro é negativo e então na maioria das implementações é utilizado a função _abs_ (valor absoluto) no erro ou a função _squared loss_ (eleva o erro ao quadrado).

Por fim, podemos calcular a média para descobrir o erro médio desse conjunto de pesos.

$$
\text{Erro médio} = \frac{-0.406 + 0.568 + 0.563 + -0.458}{4} = 0.49
$$

Por tanto o erro médio é de $0.49$.