#CSMA/CA
	(Carrier Sense Multiple Access with Collision Avoidance) est un protocole de contrôle d'accès au réseau utilisé principalement dans les réseaux sans fil, comme le Wi-Fi. 
#CSMA/CD
	(Carrier Sense Multiple Access with Collision Detection) est un protocole de contrôle d'accès au réseau qui permet à plusieurs appareils de partager un même canal de communication, comme un câble Ethernet, en minimisant les risques de collisions entre les transmissions.
#vrc
#lrc
#crc
#DIFS
#ACK
 #SIFS
 #HAMMING
	 -distance de hamming
#redondance



### 1. Politiques d’accès statiques
- **FDMA** (Frequency Division Multiple Access) : Bande passante découpée en sous-bandes de fréquence, chaque bande étant allouée à un communicateur.
- **TDMA** (Time Division Multiple Access) : Temps divisé en intervalles, chaque intervalle étant affecté successivement aux communicateurs.
#### Exercice 1.1 Norme GSM 900 MHz

1. **Calcul des canaux** : Utilisez la largeur de bande (200 kHz par canal) pour déterminer le nombre total de canaux disponibles dans les bandes montante et descendante.
2. **Fréquences pour l’opérateur** : Identifiez les fréquences pour les canaux attribués à l'opérateur en tenant compte des limites données (31 à 60 et 91 à 95).
3. **Utilisateurs par cellule et cluster** : En fonction des intervalles de temps par canal (8 IT par canal), calculez le maximum d’utilisateurs par cellule et par cluster.
#### Exercice 1.2 : Conditions d’efficacité des accès statiques

1. **Simplicité et efficacité** : Le partage statique est efficace pour des réseaux avec peu de variation dans l’utilisation des ressources.
2. **Adaptation aux LAN** : La faible adaptation des techniques statiques dans des environnements locaux est due à l’imprévisibilité de la demande de communication.

### 2. Politiques d’accès dynamiques à allocation déterministe

- **Roll-Call Polling** : Une station maître interroge chaque station secondaire séquentiellement pour leur attribuer des ressources si nécessaire. Efficace pour des réseaux à charge faible.

#### Exercice 2.1 : Calcul de l’utilisation U

1. **Configuration en chaîne (câble coaxial)** et **liaison hertzienne** : Utilisez le temps de propagation et le temps de transmission pour exprimer l’utilisation de la liaison UUU en fonction du nombre de stations NNN et de a=tptta = \frac{tp}{tt}a=tttp​.
2. **Chargement du réseau** : Cette méthode est plus efficace pour les réseaux faiblement chargés.

#### Exercice 2.2 : Bluetooth

1. **Calcul de Nmax** : Utilisez l’espace alloué dans le champ de 3 bits (8 combinaisons possibles) pour déterminer le nombre maximum d’esclaves actifs.
2. **Efficacité** : Évaluez l’efficacité en considérant les temps de transmission et de propagation, ainsi que le nombre d’esclaves actifs
### 3. Politiques d’accès dynamique à allocation aléatoire (ALOHA et CSMA/CD)

- **ALOHA pur** : Envoi dès que nécessaire, mais présente des risques élevés de collision.
- **CSMA/CD (Ethernet)** : Écoute avant de transmettre pour réduire les collisions. En cas de collision, les stations arrêtent la transmission et attendent un délai aléatoire pour réessayer.

#### Exercice 3.1 : Collisions dans CSMA/CD

1. **Schéma de collision** : Illustrez pourquoi une collision est possible même avec l’écoute préalable (par exemple, si deux stations commencent à émettre presque simultanément).
2. **Longueur minimale de trame** : Utilisez la formule de durée de transmission basée sur la vitesse de propagation, longueur de la ligne, et capacité de transfert pour que CSMA/CD fonctionne.
#### Exercice 3.2 : Exponential Backoff

1. **Délai d’attente en cas de collisions** : Le backoff exponentiel détermine le temps d’attente aléatoire avant retransmission, augmentant après chaque collision.
2. **Diagramme des temps** : Remplissez le diagramme en ST en utilisant les valeurs de backoff fournies pour chaque station.

### 4. Contrôle d’erreurs

- **Détection et correction d’erreurs** : Les données sont protégées par des bits supplémentaires pour vérifier ou corriger les erreurs.

#### Exercice 4.1 : Codes détecteurs

1. **Mots légaux et illégaux** : Le nombre de mots légaux et illégaux dépend des bits de contrôle ajoutés aux bits de données.
2. **Détection d’erreur** : En vérifiant si un mot reçu correspond aux règles de parité, il est possible de détecter une erreur.
#### Exercice 4.2 : Parité VRC et LRC

1. **VRC (Vérification de Redondance Verticale)** : Utilisé pour détecter des erreurs simples.
2. **LRC (Vérification de Redondance Longitudinale)** : Utilisé pour détecter des erreurs sur un bloc de caractères.
3. **Détection de plusieurs erreurs et correction** : Exemples de détection et de correction d’erreurs pour des cas spécifiques de parité.

#### Exercice 4.3 : CRC (Contrôle de Redondance Cyclique)

1. **Codage polynômial** : Basé sur l’arithmétique modulo-2 et la division polynomiale.
2. **Calcul du mot de code** : Multiplier le polynôme des données, diviser et obtenir le reste pour transmettre un mot codé.
3. **Décodage et détection** : Une erreur est détectée si le reste de la division du mot reçu ne respecte pas les règles établies par le polynôme générateur.