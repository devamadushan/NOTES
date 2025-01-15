
#yml
	Dans : `docker-compose.yml`
```:
  app_service:
    restart: always
    container_name: my_container
    networks:
      - my_network
    hostname: my_container
    build:
      context: .
      dockerfile: Dockerfile-app
    image: <nom_image> # Remplacer par l'image de votre choix
    environment:
      # Ajoutez ici des variables d'environnement génériques ou spécifiques à votre image
      APP_ENV_VARIABLE: "default_value"
    ports:
      - "8080:80"  # Adapter les ports selon l'application
      - "4430:443"
      - "2222:22"
    volumes:
      - ./v_config:/app/config # Adapter le volume pour l'image utilisée
      - ./v_logs:/app/logs
      - ./v_data:/app/data
    logging:
      options:
        max-size: "10m"
        max-file: "5"

networks:
  my_network:
    name: 'my_network'

volumes:
  v_config:
    name: myapp_v_config
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/Vol/myapp/config'
  v_logs:
    name: myapp_v_logs
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/Vol/myapp/logs'
  v_data:
    name: myapp_v_data
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/Vol/myapp/data'

```

#env 
	Le fichier `.env` contiennent des Variables d’environnement.
		`-DB_PASSWORD = 123` 
		Exemple de fichier `.yml`
			`-MARIADB_PASSWORD: ${DB_PASSWORD}`
#Dockerfile-app
	Dans le répertoire du projet on va crée aussi un fichier **Dockerfile** ou on va garder quel application télécharger.
	Par Exemple pour installer GitLab:

	