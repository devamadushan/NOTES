### 1. Concepts et Rappels

- **fork()** :
    
    - Crée un processus fils identique au processus père, hormis les numéros de `pid = id de fils`  et  `ppid = ID de pére`.
    - Retourne `0` pour le fils et le `pid` du fils pour le père.
    - Chaque processus dispose de sa propre copie de données et de pile (pas de partage).
- **wait()** :
	
    - Bloque un processus jusqu'à la fin d'un de ses processus fils.
    - Renvoie le `pid` du fils terminé et peut recevoir un paramètre pour récupérer des informations sur la fin du fils.
```c
int status; // déclaration d'une variable status
pid_t child_pid = wait(&status); //
```
	- status = les informations détailler du processus fils
	- child_pid = le ID du  processus fils qui vien de se terminer ou -1 si ya plus de fils
- **exec** (famille des appels système `exec`) :
    
    - Lance un programme exécutable dans le processus courant.
    - Si réussi, le processus qui appelle `exec` est remplacé par le nouveau programme (ne retourne pas d'appel sauf en cas d'échec).
    - son vrai programme après l'exec sera remplacer par un nouveau programme de exec().
	1. **`execl()`** 
		 La fonction `execl()` permet de passer les arguments au programme sous forme de liste.
````c
	
	int execl(const char *path, const char *arg, ..., (char *)NULL);
	//Exemple
	execl("/bin/ls", "ls", "-l", "/home", (char *)NULL);

````
___
	2.   **`execlp()`**
		Similaire à `execl()`, mais avec la différence que cette fonction recherche le programme dans les répertoires listés dans la variable d'environnement `PATH` si le chemin n'est pas absolu.
```c
int execlp(const char *file, const char *arg, ..., (char *)NULL);
// EXemple
execlp("ls", "ls", "-l", "/home", (char *)NULL);

```
____
	3. **`execv()`**
		La fonction `execv()` est similaire à `execl()`, mais les arguments sont passés sous forme de tableau (vecteur) de chaînes de caractères.
```c
int execv(const char *path, char *const argv[]);
//Exemple
char *argv[] = {"ls", "-l", "/home", NULL};
execv("/bin/ls", argv);

```
---
	4. **`execvp()`** 
		Similaire à `execv()`, mais cette fonction recherche le programme dans les répertoires listés dans la variable d'environnement `PATH` si le chemin n'est pas absolu.
```c
int execvp(const char *file, char *const argv[]);
//Exemple
char *argv[] = {"ls", "-l", "/home", NULL};
execvp("ls", argv);

```
___
	5.  **`execve()`** 
		`execve()` est la fonction la plus générique et la plus bas niveau parmi toutes les variantes d'`exec`. Elle permet de spécifier non seulement les arguments du programme mais aussi l'environnement dans lequel il doit être exécuté.
```c
int execve(const char *path, char *const argv[], char *const envp[]);
//Exemple
char *argv[] = {"ls", "-l", "/home", NULL};
char *envp[] = {"PATH=/usr/bin", "HOME=/home/user", NULL};
execve("/bin/ls", argv, envp);

```

___

### 2. Exécution d’un `fork` simple

- Programme simple illustrant l'usage de `fork()` avec des affichages différents selon le processus (père ou fils).
- Point clé : Identifier les messages affichés par le processus père et le fils après l’appel `fork()`.

---

### 3. Exécution d'opérations `fork` imbriquées

- **Structure de Programme** :
    
    - Création de processus par des `fork()` imbriqués.
    - Calculs et affichages conditionnels selon le processus.
- **Points à retenir** :
    
    - Nombre total de processus créés.
    - Affichages et valeurs affichées par chaque processus.
    - Impact de la suppression d’un appel `exit()`.
- **Modification** : Créer un processus zombie (processus terminé, mais non libéré par le père).
    

---

### 4. Création de processus en chaîne

- **Programme demandé** :
    - Un processus qui crée un fils, lequel crée un autre fils, etc., jusqu'à N processus.
- **Points à explorer** :
    - Représentation des processus créés pour un nombre donné (ex. N = 3).
    - Modifications pour :
        - Attente de fin uniquement pour le processus fils direct du père.
        - Terminaison du processus principal après tous les processus.

---

### 5. Modification de l'exécution avec `exec`

- **Appel à `execl`** :
    
    - Utilisation de `execl` pour remplacer le processus par un autre programme.
    - Point à retenir : Si `execl` réussit, le processus fils exécute le nouveau programme, ici `echo "je suis le fils"`, tandis que le père affiche "je suis le père".
- **Programme "nemaxe"** :
    
    - Programme en plusieurs étapes avec des forks et un `exec`.
    - **Arborescence de processus** : Représentation des processus créés (utilisation des lettres en commentaires pour structurer l’arbre).
- **Ordres de terminaison des processus** : Identifier les ordres possibles selon les appels `wait()` et `exit()`.
    
- **Modification pour éviter boucles infinies** :
    
    - Limitation à 2 occurrences de la section `B` du programme