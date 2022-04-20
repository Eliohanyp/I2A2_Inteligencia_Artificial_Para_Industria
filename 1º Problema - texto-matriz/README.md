
## Authors

- [Eliohan Yamauti Poiati](https://www.linkedin.com/in/eliohanyp/)

# Texto-para-Matriz

[PT-BR]

Este projeto visa solucionar o Problema 1 do Curso de Inteligencia Artifical para Industria ministrada pelo I²A² - Institut d'Intelligence Artificielle Appliquée 

O projeto utilizou as bibliotecas python: tensorflow, pandas, seaborn, matplotlib, wordcloud e openpyxl.
```bash
!pip install tensorflow pandas seaborn matplotlib wordcloud openpyxl

from tensorflow.keras.preprocessing.text import Tokenizer
import openpyxl
from wordcloud import WordCloud
import pandas as pd
import seaborn as sn
import matplotlib.pyplot as plt
from matplotlib import *
from matplotlib.colors import ListedColormap
```


A linha de pensamento:

Ler o arquivo texto:
```bash
arquivo_texto1 = 'Base Text - Matrix Representation I - v2.txt'
with open (arquivo_texto1, encoding='utf-8') as texto1:
    conteudo_texto = texto1.readlines()
```
Limpar o texto para a passagem de texto para matriz:
```bash
texto_limpo = "\n',".join(conteudo_texto).replace("\n',","")...
texto_matriz = texto_limpo.lower()
texto_matriz = texto_limpo.split('.')
```

Criar um Tokenizer:
```bash
tokenizer = Tokenizer()
```

Depois criar um dicionario com os indices e tokens e transforma-los em matriz: 
```bash
tokens = tokenizer.fit_on_texts(texto_matriz)
token_texto = tokenizer.word_index

matriz = tokenizer.texts_to_sequences(texto_matriz)
```

Transformei todos os valores nulos em '0.0' e temos nossa matriz!

Para uma visualização completa, tranformei em um arquivo '.xlsx'
```bash
df = pd.DataFrame(matriz).fillna(0)
df.to_excel("Matrix Representation I.xlsx")
```
Assim temos a visualização completa da nossa matriz, onde cada linha representa uma frase, as colunas representam as palavras que são utilizadas e cada celula representa uma palavra em nosso arquivo "Matrix Representation I.xlsx"


Depois fiz algumas coisas adicionais, fiz um stopword em latin e fiz uma Nuvem de Palavras de cada texto
```bash
#TEXTO 1 - Base Text - Matrix Representation I - v2.txt

#CRIA UMA LISTA DE STOPWORDS EM LATIN E RETIRA AS PALAVRAS E SALVA ISSO NO NOME "texto_sem_stopword2"
stopword_latin = ['a','ab','ac', 'ad', 'at', 'atque', 'aut', 'autem', 'cum', 'de', 'dum', 'e',
                       'erant', 'erat', 'est', 'et', 'etiam', 'ex', 'haec', 'hic', 'hoc', 'in', 'ita', 'me', 'nec', 'neque', 
                       'non', 'per', 'qua', 'quae', 'quam', 'qui', 'quibus', 'quidem', 'quo', 'quod', 're', 'rebus', 'rem', 'res',
                       'sed', 'si', 'sic', 'sunt', 'tamen', 'tandem', 'te', 'ut', 'vel']

texto_sem_stopword = [k for k in token_texto if not k in stopword_latin] 

texto_sem_stopword2 = " ".join(texto_sem_stopword)

#CRIA UMA NUVEM DE PALAVRAS COM AS PALAVRAS UTILIZADAS NO TEXTO
mapa_cor = ListedColormap(['orange', 'green', 'red', 'blue'])

nuvem = WordCloud(background_color = 'white', max_words = 1000, colormap=mapa_cor)

nuvem = nuvem.generate(texto_sem_stopword2)
plt.figure(figsize=(15,15))
plt.imshow(nuvem)
plt.axis('off')
plt.show()
```
Tambem é possivel reverter a matriz de volta a texto:
```bash
texto_1 = matriz
tokenizer.sequences_to_texts(texto_1)
```

[EN-US]

# Text-to-Matrix

This project aims to solve Problem 1 of the Artificial Intelligence Course for Industry taught by the I²A² - Institut d'Intelligence Artificielle Appliquée

The project used the python libraries: tensorflow, pandas, seaborn, matplotlib, wordcloud and openpyxl.
```bash
!pip install tensorflow pandas seaborn matplotlib wordcloud openpyxl

from tensorflow.keras.preprocessing.text import Tokenizer
import openpyxl
from wordcloud import WordCloud
import pandas as pd
import seaborn as sn
import matplotlib.pyplot as plt
from matplotlib import *
from matplotlib.colors import ListedColormap
```

The line of thought:

Read the text file:
```bash
arquivo_texto1 = 'Base Text - Matrix Representation I - v2.txt'
with open (arquivo_texto1, encoding='utf-8') as texto1:
    conteudo_texto = texto1.readlines()
```

Clear text for text-to-array:
```bash
texto_limpo = "\n',".join(conteudo_texto).replace("\n',","")...
texto_matriz = texto_limpo.lower()
texto_matriz = texto_limpo.split('.')
```

Create a Tokenizer:
```bash
tokenizer = Tokenizer()
```

Then create a dictionary with the indices and tokens and transform them into an array:
```bash
tokens = tokenizer.fit_on_texts(texto_matriz)
token_texto = tokenizer.word_index

matriz = tokenizer.texts_to_sequences(texto_matriz)
```

I turned all null values into '0.0' and we have our array!

For a complete view, I turned it into a '.xlsx' file
```bash
df = pd.DataFrame(matriz).fillna(0)
df.to_excel("Matrix Representation I.xlsx")
```

So we have a complete view of our matrix, where each row represents a sentence, the columns represent the total number of words that were used and each cell represents a word in our "Matrix Representation I.xlsx" file.


Then I did some additional things, I made a stopword in Latin and made a Word Cloud of each text
```bash
#TEXTO 1 - Base Text - Matrix Representation I - v2.txt

#CRIA UMA LISTA DE STOPWORDS EM LATIN E RETIRA AS PALAVRAS E SALVA ISSO NO NOME "texto_sem_stopword2"
stopword_latin = ['a','ab','ac', 'ad', 'at', 'atque', 'aut', 'autem', 'cum', 'de', 'dum', 'e',
                       'erant', 'erat', 'est', 'et', 'etiam', 'ex', 'haec', 'hic', 'hoc', 'in', 'ita', 'me', 'nec', 'neque', 
                       'non', 'per', 'qua', 'quae', 'quam', 'qui', 'quibus', 'quidem', 'quo', 'quod', 're', 'rebus', 'rem', 'res',
                       'sed', 'si', 'sic', 'sunt', 'tamen', 'tandem', 'te', 'ut', 'vel']

texto_sem_stopword = [k for k in token_texto if not k in stopword_latin] 

texto_sem_stopword2 = " ".join(texto_sem_stopword)

#CRIA UMA NUVEM DE PALAVRAS COM AS PALAVRAS UTILIZADAS NO TEXTO
mapa_cor = ListedColormap(['orange', 'green', 'red', 'blue'])

nuvem = WordCloud(background_color = 'white', max_words = 1000, colormap=mapa_cor)

nuvem = nuvem.generate(texto_sem_stopword2)
plt.figure(figsize=(15,15))
plt.imshow(nuvem)
plt.axis('off')
plt.show()
```
It is also possible to revert the array back to text:
```bash
texto_1 = matriz
tokenizer.sequences_to_texts(texto_1)
```
