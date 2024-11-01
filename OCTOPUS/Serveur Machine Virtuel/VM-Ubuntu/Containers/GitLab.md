#yml-GitLab
	Dans : `docker-compose.yml`
```
version: "3.6"
services:
  gitlab:
    restart: always
    container_name: gitlab-rc
    networks:
      - n_gitlab_rc
    hostname: gitlab-rc
    build:
      context: .
      dockerfile: Dockerfile-gitlab-rc   #fichier
    environment:
      # Password should be set
      GITLAB_OMNIBUS_CONFIG: |        
        - gitlab_rails['initial_root_password'] = 'PASSWORD_TO_SET' 
    ports:
      - '36080:80'
      - '36443:443'
      - '36022:22'
    volumes:
      - v_config:/etc/gitlab    #raccourci du sauvegarde gitlab
      - v_logs:/var/log/gitlab  #raccourci du sauvegarde gitlab
      - v_data:/var/opt/gitlab  #raccourci du sauvegarde gitlab
    logging:
      options:
        max-size: "10m"
        max-file: "5"   #taille des logs
networks:
  n_gitlab_rc:
    name: 'n_gitlab_rc'  
volumes:
  v_config:
    name: gitlabrc_v_config
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/D2R5/gitlabrc/config' #Sauvegarde sur la hote 
  v_logs:
    name: gitlabrc_v_logs
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/D2R5/gitlabrc/logs'  #Sauvegarde sur la hote 
  v_data:
    name: gitlabrc_v_data
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/D2R5/gitlabrc/data'  #Sauvegarde sur la hote 

```

#Dockerfile-gitlab
```
FROM gitlab/gitlab-ce:rc

RUN apt update && apt -y install nano

WORKDIR /etc/gitlab
```
#git-clone 
	Avant de faire un git clone il faut initialiser `.git/`dans le Dossier
		`- git init` 
	puis cloner un projet 
		`- git clone http://<IP : Port>/<User>/<Projet>`
#git-pull
	Avant de faire un git clone il faut initialiser `.git/`dans le Dossier
		`- git init` 
	puis cloner un projet 
		`- git pull http://<IP : Port>/<User>/<Projet>`



1. Installation
	 Pour installer le Container GitLab sur Docker il faut crée un répertoire **GitLab** et créé le fichier #yml-GitLab. puis #exécuter-yml 
2. création d'espace de sauvegarde 
	Pour avoir une sauvegarde de GitLab sur la hôte , on va crée des l’arborescence comme on a indiquer dans le fichier .`yml` , `device: '/D2R5/gitlabrc/data'`
		`-sudo mkdir /D2R5/gitlabrc`
3. Client GitLab
		pour se rendre sur le Gitlab , il faut aller sur le navigateur web 
			`-http://adress-ip:port/`
4. Utilisateur
		utilisateur : root
		mdp : 20072003Deva
5. Push projects:
	1. Création du projet sur GitLab
	2. Faire un #git-clone ou #git-pull
	3. Configurer le nom et mail
		- `git config --global user.name "<nom>"`
		- `git config --global user.mail "<mail>"`
	4. Ajouter l'origin
		- `git remote add origin http://<IP : Port>/<User>/<Projet>`
	5. Creé une branch
		- `git branch <nom de la branch>`
	6. Ajouter les fichiers dans la branche 
		- `git add -A / git add <nom du fichier>`
	7. Commit
		- `git commit -m "<Commit>"`
	8. Push
		- `git push < -u / -uf > origin <branche>`


Problème rencontré 
	Vu que j'utilisais Docker sur une VM la mémoire associer a la VM n’étaient pas assez pour lancer le container GitLab. donc il fallait augmenter la mémoire pour la VM.  

