# Naïve bayes - classificação

**Passo 3: Classificação**

No passo de classificação do algoritmo de Naive Bayes, usamos o Teorema de Bayes para calcular a probabilidade de um exemplo pertencer a cada classe e, em seguida, atribuímos o exemplo à classe com a maior probabilidade.

Suponha que temos um novo registro com os seguintes atributos:

- **Idade: Média**

- **Renda: Baixa**

- **Histórico de Crédito: Bom**

Vamos calcular a probabilidade para cada classe, considerando as probabilidades condicionais que calculamos anteriormente:

**Para Baixo Risco:**

$$P(\text{Baixo}|\text{Média}, \text{Baixa}, \text{Bom}) = P(\text{Média}|\text{Baixo}) \times P(\text{Baixa}|\text{Baixo}) \times P(\text{Bom}|\text{Baixo}) \times P(\text{Baixo})$$

$$P(\text{Baixo}|\text{Média}, \text{Baixa}, \text{Bom}) = 0.143 \times 0.429 \times 0.714 \times \frac{7}{15} \approx 0.0903$$

**Para Alto Risco:**

$$P(\text{Alto}|\text{Média}, \text{Baixa}, \text{Bom}) = P(\text{Média}|\text{Alto}) \times P(\text{Baixa}|\text{Alto}) \times P(\text{Bom}|\text{Alto}) \times P(\text{Alto})$$

$$P(\text{Alto}|\text{Média}, \text{Baixa}, \text{Bom}) = 0.375 \times 0.75 \times 0.125 \times \frac{8}{15} \approx 0.0469$$

**Passo 4: Escolha da classe com maior probabilidade**

Agora, comparamos as probabilidades para cada classe e concluímos que o exemplo tem maior probabilidade de ser classificado como "Baixo Risco" tendo uma probabilidade de aproximadamente 0.0903 ou 66%.

$$
Total  = P(\text{Baixo}|\text{Média}, \text{Baixa}, \text{Bom}) + P(\text{Alto}|\text{Média}, \text{Baixa}, \text{Bom}) \\
\text{Maior Probabilidade em \%} = \frac{\text{Maior Probabilidade}}{\text{Total}} \times 100 \\
$$

$$
Total = 0.0903 + 0.0469 \\
\text{Maior Probabilidade em \%} = \frac{0.0903}{0.1372} \times 100 = 0.658163265 \times 100 = 65.82 \approx 66\%
$$

Portanto, de acordo com o algoritmo de Naive Bayes, a previsão é que o exemplo pertence à classe "Baixo Risco".