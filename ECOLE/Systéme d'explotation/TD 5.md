### 1. Rappels sur les ressources et la synchronisation

- **Ressource critique** : ressource partagée entre plusieurs processus nécessitant un accès contrôlé pour maintenir la cohérence.
- **Section critique** : partie de code accédant à une ressource critique et devant être exécutée de manière indivisible pour éviter les conflits.
- **Exclusion mutuelle** : cas de synchronisation où une ressource n'est accessible que par un processus à la fois.
- **Sémaphore** : objet de synchronisation qui permet de contrôler l'accès aux ressources en évitant l'attente active. Composé d’un compteur et d’une file d’attente :
    - Compteur > 0 : nombre de ressources disponibles.
    - Compteur < 0 : nombre de processus en attente.

Opérations sur un sémaphore :

- **P** (prendre la ressource) : décrémente le compteur et bloque le processus si aucune ressource n’est disponible.
- **V** (libérer la ressource) : incrémente le compteur et débloque un processus en attente, le cas échéant.

#### Questions

1.1. **Code des primitives P et V** : Implémentez `P` et `V` en utilisant les primitives `courant()`, `insérer`, et `extraire`.

1.2. **Indivisibilité des primitives P et V** : Expliquez pourquoi elles doivent être indivisibles (prévention des interférences) et proposez des moyens d’assurer leur indivisibilité (ex. verrouillage au niveau matériel ou utilisation de verrous logiciels).

1.3. **Masquage des interruptions en mode utilisateur** : Pourquoi le masquage des interruptions n'est-il pas une bonne solution pour une section critique en mode utilisateur ? (Le mode utilisateur n’a généralement pas la permission d’interrompre l’ensemble du système.)

1.4. **Interruption en section critique** : Que se passe-t-il si un processus en section critique est interrompu ? (Cela pourrait mener à des incohérences si le processus suivant accède à la même ressource critique.)

---

### 2. Accès à une variable partagée

On analyse l’accès concurrent à une variable `x` par trois processus utilisant un sémaphore `Mutex` initialisé à 1. On doit suivre deux scénarios et identifier le contenu du compteur, de la file, et l’état des processus après chaque opération. Pour le scénario alternatif, justifiez sa possibilité ou impossibilité.

2.1. **Analyse des processus et états de `Mutex`** : Analyser la séquence des processus A, B et C.

2.2. **Valeurs finales de `a`** : Trouver les valeurs finales possibles de `a` dans différents scénarios d’exécution de trois processus synchronisés par les sémaphores `S1` et `S2`.

2.3. **Synchronisation pour des valeurs spécifiques** : Ajoutez les sémaphores nécessaires pour obtenir `a = 34` ou `a = 24` à chaque exécution. Décrivez les initialisations et la configuration requise des sémaphores.

2.4. **Suppression de sémaphores** : Identifiez quel sémaphore pourrait être supprimé sans modifier l’exécution globale et justifiez.

2.5. **Modification de la synchronisation** : Analyser une nouvelle configuration des processus utilisant les sémaphores `S1` et `S2` (initialisés à 1). Décrivez les conséquences de cette modification.

---

### 3. Synchronisation d’un ensemble de processus

3.1. **Ordre d’affichage** : Expliquez pourquoi les affichages des processus peuvent ne pas être ordonnés selon leurs identifiants croissants.

3.2. **Affichage ordonné** : Modifiez le code de chaque processus pour garantir un ordre croissant d’affichage selon les identifiants des processus.

3.3. **Affichage centralisé avec un processus dédié** : Créez un programme où un processus supplémentaire (`PN`) réalise tous les affichages dans l’ordre des identifiants (P0, P1, …, PN-1) sans appeler `calcul`. Le code doit utiliser uniquement des sémaphores et des variables partagées pour la synchronisation.

Ces questions amènent à une compréhension approfondie de l’usage des sémaphores pour la synchronisation et l’exclusion mutuelle, en particulier dans le contexte d'accès à des ressources partagées et de séquençage d’opérations entre processus.