
### Question 1
```java
public class Etudiant {
public static final Comparator<Etudiant> parNom = (Etudiant e1  , Etudiant e2) -> {
return e1.getNom().compareTo(e2.getNom())
};

//EXEMPLE 2
public static final Comarator<Etudiant> parNumeroEtudiant = (e1,e2) -> Interger.compare(e1.getNumeroEtudiant(),e2.getNumeroEtudiant()):


// EXEMPLE 1
public static final Comparaor<Etudiant> parNumeroEtudiant = 
	new Comparator<Etudiant>(){
		public int compare(Etudiant e1 , Etudiant e2){
			return Integer.compare(e1?getNumeroEtudiant() ,                                   e2.getNumeroEtudiant())
		}
	}

	private final String nom ;
	private final String prenom ;
	private ont numeroEtudiant;



}
```



### Question 2
```java
List<Etudiant> List;
List.sort(parNom);
list.sort(Etudiant.parNumeroEtudiant);
Collection.sort(list,Etudiant.parNom);
```


### Question 3
```java
Function<Etudiant, String> getNom;
Function<Etudiant, String> getPrenom;
Function<Etudiant, Integer> getNumberEtudiant;
```

### Question 4

```java
public static final Comparator<Etudiant> makeComparator(Function<Etudiant, String> f){

return (Etudiant e1 , Etudian e2) -> {
	return f.apply(e1).comareTo(f.apply(e2));
}
}


public static final Comparator<Etudiant> parNom makeComparator(Etudiant:: getNom);

public static final Comparator<Etudiant> parPrenom = makeComparator(Etudiant::getPrenom);
```

### Question 5
``` java
public static final <T> Comparator<T> makeComparator(Function<T, U extends Comparable<U>> f){
	return (T e1 , T e2) -{
		return f.apply(e1).compareTo(f.apply(e2));
	}
}


public static final Comparator<Etudiant> parNom makeComparator(Etudiant:: getNom);

public static final Comparator<Etudiant> parPrenom = makeComparator(Etudiant::getPrenom);

public static final Comparator<Etudiant> parNumeroEtudiant = makeComparator(Etudiant::getNumeroEtudiant);

```

### Question 6

```java

public static final <T> Comparator<T> makeLexicographique(Comparator<T> c , Comparator<T> d){
	return (T e1 , T e2)->{
	int value = c.compare(e1 , e2);
		if (value == 0){
			return d.compare(e1 , e2);
		}	
		return value
	}

}


public static final Comparator<Etudiant> parNomPrenom = makeLexicographic(Etudiant.parNom , Etudiant parPrenom);
```

### Question 7
```java
List<Etudiant> p;

List<Integer> q = p.filter(e -> e.getNOm().compareToIgnoreCase("M") < 0)
					.sorted(parNomPrenom)
					.map(e -> e.getNumeroEtudiant())'ou                                              .map(Etudiant::getNumeroEtudiant => (e ->                                         e.getNumeroEtudiant())'
					.collect(Collectors.toList())
```

### Question 9

``` java

public static <T> int totalSize(Stream<Collection<T>> stream) {
    return stream.map(Collection::size).reduce(0,(a,b)-> a+b);
}
// ou 
public static <T> int totalSize(Stream<Collection<T>> stream) {
    return stream.reduce(0, (a,b)-> a+b.size(), (a,b)-> a+b);
}

// ou 
public static <T> int totalSize(Stream<Collection<T>> stream) {
    return stream.collect(Collectors.summingInt(Collection::size));
}

```


### Question 10

```java
public static Stream<Integer> cstStream(int cst) {
    return Stream.generate(() -> cst);
}
```


### Question 11

``` java
public static Stream<Integer> seqStream(int first) {
    return Stream.generate(new Supplier<Integer>(){
	    private int i = first;
	    public Integer get(){
		    return i++;
	    }
    });
}

public static Stream<Integer> seqStream(int first){
	return Stream.iterate(first , a -> a+1);

}
```

