# Escalonamento dos atributos

Escalonamento de atributos, também conhecido como normalização, é um procedimento utilizado no pré-processamento de dados para ajustar as escalas dos atributos de um conjunto de dados. O objetivo é transformar os valores dos atributos para um intervalo específico ou remover a dependência do modelo com a escala dos atributos. Essa etapa é particularmente importante quando os atributos têm escalas diferentes e podem causar problemas em algoritmos de aprendizado de máquina baseado em distância como KNN e redes neurais artificiais, pois o algoritmo pode interpretar que valores maiores possuem uma maior importância.

Existem duas técnicas comuns de escalonamento de atributos:

1. **Standardization (Padronização)**: Nesta técnica, os valores dos atributos são transformados para terem média zero e desvio padrão igual a 1. Geralmente, ela é utilizado quando uma base de dados possui muitos _outlier_ (valores fora do padrão) A fórmula para a padronização é dada por:

   $$
   X_{stand} = \frac{(X - X_{mean})}{X_{std}}
   $$

   Onde X_stand é o valor padronizado do atributo, X é o valor original do atributo, X_mean é a média do atributo e X_std é o desvio padrão do atributo.

2. **Min-Max Scaling (Normalização)**: Nesta técnica, os valores dos atributos são transformados para um intervalo específico, geralmente entre 0 e 1. A fórmula para a normalização é dada por:

   $$
   X_{norm} = \frac{(X - X_{min})}{(X_{max} - X_{min})}
   $$

   Onde X_norm é o valor normalizado do atributo, X é o valor original do atributo, X_min é o valor mínimo do atributo e X_max é o valor máximo do atributo.

O escalonamento de atributos é importante porque muitos algoritmos de aprendizado de máquina são sensíveis às escalas dos atributos. Quando os atributos têm escalas muito diferentes, alguns algoritmos podem dar mais importância a atributos com valores maiores e ignorar atributos com valores menores, o que pode levar a resultados incorretos ou subótimos.

Em resumo, o escalonamento de atributos é uma etapa essencial no pré-processamento de dados para garantir que todos os atributos tenham a mesma escala e contribuam igualmente para a modelagem do algoritmo de aprendizado de máquina. Isso melhora a eficácia e a precisão dos modelos resultantes.

> ## **Biblioteca Sklearn**

A biblioteca _Scikit-learn_, frequentemente abreviada como _sklearn_, é uma das bibliotecas mais populares do Python para aprendizado de máquina (machine learning). Ela fornece uma ampla gama de algoritmos e ferramentas para tarefas de classificação, regressão, clusterização, redução de dimensionalidade, pré-processamento de dados e muito mais.

_Scikit-learn_ é de código aberto, gratuito e foi construído sobre as bibliotecas NumPy, SciPy e Matplotlib, tornando-a uma escolha poderosa e flexível para aqueles que desejam criar e aplicar modelos de aprendizado de máquina.

Algumas das principais características da biblioteca _Scikit-learn_ incluem:

1. **Ampla variedade de algoritmos:** A biblioteca oferece uma extensa coleção de algoritmos de aprendizado de máquina, incluindo regressão linear, regressão logística, máquinas de suporte vetorial (SVM), árvores de decisão, florestas aleatórias, k-vizinhos mais próximos (KNN), entre outros.

2. **Facilidade de uso:** _Scikit-learn_ é projetada para ser fácil de usar e seguir uma API consistente. Isso torna a construção e ajuste de modelos de aprendizado de máquina bastante acessível, mesmo para usuários iniciantes.

3. **Documentação abrangente:** A biblioteca possui uma documentação detalhada, incluindo exemplos e tutoriais, que facilitam a compreensão dos algoritmos e seu uso correto.

4. **Integração com outras bibliotecas:** _Scikit-learn_ é compatível com outras bibliotecas populares do ecossistema Python, como Pandas para manipulação de dados, NumPy para operações numéricas e Matplotlib para visualizações.

5. **Avaliação de modelos:** _Scikit-learn_ fornece ferramentas para avaliação de modelos, como métricas de desempenho, validação cruzada, separação de conjuntos de treinamento/teste, e seleção de hiperparâmetros.

6. **Pré-processamento de dados:** A biblioteca oferece funcionalidades para pré-processar dados, como escalonamento, codificação de variáveis categóricas e tratamento de valores ausentes.

7. **Extensibilidade:** Além dos algoritmos internos, o _Scikit-learn_ permite que os usuários implementem seus próprios estimadores personalizados e os integrem perfeitamente com a biblioteca.

Por todas essas razões, o _Scikit-learn_ é amplamente utilizado tanto por iniciantes quanto por especialistas em aprendizado de máquina para desenvolver soluções inteligentes em diversos domínios, como ciência de dados, análise de dados, bioinformática, visão computacional e processamento de linguagem natural.

### **Função "StandardScaler.fit_transform"**

O método `StandardScaler.fit_transform` pertence ao módulo `sklearn.preprocessing` da biblioteca Scikit-learn. Esse método é usado para realizar o pré-processamento de dados conhecido como padronização (standardization). A padronização é uma técnica comum de escalonamento de atributos, onde os valores dos atributos são transformados para terem média zero e desvio padrão igual a 1.

**Sintaxe:**

```python
StandardScaler.fit_transform(X)
```

**Parâmetros:**
- `X`: Uma matriz ou DataFrame de tamanho [n_samples, n_features], que representa o conjunto de dados a ser padronizado.

**Retorno:**
- Retorna os dados padronizados em forma de matriz [n_samples, n_features], onde n_samples é o número de amostras (instâncias) e n_features é o número de atributos (características).

**Exemplo:**

```python
from sklearn.preprocessing import StandardScaler

# Dados de treinamento
dados_treinamento = [[1, 2], [2, 3], [3, 4], [4, 5], [5, 6]]

# Criação do StandardScaler
scaler = StandardScaler()

# Ajuste e transformação dos dados de treinamento
dados_padronizados = scaler.fit_transform(dados_treinamento)

print(dados_padronizados)
```

**Saída:**

```
[[-1.41421356 -1.41421356]
 [-0.70710678 -0.70710678]
 [ 0.          0.        ]
 [ 0.70710678  0.70710678]
 [ 1.41421356  1.41421356]]
```

Agora com os valores escalonados, o algoritmo não dará prioridade para valores de alto valor.

O método `StandardScaler.fit_transform` é uma combinação das etapas de ajuste (`fit`) e transformação (`transform`) do `StandardScaler`, que realiza a padronização dos dados em uma única chamada. Essa técnica é útil para garantir que todos os atributos tenham a mesma escala, o que melhora a eficácia e a precisão dos modelos de aprendizado de máquina. O `StandardScaler` é uma das muitas ferramentas disponíveis no Scikit-learn para pré-processar e preparar os dados antes de alimentá-los em algoritmos de aprendizado de máquina.