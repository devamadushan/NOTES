# *2023

## Question 1 
les niveaux des visibilités de ses membre est 'public' car par défaut les visibilités sont public dans une interface 

## Question 2
```java
public class NodeImpl implements Node{
	private int id=0;
	private static int compteur = 0; 
	private List<Protocol> protocols = new ArrayList<>();
	
	public NodeImpl(){
		compteur++;
		id = compteur;		
	}


	public boolean isFail(){
		return false;
	}
	public void addProtocol(Protocole p){
		for(Protocol unProtocol : protocols){
			if(unProtocol.getName() == p.getName()){
				throw new IllegalArgumentException();
			}
		}
		protocols.add(p);
	}

	public Protocol getProtocol(string name){
		
		for(Protocol unProtocol : protocols){
			if(unProtocol.getName() == name){
				return unProtocol;
			}
		}
		return null;
	}

	


}

```

## Question 3
La modification que o dois faire dans l’interface Protocole c'est de lui ajouter une méthode 'Protocol copy()' qui permettra de faire une copy profonde d'un nœud 

```java
public interface Protocol{
	String getName();
	Protocol copy()
}
```

`NodeImp`
```java
public Node copy(){

NodeImp copy = new NodeImpl();
for(Protocol unProtocole : this.protocols){
	copy.addProtocole(unProtocole.copy());

}
return copy;
}

```


## Question 4

```java

public class ConfigBuilder implements Comfiguration{
private int nbNode;
private Node node;
private int similationTime;

public ConfigBuilder(Node n , int simulation){
	node = n;
	nbNode = 5;
	simulationTime = simulation;
}	
	
public setSize(int nbNode){
	this.nbNode = nbNode;

}
private void setParameter(String name , Object p){

	for (Node n : this.node){
		if(n.getProtocol(name)){
			
		}
	}
}

}



```