# 运算符与表达式

> **算术运算符：**

```java
/**
	 * 算术运算符：
	 * 1、双目运算符：有两个运算数参与（+ - * / %）
	 * 2、单目运算符：只有一个运算数参数(++ --) [*****重难点*****]
	 */
	private static void test01() {
		// 1. 双目运算符：
		int  a = 10;
		int b = 3;
		System.out.println("a + b = " + (a + b));
		System.out.println("a - b = " + (a - b));
		System.out.println("a * b = " + (a * b));
		System.out.println("a / b = " + (a / b));
		System.out.println("a % b = " + (a % b));

		System.out.println("------------------------------------");
		// 2. 单目运算符（++ --）
		// 2.1 ++运算符
		// 2.1.1  前加
		// 情况一：单独使用时
		++a;                    // 相当于：a = a + 1
		System.out.println("a = " + a);
		// 情况二：与表达式一起使用时
		int c = ++a;           // 相当于：① a = a + 1; ② c = a;
		System.out.println("c = " + c + ",a = " + a);

		// 2.1.2 后加
		// 情况一：单独使用时
		a++;                   // 相当于：a = a + 1;
		System.out.println("a = " + a);
		// 情况二：与表达式一起使用时
		c = a++;               // 相当于：① c = a; ② a = a + 1;
		System.out.println("c = " + c + ",a = " + a);

		// 2.2 --运算符
		// 2.2.1  前减
		// 情况一：单独使用时
		--a;                  // 相当于：a = a -1;
		System.out.println("a = " + a);
		// 情况二：与表达式一起使用时
		c = --a;             // 相当于：① a = a - 1; ② c = a;
		System.out.println("c = " + c + ",a = " + a);
		// 2.2.2 后减
		// 情况一：单独使用时
		a--;                // 相当于：a = a -1;
		System.out.println("a = " + a);
		// 情况二：与表达式一起使用时
		c = a--;            // 相当于：① c = a; ② a = a - 1;
		System.out.println("c = " + c + ",a = " + a);

	}
```

> **关系运算符：**

``` java
/**
	 * 关系运算符：> >= < <= == !=
	 * 用在关系表达式(返回的是一个布尔值)中，代表比较大小。
	 */
	private static void test02() {
		//1. 定义两个变量
		int a = 10,b = 5;
		boolean  b1 = a > b;
		System.out.println("b1 = " + b1);
		boolean b2 = a == b;
		System.out.println("b2 = " + b2);
		boolean b3 = a <= b;
		System.out.println("b3 = " + b3);
	}
```

> **赋值运算符：**

``` java
/**
	 * 赋值运算符：(= += -= *= %=)
	 */
	private static void test03() {
		// 1. 简单赋值运算符=(等号右边的值赋给=号左边的变量)
		int a = 10;
		System.out.println("a = " + a);
		// 2. 复合赋值运算符
		a += 5;
		System.out.println("a = " + a);
		a -= 3;
		System.out.println("a = " + a);
		a *= 2;
		System.out.println("a = " + a);
		a /= 5;
		System.out.println("a = " + a);
		a %= 5;
		System.out.println("a = " + a);
	}

```

> **逻辑运算符：**

```java
/**
	 * 逻辑运算符(&& || !)：用于连接多个关系表达式。
	 */
	private static void test04() {
		// 1. 逻辑与&&用法:
		// 1.1 普通用法：代表的是多个参与运算的表达式，都返回true,整个表达式才返回true
		int a = 10,b = 5,c = 8,d = 17;
		if (a > b && c > d){
			System.out.println("条件成立。");
		}else{
			System.out.println("条件不成立。");
		}
		// 1.2 短路用法：参与运算的多个表达式，只要有一个为false,此时就不会再向后执行了，整个表达式就返回false,
		if(a++ < --b && ++c < d--){
			System.out.println("------条件成立--------。");
		}
		System.out.println("a = " + a + ",b = " + b + ",c = " + c + ",d = " + d);

		// 2. 逻辑或||用法：
		// 2.1 普通用法：代表的是多个参与运算的表达式，每个表达式为false，整个表达式才为false
		boolean b1 = a < b || c > d;
		System.out.println("b1 = " + b1);
		// 2.2 短路用法：参与运算的多个表达式只要有一个为true,后面的表达式就不参与运算了。
		boolean b2 = a++ > --b || d-- < c++;
		System.out.println("b2 = " + b2);
		System.out.println("a = " + a + ",b = " + b + ",c = " + c + ",d = " + d);

		// 3. 逻辑非（取反）：
		boolean b3 = !b2;
		System.out.println("b3 = " + b3);
	}
```

> **运算符的优先级**：（由高到低）
>
> 算术运算 》 关系运算符 》逻辑运算符 》 赋值运算符

```java
（）
 ++ -- ！
 * / % 
 + - 
 > >= < <= == !=
 &&
 ||
 = += -= *= /= %=  
```