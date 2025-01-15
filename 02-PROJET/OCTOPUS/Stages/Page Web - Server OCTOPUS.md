---
tags:
  - Stage
  - Server
  - Web
---

Cible = BTS SLAM - 2ème année
## Environnement
Le **CEREEP - Ecotron IDF**, **CE**ntre de **R**echerche en **E**cologie **E**xpérimentale et **P**rédictive est situé à Saint Pierre Les Nemours.
Cette unité d'appui et de recherche (UAR 3194), propose plusieurs dispositifs expérimentaux dédiés à la compréhension du fonctionnement des écosystèmes.
Les divers plateaux techniques peuvent être aquatiques ou terrestres, d’échelles différentes, et accueillir partenaires publics ou privés pour des collaborations ou de simples prestations de service.
L'unité met à disposition des installations techniques, de l’instrumentation et les équipes supports.
L’intérêt majeur du centre reste de prédire les modifications de la biodiversité et des écosystèmes en fonction du changement climatique.

Site web : https://www.cereep.bio.ens.psl.eu/

## Introduction
Le système **OCTOPUS** (**O**rignal **C**ontrol **T**ools f**O**r **P**rocessing and acq**U**ire **S**ystems) est un ensemble de services qui permettent de gérer principalement :
- la configuration des expériences ;
- le pilotage et l'acquisition des données des cellules climatiques ;
- le pilotage et l'acquisition de l'instrumentation spécifique aux expériences ;
- la visualisation et l'extraction des données des expériences

Les services sont installés dans des containers (technologie Docker), la liste des services disponibles sera diffusée au début du stage.
Un serveur physique installé dans la baie informatique de l'Unité est dédié à assurer la mise en place de ces différents services.

Le sujet de ce stage est de mettre en place un site Web permettant d'afficher les différentes informations d'OCTOPUS.

## Objectifs
Les **objectifs** sont les suivants :
- analyser et comprendre l'architecture système de l'existant : containers ;
- mettre en place un serveur Apache qui hébergera les différentes pages Web ;
- configurer le serveur Apache pour :
	- assurer le routage vers les différents serveurs installés (virtual hosts) ;
	- assurer la connexion HTTPS ;
- développer les différentes pages Web traitant les informations suivantes :
	- page d'accueil du Serveur OCTOPUS ;
	- connaître l'état des différents services ;
	- volumétrie du stockage pour les bases de données, les espaces disques ;
	- annuaire des services / serveurs ;
	- documentations disponibles.
- développer un ensemble de pages Web permettant de gérer les données :
	- extraction des données disponibles depuis les bases de données ;
	- visualisation succinctes des données.
- assurer la portabilité de la navigation sur différents appareils (PC, tablette, téléphone) ;
- établir la charte graphique d'OCTOPUS :
	- ensemble des icônes ;
	- ensemble de choix de polices de caractères ;
	- ensemble des palettes de couleurs.

## Attentes
Les **attentes** sont les suivantes :
- Plan de développement (Gantt, par exemple).
- Arborescence / architecture de l'ensemble des pages Web.
- Code source commenté.
- Manuel d'installation (README) de l'ensemble, avec les dépendances (librairies utilisées), les étapes à suivre.
- Manuel de la partie utilisateur (navigation).

### Technologies
Les **technologies préconisées** pour le développement sont les suivantes :
- Apache
- PHP
- HTML, CSS, JavaScript
- Bootstrap
