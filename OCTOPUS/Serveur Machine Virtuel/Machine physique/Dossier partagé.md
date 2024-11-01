#installe-cd-addition 
	Aller dans :
		Périphériques 
			 Insérer l'image CD des Additions invité...
	Ouvrir un terminal :
		-sudo apt install bzip2
		-cd /media/'user'/VBox_GAs_7.'version'
		-./VBox'ISO'Additions.run
#ajoute-utilisateur-dans-vboxsf  
	Pour ajouter un utilisateur dans vboxsf ouvez le terminal:
		-groups (si l'user n’appartiens pas au groupe vboxsf):
			-sudo adduser $USER vboxsf 

Pour avoir un dossier partagé , qui relie la machine virtuelle et la machine physique : 
	1. Crée d'abord un fichier dans la machine physique (partage par exemple).
	2. Sur la machine virtuelle on #installe-cd-addition , puis #ajoute-utilisateur-dans-vboxsf et redémarrez la machine.

Problème rencontré
	Pour avoir le dossier partagé dans l'ISO (sans interface), nous avons rencontré des problèmes pour trouver l'emplacement du montage automatique. Du coup, nous avons décidé de nous orienter vers [[OpenSSH Serveur]] pour partager les dossiers/fichiers de la machine virtuelle vers la machine physique.