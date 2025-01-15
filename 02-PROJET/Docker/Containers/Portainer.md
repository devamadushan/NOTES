
```yml
version: '3.8'

services:
  portainer:
    image: portainer/portainer-ce
    container_name: portainer
    ports:
      - "9001:9000"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /D32R5/volumes/portainer:/data
    restart: always
    networks:
      - octopus_lan
networks:
  octopus_lan:
    name: 'octopus_lan'

```