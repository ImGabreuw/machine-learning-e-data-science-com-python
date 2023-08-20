# Redes multicamada - camadas ocultas

## Determinar o número de neurônios na camada oculta

A determinação do número de neurônios nas camadas ocultas de uma rede neural é uma tarefa que envolve um certo grau de experimentação e ajuste, pois não existe uma fórmula única e rígida para determinar esse número com precisão. No entanto, existem algumas regras práticas e abordagens que podem ajudar nesse processo.

Uma regra geral é que o número de neurônios nas camadas ocultas deve estar entre o número de neurônios na camada de entrada (atributos) e o número de neurônios na camada de saída (classes ou valores a serem previstos). Esta é apenas uma regra prática e não uma fórmula matemática exata.

Uma abordagem comum é usar uma proporção entre os números de neurônios de entrada e saída. Um valor típico pode ser escolher um número de neurônios ocultos que seja cerca de duas vezes a média entre o número de neurônios de entrada e o número de neurônios de saída:

$$
\text{Neurônios ocultos} = \frac{\text{Neurônios de entrada} + \text{Neurônios de saída}}{2}
$$

> Caso o $\text{Neurônios ocultos}$ resulte em valor decimal, você pode aplicar o arredondamento para cima.

No entanto, isso também pode variar dependendo da complexidade do problema e da quantidade de dados disponíveis. Problemas mais complexos podem exigir mais neurônios nas camadas ocultas para capturar padrões intricados (complexos).

É importante lembrar que o processo de ajuste de hiperparâmetros, incluindo o número de neurônios nas camadas ocultas, envolve experimentação e validação cruzada. Testar diferentes configurações e avaliar o desempenho do modelo em um conjunto de validação ou teste é crucial para encontrar a melhor arquitetura de rede para o seu problema específico.

## Observações

- Problemas linearmente separáveis podem ser tratados sem a necessidade de camadas ocultas, ou seja, redes neurais Perceptron de uma única camada são adequadas para tais casos.

- Para determinar a melhor configuração, é recomendável empregar a técnica de _cross validation_ (validação cruzada).

- A automação do aprendizado de máquina, também conhecida como AutoML, oferece abordagens automatizadas para otimizar o processo de construção de modelos.

- Em conjuntos de dados pequenos, geralmente uma rede neural com duas camadas gera resultados satisfatórios.

- Pesquisas em _deep learning_ sugerem que o número de camadas está diretamente relacionado à complexidade do problema. Em outras palavras, problemas mais complexos tendem a exigir um maior número de camadas para serem resolvidos adequadamente.

- Uma sugestão inicial de configuração para uma rede neural envolve as seguintes etapas:

  1. Use a fórmula abaixo para determinar o número de neurônios na camada oculta:

     $$
     \text{Neurônios ocultos} = \frac{\text{Neurônios de entrada} + \text{Neurônios de saída}}{2}
     $$

  2. Empregue a **função de ativação ReLU** (Rectified Linear Unit) nas camadas ocultas.

  3. Utilize a **função de ativação Sigmoid** na camada de saída, caso tenha apenas um neurônio de saída. Para mais de um neurônio de saída, considere a **função de ativação softmax**.
