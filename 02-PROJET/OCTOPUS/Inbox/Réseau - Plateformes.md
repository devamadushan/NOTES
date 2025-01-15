---
tags:
  - Reseau
  - ECOLAB
  - ECOCUBE
  - VLAN
---
## DATA 4G
Une carte SIM est installée dans le routeur de l'ECOCUBE, les informations sont les suivantes :
- Numéro de téléphone : 0629603411
- Adresse IP du routeur : 192.168.0.1
- Login / password : admin/admin

## VLAN
Tous les VLAN sont déclarés sur le réseau interne du site, ils sont gérés par le routeur pfSense.
### Plateformes
Les plateformes ECOLAB et ECOCUBE sont configurées sur un **VLAN** particulier, il y a un VLAN par plateforme.
Ces VLAN ont pour configuration :
- Adresses IP : 10.119.**E**0.XXX
- Masque : 255.255.255.0
- Passerelle : 10.119.**E**0.1
Avec : **E** = Numéro d'ECOLAB, **6** = ECOCUBE

### Instrumentation
Les périphériques d'instrumentation sont configurés sur un **VLAN** particulier, selon la plateforme sur laquelle ils sont utilisés.
Ces VLAN ont pour configuration :
- Adresses IP : 10.119.**E**1.XXX
- Masque : 255.255.255.0
- Passerelle : 10.119.**E**1.1
Avec : **E** = Numéro d'ECOLAB, **6** = ECOCUBE

## Adresses IP
### Supervision
Les **adresses IP** de chaque **PC** de **Supervision** des ECOLAB sont les suivantes :

| Plateforme | Adresse IP    | Utilisateur    |
| ---------- | ------------- | -------------- |
| ECOLAB 1   | 10.119.10.100 | ECOLAB-1       |
| ECOLAB 2   | 10.119.20.100 | Administrateur |
| ECOLAB 3   |               |                |
| ECOLAB 4   | 10.119.40.100 | SIMON          |
| ECOLAB 5   |               |                |

### Instrumentation
Les **adresses IP** de chaque **PC** d'**Instrumentation** sont les suivantes :

| Plateforme | Périphérique | Adresse IP   | Utilisateur |
| ---------- | ------------ | ------------ | ----------- |
| ECOLAB 4   | PC Spectro   | 10.119.41.41 | ecotron     |

## Connexion à distance
La connexion à distance est possible par le **protocole RDP** (Remote Desktop Protocol).

Les applications utilisables sont les suivantes :
- Remmina : utilisable sous Linux.
- Bureau à distance : utilisable sous Windows.
- AnyDesk : dans le cas où le PC n'est pas sur le réseau interne du site.

