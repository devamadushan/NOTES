### TME 7_8


#### Question 14

VisitorToString. Le résultat de ce visiteur est une chaîne de caractères ; pour cela, la classe VisitorToString implante l’interface `IVisitor<String>` . La méthode visit est surchargée, permettant d’effectuer un travail spécifique pour chaque classe concrète sous-
classe d’Expression. Si nécessaire pour le calcul, le visiteur peut parcourir les sous-expressions qui composent l’expression et obtenir leur valeur générée par le visiteur, avant de construire sa valeur de retour (comme pour Add et Mult). Ceci est réalisé par un appel à accept sur chaque sous-expression, en passant le visiteur courant (this) en argument.



- `IVisitor`
``` java
package pobj.expr;

public interface IVisitor<T> {

	T visit(Constant c);
	T visit(Add e);
	T visit(Mult e);
	T visit(Var v);

}

```

- `VisitorToString`
``` java
package pobj.expr;

public class VisitorToString implements IVisitor<String> {

	public String visit(Constant c) {
		return Integer.toString(c.getValue());
	}

	public String visit(Var v) {
		return v.getName();
	}

	public String visit(Add a) {
		String s1 = a.getLeft().accept(this);
		String s2 = a.getRight().accept(this);
		return "( "+ s1 + " + " + s2 + " )";
	}

	public String visit(Mult a) {
		String s1 = a.getLeft().accept(this);
		String s2 = a.getRight().accept(this);
		return s1 + " * " + s2;
	}

}
```



- `testVisirorToSTring`
``` java

	VisitorToString vts = new VisitorToString();
	Var var = new Var ("a");
	Constant ct = new Constant(3);
	Add add = new Add(var, ct);
	assertEquals("( a + 3 )", add.accept(vts));

```



- `Add`
``` java
package pobj.expr;

  

public class Add extends BinOP implements Expression {

	public Add(Expression left , Expression right){
		super(left,right);
	}

  
	@Override
	public String toString() {
		return "( "+left.toString()+" + "+right.toString()+" )";
	}

  

	@Override
	public int eval() {
		int rep;
		if(super.getLeft() instanceof Var || super.getRight()                 instanceof Var ) {
			throw new UnsupportedOperationException();
		}else {
			rep = left.eval()+right.eval();
		}
			return rep;
	}

///////////////////////////////////////////////////////////////////////////

/*  probléme  */

	@Override
	public <T> T accept(IVisitor<T> vis) {
		return vis.visit(this) ;
	}
	
//////////////////////////////////////////////////////////////////////////

}

```


Ici, le problème que j'ai rencontré, c'était de trouver comment utiliser la méthode `visit()` de la classe `VisitorToString`, sachant que cette méthode utilise l'interface `IVisitor<T>` en paramètre. J'avais du mal à faire la liaison entre `IVisitor` et `VisitorToString`. C'est ce genre de petit problème que je rencontre.


