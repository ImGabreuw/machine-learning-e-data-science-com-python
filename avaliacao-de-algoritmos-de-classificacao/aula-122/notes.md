# Análise da matriz de confusão

Na matriz de verdadeiro positivo (TP), falso positivo (FP), verdadeiro negativo (TN) e falso negativo (FN), os termos "Type I Error" e "Type II Error" referem-se a dois tipos diferentes de erros que podem ocorrer em um teste estatístico ou em um modelo de classificação:

1. **Type I Error (Erro do Tipo I)**: Também conhecido como erro de falso positivo, ocorre quando o teste ou o modelo erroneamente rejeita a hipótese nula (afirmação de não haver efeito ou relação), quando na verdade a hipótese nula é verdadeira. Em termos de classificação, isso significa que o modelo classifica incorretamente uma instância como pertencente a uma classe positiva quando, na verdade, pertence à classe negativa.

2. **Type II Error (Erro do Tipo II)**: Também conhecido como erro de falso negativo, ocorre quando o teste ou o modelo falha em rejeitar a hipótese nula quando a hipótese alternativa (afirmação de um efeito ou relação) é verdadeira. Em classificação, isso significa que o modelo classifica erroneamente uma instância como pertencente à classe negativa quando, na verdade, pertence à classe positiva.

A matriz de confusão resume esses erros, juntamente com os acertos, em uma tabela que ajuda a avaliar o desempenho de um modelo de classificação. A matriz inclui os seguintes valores:

- Verdadeiro Positivo (TP): Instâncias positivas corretamente classificadas.
- Falso Positivo (FP): Instâncias negativas incorretamente classificadas como positivas.
- Verdadeiro Negativo (TN): Instâncias negativas corretamente classificadas.
- Falso Negativo (FN): Instâncias positivas incorretamente classificadas como negativas.

Então, em resumo, Type I Error refere-se à situação em que o modelo erradamente identifica algo que não deveria, e Type II Error refere-se à situação em que o modelo deixa de identificar algo que deveria.
