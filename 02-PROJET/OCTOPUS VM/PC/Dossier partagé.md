#installe-cd-addition 
	1.Aller dans le menu :
	    - **Périphériques**
	    - **Insérer l'image CD des Additions invité...**
	2. Ouvrir un terminal :
		-` sudo apt install bzip2`
		- `cd /media/<<user>>/VBox_GAs_7.<<version>>
		- `./VBox<<ISO>>Additions.run`
#ajoute-utilisateur-dans-vboxsf  
	Pour ajouter un utilisateur au groupe `vboxsf`, ouvrez un terminal et tapez :
		- `groups` 
	 Si l'utilisateur n'appartient pas au groupe `vboxsf` :
		- `sudo adduser $USER vboxsf` 

### Partager un dossier entre la machine virtuelle et la machine physique
1. **Créer un dossier partagé** dans la machine physique (par exemple, un dossier nommé `partage`).
 2. Suivre les étapes de #installe-cd-addition. ,
 3. puis #ajoute-utilisateur-dans-vboxsf et redémarrez la machine.

### Problème rencontré

Lors de la configuration du dossier partagé dans un environnement **sans interface graphique** (via ISO), nous avons eu des difficultés à localiser l'emplacement du montage automatique.  
En conséquence, nous avons décidé d'utiliser **[[OpenSSH Serveur]]** pour partager les dossiers et fichiers entre la machine virtuelle et la machine physique.