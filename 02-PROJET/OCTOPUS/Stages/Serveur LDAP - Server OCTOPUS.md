---
tags:
  - Stage
  - LDAP
  - Server
---

Cible = BUT Fontainebleau

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

Le sujet de ce stage est de mettre en place un serveur permettant de gérer les utilisateurs des différents services d'OCTOPUS.

## Objectifs
Les **objectifs** sont les suivants :
- analyser et comprendre l'architecture système de l'existant : containers ;
- analyser et comprendre l'architecture de la technologie LDAP ;
- mettre en place un serveur de LDAP qui permettra de gérer les utilisateurs et les groupes ;
- configurer le serveur LDAP pour :
	- assurer l'enregistrement des utilisateurs et des groupes ;
	- assurer la connexion sécurisée (certification) ;
- tester le serveur avec différents services tels que : GitLAB, Vikunja, etc. ;
- tester plusieurs solutions d'interface d'administration graphique (si possible) pour le serveur LDAP.

## Attentes
Les **attentes** sont les suivantes :
- Plan de développement (Gantt, par exemple).
- Description succincte des mécanismes de LDAP.
- Code source commenté.
- Manuel d'installation (README) de l'ensemble, avec les dépendances (librairies utilisées), les étapes à suivre.
- Manuel de la partie utilisateur (navigation).

### Technologies
Les **technologies préconisées** pour le développement sont les suivantes :
- LDAP
- Docker

## Liens :
- Différences entre LDAP et OAuth2 : https://www.geeksforgeeks.org/difference-between-ldap-and-oauth-2/
- 