# Indução de regras - algoritmo PRISM

O algoritmo PRISM é um método de aprendizado de máquina utilizado para a geração de regras de classificação. Ele foi desenvolvido para lidar com conjuntos de dados contendo variáveis categóricas, onde a maioria dos algoritmos tradicionais de aprendizado de regras enfrenta dificuldades.

O funcionamento do algoritmo PRISM é baseado em uma abordagem de **indução de regras parcial**, ou seja, em vez de tentar criar regras que cubram todo o conjunto de dados, o PRISM foca em criar regras para partes específicas dos dados, levando em conta a ordem dos atributos. A indução de regras parcial permite lidar com a natureza categórica dos atributos e extrair regras mais precisas para classificação.

Os passos principais do algoritmo PRISM são os seguintes:

1. **Divisão do Conjunto de Dados:** O conjunto de dados é dividido em partes menores com base nos valores dos atributos categóricos para realizar o cálculo da abrangência. Isso é feito para criar grupos de dados semelhantes, o que facilita a geração de regras específicas para cada grupo.

   Considere a tabela abaixo para a geração da regra parcial da classe `risco = "alto"`:

   | História do crédito | Dívida | Garantias |      Renda anual      | Risco |
   | :-----------------: | :----: | :-------: | :-------------------: | ----- |
   |        Ruim         |  Alta  |  Nenhuma  |       < 15.000        | Alto  |
   |    Desconhecida     |  Alta  |  Nenhuma  | >= 15.000 a <= 35.000 | Alto  |
   |    Desconhecida     | Baixa  |  Nenhuma  |       > 35.000        | Alto  |
   |        Ruim         | Baixa  |  Nenhuma  |       < 15.000        | Alto  |
   |         Boa         |  Alta  |  Nenhuma  |       < 15.000        | Alto  |
   |        Ruim         |  Alta  |  Nenhuma  | >= 15.000 a <= 35.000 | Alto  |

2. **Geração de Regras Parciais:** Para cada grupo de dados criado na etapa anterior, o PRISM gera regras de classificação que se aplicam apenas a esse grupo específico. Essas regras são criadas considerando a ordem dos atributos categóricos, de modo a obter regras mais precisas e específicas.

   |          Atributo = Valor          |  Abrangência  |
   | :--------------------------------: | :-----------: |
   |     História de crédito = Boa      | $\frac{1}{1}$ |
   | História de crédito = Desconhecida | $\frac{2}{2}$ |
   |     História de crédito = Ruim     | $\frac{3}{3}$ |
   |           Dívida = Alta            | $\frac{4}{4}$ |
   |           Dívida = Baixa           | $\frac{2}{2}$ |
   |      **Garantias = Nenhuma**       | $\frac{6}{6}$ |
   |        Garantias = Adequada        | $\frac{0}{3}$ |
   |          Renda = < 15.000          | $\frac{3}{3}$ |
   |   Renda = >= 15.000 a <= 35.000    | $\frac{2}{2}$ |
   |          Renda = > 35.000          | $\frac{1}{1}$ |

   O atributo e valor que possuem a maior abrangência é `Garantias = Nenhuma` com $\frac{6}{6}$, ou seja, todos os registro com `Risco = Alto` possuem o atributo `Garantia = Nenhuma`. Então a regra parcial é `SE Garantias = Nenhuma ENTÃO Risco = Alto`

3. **Combinação de Regras:** Após a geração das regras parciais, o PRISM combina essas regras para formar um conjunto completo de regras para a classificação de todo o conjunto de dados. As regras são combinadas de forma a evitar sobreposição e redundância, garantindo que cada instância seja classificada de forma única.

   Agora vamos gerar outra regra parcial para combinar com `SE Garantias = Nenhuma ENTÃO Risco = Alto`:

   |          Atributo = Valor          |  Abrangência  |
   | :--------------------------------: | :-----------: |
   |     História de crédito = Boa      | $\frac{1}{1}$ |
   | História de crédito = Desconhecida | $\frac{2}{2}$ |
   |     História de crédito = Ruim     | $\frac{3}{3}$ |
   |         **Dívida = Alta**          | $\frac{4}{4}$ |
   |           Dívida = Baixa           | $\frac{2}{2}$ |
   |          Renda = < 15.000          | $\frac{3}{3}$ |
   |   Renda = >= 15.000 a <= 35.000    | $\frac{2}{2}$ |
   |          Renda = > 35.000          | $\frac{1}{1}$ |

   O atributo e valor com a maior abrangência é `Dívida = Alta` com $\frac{4}{4}$. Então juntando as 2 regras parciais temos: `SE Garantias = Nenhuma e Dívida = Alta ENTÃO Risco = Alto`

   Repetimos esse processo de combinação de regras parciais até atingirmos uma regra completa. No final temos a seguinte regra:

   `SE Garantias = Nenhuma e Dívida = Alta e História = Ruim e Renda < 15.000 ENTÃO Risco = Alto`

O algoritmo PRISM é especialmente eficiente para conjuntos de dados com muitas variáveis categóricas e para problemas de classificação com classes desbalanceadas. Ele tende a gerar regras mais precisas e interpretáveis, o que facilita a compreensão e a validação do modelo por especialistas.

No entanto, o PRISM pode enfrentar algumas limitações quando aplicado a conjuntos de dados com muitas variáveis contínuas ou atributos altamente correlacionados. Nessas situações, outros algoritmos de aprendizado de máquina, como árvores de decisão ou algoritmos baseados em redes neurais, podem ser mais adequados.

Em resumo, o algoritmo PRISM é uma abordagem eficiente e eficaz para a geração de regras de classificação em conjuntos de dados com variáveis categóricas, fornecendo modelos interpretáveis e de alta qualidade para problemas de aprendizado por regras.

### **Comparação com árvores de decisão**

- Maior compreensibilidade das regras geradas pelo PRISM.

- Requer menos espaço de armazenamento devido à simplicidade das regras.

- Pode ser mais lento em comparação com árvores de decisão.

- Em geral, as regras não apresentam resultados significativamente melhores do que as árvores de decisão, dependendo da natureza do conjunto de dados e do problema em questão.
