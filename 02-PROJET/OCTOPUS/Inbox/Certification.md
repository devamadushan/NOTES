---
tags:
  - Bug
---


Certification du serveur OCTOPUS

Dans la configuration du container Apache, situé sur le serveur Ecotron, il faut configurer la redirection de l'URL "octopus.cereep-ecotron.cnrs.fr".


Sur le serveur ECOTRON :

- Fichier "httpd-vhost.conf" :
```
<VirtualHost *:80>
    ServerName octopus.cereep-ecotron.cnrs.fr
    Redirect permanent / https://octopus.cereep-ecotron.cnrs.fr/
</VirtualHost>

<VirtualHost *:80>
    ServerName gitlab.octopus.cereep-ecotron.cnrs.fr
    Redirect permanent / https://gitlab.octopus.cereep-ecotron.cnrs.fr/
</VirtualHost>
```

- Fichier "httpd-ssl.conf" :
```
<VirtualHost _default_:443>
  ServerName octopus.cereep-ecotron.cnrs.fr
  ProxyPass / http://10.117.50.100/
  ProxyPassReverse / http://10.117.50.100/
  ProxyPreserveHost On
  ErrorLog /proc/self/fd/2
  TransferLog /proc/self/fd/1

  # HTTPS
  SSLEngine on
  # Certificates
  SSLCertificateFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_cer"
  SSLCertificateKeyFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr.key"
  SSLCertificateChainFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_interm.cer"

  <FilesMatch "\.(cgi|shtml|phtml|php)$">
    SSLOptions +StdEnvVars
  </FilesMatch>
  <Directory "/usr/local/apache2/cgi-bin">
    SSLOptions +StdEnvVars
  </Directory>
  BrowserMatch "MSIE [2-5]" \
         nokeepalive ssl-unclean-shutdown \
         downgrade-1.0 force-response-1.0
  CustomLog /proc/self/fd/1 \
          "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
</VirtualHost>

<VirtualHost _default_:443>
  ServerName gitlab.octopus.cereep-ecotron.cnrs.fr
  ProxyPass / http://10.117.50.100/
  ProxyPassReverse / http://10.117.50.100/
  ProxyPreserveHost On
  ErrorLog /proc/self/fd/2
  TransferLog /proc/self/fd/1

  # HTTPS
  SSLEngine on
  # Certificates
  SSLCertificateFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_cer"
  SSLCertificateKeyFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr.key"
  SSLCertificateChainFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_interm.cer"

  <FilesMatch "\.(cgi|shtml|phtml|php)$">
    SSLOptions +StdEnvVars
  </FilesMatch>
  <Directory "/usr/local/apache2/cgi-bin">
    SSLOptions +StdEnvVars
  </Directory>
  BrowserMatch "MSIE [2-5]" \
         nokeepalive ssl-unclean-shutdown \
         downgrade-1.0 force-response-1.0
  CustomLog /proc/self/fd/1 \
          "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
</VirtualHost>

<VirtualHost _default_:443>
  ServerName vikunja.octopus.cereep-ecotron.cnrs.fr
  ProxyPass / http://10.117.50.100/
  ProxyPassReverse / http://10.117.50.100/
  ProxyPreserveHost On
  ErrorLog /proc/self/fd/2
  TransferLog /proc/self/fd/1

  # HTTPS
  SSLEngine on
  # Certificates
  SSLCertificateFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_cer"
  SSLCertificateKeyFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr.key"
  SSLCertificateChainFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_interm.cer"

  <FilesMatch "\.(cgi|shtml|phtml|php)$">
    SSLOptions +StdEnvVars
  </FilesMatch>
  <Directory "/usr/local/apache2/cgi-bin">
    SSLOptions +StdEnvVars
  </Directory>
  BrowserMatch "MSIE [2-5]" \
         nokeepalive ssl-unclean-shutdown \
         downgrade-1.0 force-response-1.0
  CustomLog /proc/self/fd/1 \
          "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
</VirtualHost>

<VirtualHost _default_:443>
  ServerName portainer.octopus.cereep-ecotron.cnrs.fr
  ProxyPass / http://10.117.50.100/
  ProxyPassReverse / http://10.117.50.100/
  ProxyPreserveHost On
  ErrorLog /proc/self/fd/2
  TransferLog /proc/self/fd/1

  # HTTPS
  SSLEngine on
  # Certificates
  SSLCertificateFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_cer"
  SSLCertificateKeyFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr.key"
  SSLCertificateChainFile "/usr/local/apache2/certs/star_octopus_cereep-ecotron_cnrs_fr_interm.cer"

  <FilesMatch "\.(cgi|shtml|phtml|php)$">
    SSLOptions +StdEnvVars
  </FilesMatch>
  <Directory "/usr/local/apache2/cgi-bin">
    SSLOptions +StdEnvVars
  </Directory>
  BrowserMatch "MSIE [2-5]" \
         nokeepalive ssl-unclean-shutdown \
         downgrade-1.0 force-response-1.0
  CustomLog /proc/self/fd/1 \
          "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
</VirtualHost>
```

Sur le serveur OCTOPUS :

Fichier "conf/httpd.conf" :

```
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_fcgi_module modules/mod_proxy_fcgi.so
LoadModule proxy_http2_module modules/mod_proxy_http2.so
LoadModule ssl_module modules/mod_ssl.so
LoadModule socache_shmcb_module modules/mod_socache_shmcb.so

# Virtual hosts
Include conf/extra/httpd-vhosts.conf



# Secure (SSL/TLS) connections
Include conf/extra/httpd-ssl.conf

# Secure (SSL/TLS) connections
Include conf/extra/httpd-ssl.conf
```


- Fichier "httpd-vhost.conf" :
```
<virtualHost *:80>
    ServerName octopus.cereep-ecotron.cnrs.fr
	<Proxy *>
        Order allow,deny
        Allow from all
    </Proxy>
    ProxyPass / http://octopus_web:80
    ProxyPassReverse / http://octopus_web:80
    ErrorLog "logs/octopus-error_log"
    CustomLog "logs/octopus-access_log" common
</VirtualHost>

<VirtualHost *:80>
    ServerName gitlab.octopus.cereep-ecotron.cnrs.fr
	<Proxy *>
        Order allow,deny
        Allow from all
    </Proxy>
    ProxyPass / http://gitlab:33070
    ProxyPassReverse / http://gitlab:33070
    ErrorLog "logs/gitlab-octopus-error_log"
    CustomLog "logs/gitlab-octopus-access_log" common
</VirtualHost>

<VirtualHost *:80>
    ServerName vikunja.octopus.cereep-ecotron.cnrs.fr
	<Proxy *>
        Order allow,deny
        Allow from all
    </Proxy>
    ProxyPass / http://vikunja:33050
    ProxyPassReverse / http://vikunja:33050
    ErrorLog "logs/vikunja-octopus-error_log"
    CustomLog "logs/vikunja-octopus-access_log" common
</VirtualHost>

<VirtualHost *:80>
    ServerName portainer.octopus.cereep-ecotron.cnrs.fr
	<Proxy *>
        Order allow,deny
        Allow from all
    </Proxy>
    ProxyPass / http://portainer:9001
    ProxyPassReverse / http://portainer:9001
    ErrorLog "logs/portainer-octopus-error_log"
    CustomLog "logs/portainer-octopus-access_log" common
</VirtualHost>
```







26/11/2024 : ne fonctionne pas ... retombe toujours sur le site "cereep-ecotron.cnrs.fr" ...


## TODO : 
- Dans la configuration du container Apache, situé sur le serveur OCTOPUS, il faut configurer les redirections vers les différents services :
	- Vikunja : vikunja.octopus.cereep-ecotron.cnrs.fr -> 10.117.50.100:33061
	- Gitlab : gitlab.octopus.cereep-ecotron.cnrs.fr -> 10.117.50.100:
	- Portainer : portainer.octopus.cereep-ecotron.cnrs.fr -> 10.117.50.100:
