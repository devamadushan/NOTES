#ip 
	%
	10.118.10.10
	127.0.0.1 / localhost

| SQL                                                                                           |                                                                              |
| --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| CREATE DATABASE 'Nom de la Base de Donnée';                                                   | Pour crée une base de donnée                                                 |
| CREATE USER 'User Name'@' #ip' IDENTIFIED BY 'MDP';                                           | Pour crée un utilisateur                                                     |
| GRANT ALL PRIVILEGES ON **BDD**`.*` TO 'utilisateur'@' #ip';<br>                              | Pour donner tout les droits sur une BDD a un utilisateur que on souhaite.    |
| GRANT ALL PRIVILEGES ON `*.*` TO 'utilisateur'@' #ip';<br>                                    | Pour donner tout les droit sur tout les BDD a l'utilisateur que on souhaite. |
| USE 'BDD';                                                                                    | Pour utiliser une Base de donnée                                             |
| SELECT User, Host FROM mysql.user;<br>                                                        |                                                                              |
| DROP USER 'utilisateur'@'%';                                                                  |                                                                              |
| RENAME USER 'root'@'ancien_ip' TO 'root'@'nouvelle_ip';<br>                                   |                                                                              |
| GRANT ALL PRIVILEGES ON *.* TO 'test'@'localhost' WITH GRANT OPTION;<br>FLUSH PRIVILEGES;<br> |                                                                              |
| DROP DATABASE nom_de_la_base_de_données;<br>                                                  |                                                                              |
