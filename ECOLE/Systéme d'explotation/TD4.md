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
- **`/bin/ls`** : C'est le chemin complet vers le programme `ls` qui doit être exécuté. Le programme `ls` permet de lister les fichiers et dossiers dans un répertoire.
    
- **`"ls"`** : C'est le premier argument passé au programme `ls`, et dans la convention Unix, c'est généralement le nom du programme lui-même. Cela permet au programme `ls` de savoir quel est son propre nom, bien que ce soit une redondance ici.
    
- **`"-l"`** : Il s'agit d'un argument pour `ls` qui indique à `ls` de lister les fichiers avec des informations détaillées (format long).
    
- **`"/home"`** : C'est un autre argument pour `ls` qui spécifie le répertoire dont on souhaite afficher le contenu, ici le répertoire `/home`.
    
- **`(char *)NULL`** : Cela marque la fin de la liste des arguments. Dans toutes les fonctions `exec*()`, le dernier argument doit être `NULL` pour indiquer que la liste des arguments est terminée.
___
	2.   **`execlp()`**
		Similaire à `execl()`, mais avec la différence que cette fonction recherche le programme dans les répertoires listés dans la variable d'environnement `PATH` si le chemin n'est pas absolu.
```c
int execlp(const char *file, const char *arg, ..., (char *)NULL);
// EXemple
execlp("ls", "ls", "-l", "/home", (char *)NULL);

```
Ici, `execlp()` recherche le programme `ls` dans les répertoires définis dans `PATH` (par exemple `/usr/bin`, `/bin`, etc.), sans nécessiter un chemin complet comme `/bin/ls`.
____
	3. **`execv()`**
		La fonction `execv()` est similaire à `execl()`, mais les arguments sont passés sous forme de tableau (vecteur) de chaînes de caractères.
```c
int execv(const char *path, char *const argv[]);
//Exemple
char *argv[] = {"ls", "-l", "/home", NULL};
execv("/bin/ls", argv);
```
	ici, `execv()` prend le tableau `argv`, où le dernier élément doit être `NULL`, pour fournir les arguments au programme. Le chemin du programme est toujours absolu (`/bin/ls`).
---
	4. **`execvp()`** 
		Similaire à `execv()`, mais cette fonction recherche le programme dans les répertoires listés dans la variable d'environnement `PATH` si le chemin n'est pas absolu.
```c
int execvp(const char *file, char *const argv[]);
//Exemple
char *argv[] = {"ls", "-l", "/home", NULL};
execvp("ls", argv);
```
Dans ce cas, `execvp()` cherche `ls` dans les répertoires définis dans `PATH` si un chemin relatif est utilisé.
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
