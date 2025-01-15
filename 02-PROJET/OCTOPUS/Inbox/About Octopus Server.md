- IP : 10.117.50.100 (fixe)
- URL : octopus.cereep-ecotron.cnrs.fr
- DMZ ou LAN
- OS : Debian(12) Server
- Stockages :
	- OS : RAID 1 logiciel
	- DATA : RAID 5 matériel

### Arborescence
```
/D32R5
	volumes
		gitlab
		mariadb
		portainer
		vikunja
		...
	containers
		vikunja
		gitlab
		mariadb
		portainer
		...
	share
		Documentation
		coffre
		Notes
		Guide
```

### Utilisateurs
- [[Pattern Login octopus.canvas|Pattern Login octopus]]
- [[Liste Users]]

