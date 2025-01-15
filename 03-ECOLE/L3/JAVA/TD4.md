
### Question 5

on doit assurer qu'une Collection` <E>` ne contiennent que des elements de type E, on doit simplement garantir que seul des element de type E soient ajoutés. c'est a dire :
que la méthode  `add`  prennent en argument un type 

pour `contains ` et `remove` , on ne viole pas cette intervenant , donc on peut se permettre d'etre moins strict sur le type statique.

De plus `contains` et `remove` utilisant equals , et l'egalité logique n'implique pas forcément l'égalité des types.


## Exercice 2 - Itérateur sur une matrice 

il faut que la classe `Matrice` implémente l'interface `Iterable` 

### Question 2


````
public class Matrice<T> implements Interable {

Private class MatriceIterator imlements Iterator<T>{

	private int i =0;
	private int j =0;

	prublic boolean hasNext(){
		return i <nbLignes();	
	}
	public T next(){
		T res = mat[i][j++];
		if (j== nbColonnes()){
			j =0;
			i++
		}
		return res;
	}
	
}
public Iterator<T> iterator(){
	retrn new MaticeIterator();
}
}
````

## Exercice 3

### Question 1
Gestion de la mémoire :
- ArrayList => stockage contigu
- LinkedList => stockage non-contig
Accés 
- Accés Arraylist => 0(1)
- Accés LinkedList => 0(n)autrement
Insertion:
- ArrayList => 0(n) amorti en 0(1) (en  cas d'insertion a l fin)
- LinkedList => 0(1) si on connait la position (e.g. insertion)

### Question 2

````
public boolean add(T object) { 
	if ((size % allocationSize)==0){
		list.add(new MyArrayList<T>(allocationSize));
	}
	MyArrayList<T> vec = list.get(list.size() -1);
	vec.add(object);
	size++
	return true;
}
public T get(int index){
	int chaininIndex = index / allocationSize;
	int cell = index % allocationSize;
	return list.get(chainonIndex).get(cell);
}
````

### Question 3
`Iterator<MyArrayList<T>> listIT;`

`Iterator<T> vectIt;`

### Question 4

````

Class ListVescor<T> implements Iterable<T>{
	private class ListVectorIterator implements Iterator<T>{
		Interator<MyArrayList<T>> listIt = Collection.emptyIterator();
	}
	public boolean hasNext(){
		return listIt.hasNext() || vactIt.hasNext();
	
	}
	public T next(){
		if (!vectIt.hasNext()){
			MyArrayList<T> vec = listIt.next();
			vecIt = vec.iterator();
		}
		return vectIt.next();
	}
}
```
