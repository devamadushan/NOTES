	-docker run
	-docker ps / -docker ps -a
	
	-docker run --detach --name 'Nom du Container' --env      MARIADB_ROOT_PASSWORD='MDP du Container' -p 'le port souhaité':3306 mariadb:latest 
	
	-docker exec -it 'Container Name' mariadb -u root -p
	-docker-compose up / -docker-compose up -d
	-docker-compose down -v
	-docker rm <container_id>
	-docker image -a
	-docker rmi image <nom de l'image>
	-docker exec <-t / -it> <nom du container>  /bin/bash
		-Gitlab 
			gitlab-rails console
			gitlab-ctl reconfigure

	-sudo docker restart <nom du container>
	-docker system prune -a
	-docker update --cpus="2" gitlab
	-docker stats
	-docker inspect gitlab | grep -i cpu
