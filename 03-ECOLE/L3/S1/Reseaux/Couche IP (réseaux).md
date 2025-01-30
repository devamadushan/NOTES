
#protocole-IP
	Internet Protocol 
#datagramme
	**datagramme** est une unité de données utilisée par les protocoles sans connexion , pour transmettre des informations à travers un réseau.
	1. Le datagramme est un paquet de données autonome, envoyé d'un #émetteur à un #destinataire via le réseau.
	2. Structure
		- #en-tête 
		- Données **(payload)** : Ce sont les informations utiles (le contenu) que le datagramme transporte.
	3.Chaque datagramme peut emprunter un chemin différent à travers le réseau en fonction des conditions de routage. Les datagrammes peuvent arriver dans un ordre différent de celui où ils ont été envoyés, ou certains peuvent être perdus en chemin.
#en-tête 
	**En-tête** : Contient des informations cruciales pour le routage, comme les adresses IP source et destination, le temps de vie (TTL), et d'autres détails de contrôle.
#encapsulation 
	**encapsulation** est un concept clé dans les réseaux informatiques qui désigne le processus d'ajout d'en-têtes.
	1. Lorsque des données sont transmises sur un réseau, chaque couche du modèle ajoute ses propres informations sous forme d'en-tête (header) autour des données provenant de la couche supérieure. Ce processus d'ajout d'informations s'appelle l'encapsulation.
	2. Chaque couche ne peut voir que son propre en-tête et les données qu'elle reçoit de la couche supérieure. Elle encapsule ces données avec des informations nécessaires pour la communication et les transmet à la couche inférieure.
	- Désencapsulation
#fragments
	La **fragmentation** est le processus par lequel un datagramme IP est divisé en plus petits morceaux, appelés **fragments**, pour pouvoir être transmis sur un réseau qui impose une taille maximale pour les paquets, appelée #MUT
	1. Lorsque la taille d'un datagramme dépasse la #MTU du réseau, il est divisé en plusieurs fragments. Chaque fragment devient un #datagramme IP séparé, avec son propre en-tête IP, mais ils contiennent tous les parties du #datagramme original.
	2. Chaque datagramme a un identifiant unique. Tous les fragments d'un même datagramme original partagent le même ID.
	3. 
#MTU
#trinping
	protocole 802.1Q

durée de vie d'un paquet
#pointer
#longueur
#classe
#DNS
#Net-ID