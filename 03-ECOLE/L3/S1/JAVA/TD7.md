## Polymorphisme

### Exercice 1
```txt
P1
L1 : statique = A ; Dynamique = A
L2 : statique = B ; Dynamique = B
L3 : statique = A ; Dynamique = B
L4: statique = B ; Dynamique = A 
	ERROR de compilation
	Solution : B ba= (B) new A()
P2
x : statique = A ; Dynamique = B
y : statique = B ; Dynamique = A
	ERROR de compilation
	solution : B y = (B)x

P3
tb : statique = B[] ; Dynamique = B
ta :  statique = A ; Dynamique = B
L3 : tb[0] = new A();
	ERROR de l'execution
L4 : ta[0] = new A();
	ERROR de l'execution
```

type dynamique (fille) type statique (Mère) n'est pas possible (erreur de compilation) 
type dynamique (Mère) type statique (Fille) c'est possible
Tableaux il prend en compte toujours type dynamique 


Question 2
```
a: type statique A et type dynamique A 
	affichage "f dans A"
b: type statique A et type dynamique B
	affichage "f dans B"
c : type statique B et type dynamique B
	affichage "f dans B"
```

Question 3

a : Type statique = A et Dynamique = A
b : Type statique = A et Dynamique = B
c : Type statique = B et Dynamique = B

```
a.m(a)
	"m(A) dans A"
a.m(b)
	"m(A) dans A"
a.m(c)
	"m(A) dans A"
b.m(b)
	"m(A) dans B"
b.m(b)
	"m(A) dans B"
b.m(c)
	"m(A) dans B"
c.m(a)
	"m(A) dans B"
c.m(b)
	"m(A) dans B"
c.m(c)
	"m(B) dans B"
```

## Héritage et comparaison

Question4

```
public String getCouleur() -> Extend
public int getLongueur() -> EXtend
public boolean estSimilaire(Voiture v) -> Extend

public boolean isCommonRail() -> New 
public boolean estSimilaire(VoitureDiesel v) -> New
```


Question 5 

v1 , v2 , v3 : Type statique = Voiture et Dynamique = Voiture
```
v1.estSimilaire(v1) 
	Preselection dans  VOITURE 
	estSimilaire(Voiture): boolean
	Invocation dans voiture 
	Return True
v1.estSimilaire(v2)
	Preselection dans  VOITURE 
	estSimilaire(Voiture): boolean
	Sugnature trouver dzns la classe dynamiqye
	Return true
v1.estSimilaire(Voiture): boolean
	Preselection dans  VOITURE 
	estSimilaire(Voiture): boolean
	Signature trouveée 
	retrun false
```

Question 7
v4, v5 , v6 : Type statique = VoitureDiesel et Dynamique = VoitureDiesel
v7 , v8 : Type statique = Voiture et Dynamique = Voiture
v9 : Type statique = Voiture et Dynamique = VoitureDiesel


```
v4.estSimilaire(v7)
	Preselection dans  VOITURE Diesel
	n'esite pas dans voitureDiesel donc 
	super.estSimilaire(v7) dans Voiture
		return true
v7.estSimilaire(v4)
	Preselection dans  VOITURE 
	estSimilaire(v4)
		return true
v4.estSimilaire(v8)
	Preselection dans  VOITURE Diesel
	Invocation dans Voiture Diesel 
	return false
v8.estSimilaire(v4)
	preselection dans Voiture 
	Invocation dans voiture 
	false
v4.estSimilaire(v9)
	preselection dans Voiture Diesel
	Invocation Voiture 
	return true
v9.estSimilaire(v4)
	Preselection dans voiture 
	Invocation dans voiture Diesel
	super.estSimilaire(Voiture)
	true
v6.estSimilaire(v9)
	Preselection VOiture Diesel
	Invocation dans VoitureDiesel
	super.estSimilaire(Voitrure)
	renvoie true
```

Question 8
	on ajoute dans Voiture Diesel ()boolean estSimilaire (Voiture v)
```
	if(v instence of VoitureDiesel){
		return estSimilaire((voitureDiesel) v)
	}
	return super.EstSimilaire(v);
```

Question 9
la solution consite a ref=définition de equal(Object)
```
boolean equal (object o){
	if (this== 0  ){
		return true;
	}
	if(o  instenceof Voiture){
		return this.estSimilaire((Voiture)o)
	}
	return false;
}
```