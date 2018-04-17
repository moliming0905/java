##instanceof关键字
<pre>
package 静态函数;

/*instanceof关键字：
 * <font color="red">
 * instanceof 关键字的作用：判断一个对象是否属于指定的类别。
 * 
 * instanceof关键字的使用前提：判断的对象与指定的类别必须要存在继承或者实现的关系。
 * 
 * instanceof关键字的使用格式：
 * 		对象	instanceof	类别
 * 
 * instanceof关键字的作用：目前没用，但是学到多态的话，才有用武之地。
 * </font><font color="blue">
 * 一般我们做强制类型转换之前都会使用该关键字先判断，然后再进行转换的 。</font>
 * */
//动物
class Animal2{
	String name;
	String  color;
	public Animal2(String name,String color){
		this.name = name;
		this.color = color;
	}
}
//狗是属于动物中的一种
class Dog extends Animal2{
	public Dog(String name,String color){
		super(name,color);//指定调用父类两个参数的构造函数。
	}
	public void bite(){
		System.out.println(name+"咬人！！");
	}
}

//老鼠也是动物的一种
class Mouse extends Animal2{
	public Mouse(String name,String color){
		super(name,color);	//指定调用父类两个参数的构造函数。
	}
	public void dig(){
		System.out.println(name+"打洞。。。");
	}
}

public class Demo12 {

	public static void main(String[] args) {
		Dog d = new Dog("哈士奇","白色");
		d.bite();
		System.out.println(d instanceof Dog);
		System.out.println(d instanceof Animal2);
		//报错
		//System.out.println(d instanceof Mouse);
		
		Animal2 a = new Animal2("狗娃","黄色");
		
		System.out.println(a instanceof Dog);
	}

}

</pre>
<h3><b>执行结果</b></h3>
<pre>
哈士奇咬人！！
true
true
false
</pre>