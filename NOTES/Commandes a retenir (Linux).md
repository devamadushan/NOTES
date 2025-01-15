	-man users : affiche le manuel de la commande users.
	
	-man adduser : affiche le manuel de la commande adduser.
	
	-df -h : affiche l'utilisation du disque en format lisible.
	
	-du : affiche l'utilisation de l'espace disque.
	
	-touch : crée un fichier vide.
		-touche 'chemin'/'nom-du-fishier.txt' 
		
	-chown : change le propriétaire d'un fichier ou répertoire.
		-sudo chown octopus:octopus /DATA
	-chmod +x script.sh
		
	-groups : affiche les groupes de l'utilisateur.
		Pour ajouter l'utilisateur au groupe vboxsf :
			-sudo adduser $USER vboxsf
			
	-ll : équivalent à `ls -l`, affiche les fichiers  avec détails.
	
	-rsync -r : copie récursive avec `rsync`.
		-rsync -r partage octopus@"IP":/DATA
		
	-openssh-serveur
		-sudo apt install openssh-server
		-rsync -version
		
	-cat /more : affiche le contenu d'un fichier.
		-cat 'chemin'/'fishier.txt'
		-more test.txt
	
	-sudo nano fichier.txt
	
	-mv ancien_nom_dossier nouveau_nom_dossier
	
	-rm <fichier/Dossier>  / rm -rf <fichier/Dossier> 
	
	-sudo dpkg -i <nom du fichier>
	
	ln -s <nom> /chemin/...
	
	mkdir -p /chemin/vers/mon_repertoire
