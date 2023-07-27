# Atributos categóricos - LabelEncoder

A conversão de atributos categóricos em valores numéricos é um processo importante na preparação de dados para análise e modelagem em aprendizado de máquina. Em muitos algoritmos de aprendizado de máquina, os dados precisam estar em formato numérico para serem processados corretamente. No entanto, os dados do mundo real frequentemente contêm atributos categóricos, que são representados por rótulos ou categorias, como cores, nomes de países, tipos de veículos, etc.

Existem várias técnicas para realizar a conversão de atributos categóricos em valores numéricos:

1. **Mapeamento manual:** Consiste em atribuir manualmente valores numéricos a cada categoria. Por exemplo, podemos mapear "Masculino" para 0 e "Feminino" para 1 em uma coluna de gênero.

2. **Label Encoding:** É uma técnica automática fornecida por bibliotecas como o scikit-learn. Cada categoria é mapeada para um valor numérico único. No entanto, essa abordagem pode levar ao problema de ordenação implícita em algumas variáveis categóricas que não têm uma ordem natural.

3. **One-Hot Encoding:** Essa técnica cria uma matriz binária para cada categoria, onde cada coluna representa uma categoria e possui um valor binário 0 ou 1 para indicar a presença ou ausência da categoria em uma observação. É útil quando as variáveis categóricas não têm uma ordem natural e quando não queremos impor relações de ordem nas categorias.

4. **Ordinal Encoding:** É usado quando as categorias possuem uma ordem natural. As categorias são mapeadas para valores numéricos de forma que a ordem seja preservada. Por exemplo, "Baixo", "Médio" e "Alto" podem ser codificados como 1, 2 e 3, respectivamente.

A escolha da técnica de conversão depende do tipo de atributo categórico, do contexto do problema e do algoritmo de aprendizado de máquina a ser utilizado. A conversão adequada de atributos categóricos em valores numéricos é essencial para garantir que os dados sejam representados de forma adequada e útil para o processo de modelagem e análise.

> ## **Biblioteca Sklean**

### Função `LabelEncoder.fit_transform`

O método `fit_transform` do `LabelEncoder` é uma função do módulo `sklearn.preprocessing` da biblioteca scikit-learn. Ele é usado para realizar a codificação de atributos categóricos em valores numéricos de forma automática. Especificamente, o `LabelEncoder` converte as categorias presentes em uma coluna de dados em valores inteiros únicos, atribuindo a cada categoria um número inteiro sequencial.

**Sintaxe:**

```
from sklearn.preprocessing import LabelEncoder

encoder = LabelEncoder()
encoded_data = encoder.fit_transform(data)
```

**Parâmetros:**

- `data`: Uma lista ou array contendo os atributos categóricos que se deseja codificar.

**Retorno:**

- `encoded_data`: Uma nova lista ou array com os atributos categóricos codificados em valores numéricos.

**Exemplo:**
Suponha que temos uma coluna de dados categóricos representando o gênero de uma pessoa, onde as categorias são "Masculino" e "Feminino". Utilizaremos o `LabelEncoder` para codificar esses valores em números inteiros:

```python
from sklearn.preprocessing import LabelEncoder

gender = ["Masculino", "Feminino", "Feminino", "Masculino", "Masculino"]
encoder = LabelEncoder()
encoded_gender = encoder.fit_transform(gender)
print(encoded_gender)
```

**Saída:**

```
[1 0 0 1 1]
```

> Explicação: "Masculino" foi codificado como 1 e "Feminino" foi codificado como 0.

O `LabelEncoder` é útil quando temos atributos categóricos sem uma ordem específica e queremos atribuir valores numéricos distintos a cada categoria para que os algoritmos de aprendizado de máquina possam processá-los adequadamente. No entanto, é importante ter em mente que essa codificação impõe uma ordem implícita às categorias, o que pode ser problemático em alguns cenários, especialmente quando as categorias não têm uma relação de ordem natural. Nesses casos, é recomendado o uso da técnica de `One-Hot Encoding`.
