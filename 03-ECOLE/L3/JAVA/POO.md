
#Encapsulation
	Classes
		1. peut encapsuler une liste d'attribut .
		2. peut encapsuler une liste de (méthodes Constructeur).
		3. peut encapsuler d'autres classe.
		Exemple:
			`public class Voiture {` 
			`// 1. Encapsulation d'une liste d'attributs` 
				`private int id; // Nouvel attribut 'id'` 
				`private String marque;` 
				`private Moteur moteur;`
			`// 2. Encapsulation d'une liste de constructeurs` 
				`public Voiture(int id, String marque, String typeMoteur, int puissance) {` 
					`this.id = id; // Initialisation de l'attribut 'id'` 
					`this.marque = marque;` 
					`this.moteur = new Moteur(typeMoteur, puissance);`  
				`}` 
			`// Méthode pour afficher les détails de la voiture` 
				`public String getDetailsVoiture() {` 
					`return "Voiture ID: " + id + ", Marque: " + marque + ", Moteur: " + moteur.getDetailsMoteur();` 
				`}`
	Package
		**Packages** : En Java, un package est un ensemble de classes et d'interfaces
#Abstraction
	Classe Abstract
		1. Contient au moins une méthode **Abstact**,
		2. Définie aussi avec le mot java abstract
		3. Utilisée uniquement pour être hérité 
		4. On ne peut pas crée des objets a partir de cette classe
		5. Sa sous-classe donnera un corps aux méthodes abstraites en les redéfinissant.
			`abstract class Animal { // Méthode abstraite sans paramètre public abstract void makeSound(); }`
	Méthode Abstract
		1. elle n'a pas de corps , Juste une en-téte
		2. Doit être définie avec un mot **abstract**
			-`public abstract void makeSound();`
		3. Cette méthode sera redéfinie dans une sous-classe qui lui donnera  un corps
			`@Override 
			`public void makeSound() {`
			 `System.out.println(name + " aboie.");` 
			 `}`
#Réutilisation/factorisation
#Polymorphisme