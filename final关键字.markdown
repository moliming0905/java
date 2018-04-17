##final关键字
<pre>
package 数据抽象;
/*<font color="red">
 * final关键字（最终的）
 * 
 * final关键字的用法：
 * 	1.final关键字修饰一个基本类型的变量时，该变量不能重新赋值，第一次的值为最终的。
 * 	2.final关键字修饰一个引用类型变量时，该变量不能重新指向新的对象。
 * 	3.final关键字修饰一个函数的时候，该函数不能被重写。
 * 	4.final关键字修饰一个类的时候，该类不能被继承。
 * </font><font color="blue">
 * 常量的修饰符一般为： public static final
 * </font>
 * */
//圆形
final class Circle{
	double  r;//半径
	//double pi = 3.14;		//固定不变的，不想被别人修改
	//private double pi = 3.14;	//方式一 私有化。
	public static final double pi = 3.14;	//方式二 使用final修饰。
	
	
	public Circle(){
		
	}
	
	public Circle(double r){
		this.r = r;
	}
	
	public void getArea(){
		System.out.println("圆形的面积是:"+r*r*pi);
	}
}

public class Demo1 extends Circle{
	public Demo1(double r){
		super(r);
	}
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//final Circle c = new Circle(1.0);
		//c = new Circle(5.0);	//c变量又重新指向新的变量。
		//c.pi = 0.0;
		//c.getArea();
		//test(c);
		Demo1 c = new Demo1(4.0);
		c.getArea();
	}
	public void getArea(){
		System.out.println("草拟妹");
	}
	public static void test(Circle c){
		c = new Circle(5.0);
		c.getArea();
	}
}

</pre>