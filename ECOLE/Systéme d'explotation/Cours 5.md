
- **Synchronisation des Processus**
    
    - Processus concurrents peuvent partager des ressources (variables, fichiers).
    - Accès concurrent peut entraîner des incohérences ; il faut des mécanismes pour garantir la cohérence.
- **Ressource Critique**
    
    - Ressource partagée qui nécessite un contrôle d'accès.
    - **Section Critique (SC)** : Partie du code qui manipule la ressource critique, doit être indivisible.
- **Exclusion Mutuelle**
    
    - Garantit qu’un seul processus accède à une SC à la fois.
    - Mécanismes d'exclusion :
        - **Masquage IT Horloge** : Mauvaise solution car monopolise le processeur.
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
- **Propriétés de Synchronisation**
    
    - **Sûreté** : Pas plus d'un processus en SC.
    - **Vivacité** : Chaque demande d'accès à la SC doit être satisfaite.
    - **Indivisibilité de `EntrerSC()` et `SortirSC()`**.
- **Problèmes classiques**
    
    - **Producteur-Consommateur** : Coopération entre processus pour utiliser un tampon partagé.
        - **Conflits** : Producteur ne peut pas déposer si le tampon est plein ; consommateur ne peut retirer si vide.
        - Utilisation de sémaphores pour gérer :
            - `scons` : Contrôle les cases pleines (initialisé à 0).
            - `sprod` : Contrôle les cases vides (initialisé à N).
            - `mutex` : Exclusion mutuelle.
- **Interblocage et Famine**
    
    - **Interblocage (Deadlock)** : Processus se bloquent mutuellement, attendant un événement impossible.
    - **Famine** : Un processus attend indéfiniment l'accès à une SC.