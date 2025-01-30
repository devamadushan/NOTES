---
tags:
  - Installation
  - Python
  - venv
---


## Librairies Python
- [[Pandas]]
- [[Tensorflow]]

---
## Template


```python

# date du derniere modification 
# objectif 


#************************************* Imports ******************************#  
  
...
  
#******************************** Imports Terminal **************************#  
#   pip install ...

  
#----------------------------* Main programme *---------------------#  
  

  
#___________________________________*  *_________________________________#  
  
 
  
#-------------------------------------*  *-----------------------------#  
  
  
#:::::::::::::::::::::::::::::::::::* Test *:::::::::::::::::::::::::::::::::#  
  

```

---

## Installation 

   ```bash
   sudo apt install python
   ```
   - Installe Python via le gestionnaire de paquets `apt`.
   - Note : Par défaut, cela installe Python 2 si aucun autre paramètre n'est configuré.

   ```bash
   sudo apt install python-pip
   ```
   - Installe le gestionnaire de paquets `pip` pour gérer les modules Python.

   ```bash
   sudo apt install python-venv
   ```
   - Nécessaire pour créer des environnements virtuels Python isolés.

   ```bash
   sudo apt install python-is-python3
   ```
   - Configure le système pour que la commande `python` pointe vers Python 3 au lieu de Python 2.

--- 

## Environnement Virtuel

   ```bash
   python -m venv Brain_models
   ```
   - Crée un environnement virtuel nommé `Brain_models` dans le répertoire courant.

   ```bash
   source Brain_models/bin/activate
   ```
   - Active l'environnement virtuel, isolant les dépendances des projets Python.


