# Méthodes

- **Signature d'une méthode** : Le nom de la méthode et les types des arguments.
    
- **En-tête d'une méthode** : La visibilité, le type de retour, le nom de la méthode, et les arguments.
    
- **Surcharge** : Déclarer une méthode avec le même nom mais des types ou un nombre d'arguments différents.
    
- **Redéfinition** : Réimplémenter la méthode de la mère en changeant uniquement le corps de la méthode.
    
- **Masquage** : Lorsque des méthodes statiques ont le même nom dans la classe fille et la classe mère, le choix est fait en fonction du type statique.
    

# Visibilité

- **Public** : Niveau de visibilité ouvert à tout le monde.
    
- **Package** : Niveau de visibilité restreint aux classes du même package (par défaut, sans modificateur explicite).
    
- **Protected** : Niveau de visibilité accessible à la classe elle-même, à ses filles, et aux classes du même package.
    
- **Private** : Niveau de visibilité très restreint, accessible uniquement à la classe elle-même.
---

### **Héritage**

1. **Empêcher une classe d'être héritée :**
    
    - Utiliser le mot-clé **`final`** sur la classe.
    - Exemple :
        
        ```java
        final class Exemple {
            // Cette classe ne peut pas être héritée
        }
        ```
        
2. **Appel au constructeur parent :**
    
    - Utiliser **`super()`** pour appeler le constructeur de la classe parente.
    - Obligatoire si la classe parente n'a pas de constructeur sans paramètre.
    - Exemple :
        
        ```java
        class Parent {
            Parent(String message) {
                System.out.println(message);
            }
        }
        
        class Enfant extends Parent {
            Enfant(String message) {
                super(message); // Appel au constructeur parent
            }
        }
        ```
        
3. **Accès à une méthode ou un attribut parent masqué :**
    
    - Utiliser **`super.nomDeLaMéthode()`** pour appeler une méthode de la classe parente redéfinie dans la classe fille.
4. **Héritage multiple :**
    
    - Interdit en Java pour éviter les conflits et le "problème du diamant".
    - Alternative : utiliser plusieurs **interfaces**.
5. **Constructeur privé :**
    
    - Une sous-classe ne peut pas appeler un constructeur **`private`** de la classe parente.
    - Les constructeurs privés sont souvent utilisés dans les **design patterns** comme le singleton.

---

### **Polymorphisme**

1. **Redéfinition de méthodes (Overriding) :**
    
    - Une classe fille peut redéfinir une méthode de la classe parente avec la même signature.
    - La version de la méthode à exécuter est déterminée à l'exécution (à partir du type dynamique).
2. **Surcharge de méthodes (Overloading) :**
    
    - Déclarer plusieurs méthodes avec le même nom mais des paramètres différents (nombre ou type).
    - Résolu à la compilation.
3. **Masquage (Hiding) des méthodes `static` :**
    
    - Si une méthode `static` a le même nom dans une classe parente et une classe fille, la méthode à exécuter est déterminée à la compilation (à partir du type statique).
    - Exemple :
        
        ```java
        class Parent {
            static void afficher() {
                System.out.println("Parent");
            }
        }
        
        class Enfant extends Parent {
            static void afficher() {
                System.out.println("Enfant");
            }
        }
        
        public class Main {
            public static void main(String[] args) {
                Parent obj = new Enfant();
                obj.afficher(); // Affiche : Parent
            }
        }
        ```
        
4. **`instanceof` :**
    
    - Vérifie si un objet est une instance d’une classe ou d’une interface.
    - Retourne **`true`** si l’objet est de la classe spécifiée ou d’une de ses sous-classes.
    - Exemple :
        
        ```java
        Parent parent = new Enfant();
        System.out.println(parent instanceof Parent); // true
        System.out.println(parent instanceof Enfant); // true
        ```
        
5. **Accès aux méthodes filles via une référence parent :**
    
    - Impossible sans cast explicite.
    - Exemple :
        
        ```java
        Parent parent = new Enfant();
        if (parent instanceof Enfant enfant) {
            enfant.methodeSpecifique();
        }
        ```
        

---

### **Interfaces**

1. **Méthodes avec implémentation dans une interface :**
    
    - Depuis **Java 8**, les interfaces peuvent avoir :
        - Des méthodes **`default`** avec une implémentation par défaut.
        - Des méthodes **`static`** avec une implémentation.
    - Depuis **Java 9**, elles peuvent avoir des méthodes **`private`** pour factoriser du code interne.
2. **Pourquoi utiliser ces méthodes dans une interface ?**
    
    - Éviter de casser les classes existantes lorsqu'on ajoute une nouvelle fonctionnalité à une interface.
3. **Exemples :**
    
    - **Méthode `default` :**
        
        ```java
        interface Animal {
            default void manger() {
                System.out.println("L'animal mange.");
            }
        }
        
        class Chien implements Animal {}
        
        public class Main {
            public static void main(String[] args) {
                Animal chien = new Chien();
                chien.manger(); // Affiche : L'animal mange.
            }
        }
        ```
        
    - **Méthode `static` :**
        
        ```java
        interface Animal {
            static void info() {
                System.out.println("Ceci est une méthode statique d'une interface.");
            }
        }
        
        public class Main {
            public static void main(String[] args) {
                Animal.info();
            }
        }
        ```
        
    - **Méthode `private` :**
        
        ```java
        interface Animal {
            private void helper() {
                System.out.println("Code interne de l'interface.");
            }
        
            default void afficher() {
                helper();
                System.out.println("Affichage depuis l'interface.");
            }
        }
        
        class Chien implements Animal {}
        
        public class Main {
            public static void main(String[] args) {
                Animal chien = new Chien();
                chien.afficher();
            }
        }
        ```
# Résumé des concepts Java par cours

## **Cours 1 : Les bases de Java**

### **Variables et expressions**
- Une **variable** est un nom qui fait référence à une case mémoire où une valeur est stockée.
- Une **expression** permet de calculer une valeur et a un type statique (constante, variable, méthode, etc.).

### **Portée des variables**
- La portée est la zone du code où une variable est accessible.
- Une variable déclarée dans un bloc ne peut pas être utilisée en dehors de ce bloc.

### **Visibilité**
- **Public** : Accessible de partout.
- **Protected** : Accessible par les classes filles et les classes du même package.
- **Package (défaut)** : Accessible uniquement dans le même package.
- **Private** : Accessible uniquement dans la classe.

### **Classes immuables**
- Une classe immuable est une classe dont les instances ne peuvent pas être modifiées après leur création.
- Pour créer une classe immuable :
  - Champs `final`.
  - Pas de setters.
  - Constructeur qui initialise tous les champs.

### **Exceptions**
- **Checked Exceptions** : Vérifiées à la compilation, doivent être gérées ou déclarées (`IOException`, `SQLException`).
- **Runtime Exceptions** : Non vérifiées, souvent causées par des erreurs de logique (`NullPointerException`, `ArrayIndexOutOfBoundsException`).

---

## **Cours 2 : Héritage, polymorphisme, classes internes**

### **Héritage**
- Une classe fille hérite des attributs et méthodes publiques ou protégées de la classe mère.
- **super** : Permet d’appeler un constructeur ou une méthode de la classe mère.

### **Polymorphisme**
- **Liaison dynamique** : Le type dynamique détermine la méthode exécutée à l’exécution.
- Exemple : Une méthode redéfinie dans une classe fille sera appelée même si la référence est de type parent.

### **Classes internes**
- **Membre interne** : Définie au niveau de la classe mais en dehors des méthodes.
- **Locale** : Définie dans un bloc de code (méthode ou constructeur).
- **Anonyme** : Classe interne sans nom utilisée lors d’une instanciation unique.

---

## **Cours 3 : Abstraction, typage, immutabilité**

### **Abstraction**
- Une **classe abstraite** :
  - Peut avoir des attributs et méthodes concrètes.
  - Ne peut pas être instanciée.
- Une **interface** :
  - Ne peut pas avoir d’attributs (sauf `static final`).
  - Peut avoir des méthodes abstraites et concrètes (depuis Java 8).

### **Typage et conversion**
- **Statique** : Vérifié à la compilation.
- **Dynamique** : Vérifié à l’exécution.
- Conversion implicite : Automatique.
- Conversion explicite (cast) : Nécessite une déclaration explicite.

### **Liaison**
- **Statique** : Lors de la compilation (surcharge).
- **Dynamique** : Lors de l’exécution (redéfinition).

---

## **Cours 4 : Collections et itérateurs**

### **ArrayList vs LinkedList**
- **ArrayList** : Basée sur un tableau dynamique, rapide pour accéder par index, lente pour insérer/supprimer au milieu.
- **LinkedList** : Basée sur une liste chaînée, rapide pour insérer/supprimer, lente pour accéder par index.

### **Tri des collections**
- **Comparable** :
  - Implémenté dans la classe pour définir un ordre naturel.
  - Méthode `compareTo`.
- **Comparator** :
  - Définit des critères de tri externes.
  - Peut être combiné avec `thenComparing`.

#### Exemple :
```java
List<Personne> personnes = Arrays.asList(
    new Personne("Alice", 30),
    new Personne("Bob", 25)
);
personnes.sort(Comparator.comparingInt(p -> p.age));
```

### **Stream API**
- **Opérations courantes :**
  - `filter` : Filtrer les éléments selon un prédicat.
  - `map` : Transformer les éléments.
  - `toList` : Collecter les résultats dans une liste.

#### Exemple :
```java
List<String> noms = List.of("Alice", "Bob", "Charlie");
List<String> resultat = noms.stream()
    .filter(nom -> nom.startsWith("C"))
    .map(String::toUpperCase)
    .toList();
```

---

Ce résumé regroupe les concepts majeurs des cours 1 à 4. Veux-tu approfondir un point ou ajouter d’autres notions ? 😊
