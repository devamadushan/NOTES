
#trow
#finnaly
#types-de-exceptions


Le mécanisme principal pour gérer les exceptions est à travers les blocs `try-catch`

````
try {
    System.out.println("Tentative de division par zéro");
    
    int x = 10 / 0;  // Ceci lance une exception                                           ArithmeticException
    System.out.println("Ceci ne sera pas affiché");
    
} catch (ArithmeticException e) {
    System.out.println("Erreur : Division par zéro !");
} finally {
    System.out.println("Bloc finally exécuté");
}

````

![[Pasted image 20241017222926.png]]