
# Sujet  Janvier 2024
## Exercice 1

### Question 1
- a) Decorator
- b) Command
- c) Adapter
- d) 
- e)Abstract Factory
- f) Iterator
- g)
- h)Composit
### Question 2
il manque la visibilité pour la méthode `f` de la classe `TrucImpl`.
on peut la corriger en mettant *private* ou *public* avant la méthode.

### Question 3
La signature d'une méthode montre quel est le type de retour d'une méthode tu quel sont les paramètre que elle aura besoin .

### Question 4

### Question 5
**A** est un sous type de **B** signifie que **A** hérite de **B**

### Question 6
1) `1`
2) `4`
3) `1 3 6`

## Exercice 2

### Question 1

```java

public class ArtefactGroup{

		package Map<String,int> artefacts = new Map<String,int>();

public ArtefactGroup(String artefact, int nb){
	if(nb > 0){
		this.artefacts.put(artefact,nb);
	}
}
public Collection<String> getArtefacts(){
	Collection<String> result = this.artefacts.values();
	return result;

}

public int getQuantity(String artefact){

	int result = this.artefacts.getOrDefault(artefact,0);
	return result;
}

public boolean isEmty(){
	boolean result = this.artefact.isEmpty();
	return result;
}

}

```

### Question 2
cela peut causer beaucoup de problème , car n'importe qui peuvent modifier la list , on peut mémé perdre la list donc il faut eviter de donne l'acces direct a des références.

### Question 3
```java
public int alert(String artefact, int nb){
	int oc = 0;
	if(nb >0 && this.artefacts.containsKey(artefact)){
		oc = this.artefacts.get(artefact)
		oc += nb;
		this.artefacts.put(artefact,oc)
	}
	if(nb < 0 && this.artefacts.containsKey(artefact)){
		oc = this.artefacts.get(artefact)
		oc += nb;
		if(oc > 0){
			this.artefacts.put(artefact,oc)
			
		}else{
			this.artefacts.remove(artefact);
			oc = 0;
		}
	}
	return oc;
	
}

```

### Question 4
```java

public Map<String,int> copy(){
	Map<String,int> copy = new Map<String,int>(this.artefacts);
	return copy;
}

```

### Question 5
```java

//1
AssertEquals(1,s1.getQUantity("a1"));
AssertEquals(1,s1.getQUantity("a2"));

AssertEquals(2,s2.getQUantity("a1"));
AssertEquals(0,s1.getQUantity("a4"));

//2
AssertFalse(s1.contains(s2));
AssertTrue(s2.contains(s1));

//3


```


### Question 6

```java

public class Recette{
	package final AtefactGroupe entree;
	package final ArtefactGroupe sortie;

	public Rescette(ArtefactGroup a , ArtefactGroup b){
		this.entree = a;
		this.sortie = b;
	}

	public Artefact getIn(){
		return this.entre;
	}
	public Artefact getOut(){
		return this.sortie;
	}

}


```

### Question 7
```java

public void assemble(){

	Collection<String> besoin = this.recette.getIn().getArtefact();
	Collection<String> rest = this.recette.getOut().getArtefact();
	boolean contains = this.storage.contains(besoin);
	if(!contains){
		trow new IllegalStateException();
	}
	for(String in : besoin){
		this.storage.alert(this.recette.getIn().getQuantity(in));
	}
	for(String out : rest ){
		this.strorage.alert(this.recette.getOut().getQuantity(out));
	}
	
}

```


### Question 8
On ne peut pas assurer car on que une espace stockage pour tout les recettes que et on va  produire et on peut fabriquer plusieurs recettes en mémé temps , donc l’état de l'espace stockage est peut changer a tout moment, donc ceci est difficile d'assurer .


### Question 10
```java

public class ArtefactGrouObservable extends ArtefactGroup{

	public int alert(String artefact, int nb){
		int old = artefacts.getQuantity(artefact);
		int newNb = super.alert(artefact,nb)
		ArtefactGroupObserver.update(this, artefact , old , nouv);

	}
}

```

### Question 10/11
```java 

public class MachineAssemblage implements ArtefactGroupeObserver{

	@Override 
	public void update(ArtefactGroupObservable obs, String type_art, int old, int nouv){
		this.storage.alert(type_art , old - nouv);
	}
}

```

### Question 12

```java

public class RecetteBuilder extends Recette{

	reset(){
		
	}



}

```