# Redes multicamada - camada saída categórica

A camada de saída categórica em redes neurais é usada quando o objetivo da rede é realizar uma tarefa de classificação com mais de duas classes distintas. Ela é responsável por produzir as saídas finais da rede, onde cada neurônio na camada de saída representa uma classe possível de classificação.

Existem duas principais abordagens para configurar a camada de saída em um problema de classificação com várias classes:

1. **Ativação Softmax:** A ativação softmax é frequentemente usada na camada de saída quando há mais de duas classes. A função softmax normaliza as saídas dos neurônios na camada de saída de forma que a soma das saídas seja igual a 1. Cada neurônio de saída fornece a probabilidade de pertencer a uma classe específica. O neurônio com a maior probabilidade é então considerado como a classe prevista pela rede.

2. **Codificação One-Hot:** A codificação one-hot é uma representação em que cada classe é mapeada para um vetor binário onde apenas um dos elementos é 1 (quente) e os outros são 0 (frio). Cada neurônio na camada de saída representa uma classe possível, e o neurônio correspondente à classe correta terá uma saída de 1, enquanto os outros terão saídas de 0.

A escolha entre essas abordagens depende da natureza do problema e da arquitetura da rede. A ativação softmax é útil quando se deseja obter probabilidades claras para cada classe, enquanto a codificação one-hot é mais direta para algumas tarefas de classificação.

Em resumo, a camada de saída categórica é fundamental para problemas de classificação com várias classes e é projetada para gerar as saídas finais da rede, seja na forma de probabilidades ou codificação one-hot, permitindo assim a classificação adequada das entradas em diferentes classes.
