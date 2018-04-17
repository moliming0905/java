##abstract关键字

<pre>
package 数据抽象;
/*
 * 抽象类：
 * 
 * 
 * 目前存在的问题：
 * 	1.动物类的run方法描述的不正确
 * 	2.没有强制要子类一定要重写run方法。
 * <font color="blue">
 * 抽象类的应用场景：
 * 	我们在描述一类事物的时候，发现这种事物确实存在着某种行为，
 *  但是这种行为目前是不具体的，那么我们可以抽取这种行为的声明，但是不去
 *  实现该种行为，这时候这种行为我们称作为抽象的行为，我们就需要使用抽象类。
 * </font>
 * 抽象类的好处：强制要求子类一定要实现指定的方法。
 * 
 * <font color="red">
 * 抽象类要注意的细节：
 * 	1.如果一个函数没有方法体，那么该函数必须要使用abstract修饰，把该函数修饰成抽象的函数。
 * 	2.如果一个类出现了抽象的函数，那么该类也必须使用abstract修饰。	
 * 	3.如果一个非抽象类继承了抽象类，那么必须要把抽象类的所有抽象方法全部实现。
 * 	4.抽象类可以存在非抽象方法，也可以存在抽象的方法。
 * 	5.抽象类可以不存在抽象方法的。
 * 	6.抽象类不能创建对象。
 * 		疑问：为什么抽象类不能创建对象？
 * 			因为抽象类是存在抽象方法的，如果能让抽象类创建对象的话，那么使用抽象的对象调用
 * 		    抽象方法是没有任何意义的。
 * 	7.抽象类是存在构造函数的，其构造函数是提供给子类创建对象的时候初始化父类的属性的。
 * </font>
 * */
//动物类
abstract class Animal{
	String name;
	String color;
	public Animal(){}
	public Animal(String name,String color){
		this.color =color;
		this.name = name;
	}
	public void eat(){
		System.out.println(this.name+"吃东西。。。");
	}
/*
	public void run(){
		System.out.println(name+"小短腿跑的还挺快");
	}
*/
	
	public abstract void run();
}
//狗
class Dog extends Animal{
	public Dog(String name,String color){
		super(name,color);
	}
	public void run(){
		System.out.println(name+"四条腿跑的挺快");
	}
}
//鱼
class Fish extends Animal{
	public Fish(String name,String color){
		super(name,color);
	}
	public void run(){
		System.out.println(name+"游得挺快");
	}
}

public class Demo2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Dog d = new Dog("哈士奇","雪白");
		d.run();
		
		//创建一个鱼
		Fish f = new Fish("小鲤鱼","青黑色");
		f.run();
	}

}

<pre>
执行结果：

哈士奇四条腿跑的挺快
小鲤鱼游得挺快

</pre>
</pre>
<hr/>
###Example
<pre>
package 数据抽象;
/*
 * 需求：描述一个图形、圆形、矩形三个类。不管哪种图形都会具备计算面积与周长的行为，
 * 只不过每种图形计算的方式不一致而已。
 * 
 * 常量的命名规范：全部字母大写，单词与单词之间使用下划线分隔。
 * <font color="red" size="5">
 *abstract<font color="green"><b>不能</b></font>与以下关键字共同修饰一个方法:
 * 	1.abstract不能与<font color="green"><b>private</b></font>共同修饰一个方法。
 * 	2.abstract不能与<font color="green"><b>static</b></font>共同修饰一个方法。
 * 	3.abstract不能与<font color="green"><b>final</b></font>关键字共同修饰一个方法。</font>
 * */
//图形类
abstract class MyShape{
	String name;
	//private String name;
	public MyShape(String name){
		this.name = name;
	}
	//private abstract void getArea();
	//public final abstract void getArea();
	public abstract void getArea();
	public abstract void getPerimeter();
}

//圆形
class Circle2 extends MyShape{
	public final double PI = 3.1415926;
	private double r;
	public Circle2(String name,double r){
		super(name);
		this.r = r;
	}
	@Override
	public void getArea() {
		// TODO Auto-generated method stub
		double area = PI*r*r;
		System.out.println(super.name+"的面积是:"+area);
	}

	@Override
	public void getPerimeter() {
		// TODO Auto-generated method stub
		double perimeter = 2*PI*r;
		System.out.println(super.name+"的周长是："+perimeter);
	}	
}
//矩形
class Rectangle extends MyShape{
	private double width;
	private double height;
	public Rectangle(String name,double width,double height) {
		super(name);
		// TODO Auto-generated constructor stub
		this.width = width;
		this.height = height;
	}

	@Override
	public void getArea() {
		// TODO Auto-generated method stub
		double area = this.width*this.height;
		System.out.println(super.name+"的面积是："+area);
	}

	@Override
	public void getPerimeter() {
		// TODO Auto-generated method stub
		double perimeter = 2*(this.width+this.height);
		System.out.println(super.name+"的周长是："+perimeter);
	}	
}

class Triangle extends MyShape{
	private double side1;
	private double side2;
	private double side3;
	
	public Triangle(String name,double side1,double side2,double side3) {
		super(name);
		// TODO Auto-generated constructor stub
		this.side1 = side1;
		this.side2 = side2;
		this.side3 = side3;
	}

	@Override
	public void getArea() {
		// TODO Auto-generated method stub
		//求三角形面积用了海伦公式
		double HalfOfPerimeter = (this.side1+this.side2+this.side3)/2;
		double area = Math.sqrt(HalfOfPerimeter*(HalfOfPerimeter-this.side1)*(HalfOfPerimeter-this.side2)*(HalfOfPerimeter-this.side3));
		System.out.println(super.name+"的面积是："+area);
	}

	@Override
	public void getPerimeter() {
		// TODO Auto-generated method stub
		double perimeter = (this.side1+this.side2+this.side3);
		System.out.println(super.name+"的周长是："+perimeter);
	}
}

public class Demo3 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Circle2 c1 = new Circle2("圆",1.0);
		c1.getArea();
		c1.getPerimeter();
		
		Rectangle r1 = new Rectangle("矩形",2,4);
		r1.getArea();
		r1.getPerimeter();
		
		Triangle t1 = new Triangle("三角形",3,4,5);
		t1.getArea();
		t1.getPerimeter();
		
		
	}
}

</pre>
####执行结果：
<pre>
圆的面积是:3.1415926
圆的周长是：6.2831852
矩形的面积是：8.0
矩形的周长是：12.0
三角形的面积是：6.0
三角形的周长是：12.0
</pre>