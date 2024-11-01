
Java est un langage de programmation créé par _James Gosling_ chez Sun Microsystems en 1995. Il s'inspire fortement du langage C++, tout en éliminant certaines complexités comme les **pointeurs**, afin de rendre la programmation plus simple et plus sécurisée. Un des principes fondamentaux de Java est **"Write Once, Run Anywhere"**, ce qui signifie qu'un programme écrit en Java peut être exécuté sur n'importe quel système d'exploitation doté d'une machine virtuelle Java (JVM), sans modifications.


#Type 
	Types primitifs :
		1. Type natif au langage Java 
		2. La case mémoire de la variable contient une valeur (sauf void)
		3. Valeurs par défaut : 0.0 (flottants), 0 (entiers), false (booléens)
		 **boolean** : Représente une valeur vraie ou fausse.
			 `boolean isJavaFun = true;`
		 **byte** : Un entier de 8 bits.
			 `byte b = 100;`
		 **short** : Un entier de 16 bits. 
			 `short s = 30000;`
		 **char** : Utilisé pour représenter un caractère unique 16bits, valeur Unicode.
			 `char c = 'A';`
		 **int** : Un entier de 32 bits, le type de base pour les entiers.
			 `int x = 100000;`
		 **long** : Un entier de 64 bits.
			 `long y = 100000L;`
		 **float** : Un nombre à virgule flottante de 32 bits, 
			 `float f = 5.75f;`
		**double** : Un nombre à virgule flottante de 64 bits, 
			`float f = 5.75f;`
		Exemple :
		`public class PrimitiveExample {` 
			`public static void main(String[] args) {`
				`int number = 10; // Type primitif` 
				`System.out.println("Valeur du type primitif int : " + number);`
			`}`
	Types objet
		1. Type défini par le programmeur ou dans une librairie tierce
		2. La case mémoire de la variable contient une référence sur un objet
		3. Valeur par défaut : null
		Exemple:
		`public class ObjectExample {` 
			`public static void main(String[] args) {` 
				`Integer number = 10; // Type objet (classe wrapper)` 
				`System.out.println("Valeur du type objet Integer : " + number);`
				`int maxValue = Integer.MAX_VALUE; // Méthode de classe` 
				`System.out.println("Valeur maximale d'un Integer : " + maxValue);`
			 `}`
		`}`
#exprsesion 
	Constante
		`final int nombre = 5;         // 'nombre' est une constante.
		`final boolean estVrai = true; // 'estVrai' est une constante.`
		`final char lettre = 'A';      // 'lettre' est une constante.`
	Variable
		`int x = 10;  // 'x' est une variable qui contient la valeur 10.`
		`int y = x;   // Ici, 'x' est une expression qui évalue à 10, et cette valeur est assignée à 'y'.`
	Appel d'une fonction ou méthode
		`double racineCarree = Math.sqrt(16); // 'Math.sqrt(16)' est une expression.`
		`String texte = "Bonjour".toUpperCase(); // 'toUpperCase()' est une méthode qui.`
	opération unaire composée : `++ ,-- , - , !`
		`int y = 5;`
		`int negatif = -y; // 'negatif' vaut -5, 'y' est la sous-expression.`
		`int increment = ++y; // '++y' est une opération unaire qui incrémente y.`
	opération binaire composée : `+ , - , % , * , / , >, < , && , || , == ,!=`
		`int a = 10;`
		`int b = 20;`
		`int somme = a + b; // 'a + b' est une expression binaire.`
		`boolean comparaison = a > b; // 'a > b' est une autre expression binaire.`


Pour crée des variables en JAVA
	#Type identificateur = #exprsesion;
		`int num = 3;`