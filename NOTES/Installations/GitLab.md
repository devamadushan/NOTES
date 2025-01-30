


```txt
FROM gitlab/gitlab-ce:rc

RUN apt update && apt -y install nano

WORKDIR /etc/gitlab

```




```yml                                                                            
version: "3.6"
services:
  gitlab:
    restart: always
    container_name: gitlab
    networks:
      - gitlab
    hostname: gitlab
    build:
      context: .
      dockerfile: dockerfile_gitlab
	environment:
      GITLAB_OMNIBUS_CONFIG: |        
        - gitlab_rails['initial_root_password'] = '124356Gitlab'
    ports:
      - '33070:80'
      - '33071:443'
      - '33072:22'
    volumes:
      - /D32R5/volumes/gitlab/config:/etc/gitlab
      - /D32R5/volumes/gitlab/logs:/var/log/gitlab
      - /D32R5/volumes/gitlab/data:/var/opt/gitlab
    logging:
      options:
        max-size: "10m"
        max-file: "5"
networks:
  gitlab:
    name: 'gitlab'
```


```rb
puma['worker_processes'] = 2
sidekiq['concurrency'] = 10





gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.biologie.ens.fr"
gitlab_rails['smtp_port'] = 465
gitlab_rails['smtp_user_name'] = "serv3194"
gitlab_rails['smtp_password'] = "ip=VK=3a3J"
gitlab_rails['smtp_domain'] = "bio.ens.psl.eu"
gitlab_rails['smtp_authentication'] = "login"
gitlab_rails['smtp_enable_starttls_auto'] = false
gitlab_rails['smtp_tls'] = true
#gitlab_rails['smtp_openssl_verify_mode'] = 'peer'


gitlab_rails['gitlab_email_enable'] = true
gitlab_rails['gitlab_email_from'] = 'server.uar3194@bio.ens.psl.eu'
gitlab_rails['gitlab_email_display_name'] ='Gitlab'
gitlab_rails['gitlab_email_reply_to'] = 'server.uar3194@bio.ens.psl.eu'

external_url 'http://octopus.cereep-ecotron.cnrs.fr'


```

