

```yml                                                                           
version: '3.8'

services:
  apache:
    build:
      context: .
      dockerfile: dockerfile_octopus_web # httpd:latest
    container_name: octopus_web
    ports:
      - "8080:80"
    volumes:
      - /D32R5/volumes/octopus_web/sites:/usr/local/apache2/htdocs
      - /D32R5/volumes/octopus_web/conf:/usr/local/apache2/conf
      - /D32R5/volumes/octopus_web/logs:/usr/local/apache2/logs
      - /D32R5/volumes/octopus_web/certs:/usr/local/apache2/certs
    networks:
      - octopus_lan
    restart: unless-stopped

networks:
  octopus_lan:
    name: 'octopus_lan'




```