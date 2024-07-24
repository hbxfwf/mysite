# 循环结构

## 1、 while循环结构：

```java
public class Lesson1_06 {

	/**
	 * 案例一：打印1-100之间所有数字之和。
	 * 推导过程：
	 * i = 1,sum = 0 + 1
	 * i = 2,sum = 1 + 2
	 * i = 3,sum = 1 + 2 + 3
	 * i = 4,sum = 1 + 2 + 3 + 4
	 * ...
	 * i = 100,sum = 1 + 2 + 3 + 4 + ... + 100
	 * 得到如下结论：
	 * sum = sum + i;
	 * 简化成：
	 * sum += i;
	 */
	@Test
	public void test01() {
		// 1. 定义循环变量并初始化
		int i = 1;              // ① 循环变量初始化
		// 2. 定义存放结果的变量
		int sum = 0;
		// 3. 开始循环求和
		while (i <= 100) {      // ② 循环条件
			sum += i;          // 累加循环变量
			i++;               // ③ 循环变量修改
		}
		//4. 最后，打印结果
		System.out.println("sum = " + sum);
	}

	/**
	 * 案例二：打印输出1-100之间所有偶数，每10个一换行
	 * 分析过程：
	 * 1、偶数：能被2整除的数
	 * 2、每10个一换行，可以使用一个计数器，每找到一个偶数就累加计数器，如果计数器是10个倍数就打印换行！
	 */
	@Test
	public void test02() {
		// 2.1 定义循环变量及计数器变量
		int i = 1, count = 0;
		// 2.2 开始循环打印偶数
		System.out.println("1-100之间所有的偶数如下：");
		while (i <= 100){
			if(i % 2 == 0){     // i % 2 == 0: 证明i是偶数
				System.out.print(i + "\t");     // 打印偶数
				count++;                        // 累加计数器
				if(count % 10 == 0){            // 如果偶数个数是10个倍数就打印换行
					System.out.println();
				}
			}
			i++;
		}
	}
}

```

## 2、do...while循环：

> **while循环与do...while循环的区别**：
>
> 1、都需要循环三要素。
>
> 2、前者是判断再执行，如果条件不成立，则一次也不会执行！
>
> 3、后者是执行再判断，当条件不成立时，此时会至少执行一次！
>
> 4、适用于循环次数不固定的场景。

```java
public class Lesson2_02 {

	/**
	 * 比较while与do...while循环区别：
	 */
	@Test
	public void test01(){
		// 1. while循环
		int a = 10;
		System.out.println("while循环执行如下：");
		while(a > 20){
			System.out.println("hello,world");
			a++;
		}
		System.out.println("do...while的执行如下：");
		do{
			System.out.println("hello,world");
			a++;
		}while(a > 20);
	}

	public static void main(String[] args) {
		test02();
	}
	/**
	 * 打印菜单实现用户重复选择功能。
	 */

	private static void test02(){
		//1. 定义循环变量
		String iscon = "y";         // 用户是否继续选择菜单
		Scanner scanner = new Scanner(System.in);
		// 1.1 打印菜单
		System.out.println("=========================== 图书管理系统 ===========================");
		System.out.println("[1] 添加图书");
		System.out.println("[2] 查看图书");
		System.out.println("[3] 查找图书");
		System.out.println("[4] 修改图书");
		System.out.println("[5] 退出系统");
		System.out.println("==================================================================");
		do {
			// 1.2 用户选择：
			System.out.println("请选择：");
			int choice = scanner.nextInt();
			//1.3 根据选择判断
			switch (choice) {
				case 1:
					System.out.println("添加图书");
					break;
				case 2:
					System.out.println("查看图书");
					break;
				case 3:
					System.out.println("查找图书");
					break;
				case 4:
					System.out.println("修改图书");
					break;
				case 5:
					System.exit(0);             // 退出系统
					break;
			}
			System.out.println("是否继续?(y/n)");
			iscon = scanner.next();
		}while(iscon.equalsIgnoreCase("y"));        // equalsIgnoreCase()判断字符串是否相等时忽略大小写

		System.out.println("hello,我在循环外，你能怎么样？");
	}
}

```

## 3、for循环：

```java
public class Lesson2_03 {

	public static void main(String[] args) {
		// test02();
		test03();
	}


	/**
	 * 案例一：打印1-100之间所有的数字之和
	 */
	@Test
	public void test01(){
		//1. 定义一个累加的求和变量
		int sum = 0;
		//2. 开始求和
		for(int i = 1;i <= 100;i++){        //①循环变量初始化： int i = 1; ② 循环条件： i <= 100;  ③ 循环变量修改 ： i++
			// 3. 累加求和
			sum += i;
		}
		// 4. 打印求和结果
		System.out.println("sum = " + sum);

		/**
		 * 	for(①;②;③){
		 * 	   ④
		 * 	}
		 * ==================
		 * for循环执行流程分析：
		 * ==================
		 * 1、首先执行：int i = 1;  只执行一次
		 * 2、再执行循环条件：i <= 100;
		 * 3、当条件成立时，就执行循环体语句：sum += i;
		 * 4、最后，执行循环变量的累加
		 * 5、接着，再执行条件判断：i <= 100
		 * 6、条件成立再执行循环体语句
		 * 7、再执行循环变量的修改。
		 * 8、最后，总结流程：①②④③②④③②④③。。。
		 *
		 * ==================
		 * for循环适用场景：
		 * ==================
		 *   适用于循环次数固定的场合。
		 * while与do...while适用于：循环次数不固定的场景。
		 */
	}

	/**
	 * 案例二：：输入10个字符，判断其中数字和字母的个数？
	 * 分析：
	 * ① 需要输入，需要使用Scanner对象
	 * ② 输入10个字符，需要循环，因为次数固定，首选for
	 * ③ 需要准备两个计数器，分别代表数字及字母的个数，int m = 0,n = 0
	 * ④ 数字范围：i >= '0' && i <= '9'
	 *    字母的范围：(i >= 'A' && i <= 'Z') || (i >= 'a' && i <= 'z')
	 */
	private static void test02() {
		// 1. 定义代表数字及字母个数的计数器变量
		int m = 0,n = 0;
		// 2. 定义键盘扫描器对象
		Scanner scanner = new Scanner(System.in);
		// 3. 开始循环统计个数
		System.out.println("请输入10个字符：");
		String info = scanner.next();
		// 4. 取出每个字符 hello
		if(info.length() >= 10){
			for (int i = 0; i < 10; i++) {
				// 4.1 取得每个字符
				char ch = info.charAt(i);           // charAt(i): 代表取出位置i处的字符，i从0开始
				// 4.2 进行判断比较
				// 判断是否是数字
				if (ch >= '0' && ch <= '9'){
					m++;
				}
				// 判断是否是字母？
				if((ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z')){
					n++;
				}
			}
			// 5. 最后，打印字符的个数
			System.out.println("数字个数 ： " + m + ",字母的个数：" + n);
		}else{
			System.out.println("对不起，你输入的字符串少于10个！");
		}
	}

	/**
	 * 案例三：求输入一个数的阶乘?
	 * 阶乘: ！5 = 5 x 4 x 3 x 2 x 1
	 * 分析：
	 *   ① 联想到，累加求和，现在的情况变成了累积相乘了，此时初始值sum = 1，不能为0
	 *   ② 循环次数固定，首选for
	 *   ③ 需要输入，定义一个Scanner对象
	 *   ④ 定义存放求阶乘的变量，这个变量存放的数据大，可以使用long型。
	 */
	private static void test03() {
		// 1. 定义Scanner对象
		Scanner scanner = new Scanner(System.in);
		// 2. 开始输入
		System.out.println("请输入一个要求阶乘的变量：");
		int n = scanner.nextInt();
		// 3.定义存放阶乘的结果的变量
		long sum = 1;
		// 4. 开始求阶乘
		for (int i = 1; i <= n ; i++) {
			sum = sum * i;
		}
		// 5. 最后，打印数字的阶乘
		System.out.println(n + "的阶乘是：" + sum);
	}

}

```

## 4、 循环练习题：

> ### **案例一：求五个整数的平均值？**

```java
public class Lesson2_04 {

	public static void main(String[] args) {
		// test01();
		test02();
	}


	/**
	 * 案例一：求五个整数的平均值？
	 * 分析：
	 *   ① 输入五个整数，需要定义Scanner键盘扫描器对象，需要for循环。
	 *   ② 要对五个数累加求和。
	 *   ③ 最后，再计算平均值。
	 */
	private static void test01(){
		// 1. 定义键盘扫描器对象
		Scanner scanner = new Scanner(System.in);
		// 2. 定义存放五个数字和的变量及平均值变量
		int sum = 0;
		double avg ;
		// 3. 输入五个整数
		System.out.println("请输入五个整数：");
		// 4. 循环输入五次，累加到sum变量中
		for (int i = 0; i < 5; i++) {
			// 4.1 得到一个整数
			int num = scanner.nextInt();
			// 4.2 放到sum中
			sum += num;
		}
		// 5. 求平均值
		avg = sum / 5.0;
		System.out.println("五个数的平均值是： " + avg);
	}

}

```

> **案例二：求一个五位数是否是回文数字？**

```java
	/**
	 * 案例二：求输入的一个五位数是否是回文数字？
	 * 回文数字：
	 *    就是一个五位数，从左到到右与从右数到左是一样的。
	 * 分析:
	 *   ① 取出五位数各个位上的数字
	 *   ② 再将万位与个位比较、千位与十位比较，如果相等就是回文数字。
	 */
	private static void test02() {
		//1. 定义一个键盘扫描器对象
		Scanner scanner = new Scanner(System.in);
		//2. 开始输入一个五位数
		System.out.println("请输入一个五位数：");
		int num = scanner.nextInt();
		//3. 得到其各个位上的数字
		int ge = num % 10;                  // 个位
		int shi = num / 10 % 10;            // 十位
		int qian = num / 1000 % 10;         // 千位
		int wan = num / 10000;              // 万位
		//4. 比较是否相等
		if (ge == wan && shi == qian){
			System.out.println(num + "是一个回文数字。");
		}else{
			System.out.println(num + "不是一个回文数字。");
		}

	}
```

## 5、嵌套for循环：

> **案例一：打印直角三角形**

```java
/**
	 * 案例一：打印直角三角形
	 * 1*
	 * 2**
	 * 3***
	 * 4****
	 * 5*****
	 * 6******
	 * 分析特点：
	 *   1、需要两层循环
	 *   2、内层循环打印*号，*号的个数为行号
	 *   3、外层循环打印换行
	 */
	@Test
	public void test01(){
		for (int i = 1; i <= 6; i++) {      // i：外层循环变量，也是行号
			// 1. 内层循环打印*号
			for (int j = 1; j <= i ; j++) {
				System.out.print("* ");
			}
			// 2. 外层循环打印换行
			System.out.println();
		}
	}
```

> **案例二：打印九九乘法表。**

```java
/**
	 * 案例二：打印九九乘法表
	 */
	@Test
	public void test02(){
		for (int i = 1; i <= 9; i++) {      // i：外层循环变量，也是行号
			// 1. 内层循环打印*号
			for (int j = 1; j <= i ; j++) {
				System.out.print(j + "x" + i + "=" + i * j + "\t");
			}
			// 2. 外层循环打印换行
			System.out.println();
		}
	}
```

> **案例三：打印等腰三角形**

```java
/**
	 * 案例三：打印等腰三角形
	 *     *
	 *    ***
	 *   *****
	 *  *******
	 * *********
	 * 分析：
	 *  1、根据画图分析，找到如下空格、星号、行号i的变化规律：
	 *  2、空格个数为: 5 - i
	 *  3、星号*的个数：2 * i - 1
	 *  4、打印时先打印空格再打印星号
	 *  5、外层循环还是打印换行，内层循环一：打印空格 内层循环二：打印星号
	 */
	@Test
	public void test03(){
		for (int i = 1; i <= 5; i++) {
			// 1. 打印空格
			for (int j = 1; j <= 5-i; j++) {
				System.out.print(" ");
			}
			// 2. 打印*号
			for (int j = 1; j <= 2 * i -1 ; j++) {
				System.out.print("*");
			}
			//3. 打印换行
			System.out.println();
		}
	}
```

## 6、流程控制语句：

### 1、break语句：

```java
/**
	 * 案例一：打印1-1000个位数是3的数字，只打印前5个
	 * 分析：
	 * 1、循环次数固定，首选for循环。
	 * 2、个位数是3，i % 10 == 3
	 * 3、只打印前5个，可以定义一个计数器，统计出5个满足条件的数字就退出。
	 */
	@Test
	public void test01(){
		// 1. 定义计数器变量
		int count = 0;
		//2. 开始循环打印
		System.out.println("1-1000之间个位数是3的前5个数字如下：");
		for (int i = 1; i <= 1000 ; i++) {
			if(i % 10 == 3){            // 代表个位数是3的数字
				System.out.print(i + "\t"); // 打印个位数是3的数字
				count++;                    // 累加计数器
				if(count == 5){             // 找到满足条件的数字有5个就退出
					break;
				}
			}
		}
		// break：代表退出其所在的哪层循环。
	}
```

### 2、continue:

```java
	/**
	 * 案例二：打印1-100之间所有奇数之和。
	 * 分析：
	 *   1、1-100循环次数固定，首选for
	 *   2、打印奇数，我们可以跳过偶数，使用continue，代表退出本次循环，接着执行下一次循环。
	 *   3、定义一个求和变量，将奇数累加求和
	 */
	@Test
	public void test03(){
		// 1. 定义求和变量
		int sum = 0;
		// 2. 开始求奇数之和
		for (int i = 1; i <= 100 ; i++) {
			// 2.1 如果是偶数就跳过,其后的代码就不再执行
			if(i % 2 == 0){
				continue;
			}
			// 2.2 累加循环变量
			sum += i;
		}
		// 3. 打印求和结果
		System.out.println("sum = " + sum);
	}
```

> **continue与break区别：**
>
> 1、前者是退出本次循环，后者就是退出它所在的哪层循环.
>
> 2、break可以用在循环中也可以用在switch...case中，代表退出switch...case结构。
>
> 3. continue只能用在循环中。

### 3、return语句：

```java
/**
	 * 案例三：将1-100之间前3个个位数是3的数字之和。
	 * 分析：
	 *  1、1-100之间的数字，循环次数固定，首选for
	 *  2、个位数是3，i % 10 == 3代表。
	 *  3、求数字之和，定义一个求和变量sum=0
	 *  4、定义一个计数器，找到满足条件的数字就累加求和，直到累加3个就停止并退出。
	 */
	@Test
	public void test04(){
		// 1. 定义求和变量与计数器变量
		int sum = 0,count = 0;
		// 2. 开始循环求和
		System.out.println("1-100之间个位数是3的前3个数字如下：");
		for (int i = 1; i <= 100 ; i++) {
			// 2.1 代表个位数是3的数字
			if(i % 10 == 3){
				sum += i;               // 累加求和
				count++;                // 累加计数器
				System.out.print(i + "\t");
				if(count == 3){
					System.out.println("\nsum = " + sum);
					return;
				}
			}
		}
		System.out.println("break可以看到，return看不到！");
	}
```

> **return与break语句区别：**
>
> 1、前者是代表退出当前所在的方法（函数），其后的代码不会执行。
>
> 2、后者代表退出其所在的循环，循环外的代码还是会执行。

## 7、 循环综合练习、面试题讲解：

> **案例一**：输入五个整数，打印个位数是3的数字个数。

```java
/**
	 * 案例一：找出五个数字中个位数是3的数字个数?
	 * 分析：
	 *  1、输入五个数，需要使用Scanner键盘扫描器对象。
	 *  2、输入五次，需要使用for循环。
	 *  3、个位数是3的数字，i % 10 == 3,代表个位数是3，此时可以定义一个计数器count=0，在此累加计数器
	 * 考查知识点：
	 *  ① 输入与输出 ② for循环 ③ if条件结构 ④ 比较运算符与算术运算符
	 */
	private static void test01() {
		// 1. 定义扫描器对象
		Scanner scanner = new Scanner(System.in);
		// 2. 定义一个计数器，用于统计个位数是3的数字的个数
		int count = 0;
		// 3. 提示输入
		System.out.println("请输入五个整数：");
		for (int i = 0; i < 5; i++) {
			// 3.1 代表输入的一个数字
			int num = scanner.nextInt();
			// 3.2 判断个位数是否是3
			if(i == 0){
				System.out.println("个位数是3的数字如下：");
				System.out.println("-----------------------------");
			}
			if(num % 10 == 3){          // 证明个位数是3
				count++;                // 累加计数器
				System.out.print(num + "\t");
			}
		}
		System.out.println("\n个位数是3的数字一共有：" + count + "个！");
	}
```

> **案例二**：使用switch...case结构实现根据学生成绩打印成绩评分

```java
/**
	 * 案例二：使用switch...case结构实现根据学生成绩打印成绩评分
	 * （90-100：评分‘A’ 80-90：评分‘B’70-80：评分 'C' 60-70：评分‘D’60分以下：评分‘E’）
	 * 分析：
	 *  1、己知题目说明只能使用switch...case结构完成。
	 *  2、考虑：将分数除以10得到的商进行比较，
	 */
	private static void test02() {
		// 1. 定义键盘扫描器对象
		Scanner scanner = new Scanner(System.in);
		//2. 开始输入学生成绩
		System.out.println("请输入学生成绩：");
		int score = scanner.nextInt();
		//3. 将成绩除以10再进行比较
		if(score >= 0 && score <= 100){
			switch (score / 10){
				case 10:
				case 9:
					System.out.println("优秀");
					break;
				case 8:
					System.out.println("良好");
					break;
				case 7:
					System.out.println("一般");
					break;
				case 6:
					System.out.println("及格");
					break;
				case 5:
				case 4:
				case 3:
				case 2:
				case 1:
				case 0:
					System.out.println("不及格");
					break;
			}
		}else{
			System.out.println("输入不合法!");
		}

	}
```

> **案例四**：随便输入10个数字，判断10个数中奇数和偶数的个数？

```java
/**
	 * 案例四：随便输入10个数字，判断10个数中奇数和偶数的个数？
	 * 分析：
	 * 1、输入10个整数，需要使用for循环，定义Scanner扫描器对象
	 * 2、奇数就可以使用：i % 2 == 1
	 * 3、偶数就可以使用：i % 2 == 0
	 * 4、统计个数可以使用计数器，这里可以声明一个count=0，代表偶数个数，奇数就是10-count
	 * 考查知识点：
	 *  for循环、输入、奇数与偶数的判断、计数器的使用。
	 */
	private static void test04() {
		// 0. 定义键盘扫描器对象，用于输入
		Scanner scanner = new Scanner(System.in);
		// 1. 定义计数器变量,代表奇数的个数
		int count = 0;
		// 2. 输入10个整数：
		System.out.println("请输入10个整数：");
		// 3. 开始计算奇数和偶数的个数
		for (int i = 0; i < 10; i++) {
			// 3.1 输入一个整数：
			int num = scanner.nextInt();
			// 3.2 如果是奇数就累加计数器
			if(num % 2 == 1){
				count++;
			}
		}
		// 4. 最后，打印结果
		System.out.println("输入的10个整数中奇数有：" + count + "个，偶数有：" + (10-count) + "个！");
	}
```

> **案例五**：如何交换两个变量？

```java
/**
	 * 交换两个变量（方法一:借助第三方变量）
	 */
	@Test
	public void test01(){
		//1. 定义两个变量
		int a = 10,b = 5;
		// 2. 再定义第三方临时变量
		int temp ;
		//2. 开始交换两个数
		System.out.println("交换前：a = " + a + ",b = " + b);
		temp = a;
		a = b;
		b = temp;
		System.out.println("交换后：a = " + a + ",b = " + b);
	}

	/**
	 * 交换两个变量（方法二：不借助第三方变量: 加减法）
	 */
	@Test
	public void test02(){
		//1. 定义两个变量
		int a = 10,b = 5;
		System.out.println("交换前：a = " + a + ",b = " + b);
		// 2. 开始交换两个变量的值
		a = a + b;
		b = a - b;
		a = a - b;
		System.out.println("交换后：a = " + a + ",b = " + b);
	}
	/**
	 * 交换两个变量（方法三：不借助第三方变量: 乘除法）
	 */
	@Test
	public void test03(){
		//1. 定义两个变量
		int a = 10,b = 5;
		System.out.println("交换前：a = " + a + ",b = " + b);
		// 2. 开始交换两个变量的值
		a = a * b;
		b = a / b;
		a = a / b;
		System.out.println("交换后：a = " + a + ",b = " + b);
	}
```

> **案例六：**打印1-60之间的安全数？

```java
/**
	 * 案例一：
	 * 报7游戏的安全数。
	 * 大家从小到大，都玩儿过的一个庸俗的游戏：
	 * 游戏玩儿法就是，大家轮流报数，如果报到能被7整除的数字，或者尾数是7的数字，都算踩地雷了。就应该罚唱歌。
	 * 请在控制台输出1~60之间的所有“安全数”。
	 * 分析：
	 * 1、将能被7整除的数字及个位数是7的数字跳过，使用continue，其它就是安全数
	 * 2、这里循环60次，可以使用for循环
	 */
	@Test
	public void test01(){
		// 1. 定义一个计数器，我们10个一换行
		int count = 0;
		System.out.println("1-60之间的安全数如下：");
		System.out.println("-----------------------------------------------");
		for (int i = 1; i <= 60 ; i++) {
			if(i % 7 == 0 || i % 10 == 7){
				continue;
			}
			// 2. 累加计数器
			count++;
			System.out.print(i + "\t");
			// 3. 如果是10个倍数就打印换行
			if(count % 10 == 0){
				System.out.println();
			}
		}
	}
```

> **案例七：**打印1-1000之间的完数？

```java
/**
	 * 案例六：打印1-1000之间的完数。
	 * 分析：
	 * 1、完数：就是一个数，将其拆分成各个因子(分子不能是1)，将各个因子加起来等于它自身，如：6 = 6/6 + 6/3 + 6/2
	 * 2、如何求因子，考虑使用两层循环解决：
	 *    ① 外层循环定义一个求和变量sum = 0
	 *    ② 内层循环解决找因子，可以考虑，将外层循环变量i除以内层循环变量j，如果除得尽证明找到因子，这个因子就是: i / j
	 *       然后将这个因子（i/j）进行累加到sum中
	 *    ③ 在外层循环最后，判断sum是否等于外层循环变量i，如果相等就是完数。
	 */
	@Test
	public void test04(){
		System.out.println("1-1000之间的完数如下：");
		System.out.println("-------------------------------");
		for (int i = 1; i <= 1000 ; i++) {
			// 1. 定义求因子之和的变量
			int sum = 0;
			// 2. 内层循环求因子之和
			for (int j = 2; j <= i ; j++) {
				if(i % j == 0){
					sum +=  i/j;            // i/j: 代表一个因子
				}
			}
			if(sum == i){
				System.out.print(i + "\t");
			}
		}
	}
```

