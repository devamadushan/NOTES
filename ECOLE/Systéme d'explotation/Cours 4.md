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

### 3. **Communication inter-processus (IPC)**

- **Définition** : Mécanismes permettant aux processus de communiquer et de synchroniser leurs actions.
- **Points clés** :
    - **Pipes** : Communication entre processus apparentés, unidirectionnelle.
    - **FIFOs (named pipes)** : Comme les pipes, mais permettent la communication entre processus indépendants.
    - **Signaux** : Notifications de base entre processus (ex. : `SIGINT` pour interruption).
    - **Sockets** : Communication réseau ou locale, indépendamment de la parenté des processus.
    - **Mémoire partagée** : Zone mémoire partagée entre processus pour un échange rapide de données.

### 4. **Signaux**

- **Définition** : Mécanismes pour envoyer des interruptions simples aux processus.
- **Points clés** :
    - **Signaux standards** : (ex. `SIGINT`, `SIGKILL`, `SIGTERM`) pour arrêter ou interrompre un processus.
    - **Gestion des signaux** : Utilisation de `signal()` ou `sigaction()` pour définir des gestionnaires de signaux personnalisés.
    - **Masquage des signaux** : Bloquer temporairement certains signaux pour protéger une section de code critique.

### 5. **Threads et parallélisme**

- **Définition** : Unité de traitement au sein d'un processus qui partage la mémoire avec d'autres threads du même processus.
- **Points clés** :
    - **Création** : `pthread_create()` pour créer un nouveau thread.
    - **Synchronisation** : Utilisation de mutex, sémaphores, et variables de condition pour gérer l'accès concurrent aux ressources.
    - **Différences processus/threads** : Les threads partagent la mémoire, alors que les processus ont chacun leur espace mémoire.

### 6. **Planification des processus**

- **Définition** : Gestion de l'ordre et du temps d'exécution des processus par le système d'exploitation.
- **Points clés** :
    - **Priorité de processus** : Ajustée avec `nice` et `renice` pour modifier les priorités.
    - **Algorithmes de planification** : Exemples : round-robin (tourniquet), priorité, temps réel.
    - **États de processus** : Les processus peuvent être exécutants, bloqués, suspendus, etc.

### 7. **Environnement d'exécution des processus**

- **Définition** : Contexte dans lequel un processus s'exécute, incluant les variables d'environnement et les descripteurs de fichiers.
- **Points clés** :
    - **Variables d'environnement** : Contiennent des informations sur le système et l'utilisateur ; modifiables via `getenv()` et `setenv()`.
    - **Descripteurs de fichiers** : Hérités par les processus fils, permettant la redirection d'entrées/sorties.
    - **E/S standards** : Flux `stdin`, `stdout`, `stderr` redirigeables pour contrôler les entrées/sorties.

### 8. **Gestion des erreurs et débogage**

- **Définition** : Techniques pour identifier et gérer les erreurs dans les processus.
- **Points clés** :
    - **Gestion d'erreurs** : Utilisation de `errno` pour interpréter les erreurs des appels système.
    - **Outils de débogage** : `strace` pour suivre les appels système, `gdb` pour analyser les erreurs et plantages de processus.

### 9. **Isolation et conteneurisation**

- **Définition** : Techniques pour isoler les processus dans des environnements protégés ou partiellement indépendants.
- **Points clés** :
    - **chroot** : Change la racine du système de fichiers d’un processus pour l'isoler.
    - **Namespaces** : Permettent l’isolation de ressources système (ex. réseaux, utilisateurs, PID).
    - **cgroups** : Limitent et isolent l'utilisation de ressources (CPU, mémoire) pour un groupe de processus (utilisé dans les conteneurs).