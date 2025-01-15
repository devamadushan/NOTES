---

---

## Bugs
2024/10/29 :
- à l'installation de Debian Server, impossible de terminer. L'erreur : impossible d'installer GRUB.
- Le PB est :
	- Il faut un disque dur physique pour l'installation de GRUB (programme de démarrage). Les disques durs sont montés en RAID 1 avec une configuration software et hardware.
	- Le noyau de Linux au démarrage monte ce RAID software, il n'est donc pas possible de mettre le GRUB dessus.
- La solution : installer une partition ESP (boot) sur un disque physique.
