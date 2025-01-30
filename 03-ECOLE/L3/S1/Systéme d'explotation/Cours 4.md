### **Processus**

- **Définition** : Une instance d'un programme en cours d'exécution, avec son propre espace mémoire, piles, et compteurs.
- **Points clés** :
    - Création via `fork()`.
    - Attribution de PID unique.
    - Types de processus : père (parent) et fils (child).

### 2. **Création de processus**

- **Définition** : Lancement d'un nouveau processus par un processus existant.
- **Points clés** :
    - `fork()` : Crée une copie du processus appelant.
    - `exec()` : Remplace le processus actuel par un autre programme.
    - `wait()` : Bloque le processus père jusqu'à la fin du processus fils.
	    - Exécution sans `wait()` – Problème du zombie
	    - Un processus fils **ne peut pas être totalement supprimé** tant que le parent ne récupère pas son état via `wait()`.
	- `waitpid()` :est une fonction qui permet au processus parent d'attendre la fin d'un processus fils spécifique,
	
	- `exit()`
		- exit(0) termine un programme et indique son statut grâce à un code de retour.
		- exit(!=0)
	- options()
		- `WNOHANG`
		- `WUNTRACED`
		- `WCONTINUED`
### 3. **Processus Zombie

Un **processus zombie** est un processus qui a terminé son exécution, mais dont le parent n'a pas encore récupéré son statut de sortie via `wait()`. Un processus zombie conserve certaines informations (comme son PID et son statut de terminaison) dans la table des processus du système d'exploitation, ce qui permet au parent de récupérer ces informations à un moment donné.

Voici comment un processus zombie se produit :

1. Un processus enfant termine son exécution.
2. Le processus enfant envoie un signal à son parent pour lui indiquer qu'il est terminé.
3. Si le parent ne récupère pas l'état de sortie du processus avec `wait()` ou `waitpid()`, le processus enfant reste dans la table des processus avec un statut =="terminé" mais "non récupéré".==
4. Ce processus est dit **zombie**, et il reste ainsi jusqu'à ce que le parent récupère l'état de sortie via `wait()`.

Apres avoir récupérer le statu du fils en utilisant : `wait(&status)`, `waitpid(&status)`, ou `wait3(&status)`. 
- **`WIFEXITED(status)`** :
    
    - Retourne vrai si le processus enfant s'est terminé normalement (avec `exit` ou la fin de `main`).
    - Utilisé pour vérifier si le processus a terminé sans être interrompu.
- **`WEXITSTATUS(status)`** :
    
    - Retourne le code de sortie du processus enfant si `WIFEXITED(status)` est vrai.
    - Ce code correspond à la valeur passée dans `exit()` ou au retour de la fonction `main`.
- **`WIFSIGNALED(status)`** :
    
    - Retourne vrai si le processus enfant s'est terminé suite à un signal non intercepté.
    - Cela se produit si le processus a été interrompu par un signal comme `SIGKILL` ou `SIGTERM`.
- **`WTERMSIG(status)`** :
    
    - Si `WIFSIGNALED(status)` est vrai, cette macro retourne le numéro du signal qui a causé l'arrêt du processus enfant.
- **`WIFSTOPPED(status)`** :
    
    - Retourne vrai si le processus enfant est arrêté (par exemple, suite à un signal `SIGSTOP` ou `SIGTSTP`).
    - Utilisé avec `ptrace` (pour le débogage) ou pour gérer des arrêts temporaires de processus.
- **`WSTOPSIG(status)`** :
    
    - Si `WIFSTOPPED(status)` est vrai, cette macro retourne le numéro du signal qui a arrêté le processus enfant.
- **`WIFCONTINUED(status)`** (disponible dans certains systèmes) :
    
    - Retourne vrai si le processus enfant a été redémarré après un arrêt avec `SIGCONT`.
    - Cela est utile pour suivre un processus qui alterne entre l’arrêt et la reprise.