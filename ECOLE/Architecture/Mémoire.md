#octet
	Un **octet** est une unité de base de stockage de données en informatique, composée de **8 bits**.
#mot
#Endian (boudien)
	#little-endian
		Le **Little Endian** est une méthode d'organisation des données dans la mémoire où les **octets les moins significatifs** (le moins grand) d'un nombre sont stockés en premier (à l'adresse mémoire la plus basse).
	big endian
		Le **Big Endian** est l'opposé du Little Endian. C'est une méthode d'organisation des données en mémoire où les **octets les plus significatifs** (le plus grand)
#capacité-de-stockage
	- 1 kilo-octet ou 1 Kio = 210 = 1 024 octets
	- 1 mega-octet ou 1 Mio = 220 = 1 048 576 octets
	- 1 giga-octet ou 1 Gio = 230 octets
	- 1 tera-octet ou 1 Tio = 240 octets	


L'architecture mémoire stocke et organise les données en petites unités appelées octets ou mots, avec des niveaux de vitesse différents, du plus rapide (proche du processeur) au plus lent (stockage à long terme).


![[Pasted image 20241010220101.png]]

Transfert entre la mémoire et le processeur

Le processeur effectue plusieurs types de transferts avec la **RAM**:
1. Lecture de données
2. Ecriture de données
3. Gestion des instructions
4. Stockage temporaire
![[Pasted image 20241010221919.png]]
- Si le processeur ->memoire alors c'est une #ecriture ou un Store.
- Si mémoire → processeur alors c’est une #lecture ou un load (chargement).