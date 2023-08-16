# Redes multicamada - pesos e erros

Em redes neurais Perceptron multicamadas o ajuste de pesos é feito da seguinte forma:

1. Inicialização dos pesos com valores aleatórios

2. Realização dos cálculos com os pesos e calcula o erro com base nos dados (na aprendizagem supervisionada)

3. Backpropagation: atualização dos pesos

4. O algoritmo encerro o processo de ajuste de pesos quando o erro é irrelevante (mas nunca chega a 0)

Na literatura, é referenciado como _cost function_ (função de custo), o indicador que mostra a quantidade de erro da rede neural.