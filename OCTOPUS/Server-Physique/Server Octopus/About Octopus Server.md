IP : 10.117.50.100 (fixe)
URL  octopus.cereep-ecotron.cnrs.fr
DMZ ou LAN
OS : Debian(12) Server
Users : ACL
Stockage : R5

### Arborescence
```
/D32R5
	volumes
		vikunja
		gatlab
		mariadb
		portainer
	containers
		vikunja
			.docker-compose.yml
		gitlab
			.docker-compose.yml
		mariadb
			.docker-compose.yml
		portainer
			.docker-compose.yml
	users_share
		coffre
		Guide
```

### Utilisateurs
[[Pattern Login octopus.canvas|Pattern Login octopus]]
#### Les Utilisateur

| Login    | MDP      |
| -------- | -------- |
| root     | octopus  |
| octopus  | octopus  |
| dthevara | dthevara |
| schollet | schollet |
|          |          |
|          |          |
|          |          |

