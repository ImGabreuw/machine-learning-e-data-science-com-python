# Melhor algoritmo com ANOVA e Tukey

## Teste de Tukey

O teste de Tukey, também conhecido como o teste de comparação múltipla de Tukey, é uma técnica estatística utilizada para avaliar diferenças entre todas as combinações possíveis de médias de grupos em uma análise de variância (ANOVA). Ele é particularmente útil quando você realizou uma ANOVA e encontrou uma diferença estatisticamente significativa entre as médias dos grupos, mas deseja identificar quais pares específicos de grupos têm diferenças significativas.

O teste de Tukey é uma forma de controle da taxa de erro familiar, o que significa que ele ajusta os valores críticos de significância para considerar o aumento das comparações feitas. Isso ajuda a evitar falsos positivos, ou seja, identificar diferenças onde não existem.

Aqui estão os passos principais do teste de Tukey:

1. **Realizar a ANOVA**: Primeiro, você deve realizar a análise de variância (ANOVA) para determinar se há diferenças significativas entre as médias dos grupos.

2. **Calcular a diferença mínima significativa (LSD)**: A LSD é uma estimativa da menor diferença entre duas médias que pode ser considerada estatisticamente significativa.

3. **Calcular a estatística de teste (q)**: Para cada par de grupos, calcula-se a estatística de teste q, que é a diferença entre as médias dividida pela LSD.

4. **Comparar com valor crítico de Tukey**: Usa-se a tabela de valores críticos de Tukey para determinar se a estatística de teste q é maior do que o valor crítico correspondente, ajustado com base no número de grupos e no tamanho da amostra.

5. **Interpretação**: Se a estatística de teste q for maior que o valor crítico, podemos concluir que existe uma diferença estatisticamente significativa entre as médias dos grupos comparados.

O teste de Tukey é amplamente utilizado em experimentos onde se deseja identificar quais grupos possuem médias significativamente diferentes após encontrar uma diferença global significativa na análise de variância. Isso é particularmente útil em avaliações de algoritmos, onde se deseja identificar quais algoritmos têm desempenho significativamente melhor ou pior do que os outros.

## Biblioteca scipy

### Função `f_oneway`

A função `f_oneway` do módulo `scipy.stats` é utilizada para realizar a análise de variância (ANOVA) de uma ou mais amostras independentes. A ANOVA é um teste estatístico que compara as médias de três ou mais grupos para determinar se há diferenças significativas entre eles. A função calcula a estatística F e o valor p associado para testar a hipótese nula de que as médias dos grupos são iguais.

**Parâmetros**:

- `sample1, sample2, ...` (arrays-like): São as amostras dos grupos que você deseja comparar. Cada amostra é um array ou sequência de valores numéricos.

**Retorno**:

- `F` (float): A estatística F calculada para o teste.
-
- `p-value` (float): O valor p associado à estatística F.

**Exemplo**:

```python
from scipy.stats import f_oneway

# Amostras dos grupos
group1 = [25, 30, 32, 28, 35]
group2 = [40, 38, 42, 45, 36]
group3 = [20, 22, 25, 28, 26]

# Realiza o teste ANOVA
F, p_value = f_oneway(group1, group2, group3)

# Verifica os resultados
if p_value < 0.05:
    print("Há diferença significativa entre as médias dos grupos.")
else:
    print("Não há diferença significativa entre as médias dos grupos.")
```

**Interpretação dos resultados**:

- Se o valor p (`p-value`) for menor ou igual ao nível de significância (geralmente definido em 0.05), então há evidência estatística para rejeitar a hipótese nula de que as médias dos grupos são iguais. Isso sugere que pelo menos um par de grupos possui médias estatisticamente diferentes.
- Se o valor p for maior que o nível de significância, não há evidência para rejeitar a hipótese nula, indicando que as médias dos grupos são estatisticamente iguais.

## Biblioteca `statsmodels`

### Classe `MultiComparison`

A classe `MultiComparison` do módulo `statsmodels.stats.multicomp` é uma ferramenta do Python utilizada para realizar comparações múltiplas entre grupos, especialmente após a realização de testes de ANOVA ou outras análises de variância. Ela oferece uma maneira conveniente de aplicar métodos estatísticos de comparação múltipla, como o teste de Tukey, para determinar quais grupos têm médias significativamente diferentes.

**Sintaxe:**

```python
from statsmodels.stats.multicomp import MultiComparison

multi_comp = MultiComparison(data, groups)
```

Parâmetros:

- `data`: Um array ou DataFrame contendo os dados de todos os grupos.
- `groups`: Uma array ou lista indicando a qual grupo cada observação pertence.

**Principais métodos:**

1. `tukeyhsd()`:

   Este método aplica o teste de Tukey Honest Significance Difference (HSD) para comparações múltiplas. Ele retorna um objeto `MultiComparisonResults` contendo os resultados do teste, como intervalos de confiança, valores p, diferenças médias e mais.

   ```python
   result = multi_comp.tukeyhsd()
   ```

2. `plot_simultaneous()`:

   Esse método gera um gráfico de barras com intervalos de confiança para as comparações múltiplas. Pode ser útil para visualizar as diferenças entre as médias dos grupos.

   ```python
   result.plot_simultaneous()
   ```

3. `summary()`:

   Este método imprime um resumo tabular dos resultados das comparações múltiplas, incluindo intervalos de confiança, diferenças médias e valores p corrigidos.

   ```python
   result.summary()
   ```

**Exemplo**:

```python
import numpy as np
import pandas as pd
from statsmodels.stats.multicomp import MultiComparison

# Dados fictícios
data = np.concatenate([np.random.normal(loc=10, scale=2, size=30),
                       np.random.normal(loc=15, scale=2, size=30),
                       np.random.normal(loc=18, scale=2, size=30)])
groups = np.repeat(['A', 'B', 'C'], 30)

# Instanciando a classe MultiComparison
multi_comp = MultiComparison(data, groups)

# Aplicando o teste de Tukey
result = multi_comp.tukeyhsd()

# Imprimindo os resultados
result.summary()
```

Saída do teste de Tukey:

Multiple Comparison of Means - Tukey HSD, FWER=0.05

| group1 | group2 | meandiff | p-adj | lower  | upper  | reject |
| ------ | ------ | -------- | ----- | ------ | ------ | ------ |
| 'A'    | 'B'    | 5.04     | 0.001 | 4.4165 | 5.6635 | True   |
| 'A'    | 'C'    | 8.02     | 0.001 | 7.3965 | 8.6435 | True   |
| 'B'    | 'C'    | 2.98     | 0.001 | 2.3565 | 3.6035 | True   |

O resultado apresenta as comparações entre grupos, indicando se a diferença entre as médias é estatisticamente significativa. O valor "reject" indica se a hipótese nula de que as médias são iguais pode ser rejeitada. Neste exemplo, todas as comparações têm o valor "True" em "reject", indicando que há diferenças estatisticamente significativas entre os grupos.

A classe `MultiComparison` é útil quando você deseja realizar comparações estatísticas entre múltiplos grupos sem o risco de aumentar o erro de tipo I devido a comparações múltiplas excessivas. Ela oferece uma maneira eficaz de analisar as diferenças entre grupos após a detecção de diferenças significativas por meio de testes como a ANOVA.
