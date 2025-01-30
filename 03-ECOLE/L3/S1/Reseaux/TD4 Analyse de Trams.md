
### 1. Compréhension des champs de la trame MAC IEEE 802.3

- **Adresse de destination et d'origine (MAC)** : 48 bits pour chaque adresse ; savoir identifier et extraire ces adresses.
- **Champ de longueur** : indique la longueur des données encapsulées, et non pas celle de la trame entière. Cela permet d’identifier le début des données LLC.
- **Données LLC (Logical Link Control)** : le contenu de la trame qui inclut des informations spécifiques sur le protocole supérieur utilisé, comme STP.
- **Bourrage (Padding)** : vérifier si les données sont complétées pour atteindre une longueur minimale et calculer la longueur des données utiles en tenant compte de cette possibilité.

### 2. Analyse des adresses MAC et leur identification

- **Extrait d’adresse constructeur (OUI)** : les trois premiers octets de l’adresse MAC sont souvent spécifiques à un constructeur (ex. Cisco, Intel) ; connaître les principaux OUIs pour l’interprétation.
- **Adresses de diffusion** : connaître les adresses multicast et leur signification (ex. adresse 01-80-C2-00-00-00 pour le protocole STP).
- **Destination de la trame** : identifier si la trame est destinée à une machine spécifique ou à un groupe, et comprendre les cas de multicast et de broadcast.
### 3. Champs LLC

- **SAP (Service Access Point)** : points d’accès qui identifient le protocole de couche supérieure (ex. STP) ; savoir localiser et interpréter ce champ.
- **Type de trame LLC (Information, Supervision, Non-numérotée)** : analyser le champ de contrôle pour déterminer si la trame contient des informations, des commandes de contrôle ou des données non-numérotées.
### 4. Différences entre IEEE 802.3 et Ethernet

- **Champ Length vs. Type** : dans IEEE 802.3, le champ ‘‘Length’’ spécifie la longueur des données ; en Ethernet, ce champ est remplacé par ‘‘Type’’ pour indiquer le protocole (ex. 0x0800 pour IP, 0x0806 pour ARP).
- **Distinction entre Ethernet et 802.3** : une carte réseau compatible doit différencier les deux formats de trame pour gérer les champs correctement.
### 5. Interprétation des trames Ethernet

- **Capture et affichage de trames** : analyse des octets capturés par Wireshark ou tcpdump, lecture des données brutes, et interprétation des adresses et des champs.
- **Champ Type dans Ethernet** : savoir interpréter ce champ pour reconnaître le protocole supérieur (ex. IP, ARP).
- **Longueur des données utiles en cas de bourrage** : comprendre comment est calculée cette longueur en MAC, malgré l’ajout de bourrage, et vérifier si cela peut compromettre l’architecture en couches.