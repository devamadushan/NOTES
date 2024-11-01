
Une collection est un **objet** qui permet de gérer un regroupement d'éléments (objets individuels). Elle se distingue par deux aspects principaux :

1. **Interface** : Elle définit les opérations publiques que l'on peut effectuer sur la collection, telles que l'ajout, la suppression, la recherche ou encore la modification des éléments.
    
2. **Implémentation** : Elle spécifie la structure interne de la collection, ses contraintes (par exemple, si elle accepte des doublons ou si elle est triée) et la manière dont les éléments sont parcourus (politique d'itération).





![[Pasted image 20241011232148.png]]

| `List<E>`  | `Set<E>`           | `Map<K,V>`    | `Queue<E>`         |
| ---------- | ------------------ | ------------- | ------------------ |
| ArrayList  | HashSet            | HashMap       | PriorityQueue      |
| LinkedList | LinkedHashSet      | LinkedHashMap | ArrayDeque         |
| Vector     | TreeSet            | TreeMap       | ArrayBlockingQueue |
| Stack      | copyOnWriteAraySet | Hashtable     | DelayQueue         |
| SubList    | EnumSet            | EnumMap       | SynchronousQue     |
| ...        | ...                | ...           | ...                |

## List


![[Pasted image 20241012001814.png]]

### Hiérarchie de type des Listes
![[Pasted image 20241012000259.png]]
### ==Principales implantations de List==

#### La classe ArrayList
- Utilise un tableau pour stocker ses éléments 
- La taille du tableau s’adapte automatiquement au nombre d’éléments *
- Complexité ajout/suppression : O(N) 
- Complexité accès : O(1)
#### La classe LinkedList
- Utilise un double chaînage 
- Il n’est pas redimensionnée quelque soit le nombre d’éléments
- Complexité ajout/suppression : O(1) 
- Complexité accès : O(N)




## Set

![[Pasted image 20241012002446.png]]


### Hiérarchie de type des Set
![[Pasted image 20241012002835.png]]
## Map

![[Pasted image 20241012002238.png]]


### Hiérarchie de type des Set
![[Pasted image 20241012003743.png]]![[Pasted image 20241012004300.png]]