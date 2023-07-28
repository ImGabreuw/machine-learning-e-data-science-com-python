# Salvar as bases de dados

> ## **Biblioteca pickle**

A função `dump` faz parte da biblioteca `pickle` em Python e é usada para salvar objetos Python em um arquivo. Ela é frequentemente utilizada para salvar bases de dados de treinamento e teste após a divisão do conjunto de dados, para que possam ser reutilizadas em futuras execuções ou compartilhadas com outras pessoas.

**Sintaxe:**

```python
import pickle

# Salvar objeto em um arquivo
with open('arquivo.pkl', 'wb') as arquivo:
    pickle.dump(objeto, arquivo)
```

**Parâmetros:**

- `objeto`: O objeto Python que será salvo em um arquivo.

- `arquivo`: O nome do arquivo onde o objeto será salvo.

**Exemplo:**

```python
import pickle

# Dados de treinamento e teste
X_train = [...]
y_train = [...]
X_test = [...]
y_test = [...]

# Salvar os dados em arquivos separados
with open('X_train.pkl', 'wb') as file:
    pickle.dump([X_train, y_train, X_test, y_test], file)
```

**Explicação:**

A função `dump` da biblioteca `pickle` permite que os objetos Python, como conjuntos de dados de treinamento e teste, sejam serializados e salvos em arquivos. Isso é especialmente útil quando precisamos reutilizar os mesmos dados em outras partes do código ou em outras execuções do programa. Além disso, também é possível compartilhar esses arquivos com outros usuários, permitindo que eles utilizem os mesmos conjuntos de dados sem precisar recriá-los.

**Conclusão:**

A função `dump` da biblioteca `pickle` é uma maneira eficiente de salvar objetos Python, como bases de dados de treinamento e teste, em arquivos. Isso facilita a reutilização dos dados em diferentes partes do código e permite que outras pessoas também utilizem os mesmos conjuntos de dados, tornando o processo de compartilhamento de informações mais simples e prático.
