
#Fork
	**`fork()`** est utilisée pour créer un **processus fils**. Le processus fils est une copie presque exacte du processus parent, sauf qu'il a un PID (Process ID) différent.
		- Un pére peut crée un fils (Utilisé `fork()`)
		- Les fils peuvent crée des sous fils
	 `fork()` Return :
		 1. **0** : Si le processus appartiens au fils
		 2. **-1** : Si le **fork échoue** (en raison d'un manque de ressources par exemple).
		 3. **autres** : (PID de Fils) et il le processus appartiens au pére.
#get-pid 
	`getpid()` est une méthode utiliser pour avoir le ID d'un processus.
		`pid_t pid = getpid();`
#exit
	Peut importe la quantité des Fils ou sous fils , il vont prendre la fin une fois que il ont a méthode `exit()`
	Méthode `exit()` a 2 rôle :
	1. Terminer le processus
		Lorsque le processus a fini d'exécuter ses instructions, il doit quitter l'exécution en appelant `exit()`.
	2. Retourner un code de sortie
		Un code de sortie **0** indique une fin réussie, tandis qu'un code différent de **0** peut indiquer une erreur ou une condition particulière.
#wait
	La méthode **`wait()`** est utilisée par un **processus parent** pour **attendre** que ses processus **fils** se terminent. Elle est essentielle pour synchroniser les processus et éviter les processus **zombies**.
		- Retourne le **PID** du processus fils qui s'est terminé.
		- Si le processus n'a pas de fils en attente, `wait()` retourne **-1**
#processus-zombie
	Si un processus fils se termine et que le parent ne récupère pas son code de sortie, le processus reste en mémoire comme un **zombie**. #wait permet au parent de "récolter" les informations de terminaison du fils et de nettoyer le processus fils de la mémoire.
#kill
	la fonction `kill(pid)` permet de arrêter un processus qui est encours... (pére ou fils) 
#zombie
	Un **processus zombie** est un processus qui a terminé son exécution (c'est-à-dire qu'il a appelé #exit  mais dont l'**entrée dans la table des processus** n'a pas encore été supprimée par le système d'exploitation parce que son **processus parent** n'a pas récupéré son code de sortie avec #wait .
#sleep
	La méthode `sleep(n)` fera arrêter un processus `n` seconde  qui l'exécute.
	

Un **processus** est une instance d’un programme en cours d'exécution. Il représente non seulement le programme lui-même (le code) mais aussi tout ce qui est nécessaire à son exécution.
- Chaque processus a un ID et on peut les trouver avec #get-pid .
- Chaque processus ont une méthode #get-pid 

Dans un **processus**, la mémoire est divisée en plusieurs sections, chacune ayant une fonction spécifique. Ces sections sont appelées **segment code**, **segment pile**, et **segment données**. 

![[Pasted image 20241010190524.png]]
1. Un processus peut crée un Fils en utilisant #Fork 
2. Un processus peut avoir aussi N-Fils , mais pour crée des N fils faut d'abord vérifier qui a le CPU. car :
	-  Si le père a la CPU il peut crée d'autres fils comme on souhaite 
	-  Si le fils prend le contrôle de la CPU c'est lui qui va crée des sous fils donc il faut contrôler cela .
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main() {
    int N = 5;  // Nombre de processus fils à créer
    int i;

    for (i = 0; i < N; i++) {
        pid_t pid = fork();  // Crée un nouveau processus

        if (pid < 0) {
            // Si la création du processus échoue
            fprintf(stderr, "Échec du fork\n");
            return 1;  // On quitte avec une erreur
        } 
        else if (pid == 0) {
            // Code exécuté par le processus fils
            printf("Je suis le processus fils %d, mon PID est %d\n", i + 1, getpid());
            // On utilise `break` pour que les fils ne continuent pas à créer d'autres              fils
            break;
        }
        // Le parent continue la boucle pour créer d'autres processus fils
    }

    // Code commun aux processus fils et au parent
    if (i == N) {
        // Ce code est exécuté uniquement par le processus parent, après la création des N fils
        printf("Je suis le processus parent. Mon PID est %d\n", getpid());
    }

    return 0;
}

```

3. Quand on crée des processus fils au processus parent faudra faire attention que on a pas des processus #zombie . pour les éviter on peut utiliser les méthodes #exit et #wait  par exemple.  
```


int main() {
    pid_t pid = fork();  // Crée un processus fils

    if (pid < 0) {
        // Si `fork()` échoue
        fprintf(stderr, "Erreur lors du fork\n");
        return 1;
    }

    if (pid == 0) {
        // Code exécuté par le processus fils
        printf("Je suis le processus fils, PID : %d\n", getpid());
        // Terminer avec un code de sortie 5
        exit(5);
    } else {
        // Code exécuté par le processus parent
        int status;
        pid_t terminated_pid = wait(&status);  // Le parent attend que le fils se               termine
        printf("Le processus fils avec PID %d s'est terminé\n", terminated_pid);
    }

    return 0;
}

```



````

int main(int argc, char *argv[]) {
    int a, e;

    a = 10;  // Initialisation de la variable 'a' à 10

    if (fork() == 0) {  // Premier fork, création du processus enfant
        a = a * 2;  // Modification de la valeur de 'a' dans l'enfant (a = 20)
        
        if (fork() == 0) {  // Deuxième fork dans l'enfant, création du sous-enfant
            a = a + 1;  // Modification de 'a' dans le sous-enfant (a = 21)
            // Le sous-enfant continue, mais ne termine pas immédiatement
        }

        printf("Dans l'enfant, a = %d \n", a);  // Affiche la valeur de 'a' dans l              'enfant (a = 20 ou 21 selon qui l'affiche)
        exit(1);  // L'enfant se termine avec le code de sortie 1
    }

    wait(&e);  // Le processus parent attend que l'enfant se termine
    printf("Dans le parent, a : %d ; e : %d \n", a, WEXITSTATUS(e));  // Affiche la         valeur de 'a' dans le parent et le code de sortie de l'enfant

    return 0;
}

```