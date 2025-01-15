---
tags:
  - Stage
  - Server
  - NAS
---

## Contexte
Le CEREEP-Ecotron Ile-de-France est une unité d’appui et de recherche (UAR 3194) rattachée aux tutelles : CNRS et ENS, elle est située à SAINT-PIERRE-LES-NEMOURS (77).
Cette unité est une structure d’accueil et d’accompagnement de la recherche expérimentale en écologie. L'unité développe une offre diversifiée de services de recherche en écologie expérimentale et dispose actuellement de huit plateaux techniques. Elle coordonne ces différentes plateformes qui permettent de confiner et de manipuler des organismes et des écosystèmes terrestres et aquatiques dans des conditions contrôlées et largement instrumentalisées. Les plateformes sont ouvertes aux équipes publiques ou privées nationales et internationales sur le principe d'une mise à disposition des équipements, des instruments et des moyens analytiques du centre par voie de collaboration ou de prestation.

## OCTOPUS
Pour les plateformes de chambres climatiques (ECOLAB), nous avons le projet de mise en place d'un ensemble de composants logiciels et matériels qui permettent de mettre à jour le contrôle-commande-acquisition de ces installations.
Cet ensemble permettra d'assurer unitairement le bon déroulement d'une expérience dans les chambres climatiques, depuis sa mise en place, son déroulement jusqu'à la livraison des données au chercheur.

Le projet est nommé "OCTOPUS" : **O**rignal **C**ontrol **T**ools f**O**r **P**rocessing and acq**U**ire **S**ystems.

Les différents **composants** de ce projet permettent de gérer :
- le pilotage des automates ;
- le contrôle des paramètres d'expérimentation ;
- l'acquisition des différentes données ;
- le stockage et l'archivage des données ;
- la mise à disposition des données aux chercheurs ;
- le traitement, l'analyse "simple" en ligne des données.

Il est développé sur des bases "Open Source".

## OctoNAS
### Introduction
L'objectif **principal** du composant OctoNAS (**O**rignal **C**ontrol **T**ools f**O**r **N**etwork **A**ttached **S**torage) est de mettre en place un système dédié aux expériences pour le stockage et éventuellement le traitement et la visualisation des données.
Ce composant est de type **serveur**.

### Fonctionnalités
Les **fonctionnalités** principales de ce système sont les suivantes :
- Stocker les données d'une expérience.
- Gérer les accès utilisateurs et groupes.
- Disposer d'une interface Web pour :
	- administrer les droits ;
	- télécharger les données ;
	- naviguer sur les données.
- Proposer les protocoles : SMB/CIFS, (S)FTP, RSYNC, NFS, SSH.
- Enregistrer/journaliser les transferts de données.
- Proposer un cryptage/décryptage de données.
- Proposer une application cliente pour l'accès distant.
- Automatiser, pour chaque expérience :
	- la création de l'arborescence ;
	- la génération de la documentation associée aux données ;
	- la génération de programmes permettant la synchronisation des données d'une machine à une autre ;
	- la génération d'une partie du PGD (Plan de Gestion de Données).
- Dupliquer les données sur d'autres serveurs.
- Exporter l'ensemble des données d'une expérience.
- Archiver les données.
- Exécuter des scripts de traitement et d'analyse de données.
- Proposer des interfaces de visualisation des données.

Le composant pourra être composé de plusieurs logiciels / scripts, chacun ayant une fonctionnalité.

### Technologies
 Les **technologies** envisagées/proposées sont les suivantes :
 - Serveurs :
	 - NAS (OpenMediaVault ?)
	 - BDD (MariaDB)
	 - Web (Apache)
	 - API REST
	 - Représentation graphique (Grafana ?)
 - Langages de programmation :
	 - Python
	 - C, JAVA
 - Systèmes :
	 - Linux
	 - Docker
	 - RAID
 - Formats :
	 - JSON
	 - NetCDF

