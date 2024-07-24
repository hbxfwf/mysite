# 循环综合练习、面试题讲解

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

