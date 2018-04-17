##main函数详解
<pre>
package 静态函数;
import java.util.*;
/*
 * main函数的详解
 * 		public: 公共的。权限是最大，在任何情况下可以访问。
 * 			原因：为了保证让JVM在任何情况下都可以访问的到main方法。
 * 		static:	静态。静态可以让jvm调用main函数的时候更加的方便，不需要通过对象调用。
 * 			1.需要创建对象调用
 * 			2.JVM不知道如何创建对象，因为创建对象有些事需要参数的，参数传递什么东西呢？
 * 		void: 没有返回值。因为返回的数据是给jvm的，而jvm使用这个数据是没有意义的，所以就不要了。
 * 
 * 		main：函数名。注意：main并不是关键字，只不过是JVM能识别的一个特殊的函数名而已。
 * 
 * 		arguments: 担心某些程序在启动需要参数。
 * 
 * */
public class Demo4 {
	public static void main(String[] args){
		for(int i = 0; i < args.length; i++){
			System.out.println(args[i]+",");	
		}
		/*输出数据一般用Scanner*/
		Scanner scanner = new Scanner(System.in);
		int arg = scanner.nextInt();
		scanner.close();
		System.out.println(arg);
		
	}
	
}

</pre>