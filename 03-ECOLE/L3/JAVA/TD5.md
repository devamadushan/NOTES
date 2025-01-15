- exceptions 
-  contrats 
-  test unitaires

## Exercice 1 
### Q1
````
Premier test : 
un
trois 
quatre

second test:
un
deux
quatre

Troisiéme test
un
cinq

Quatrieme test:
un
deux

cinqieme test:
un
trois
trois bis
cinq

Sixeme test :
un
deux
trois bis 
quatre

````

get : Alea jacta est
genstr1 :  "Cogito ergo sum
genstr2 : "Veni, vidi

### Q2

````
Premier test multiple :
un
trois ter
quatre

Seconde test muliple:
un
trois bis
quatre

Troisieme test multiple :
un
trois
quatre

Quatrieme test multiple :
un 
deux
quatre

````


## Exercice 2
#une-pile
	last in, first out 
#ternair
```
	[(limit<0) ? 0 : limit];
```

### Q1
```
size <= limit;
size <=0;
```

### Q2

````

fournisseur = BoundedStack
clients = nimporte quelle méthode qui appl une méthode
p >= la pile avant l'operation
p' =>la pile apres l'operation

+Object top()
-Préruquis =
	p.size > 0;
ou p.Size != 0;

-Garanties:
"Aucune Modification de l'etat de la pile"
	p.Size == p'.size;
	p.limit == p'.limit;
	p.top== p'.top;

+Void push (Object)
prérequis :
"la pile n'est pas pleine"
p.size < p.limite;
p.size != p.limit;

Garanties:
p.size+1 ==p'size
p'size>0;
p'.top()==0;

+Object pop()
-prerequis:
	p.size >0;
-garanties :
p.size-1 == p'size
p.top == p.pop
p.size >O , p.size >=0
p.size()<p.imit




````

### Q3

````
package pobj.stack;

public class StackException extend Exception{
	public stackEception(String message){
		super("stack Exception")
	}
}

package pobj.stack;

public class StackFullException extend StackException{
	public stackFullEception(String message){
		super("stack is full")
	}
}

package pobj.stack;

public class StackEmtyException extend StackException{
	public stackEmtyEception(String message){
		super("stack is emty")
	}
}



````

### Q4
````
Public Object top() throws stackEmtyException{
	if(this.size()==0){
		throw new StackEmtyException();
	}
	return content(this.getSize()-1);
}

public void push(object o) throws StackFullException{
	if (this.getSize()== this.getLimite()){
		throw new StackFullyException();
	}
}

Public Object top() throws stackEmtyException{
	if(this.size()==0){
		throw new StackEmtyException();
	}
	ovject o = content[size -1]
	size--
	return o;
}
````

### Q5
````
package pobj.stack.test;
import  org.junit.after;
import  org.junit.before;
import  org.junit.Test;

import static org.junit.Assert.assertEquals;
import static org.junit.Assert.assertTrue;

import pobj.stack.BoundedStack;
import pobj.stack.StackException;
import pobj.stack.StackFullException;
import pobj.stack.StackEmtyException;

pubblic class BoundStackTest{
	private BounderStack stackFull;
	private BounderStack stackEmty;
	private BounderStack stackhHalfFull;

	@Before
	public setup(){
		stackFull = new BoundedStack(1);
		stackFull.push(new Object());
		stackEmty = new BoundedStack(1);
		stackHalfFull = new BoundedStack(2);
		stackHalfFull.push(new Object());
		
	}
	@Test
	public void testBoundedStack(){
		BoundedStack stack = new BoundedStack(5);
		assertTrue(stack.getSize()==0);
		assertTrue(stack.getLimiit()5);
	}
	@Test(excepted = StackEmptyException.class)
	public void testTop1() throws StackException{
		stackEmpty.top();
	}
	@Test(excepted = StackEmptyException.class)
	public void testTop2() throws StackException{
		stackFull.top();
	}
@Test(excepted = StackFullException.class)
	public void testPush1() throws StackException{
		stackFull.push(nw Object());
	}
@Test
	public void testPush2() throws StackException{
		stackFull.push(nw Object());
	}
@Test
	public void testPush3() throws StackException{
		int oldSize = stackHalfFull.getSize();
		Object o ) new String("salut")
		stackHalfFull.push(o);
		assertTrue(stack1.getSize()==oldSize +1 );
		assertTrue(stack1.top()==o)
	}
@Test(excepted = StackEmptyException.class)
	public void testPop1() throws StackException{
		stackEmpty.pop();
	}
@Test
	public void testPop2() throws StackException{
		BoundedStack stack = new BoundedStack(3);
		stack.push("1");
		stack.push("2");
		stack.push("3");
	int oldSize = stack.getSize();
	assertEqual("3",stack.Pop());
	assertEqual(oldSize -1 ,stack.getSize());
	oldSize = stack.getSize();
	assertEqual("2",stack.pop())
	assertEquals(oldsize -1 ,oldstack.getSize());
	oldSize = stack.getSize();
	assertEquals("1",stack.pop());
	assertEquals(oldSize -1 , stack.getSize());
	
	}
	
}

```