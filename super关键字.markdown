##super关键字尝鲜
<pre>
package 静态函数;
/*
 * super关键字
 * 
 * super关键字代表了父类空间的引用。
 * <font color="blue">
 * super关键字的作用：
 * 	1.子父类存在着同名的成员时，在子类中默认是访问子类的成员，可以通过super关键字指定访问父类的成员。
 * 	2.创建子类对象时，默认会先调用父类无参的构造方法，可以通过super关键字指定调用父类的构造方法。
 * </font><font color="green">
 * super关键字调用父类构造方法要注意的事项：
 * 	1.如果在子类的构造方法上没有指定调用父类的构造方法，那么java编译器会在子类的构造方法上面加上super()语句。
 * 	2.super关键字调用父类的构造函数时，该语句必须要是子类构造函数中的第一个语句。
 * 	3.super与this关键字不能同时出现在同一个构造函数中调用其他的构造函数。
 * </font><font color="red">
 * super关键字和this关键字的区别：
 * 	1.代表的事物不一致
 * 		（1）super关键字代表的是父类空间的引用。
 * 		（2）this关键字代表的是所属函数的调用者对象。
 * 2.使用前提不一致：
 * 		（1）super关键字必须要有继承关系才能使用。
 * 		（2）this关键字不需要存在继承关系也可使用。
 * 3.调用构造函数的区别：
 * 		（1）super关键字是调用父类的构造函数。
 * 		（2）this关键字是调用本类的构造函数。 this();</font>
 * */
class Fu2{
	int x = 10;
	String name;
	public Fu2(){
		System.out.println("Fu2类无参的构造方法。。。。");
	}
	public Fu2(String name){
		this.name = name;
		System.out.println("Fu2类带参的构造方法。。。。");
	}
	public void eat(){
		System.out.println("小头爸爸吃番薯...");
	}
}

class Zi2 extends Fu2{
	int x = 20;
	public Zi2(){
		System.out.println("Zi2子类无参构造方法。。。。");
	}
	public Zi2(String name,int num){
		super(name);
		this.x = num;
		//super(name),this();	//指定调用了父类带参的构造方法。。。。
		//this();
		//super();     //指定调用了父类无参构造方法。
		System.out.println("Zi2类带参的构造方法。。。。");
		//super必须是构造函数的第一条语句。。。。不然会报错。
		//super(name);	//指定调用了父类带参的构造方法。。。。
	}
	public void print(){
		//System.out.println("x = "+this.x);
		System.out.println("x = "+super.x);
		super.eat();
	}
	public void eat(){
		System.out.println("大头儿子吃龙虾。。。");
	}	
}
public class Demo9 {
	public static void main(String[] args){
		Zi2 zi = new Zi2("离人愁",20);
		zi.print();
	}
}

</pre>