## Introduction
L'idée est de développer une application, ou une série d'outils qui permettent de pré-configurer une expérience ou un projet.

## Fonctionnalités
### Introduction
Les **fonctionnalités** possibles sont les suivantes :
- Création d'une arborescence liée à l'expérience, au projet
- Pré-configuration des noms de dossiers
- Pré-configuration du système de version : Git
- Ajout des fichiers de base :
	- README
	- LICENCE
	- INSTALL
- Possibilité d'utiliser des Templates par un outil pour un langage de programmation, une documentation, etc.
- Configuration de la synchronisation vers l'extérieur

## DATA
### Type
Selon le type de plateforme / ressource utilisée, il faut créer l'arborescence liée, par exemple pour ECOLAB :
- DATA
	- ECOLAB1
		- CELL1
		- CELL2
		- ...
	- ECOLAB3
		- CELL2
		- CELL3
		- ...

### Nextcloud
Les possibilités sous **Nextcloud** sont :
- Créer un répertoire lié au projet, à l'expérience
- Créer un groupe (?) un utilisateur pour se connecter
- Créer un utilisateur spécifique aux programmes d'acquisition / transfert de données
- Créer un programme Python qui synchronise automatiquement les données acquises

### ISIA
Les possibilités d’interactions avec ISIA sont les suivantes :
- Demander la liste des projets / expériences déjà disponibles
- Renseigner automatiquement les "logs" d'une expérience / projet
- Créer un utilisateur "générique" par expérience pour la partie automatisation

## Liens
### Générateurs
Les **liens** sont les suivants :
- Générateur de template : https://github.com/pyscaffold/pyscaffold
- Générateur de page Web : https://pypi.org/project/wbuilder/
- String Template Python : https://docs.python.org/3/library/string.html

### Nextcloud API
Les **liens** sont les suivants :
- Developper : https://docs.nextcloud.com/server/latest/developer_manual/index.html
- API : https://docs.nextcloud.com/server/latest/developer_manual/digging_deeper/api.html
- Python Nextcloud API :
	- https://pypi.org/project/nextcloud-orm/
	- https://github.com/cloud-py-api/cloud_py_api
	- https://github.com/luffah/nextcloud-API
	- https://github.com/pragmaticindustries/pyncclient
- Python requests : https://docs.python-requests.org/en/latest/index.html

## Climats
### Climat NASA
La NASA fournit une API qui permet d'accéder aux données climatiques.
Les **liens** sont les suivants :
- Point d'entrée : https://power.larc.nasa.gov/docs/services/api/
- Tutoriels : https://power.larc.nasa.gov/docs/tutorials/service-data-request/api/
- Manager : https://power.larc.nasa.gov/api/pages/?urls.primaryName=Manager
- Communautés : https://power.larc.nasa.gov/docs/methodology/communities/
- DATA VIewer : https://power.larc.nasa.gov/data-access-viewer/
### Prévisions climats
- DRIAS
- IPCC WGI
### Markdown
Les liens pour Python et Mardown sont les suivants :
- https://towardsdatascience.com/building-a-python-cli-tool-to-extract-the-toc-from-markdown-files-ab5a7b9d07f2
- https://pypi.org/project/pypandoc/

## Procédure
La procédure en fin d'expérience :
- Scanner le cahier de laboratoire, en PDF
- Placer le fichier "Cahier-Laboratoire_YYYY-MM-DD.pdf" dans le bon dossier

## TODO
La liste des choses à faire sont les suivantes :
- [ ] 