#yml-Portainer
	Dans : `docker-compose.yml`
```
	version: '3'
	services:
		portainer:
		    image: portainer/portainer-ce
		    ports:
			      - 8080:9000
		    volumes:
			      - /var/run/docker.sock:/var/run/docker.sock
			      - portainer_data:/data
		    restart: always
	volumes:
	portainer_data:
```

1. Installation
	 Pour installer Portainer dans un container ,nous avons juste crée un Dossier **Porntainer** et un fichier .`yml` dans le Dossier.Puis #exécuter-yml .
2. Client Portainer
	Pour se rendre sur l'interface de Portainer
	1. je me suis connecter à la VM a l'aide de [[OpenSSH Serveur]] depuis  a machine physique,
	2. Sur la barre de recherche du client :
		`-http://'adress-ip':port`
3. Utilisateur 
	User :admin 
	mdp : 20072003Devama