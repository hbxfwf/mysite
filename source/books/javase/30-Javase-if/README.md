# 条件结构

## 1、if条件结构

```java
/**
	 * if条件结构-简单if
	 */
	@Test
	public void test01(){
		// 1.1 获取当前时间的小时数
		int hour = LocalDateTime.now().getHour();
		System.out.println("hour = " + hour);
		// 1.2 判断小时数是否大于12，如果大于则打印下午好
		if(hour > 12){
			System.out.println("下午好！");
		}
	}

	/**
	 * if...else结构
	 */
	@Test
	public void test02(){
		// 1.1 获取当前时间的小时数
		int hour = LocalDateTime.now().getHour();
		// 1.2 判断小时数，如果大于12点，打印下午好，否则，打印上午好
		if(hour > 12){
			System.out.println("下午好");
		}else{
			System.out.println("上午好");
		}
	}
	/**
	 *  多重if结构
	 *  案例：根据当前时间打印问候信息!
	 */
	@Test
	public void test03(){
		// 1.1 获取当前时间的小时数
		int hour = LocalDateTime.now().getHour();
		// 1.2 根据小时数打印评语信息
		if(hour < 9){
			System.out.println("早上好");
		}else if (hour < 12){
			System.out.println("上午好");
		}else if(hour < 14){
			System.out.println("中午好");
		}else if(hour < 18){
			System.out.println("下午好");
		}else{
			System.out.println("晚上好");
		}
	}

```

## 2、switch...case结构：

```java
/**
	 * 案例一：根据输入的字符判断是否是元音字母？
	 * 方法一：不省略break
	 */
	private static void test01() {
		// 1. 定义键盘扫描器对象
		Scanner scanner = new Scanner(System.in);
		System.out.println("请输入一个字母：");
		String ch = scanner.next();
		// 2. 开始判断是否是元音字母
		switch (ch){
			case "a":
				System.out.println("a是一个元音字母。");
				break;
			case "e":
				System.out.println("e是一个元音字母。");
				break;
			case "i":
				System.out.println("i是一个元音字母。");
				break;
			case "o":
				System.out.println("o是一个元音字母。");
				break;
			case "u":
				System.out.println("u是一个元音字母。");
				break;
			default:
				System.out.println(ch + "不是一个元音字母。");
				break;
		}
	}

	/**
	 *  方法二：省略break简化代码书写
	 */
	private static void test02() {
		// 1. 定义键盘扫描器对象
		Scanner scanner = new Scanner(System.in);
		System.out.println("请输入一个字母：");
		String ch = scanner.next();
		// 2. 开始判断是否是元音字母
		// 2. 开始判断是否是元音字母
		switch (ch){
			case "a":
			case "e":
			case "i":
			case "o":
			case "u":
				System.out.println(ch + "是一个元音字母。");
				break;
			default:
				System.out.println(ch + "不是一个元音字母。");
				break;
		}
	}
```

> **switch...case与if结构比较：**
>
> 1、前者只适用于等值比较，让程序看上去可读性更好一点。
>
> 2、后者代表一个范围值的比较，能用switch...case结构的一定能用if条件。

> **switch...case结构语法注意事项**
>
> 1、switch结构后只能是： byte/short/int/char/String/enum/Byte/Integer/Short/Character,不能是long型
>
> 2、case后的常量值不能重复，否则，报错!
>
> 3、每个case后都有一个break语句，如果某个判断成立就执行对应的case后语句块，遇到break就退出这个switch结构。
>
> 4、如果省略了break，则程序一直向下执行，直到遇到第一个break才停止
>
> 5、default:代表所有的条件都不成立时，将执行的代码块，可以放在程序的任意地方，我们一般习惯于放最后！   