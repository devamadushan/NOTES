### Description
Un modèle qui peut récupérer un énorme fichier CSV, puis trier et nettoyer les données avec filter.py. Ensuite, il prend en compte les paramètres d'entrée et de sortie définis dans un fichier JSON, récupère uniquement les paramètres nécessaires pour l'entraînement avec formater.py, puis entraîne le modèle.

### Avantage 
Automatisation de la sélection des paramètres d'entrée et de sortie, ainsi que du tri et du formatage préalable des données, afin de réduire le temps d'entraînement.

### Inconvénient 
...

### Architecture  
   
```
data:
	brain:
		brain.hdf5
	to_client:
		data_out.csv
	to_player:
		data_in.csv
	to_tracer:
		data_true.csv
	to:traine:
		data_train.csv
	filter.py
	rebuilder.py
play:
training:
	data:
		filtered_data:
		inputs:
		outputs:
		formater.py:	
	trainer.py
brain.py:
params.json:
```
### Programmes

```python

```
