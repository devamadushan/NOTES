---
tags:
  - OpenSSH
  - Installation
---

### Installation
Pour Installer **openSsh** il faut d'abord passer en mode #su puis 
	`apt install openssh-server` 

### Configuration 
SSH sans mot de passe
	Pour se connecter au serveur SSH (Server-Octopus) sans mot de passe, nous devons générer une clé SSH sur notre machine avec la commande :
		- `ssh-keygen -t rsa` 
	résulta de la commande :
		`Generating public/private rsa key pair.`
		`Enter file in which to save the key (/home/octopus/.ssh/id_rsa):`
	Faite entrée
	résulta de la commande :
		`Enter passphrase (empty for no passphrase):` 
	vous pouvez laisser le champ vide (si vous souhaitez créer une connexion SSH sans mot de passe) ou entrer un mot de passe, puis appuyer sur Entrée. et confirmer votre reponse.
	Sécurisé votre clé priver : 
		Allez dans le dossier :
		-`cd /home/x/.ssh/`    ==*x = votre utilisaeur*==
		 Modifiez les permissions de votre clé privée :
		- `chown 400 id_rsa`
	Copiez votre clé publique vers le serveur :
		- `ssh-copy-id y@host`    *==y = utilisateur de octopus  ==* *==host = adress ip==* 
	et entée le mot de passe de Server Octopus.
	[[SSH sans mot de pass.canvas|SSH sans mot de pass]]


