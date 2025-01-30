### Description
Exactement la même chose que le modèle 003, mais cette fois avec 27 000 valeurs différentes de temps. Il récupère un fichier `CSV` en entrée et génère un fichier `CSV` contenant les prédictions.
### Avantage 
On peut lui passer directement un fichier `CSV` contenant une seule colonne `Temps`, et il trouvera la température correspondante en fonction de ce avec quoi il a été entraîné.

### Inconvénient 
Il prend beaucoup plus de temps de calcul, par exemple : environ 30 minutes pour traiter 27 000 valeurs.
### Programme
`create_data_train.py`
```python

# 15/01/2025  
# crée un fichier csv avec un tres grand nombre de donnée  
  
# ************************************* Imports ******************************#  
  
import pandas as pd  
import numpy as np  
import matplotlib.pyplot as plt  
# ******************************** Imports Terminal **************************#  
#   pip install ...  
  
  
# ----------------------------* crée un fichier (CSV) *---------------------#  
temps = list(range(1,501))  
param = 3  
temperature =[]  
for i in range(1,501):  
    temperature.append(10 * np.sin(2 * np.pi * param *i / 100)) 
  
df = pd.DataFrame({"Temps" : temps, "Temperature" : temperature} )  
df.to_csv("Brain004.csv" ,index=False)
```

`create_data_in.py`
```python

# 16 janvier 2025  
# Crée un fichier "data_in" avec une colonne "Temps" remplie de manière aléatoire  
# et une colonne "Temperature" laissée vide  
  
# ************************************* Imports ******************************#  
  
import pandas as pd  
import numpy as np  
  
# ******************************** Imports Terminal **************************#  
#   pip install ...  
  
  
# ----------------------------* crée un fichier IN (CSV) *---------------------#  
  
temps = []  
temperature = []  
  
for i in range(1, 27000):  
    temps.append(np.random.randint(1, 9951200))  
  
  
data_in_csv = pd.DataFrame({"Temps": temps , "Temperature": np.nan})  
data_in_csv.to_csv("Brain004.csv" ,index=False)

```


`brain004.py`
```python

# 17 janvier 2025  
# Un test pour récupérer un fichier CSV (IN) partiellement rempli et prédire les valeurs manquantes avec cette fois plus de donnée et une formule de mathématique plus complex  
  
# ************************************* Imports ******************************#  
  
import pandas as pd  
from keras import *  
import numpy as np  
import datetime  
  
  
# ******************************** Imports Terminal **************************#  
#   pip install tenserflow  
  
  
# ----------------------------* lire le fichier IN (CSV) *---------------------#  
  
data_train = pd.read_csv('data/data_train/Brain004.csv')  
  
entree_train = data_train['Temps'].values  
sortie_train = data_train['Temperature'].values  
  
# ___________________________________* Model *_________________________________#  
  
model = Sequential()  
model.add(layers.Dense(16, input_shape=[1]))  # input  
model.add(layers.Dense(32))  # hyden  
model.add(layers.Dense(1))  # out  
  
# -------------------------------------* Compile *-----------------------------#  
avant = datetime.datetime.now()  
model.compile(loss='mean_squared_error', optimizer='adam')  
model.fit(x=entree_train, y=sortie_train, epochs=5500)  
apres = datetime.datetime.now()  
print(f'départ : {avant}')  
print(f'fin : {apres}')  
  
print(f'la durée : {apres - avant}')  
#:::::::::::::::::::::::::::::::::::* Test *:::::::::::::::::::::::::::::::::#  
  
while True:  
    data_in_present = int(input("si vous avez charger le fichier csv dans data_in entrez 1 : "))  
    if data_in_present == 1:  
        data_in = pd.read_csv('data/data_in/Brain004.csv')  
  
        entree_in = data_in['Temps'].values  
       # print(entree_in)  
  
        prediction = model.predict(entree_in)  
        data_out = prediction.flatten()  
        #print(data_out)  
        df = pd.DataFrame({"Temps": entree_in,"Temperature":data_out})  
        df.to_csv('data/data_out/Brain004.csv', index=False)  
        data_in_present = 0  
    else:  
        print("saisie incorrect")

```