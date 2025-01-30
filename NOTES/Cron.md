---
tags:
  - GitLab
  - Web
  - Cron
  - Documentation
---
### Activer Cron
Ouvrir le fichier de configuration Cron :
```bash
crontab -e
```
Ajouter la ligne suivante pour exécuter le script .sh toutes les minutes :
```bash
* * * * * /home/wmaster/synchro_doc/synchron.sh
```
Ajouter la ligne suivante pour exécuter le script Python :
`/home/wmaster/synchro_doc/synchron.sh`
```sh
/usr/bin/python /home/wmaster/synchro_doc/pull_doc.py 2>&1 | tail -n 50 >> /home/wmaster/synchro_doc/logs.txt && tail -n 50 /home/wmaster/synchro_doc/logs.txt > /home/wmaster/synchro>
```
#### Explications :
**Exécution de Cron :**
- `* * * * *` : La tâche s'exécute **toutes les minutes**.
- `/home/wmaster/synchro_doc/synchron.sh` : Chemin du script à exécuter.
- `/usr/bin/python`: Chemin de l'interpréteur Python. 
- `/home/wmaster/synchro_doc/pull_doc.py` : Chemin de ton programme Python.
- `2>&1 `: Redirige les erreurs vers la sortie standard.
- `tail -n 50 ` :Prend uniquement les 50 dernière ligne de sortie du script Python.
- `>> /home/wmaster/synchro_doc/logs.txt` : ajoute cette ligne au fichier `logs.txt`


### Git pull 
Programme python pour faire un Git pull.

`pull_doc.py`
```python
# 27 janvier 2025
# git pull Documentation


# ************************************* Imports ******************************#

import os
import subprocess

#---------------------------* Repertoire du Documentation  *-------------------#

repository_path = "/home/wmaster/public-html/octopus_documentation/"

#_____________________________________* Pull *_________________________________#

try:
    if not os.path.exists(repository_path):
        raise FileNotFoundError(f"Le chemin {repository_path} n'existe pas.")
    os.chdir(repository_path)
    result = subprocess.run(
        ["git", "pull", "origin", "main"], capture_output=True, text=True)
    if result.returncode == 0:
        print("Git pull réussi !")
        print(result.stdout)
    else:
        print("Erreur lors du git pull :")
        print(result.stderr)

except Exception as e:
    print(f"Une erreur est survenue : {e}")

```

