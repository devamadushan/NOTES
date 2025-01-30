
- **Synchronisation des Processus**
    
    - Processus concurrents peuvent partager des ressources (variables, fichiers).
    - Accès concurrent peut entraîner des incohérences ; il faut des mécanismes pour garantir la cohérence.
- **Ressource Critique**
    
    - Ressource partagée partagée entre plusieurs processus, ce qui signifie que plusieurs processus peuvent y accéder en même temps. Cependant, lorsqu'une ressource est partagée, il est nécessaire de gérer son accès pour éviter des problèmes comme la **corruption de données**.
- **Section critique (SC)**
    - Une **section critique** est une portion de code où un processus accède ou modifie une ressource partagée. Les sections critiques doivent être exécutées de manière **indivisible**, ce qui signifie que pendant qu'un processus exécute sa section critique, aucun autre processus ne peut l'exécuter simultanément. Cela est essentiel pour maintenir l'intégrité des données.
- **ivisibilité** 
	- Cela signifie que, pour chaque ressource partagée, il doit être garanti qu'une section critique ne sera pas interrompue ou exécutée en parallèle avec une autre. Cela évite des erreurs telles que des lectures ou écritures simultanées qui pourraient entraîner des résultats incorrects.
- **Syncronisation**
	- La **synchronisation** est le mécanisme qui permet de gérer l'ordre d'exécution des processus afin de garantir qu'ils avancent de manière coordonnée. Il peut s'agir de plusieurs types de mécanismes, comme :

	- **Attendre et recevoir** des messages (ex : `wait` et `signal` dans la gestion des processus père/fils).
	- **Barrières de synchronisation** où plusieurs processus attendent d'atteindre un certain point avant de continuer leur exécution ensemble.
- **Exclusion Mutuelle**
    
    - Garantit qu’un seul processus accède à une SC à la fois.
    - Mécanismes d'exclusion :
        - **Masquage IT Horloge** : Mauvaise solution car monopolise le processeur.
	        - Désactivation du temps partagé pendant la SC.
        - **Variable de Synchronisation (attente active)** : Ex. variable booléenne `lock`.
        - **Algorithme de Peterson** : Assure exclusion pour deux processus (exclusion mutuelle par attente active).
- **Problèmes d'attente active**
    
    - Consomme du temps CPU ; privilégier des solutions sans attente active pour de meilleures performances.
- **Sémaphores**
    
    - Variables sans attente active pour gérer l'accès aux ressources partagées.
    - **Compteur** : Indique le nombre de ressources disponibles.
    - **Opérations P et V** :
        - `P(S)`: Obtenir une ressource.
        - `V(S)`: Libérer une ressource.
```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>
#include <unistd.h>

int compteur = 0;      // Ressource critique partagée
sem_t mutex;           // Mutex pour l'exclusion mutuelle

void* incrementer(void* arg) {
    for (int i = 0; i < 5; i++) {
        sem_wait(&mutex); // Entrée en section critique (P(mutex))

        // Section critique
        int valeur = compteur;
        printf("Thread %ld lit la valeur %d\n", (long)arg, valeur);
        compteur = valeur + 1;
        printf("Thread %ld met à jour le compteur à %d\n", (long)arg, compteur);

        sem_post(&mutex); // Sortie de la section critique (V(mutex))

        sleep(1); // Pause pour observer l'exécution
    }
    return NULL;
}

int main() {
    pthread_t thread1, thread2;

    // Initialisation du mutex
    sem_init(&mutex, 0, 1); // 1 pour l'exclusion mutuelle (semaphore binaire)

    // Création des threads
    pthread_create(&thread1, NULL, incrementer, (void*)1);
    pthread_create(&thread2, NULL, incrementer, (void*)2);

    // Attente de la fin des threads
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    // Destruction du mutex
    sem_destroy(&mutex);

    printf("Valeur finale du compteur : %d\n", compteur);
    return 0;
}

```
- **Propriétés de Synchronisation**
    
    - **Sûreté** : Pas plus d'un processus en SC.
    - **Vivacité** : Chaque demande d'accès à la SC doit être satisfaite.
    - **Indivisibilité de `EntrerSC()` et `SortirSC()`**.
- **Problèmes classiques**
    
    - **Producteur-Consommateur** : Coopération entre processus pour utiliser un tampon partagé.
    - Consomateur:
	    - C’est un processus qui prend des données ou messages produits par le producteur dans le tampon et les utilise (ou les traite). Le consommateur est l’entité qui **retire** des éléments du tampon pour les utiliser.
    - Producteur :
	    - C’est un processus ou programme qui crée des **données** ou des **messages** et les stocke temporairement dans un espace partagé appelé le **tampon**. Le producteur produit des éléments que d’autres processus (les consommateurs) seront utile pour  plus tard.
    - tampon
	    - C’est une **zone de stockage partagée** où le producteur et le consommateur se partagent les données. Le tampon est souvent implémenté comme un tableau fixe en mémoire, ce qui implique que chaque case représente un emplacement où un message ou une donnée peut être stocké.3..3.33
	
	- **Conflits** : Producteur ne peut pas déposer si le tampon est plein ; consommateur ne peut retirer si vide.
        - Utilisation de sémaphores pour gérer :
            - `scons` : Contrôle les cases pleines (initialisé à 0).
            - `sprod` : Contrôle les cases vides (initialisé à N).
            - `mutex` : Exclusion mutuelle.
```c
init(sprod, N);    // Nombre de cases vides = N (tampon plein de place)
init(scons, 0);    // Nombre de cases pleines = 0 (tampon vide)
init(mutex, 1);    // Mutex pour l'exclusion mutuelle (1 signifie que le mutex est disponible)
```

- **Interblocage et Famine**
    
    - **Interblocage (Deadlock)** : Processus se bloquent mutuellement, attendant un événement impossible.
    - **Famine** : Un processus attend indéfiniment l'accès à une SC.