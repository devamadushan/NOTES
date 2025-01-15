## Acronyme
### Mots clefs
Original, SCADA, TANGO, Control, Acquire, Acquisition, Tools, Process, System

### Possibilités
Orignal and Common Tools fOr Processing DATA ...
Orignal and Common TOols for Processing DATA ...
Orignal and Common Tools fOr exPeriences ...
Orignal Common Tools fOr Processing and acqUire Systems
-> **O**rignal **C**ontrol **T**ools f**O**r **P**rocessing and acq**U**ire **S**ystems
SELECT User, Host FROM mysql.user;
## Outils
La liste des outils :
- Configurateur d'expériences
- Pilotage des ECOLAB
- Acquisition des ECOLAB
- Acquisition de l'instrumentation
- Archivage des données
- Synchronisation des données
- Serveur de fichiers
- Générateur de templates : documentation, code source, projet Git, etc
- Visualiseur de données
- Extracteur de données
- Générateur de site Web associé à l'expérience
- Surveillance du fonctionnement
- Générateur de climats
- Générer le PGD
- Logger de messages
- Générateur de templates
- Killer de processus
- Surveillance onduleurs
- Crypter/décrypter des données
- Outils de traitement des données en ligne.

### OctoNAS :
- **Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **N**etwork **A**ttached **S**torage
- **Rôle :** gestionnaire de données.
- **Fonctionnalités :**
	- Stockage des données.
	- Cryptage/décryptage des données.
	- Exporter des données.
	- Archiver des données.

### OctoLAB
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r ECO**LAB**
- **Rôle :** pilotage des ECOLAB.
- **Fonctionnalités :**
	- Piloter les automates.
	- Dérouler un climat dans les cellules.

### OctoWDog
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **W**atch **Dog**
- **Rôle :** surveillance du fonctionnement.
- **Fonctionnalités :**
	- Surveiller le fonctionnement des applications.
	- Surveiller le range des données.

### OctoLOG
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **Log**ger
- **Rôle :** enregistrement des logs d'applications.
- **Fonctionnalités :**
	- Centraliser les logs.
	- Enregistrer les messages d'information.
	- Restituer les logs.

### OctoLDAP
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **L**ightweight **D**irectory **A**ccess **P**rotocol
- **Rôle :** gestion des utilisateurs.
- **Fonctionnalités :**
	- Enregistrer les utilisateurs et les groupes.
	- 

### OctoDataReap
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **Data** **Reap**
- **Rôle :** récolter les données.
- **Fonctionnalités :**
	- 

### OctoClimServ
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **Clim**ate **Serv**er
- **Rôle :** gérer les climats.
- **Fonctionnalités :**
	- Ajouter, modifier, archiver et supprimer les climats.
	- Lister les climats disponibles.
	- Maintenir les liens avec les sources de données extérieures.
	- Répondre aux demandes de paramètres climatiques.

### OctoWeaSta
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **Wea**ther **Sta**tion
- **Rôle :** récolter les données des stations météo.
- **Fonctionnalités :**
	- Acquérir régulièrement les données climatiques provenant des stations météo.
	- Acquérir les statuts des stations météo.
	- Proposer la possibilité de récupérer un climat à partir d'un serveur exterieur.

### OctoChronos
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r Time
- **Rôle :** gérer les dates et heures.
- **Fonctionnalités :**
	- Fournir une horloge commune.
	- Répondre aux demandes de synchronisation horaire.

### OctoConfExper
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r **Conf**iguring **Exper**iences
- **Rôle :** gérer les expériences.
- **Fonctionnalités :**
	- Ajouter, modifier, archiver et supprimer une expérience.
	- Lister toutes les expériences.


### Gestion des données
- Event Builder
- Générer le PGD
- Liste des expériences disponibles
- Ajouter/modifier/supprimer/archiver une expérience
- Pour chaque expérience :
	- Configurer l'arborescence
	- Configurer l'espace de stockage
	- Exporter les données

### Cryptage
Liens :
- https://stacklima.com/crypter-et-decrypter-des-fichiers-a-laide-de-python/
- https://docs.aspose.com/words/fr/python-net/encrypt-a-document/

### WatchDog
Le watchdog est une application qui permet de surveiller le fonctionnement.
Les fonctionnalités sont les suivantes :
- Cohérence des données.
- Surveillance des connexions / communications.
- Données dans les ranges.
- Surveillance des processus.
- Surveillance de la présence de données.
- Prévient le personnel en charge de la maintenance.

A définir :
- Degrés de gravité.

### OctoSMS
**Acronyme :** **O**rignal **C**ontrol **T**ools f**O**r SMS
- **Rôle :** gérer les envois de SMS.
- **Fonctionnalités :**
	- Envoi le même message à plusieurs destinataires.
	- Surveiller les acquittements des messages.
	- Renvoi le message aux personnes n'ayant pas acquitté.
- **Technologies :**
	- Commandes AT
	- Modem

### Générateur de templates
Ecrire un programme qui permet rapidement de générer des fichiers dans différents langages avec les champs modifiables déjà remplis avec les bonnes valeurs.
Les **langages** de programmation seraient :
- PHP
- Python
- JavaScript
- CSS
- ...

### Générateur de climats
- Définir les paramètres de climats:
	- T°
	- H%
	- pCO2
	- PAR
	- etc.
- BDD de climats disponibles
- Ajouter/modifier/supprimer un climat
- Visualiser un climat
- Importer/exporter un climat
- Répondre à une demande de paramètre au cours du temps : `get_param(date, param)`
- Enregistrer un climat de station météo

## Tâches
- Installer un PC "instrum" par ECOLAB
- Trouver la procédure d'installation du pilote des MOXA sous Linux
- Etablir une stratégie de gestionnaire de tâches : Anacron / Cron / Crontab

## Liens
### Moniteur
- Uptime Kuma : https://github.com/louislam/uptime-kuma
### Climats
La NASA fournit une API qui permet d'accéder aux données climatiques.
Les **liens** sont les suivants :
- Point d'entrée : https://power.larc.nasa.gov/docs/services/api/
- Tutoriels : https://power.larc.nasa.gov/docs/tutorials/service-data-request/api/
- Manager : https://power.larc.nasa.gov/api/pages/?urls.primaryName=Manager
- Communautés : https://power.larc.nasa.gov/docs/methodology/communities/

Les **prévisions** de climats :
- DRIAS
- IPCC WGI

### Langages
- WASMER : 

### Markdown
Les liens pour Python et Mardown sont les suivants :
- https://towardsdatascience.com/building-a-python-cli-tool-to-extract-the-toc-from-markdown-files-ab5a7b9d07f2
- https://pypi.org/project/pypandoc/

### Format netCDF
- netCDF, format de fichier interopérable pour la science ouverte : https://callisto-formation.fr/course/view.php?id=257
- https://doranum.fr/2023/06/08/nouveau-parcours-pedagogique-netcdf-format-de-fichier-interoperable-pour-la-science-ouverte/
- Interface graphique : https://github.com/Xavier-LOG/log_genifair_project

### Autres
- Licence : https://en.wikipedia.org/wiki/Open-source_hardware
- Liste de **services auto-hébergés** :
	- https://www.reddit.com/r/selfhosted/comments/zwcns3/most_used_selfhosted_services_in_2022/?tl=fr
	- https://github.com/awesome-selfhosted/awesome-selfhosted
