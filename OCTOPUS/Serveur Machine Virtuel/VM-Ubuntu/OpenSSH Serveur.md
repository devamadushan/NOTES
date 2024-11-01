#installer-openssh
	`-sudo apt install openssh-server`
#Rsync
	Pour communiquer avec un serveur il faut d'abord installé rsync:
		`-sudo apt install rsync`
	rsync #option 'répertoire' hostName@IP:/'chemin vers le répertoire' 
		`-rsync -r partage deva@10.10.10.10:/DATA`
#option
	-r : copie récursive (inclut les sous-répertoires)
	-a : archive (conserve les permissions, les timestamps, etc.)
	-av : mode verbeux (affiche les détails pendant le transfert)


1. Installation du OpenSSH
	1. Une fois qu'on a #installer-openssh sur la machine virtuelle ou physique, on peut essayer de communier avec le serveur en installant #Rsync 
2. Connecter avec le serveur SSH
	uns fois que on a #installer-openssh  ,sur le client il faut taper la	commande suivante :
		-ssh **nom de la machine**@**adress ip**
