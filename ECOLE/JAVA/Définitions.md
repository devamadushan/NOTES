#variables
	une variable est un nom qui fait reference a une case memoire ou une valeur est stockée , cette valeur pour changer au cours de l'execution du programme 
#expressions
	une expression permet d'exprimer un calcul 
	Evaluer une expression = calculer son resultat 
	Toute expressions a un type statique
		cela peut être une constante
		une variable
		peut être une fonction ou méthode
	
		
#porté_des_variabes
	la portée d'une variable est la zone du code ou cette variable peut etre utiliser , une varable est utiliser uniquement dans le bloc de code ou elle a été declarée et il ne peut pas y avoir deux variables au meme nom dans le meme bloc.
#Encapsulation 
		c'est le faite de regrouper au sein d'une méme entité (come une classe):
		un ensemble de donnée 
		le code permettant de le manipuler de maniére coherente
		
#Abstraction 
	le faite de séparer des spécifications communes et leur implantation
	avantages :
		une meilleur compréhension des objets.
#reutilisation/factorisation
	le fait de éviter les redondance et la duplication du code.
	agrégation : reprend les objet existant pour crée un objet plus complex 
	délegation : reprendre es objets existant pour délegué des taches
	spécalisation : héritage 
#polymorphysme
	polymorphysme permet de donner une meme interfaces a des objets ayants des propriétes ou des types differents.
#dependances-entre-objets
	Objet 01 est dépendant de l'objet 02 si l'objet 01 possédé un attribut qui référence 02
	Composition : 
		O1 construit O2 et stocke sa référence en attribut ⇒ O2 ne peut pas exister si O1 n’existe pas ou plus 
	Agrégation :
		 O1 reçoit la référence de O2 en paramètre d’un setter ou d’un constructeur et la stocke dans un attribut ⇒ O2 peut exister indépendamment de l’existence de O1 
	Délégation : 
		Les méthodes de O1 appellent les méthodes O2 ⇒ O1 utilise les fonctionnalités de O2
#references-null
	valeur par défaut de type objet qui indique que on ne référence aucune objet existant.
#final
	un attribut avec final indique que il est immuable





#membre-statique
	un membre statique d'une classe est un membre qui n'est rattaché à aucune instance de la classe mais a la classe elle même .
#package
	un package est un regroupement des classes ou interfaces permettant d'identifier de maniéré absolu un type objet.
#visibilité
	La visibilité détermine quelque partie du code peuvent accéder directement a une variable , méthode ou un type de progamme.
#tableaux
	type objet natif au langage pour manipuler un nombre fixe de variable de méme type
#String
	Type Objet de la librairie standard java modélisant une chaine de caractères.
#object
	Classe racine de la hiérarchie de héritage.
#uml
	Langage graphique de modélisation standardisé avec une approche objet offrant une quinzaine de types de diagrammes.
#heritage
	Concept permettant de déclarer une nouvelle classe (appelée classe fille ou clase délivrée) en ajoutant des caractéristique d'une autre classe existante (appelée classe mère ou super-classe)
#classe-Interne
	classe interne est une classe qui est définie dans le corps d'une autre classe dite classe englobante.
	#interne-membre
	Classe interne définie en dehors de tout corps de méthode.
	#interne-local
	classe interne définie à l'intérieur d'un bloc de code de classe englobante.
	#interne-anonyme
	une classe interne sans nom qui se définie et qui s'instancie en mémé temps et sur la mémé expression.
#classes-abstract
	Classe qui définit une implantation partielle d'une spécification mais qui ne peut pas être instanciée.
#les-interfaces
	Interface qui définit un type abstrait en spécifiant les opérations publiques qu'il offre aux codes clients.
#type-statique
	Type définit au moment de la création de la variable , elle est immuable 
	#conversion-implicite
		conversion silencieuse par le compilateur du type statique dun expression de type statique B vers un type statique A.
	#conversion-explcite
		Conversion manulle reseigné par le programmeur pour convertir une exprssion de type A en expresson de type B (cast)
#type-dynamique
	type d'instanciation de l'objet qu'une variable référence.
#lisaison
	permet de relier un appel de méthode et un impantationde cette méthode
#liaison-statique
	se produit au moment de la compiltion 
#lisaison-dynamique
	se produit au moment d l'exécution
#record
	un record permet de définir un type d'objet immuable (classe et attribut final ) qui automatise :
		- la déclaration d'attribut 
		- constructeur 
		- méthode get
		- equal
		- toString
		- hashcode
#les-collections
	objet gerant un regruppement d'objet appelés élement et se caractérise par - une interfce spécifiant ses opérations publiques
	-une implatation spécifant sa structure interne , ses contraintes et sa politique d'intéraction
#hashcode
	Méthode standard de la class Object qui permet d'identifier un objet en calculant une emprunte qu'il génere de 32 bits (int).
#interator
	Permet de parcourir l’ensemble des éléments d’une collection sans exposer sa structure interne.
	Patron de conception comportemental
#exception
	Interruption de l’exécution d’un programme à la suite d’un événement particulier
#runtime-exception
	exception dont l'exsitance du gestionnair n'est pas verifiée a la compilation
#Adapter
	Conversion d'une API interface X existante pour se conformer à une API d'interface Y attendue parle client 
#composit
	Structurer des objets pour former des hiérarchies arborescentes tout en permettant une manipulation homogène des feuilles et des nœuds.
#decorator
	Ajouter modifier dynamiquement des responsabilités à des objets
#proxy
	Utilisation d’un objet mandataire dialoguant avec un objet principal et qui offre tous les deux la même interface.
#facade
	Offrir une interface simplifiée d’un sous-système complexe d’objets