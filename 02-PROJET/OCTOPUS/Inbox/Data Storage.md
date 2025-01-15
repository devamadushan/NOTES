## Introduction
Les données des expériences proviennent de différentes sources :
- ECOLAB - ECOCUBE
- Instrumentation

Pour enregistrer les données depuis des installations distantes, il est nécessaire :
- Connecter sur le réseau les éléments qui vont pousser les données sur le serveur.
- Utiliser les outils de base, de préférence, pour synchroniser les données : `rsync` par exemple.

Les transferts de données seront assurés par un utilisateur spécifique : `octodata`.
Un services Web permettra aux utilisateurs de visualiser ces données à travers une arborescence.
Chaque utilisateur qui pourra accéder aux données devra disposer d'un login.
Ce login peut être lié à l'expérience (nom de l'expérience).

Avec l'utilitaire `rsync` : il est nécessaire de l'installer sur le serveur distant :
```
su
apt install rsync
```

## Codes :
Pour accéder avec `rsync` en `ssh` :
`rsync -av -e ssh /local/path/ user@remote:/remote/path/`

## Liens :
- File browser sur page Web : https://filebrowser.org/

