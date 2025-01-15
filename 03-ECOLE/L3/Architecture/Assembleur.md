#type-data
	- word
		- 4 Octet
	- half
		- 2 Octet
	- byte
		- 1 Octet
	- space(n)
		- Alloue un espace de `n` octets dans la mémoire, mais ne les initialise pas. La mémoire allouée contiendra des zéros.
	- aligne(n)
		- Déplace le cruor  
			- 0 : aligne à 1 octet (aucun déplacement si déjà à une adresse impaire).
			- 1 : aligne à 2 octets (adresse paire)
			- 2 : aligne à 4 octets (multiples de 4).
			- 3 : aligne à 8 octets (multiples de 8).
	- asciiz(chaine de caractère)
		- Alloue de la mémoire pour une chaîne de caractères et ajoute un caractère nul
	- ascii(chaine de caractère)
		- Alloue de la mémoire pour une chaîne de caractères sans ajouter de caractère nul à la fin.
#valeur-communes
	- 1
		- Afficher un entier (avec `$a0` contenant l'entier)
	- 4
		- Afficher une chaîne (avec `$a0` contenant l'adresse de la chaîne)
	- 5
		- Lire un entier et le stocker dans `$v0`
	- 10
		- Terminer le programme
	- 11
		- Afficher un caractère (avec `$a0` contenant le caractère)
	- 12
		- Lire un caractère
#registre-de-base-Mips
	- $8 - $15 : registre temporaire 
#instructions
	- la
	- lw
	- li
	- lui
	- addi 
	- move
Pour coder en assembleur on a 2 section `.data` et `.text`

```
.data
n: .word 10          # Déclare une variable n et l'initialise à 10
ch: .asciiz "Hello"  # Déclare une chaîne de caractères "Hello"

.text
li $v0, 4          # Charger 4 dans $v0 (service d'affichage)
la $a0, ch        # Charger l'adresse de la chaîne dans $a0
syscall            # Appeler le système pour afficher la chaîne

```