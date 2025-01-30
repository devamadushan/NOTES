``src/pobj/watch/abstractwatch.java
```java

public abstract class AbstractWatch implements Watch{

	private Display d1 = New Display();
	private Display d2 = New Display();
	public CsTimeCounter clock = New CsTimeCounter();
	
	public CsTimeCounter(){
		return this.clock;
	}
	

	public Display d1(){
		return this.d1;
	}

	public Display d2(){
		return this.d2;
	}
}

```




| (Interface)Watch |
| ---------------- |
| +tick()          |
| +pushB()         |
| +pushA()         |
| +d1()            |
| +d2()            |


Hérite de Watch

| AbstractWatch    |
| ---------------- |
| -d1              |
| -d2              |
| -clock           |
| +CsTimeCounter() |
| +d1()            |
| +d2()            |

Herite de AbstractWatch

| SimpleWatch       |
| ----------------- |
| -showDate         |
| -clock            |
| +SimpleWatch()    |
| +refreshDisplay() |
| +tick()           |
| +pushA()          |

Herite de AbstractWatch

| WatchWithStrategie |
| ------------------ |
| +tick()            |
| +refreshDisplay()  |
| +pushA()           |
| +pushB()           |

| WatchStrategie    |
| ----------------- |
| -start            |
| +tick()           |
| +refreshDisplay() |
| +pushA()          |
| +pushB()          |

Hérite de WatchStrategie 

| ClockStrategy     |
| ----------------- |
| -state            |
| -clock            |
| -showDate         |
| +refreshDisplay() |
| +tick()           |
| +pushA()          |
| +pushB()          |


## Question  3

```java 

public Class WatchWithStrategy extends AbstractWatch{
	private WatchStrategie strat;
	
public WatchWithStrategiy(WatchStrategy strat){

		this.strate = strate
}

public void tick(){
	strat.tick();
	this.strart.refreshDisplay(this)
}

public void pushA(){
	this.strat.pushA(this);
}

public void pushB(){

	this.strat.pushB(this);
}


```

```java
public class ClockStrategy implements WatchStrategy{

	private CsTimeCounter clock = new CsTimeCounter();
	private boolean showDate = false;

	public ClockStrategy(){
		clock.inct();
	}

	public void refreshDisplay(){
		// refreshDisplay de Simple Strategie
	}
}
```

```java 

watch w = new WatchSwITHStrategy(new ClockStrategy());


```


### Question 5

```java
public class ChronStrategy(){
private CsTimeCounter clock = new CsTimeCounter();
private boolean started = false;
private boolean frozen = false ;


public void tick(){

	if(started){
		clock.incr();
	}
}

public void refreshDisplay(watch w){

	Display d1 = w.d1();
	Display d2 = w.d2();
if (!frozen){
	d1.set(clock.getHour() , clock.getMinute() , clock.getSecond());
	d2.set(0,0,clock.getCentiSecond());
}
}

public void pushA(watch w){
	this.started = !started;
}

public pushB(watch w){

	if(this.started){
		this.frozen = !frozen;
	}else{
		this.clock.reset()
		this.frozen = false;
		this.started = false;
		
	}
}

}
```


### Question 6
;;
``` java
public clas WatchMultiStrategy extends AbstractWatch{

	private List<WatchStrategy> stats = new ArrayList<WatchStrategy>();
	private 







public void pushMode(){
	this.cursTRAT = (THIS.CURsTRAT +1) % STRATS.size()
}

public

} 

```

