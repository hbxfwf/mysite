# Java变量与数据类型

> **Java中变量命名原则**：
>
> 1. 变量名只能是数字、字母、下划线、$这四种字符组成，首字符不能是数字
> 2. 变量名不能是系统关键字，如：public static  String int float....
> 3. 变量名区分大小写的，如：Name与name是代表两个不同的变量

> **Java变量命名规范：**
>
> 1. java的变量名一般使用驼峰式命名法(首单词的首字母小写，其它单词的首字母必须要大写，如：helloWorld)
> 2. java的变量名尽量做到见名知义，name代表人的姓名，age代表代表人的年龄

```java
public class Lesson1_01 {
	public static void main(String[] args) {
		System.out.println("hello，java");
		int $a3 = 10;
		int b = 1;
		String name = "张三";
		String Name = "李四";
		System.out.println(name + "," + Name);
		String helloWorld = "nihao";
	}
}

```



## 数据八种基本类型：

> 八种基本类型(整型、浮点型、布尔型、字符串)

```java
public class Lesson1_02 {

	/**
	 * java的文档注释
	 * 八种基本类型(整型、浮点型、布尔型、字符串)
	 */
	public static void main(String[] args) {
		// 1. 整型(byte short int long)
		// test01();
		// 2. 浮点型(float double)
		// test02();
		// 3. boolean布尔型
		// test03();
		// 4. 字符型(char)
		test04();
	}
	/**
	 * 1. 整型(byte short int long)
	 * byte: 字节型，占1一字节，8位
	 * short: 短整型，占2个字节，16位
	 * int：整型，4个字节，32位
	 * long：长整型，8个字节，64位
	 */
	private static void test01() {
		// 第一部分：Byte字节型
		// 1.1 声明一个字节型
		byte b = -128;
		// 1.2 查看字节型范围
		byte maxValueByte = Byte.MAX_VALUE;
		byte minValueByte = Byte.MIN_VALUE;
		System.out.println("minValueByte = " + minValueByte);         // minValue_byte = -128
		System.out.println("maxValue_byte = " + maxValueByte);         // maxValue_byte = 127

		// 第二部分：Short短整型
		short s = 123;
		short minValueShort = Short.MIN_VALUE;
		short maxValueShort = Short.MAX_VALUE;
		System.out.println("minValueShort = " + minValueShort);
		System.out.println("maxValueShort = " + maxValueShort);

		// 第三部分：int整型
		int a = 12345;
		int minValueInt = Integer.MIN_VALUE;
		int maxValueInt = Integer.MAX_VALUE;
		System.out.println("maxValueInt = " + maxValueInt);
		System.out.println("minValueInt = " + minValueInt);

		// 第四部分：long型
		long l = 123;
		long minValueLong = Long.MIN_VALUE;
		long maxValueLong = Long.MAX_VALUE;
		System.out.println("minValueLong = " + minValueLong);
		System.out.println("maxValueLong = " + maxValueLong);

	}
	/**
	 * 浮点型（float double）
	 * 1. float单精度浮点型，占4字节，保留小数后七位
	 * 2. double双精度浮点型，占8字节，保留小数后15位
	 */
	private static void test02() {
		// 1.1 单精度浮点型(float)
		// float f = 2.345;                //（错误的赋值方法演示） 因为java中的小数默认为double类型，所以这里为报错！
		float f1 = 2.345f;                 // 正确的方式：可以转换为float就正常了
		float f2 = (float) 2.345;          // 正确的方式
		float f3 = 2.32324234234234324324234f;
		System.out.println("f3 = " + f3);
		// 1.2 双精度浮点型(double)
		double d1 = 2.33434222324242342343243242;
		System.out.println("d1 = " + d1);
		// 1.3 当单精度与int计算时，返回结果是一个单精度类型
		float f4 = f1 + 1;
		// 1.4 当双精度与long计算时，返回结果是一个双精度类型
		double l = d1 + 100L;
	}

	/**
	 * 1. 布尔型boolean,可能取值true或false，
	 *     true: 代表真 false：代表假
	 */
	private static void test03() {
		boolean b1 = true;
		System.out.println("b1 = " + b1);
		b1 = !b1;
		System.out.println("b1 = " + b1);

	}

	/**
	 * 字符型char:
	 * 占两个字节，可以存放汉字。
	 *
	 */
	private static void test04() {
		//1. 声明一个字符型
		char ch = 'a';
		// 2. 字符型与键盘上的ascii码值对应：
		// 如：'a'-'z': 97-122
		// 'A-'-'Z': 65-90
		// '0'-'9': 48-57
		int ch1 = ch - 2;
		System.out.println("ch1 = " + ch1);
		// 案例：将小写字母转换为对应的大写字母？
		char ch2 = 'd';
		char ch3 = (char) (ch2 - ('a' - 'A'));
		System.out.println("ch3 = " + ch3);
	}

}

```

