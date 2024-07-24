# 数组

## 1、数组的定义与声明：

```java
/**
	 * 一维数组的定义与声明
	 */
	@Test
	public void test01(){
		/**
		 * 1. 定义一个数组
		 * 基本理论：
		 * 1.1 数组中存放相同的数据类型的数据
		 * 1.2 数组要指定长度，才能为其分配空间。
		 * 1.3 数组的读写（访问）方式，可以使用数组的下标访问，下标的范围为[0,长度-1]
 		 */
		// 第一种方案：先声明再赋值
		// 第一步：先声明数组：
		int[] a = new int[5];           // 5：代表只能存放5个整数，并且开辟了5个整数的内存空间，5x4 = 20字节,数组下标从0开始，下标范围只能是[0,数组长度-1]
		// 第二步：为数组赋值
		a[0] = 'b';
		a[1] = 1;
		a[2] = 5;
		a[3] = 100;
		a[4] = 9;
		// a[5] = 18;                      // ArrayIndexOutOfBoundsException: 超过了数组下标范围，出现：数组下标越界异常
		System.out.println("hello");

		System.out.println(a[0]);

		// 第二种方案：声明的同时为其赋值：
		int[] b = new int[]{1,2,3};         // 正确的声明并赋值方式，这种方式不要自己指定长度，让系统自己计算，此时数组的个数是3个
		int[] c = {1,2,3,4,5};              // 正确的声明并赋值方式，简化版的，开发中经常使用,此时数组个数为5个

		// c[5] = 10;                       // 不能赋值,下标越界 ArrayIndexOutOfBoundsException
		

	}
```

```java
/**
	 * 二维数组的定义与声明
	 */
	@Test
	public void test02(){
		// 1. 声明一个二维数组
		int[][] a = new int[3][];           // 第一个中括号中的数字代表行数,第二个中括号数字代表列数
		// 2. 为二维数组分配空间:
		a[0] = new int[5];
		a[1] = new int[4];
		a[2] = new int[3];
		// a[3] = new int[2];               // ArrayIndexOutOfBoundsException 下标越界异常
		//3. 修改元素的内容
		a[1][0] = 11;
		a[1][1] = 12;
		a[1][2] = 13;
		a[1][3] = 14;
		// a[1][5] = 15;                    // ArrayIndexOutOfBoundsException 下标越界
		// 4. 打印每一行每一列的数据
		for (int i = 0; i < a.length; i++) {                // a.length: 代表数组的长度
			// 4.1 循环每一行的每一列的数据
			for (int j = 0; j < a[i].length; j++) {         // a[i].length: 代表一个数组
				System.out.print(a[i][j] + "\t");
			}
			// 4.2 打印完一行后来个换行
			System.out.println();
		}
	}
```

## 2、数组的应用（常用算法）：

> **案例一：**在数组中查找最值？

```java
/**
	 * 案例一: 在数组中查找最大值与最小值
	 * 分析:
	 * 1、以数组的第一个元素作为最大或最小值，以数组a为例。max = a[0] ; min = a[0];
	 * 2、找最大值：
	 *    循环数组，将数组中的第二个元素开始与最大值进行比较，如果当前元素比最大值还大，最大值max就变成当前元素a[i]
	 * 3、找最小值：
	 *    循环数组，将数组中的二个元素开始与最小值比较，如果比最小值还小，此时最小值min就换成当前元素a[i]
	 */
	@Test
	public  void test01() {
		// 1. 定义一个数组：
		int [] a = {1,0,10,4,5,9,7};
		// 2. 假设第一个元素为最大值或最小值
		int max = a[0];
		int min = a[0];
		// 3. 循环找最大值或最小值
		for (int i = 0; i < a.length; i++) {
			//3.1 找最大值
			if(a[i] > max){
				max = a[i];
			}
			// 3.2 找最小值
			if(a[i] < min){
				min = a[i];
			}
		}
		// 4. 打印最大值与最小值
		System.out.println("min = " + min  + ",max = " + max);
	}
```

> **案例二**：在数组中查找元素？(无重复元素)
>
> 查找数组元素【**方法一**】

```java
/**
	 * 案例一：在数组中查找元素（只出现一次），并打印元素在数组中的下标
	 * 分析[方法一]：
	 *  1、假疫要找到的元素为2
	 *  2、我们可以遍历数组，将数组中的每个元素与2比较如果相等就找到，并打印数组的下标
	 */
	@Test
	public void test01(){
		// 1. 定义一个数组
		int [] a = {3,1,9,10,2,19,5,6,4};
		// 2. 定义要查找的元素
		int e = 10;
		// 3. 定义要找到的元素在数组中下标
		int index = -1;
		// 4. 遍历数组，看是否能找到元素
		for (int i = 0; i < a.length; i++) {
			// 4.1 如果找到了元素就将其赋值给index
			if(a[i] == e){
				index = i;
				break;
			}
		}
		//5. 判断是否找到元素
		if( index >= 0){
			System.out.println("在位置" + index + "处找到元素" + e + "!");
		}else{
			System.out.println("没有找到元素" + e + "!");
		}

	}
```

> 查找数组元素【**方法二**】

```java
/**
	 * 案例一：在数组中查找元素（只出现一次），并打印元素在数组中的下标
	 * 方法二：
	 * 1、如果在遍历数组时找到某个元素，则当退出循环时，i的值一定要小于数组的长度a.length
	 * 2、所以，我们可以根据循环完成后这个i的值是否小于a.length来判断是否找到元素，从而打印其下标
	 *   如果找到元素，则其下标就是i
	 */
	@Test
	public void test02(){
		// 1. 定义一个数组
		int [] a = {3,1,9,10,2,19,5,6,4};
		// 2. 定义要查找的元素
		int e = 19;
		// 3. 遍历查找元素
		int i = 0;
		for (; i < a.length; i++) {
			if(a[i] == e){
				break;
			}
		}
		// 4. 根据i与a.length的关系确定找到了元素的下标的值
		if(i == a.length){
			System.out.println("没有找到元素" + e + "!");
		}else{
			System.out.println("在位置" + i + "找到元素" + e + "!");
		}
	}
```

> 数组中查找元素【**方法三**】

```java
/**
	 * 案例一：在数组中查找元素（只出现一次），并打印元素在数组中的下标
	 * 方法三：
	 * 1、 使用流程控制语句return，如果找到了就返回方法，没有找到就在循环外面打印”没有找到！“
	 */
	@Test
	public void test03(){
		// 1. 定义一个数组
		int [] a = {3,1,9,10,2,19,5,6,4};
		// 2. 定义要查找的元素
		int e = 190;
		// 3. 开始循环找到元素
		for (int i = 0; i < a.length; i++) {
			if(a[i] == e){
				System.out.println("在位置" + i + "找到元素" + e + "!");
				return;
			}
		}
		System.out.println("没有找到元素" + e + "!");
	}
```

> 在数组中查找元素【有重复元素】

> **方法一：**利用新数组实现

```java
/**
	 *  案例三：在数组中查找有重复元素的下标，并打印下标
	 *  分析【方法一】：
	 *  1、将找到的元素的下标放到一个新的数组中
	 *  2、所以，我们要确定新数组的下标及长度。
	 *  3、新数组的长度为何？
	 *    3.1 新数组的长度等于原数组的长度。
	 *  4. 定义一个计数器同时充当下标？
	 *     int count = 0;
	 */
	@Test
	public void test01(){
		//1. 声明一个数组
		int[] a = {3,1,9,10,3,1,3,1,9,8,7,10,1,4,2,1};
		//2. 定义一个新数组用于存放找到的元素的下标
		int[] b = new int[a.length];
		// 3. 定义计数器同时充当新数组的下标
		int count = 0;
		// 4. 定义要查找的元素
		int e = 1;
		// 5. 开始遍历数组a进行查询
		for (int i = 0; i < a.length ; i++) {
			if(a[i] == e){
				b[count++] = i;
			}
		}
		// 6. 最后，打印下标
		if(count > 0){
			System.out.println("在如下位置找到了元素" + e + ":");
			for (int i = 0; i < count; i++) {
				System.out.print(b[i] + "\t");
			}
		}else{
			System.out.println("没有找到元素" + e + "!");
		}
	}
```

> **方法二：**利用字符串存放下标

```java
/**
	 * 案例三：在数组中查找有重复元素的下标，并打印下标
	 * 方法二：
	 *   可以将找到的元素的下标放到一个字符串中，将字符串连接起来即可。
	 */
	@Test
	public void test02(){
		//1. 声明一个数组
		int[] a = {3,1,9,10,3,1,3,1,9,8,7,10,1,4,2,1};
		// 2. 定义存放找到的元素下标的字符串
		String info = "";
		// 3. 定义要查找的元素
		int e = 100;
		// 4. 开始查找字符串
		for (int i = 0; i < a.length; i++) {
			if(e == a[i]){
				info += i + " ";
			}
		}
		// 5. 打印找到的下标
		if(info.length() > 0){
			System.out.println("在位置" + info + "找到元素" + e + "!");
		}else{
			System.out.println("没有找到元素" + e + "!");
		}
	}
```

## 3、常用类

> **1、数学类Math**

```java
/**
	 * 数学类Math类的用法
	 */
	@Test
	public void test01(){
		//1. 求指定数字的绝对值
		int abs = Math.abs(-10);
		System.out.println("abs = " + abs);
		// 2. 返回两个数的最大值、最小值
		int max = Math.max(1,10);
		int min = Math.min(1,10);
		System.out.println("min = " + min);
		System.out.println("max = " + max);
		// 3. 求指定数的n次幂
		double pow = Math.pow(2, 3);
		System.out.println("pow = " + pow);
		// 4. 求指定数的平方根
		double sqrt = Math.sqrt(2);
		System.out.println("sqrt = " + sqrt);
		// 5. 返回一个随机小数[0,1)
		double random = Math.random();
		System.out.println("random = " + random);
		// 6. 返回一个比给定数小的最大整数(向下取整)
		double floor = Math.floor(3.14);
		// 7. 返回一个比给定数大的最小整数（向上取整）
		double ceil = Math.ceil(3.14);
		System.out.println("floor = " + floor);
		System.out.println("ceil = " + ceil);
		// 8. 得到圆周率的值
		double pi = Math.PI;
		System.out.println("pi = " + pi);
		// 9. 返回一个弧度的正弦值
		double sin = Math.sin(Math.PI / 3);
		System.out.println("sin = " + sin);
		// 10. 返回一个给定数的四舍五入值(将指定值加上0.5取整)
		long round = Math.round(3.556);
		System.out.println("round = " + round);
	}
```

> **2、字符串处理类**：String与StringBuffer

```java
/**
	 * 1. String类的用法
	 * 字符串的特点：
	 * 1、每次都会生成一个新的字符串，而原来的字符串会变成垃圾字符串，会让JVM在合适的时候进行回收！
	 */
	@Test
	public void test01(){
		// 1. 定义一个字符串
		String info = "hello,world,welcome";
		// 2. 返回字符串长度
		int length = info.length();
		System.out.println("length = " + length);
		// 3. 返回指定位置的字符
		char charAt = info.charAt(1);
		System.out.println("charAt = " + charAt);
		// 4. 返回指定字符第一次出现的下标
		int index = info.indexOf('o');
		System.out.println("index = " + index);
		// 5. 返回指定字符最后一次出现的下标
		int lastIndexOf = info.lastIndexOf('o');
		System.out.println("lastIndexOf = " + lastIndexOf);
		// 6. 将指定字符串转换为大写
		String toUpperCase = info.toUpperCase();
		System.out.println("toUpperCase = " + toUpperCase);
		// 7. 将指定字符串转换为小写
		String toLowerCase = toUpperCase.toLowerCase();
		System.out.println("toLowerCase = " + toLowerCase);
		// 8. 拆分字符串
		String[] split = info.split(",");           // 指定的符号，是指按照什么符号进行拆分
		for (String s : split) {
			System.out.println(s);
		}
		// 9. 字符串的替换
		String replace = info.replace("o", "O");
		System.out.println("replace = " + replace);
		// 10. 是否包含指定的字符串
		boolean contains = info.contains("llo");
		System.out.println("contains = " + contains);
		// 11. 是否以指定字符串开头
		boolean startsWith = info.startsWith("he");
		System.out.println("startsWith = " + startsWith);
		// 12. 是否以指定字符串结束
		boolean endsWith = info.endsWith("come1");
		System.out.println("endsWith = " + endsWith);
		// 13. 字符串截取
		// 13.1 第一种：从指定位置开始截取到结束
		String substring = info.substring(6);
		System.out.println("substring = " + substring);
		// 13.2 第二种：指定位置开始截取到结束到结束位置
		String substring1 = info.substring(6, 11);          // 两个数字类型的参数，一定是左闭右开区间，[6,11)
		System.out.println("substring1 = " + substring1);
		// 14. 去除字符串前后空格
		String str = "    to you!   ";
		info += str.trim();
		System.out.println("info = " + info);
	}

	/**
	 * 2. StringBuffer类用法：
	 * 特点：
	 *    每次都是修改原来的字符串，所以，效率较高。
	 *
	 * String与StringBuffer类的比较：
	 * ① 前者是一个不变的常量值，每次操作都是生成一个新的字符串，而后者是每次都是修改原字符串。
	 *
	 * StringBuffer与的比较StringBuilder：
	 * ① 两者都是修改原字符串，但是前者是一个线程安全的类，是线程同步，效率较低，后者是一个线程异步类，效率较高。
	 * ② 其它用法这两个类是一样的。
	 */
	@Test
	public void test02(){
		// 1. 定义一个字符串
		StringBuffer buffer = new StringBuffer();
		StringBuilder builder = new StringBuilder();
		// 2. 添加内容
		buffer.append("hello");
		buffer.append(123);
		buffer.append(true);
		buffer.append(3.14);
		buffer.append('中');
		System.out.println("buffer = " + buffer);
		// 3. 向指定位置添加字符串
		buffer.insert(8,"学");
		System.out.println("buffer = " + buffer);
		// 4. 删除指定字符串
		// 4.1 删除指定位置的字符
		buffer.deleteCharAt(8);
		System.out.println("buffer = " + buffer);
		// 4.2 删除指定范围的字符串
		buffer.delete(5,8);
		System.out.println("buffer = " + buffer);
		// 5. 字符串的反转
		buffer.reverse();
		System.out.println("buffer = " + buffer);

	}
```

> **StringBuffer与StringBuilder的比较:**
>
> ① 两者都是修改原字符串，但是前者是一个线程安全的类，是线程同步，效率较低，后者是一个线程异步类，效率较高。
>
> ② 其它用法这两个类是一样的。
>
> **String与StringBuffer类的比较：**
>
> ① 前者是一个不变的常量值，每次操作都是生成一个新的字符串，而后者是每次都是修改原字符串。

## 4、 数组练习题、面试题：

> **案例一：**编写程序，将0-99之间的数，分为奇数和偶数两组，并保存到两个数组中，将两个数组中的元素都输出到屏幕上。

```java
public class Lesson4_03 {

	public static void main(String[] args) {
			test02();
	}
	/**
	 * 分析：
	 * ① 循环判断0-99，所以首选for循环
	 * ② 我们还需要准备存放奇数和偶数的数组，还需要定义两个计数器分别代表有奇数和偶数数组的下标
	 * ③ 如何确定数组的长度，这里分别是奇数和偶数对半，各50个。
	 */
	@Test
	public void test01() {
		// 第一部分：向奇数和偶数数组中存放数据：
		// 1. 定义两个计数器
		int m = 0, n = 0;            // 分别代表有奇数、偶数个数
		// 2. 定义两个数组分别用于存放奇数和偶数
		int[] a = new int[50];      // 代表奇数数组
		int[] b = new int[50];      // 代表偶数数组
		// 3. 循环向a,b两个数组存数数据
		for (int i = 0; i < 100; i++) {
			// 3.1 存放奇数到a数组中
			if (i % 2 == 1) {
				a[m++] = i;
			}
			// 3.2 存放偶数到b数组中
			if (i % 2 == 0) {
				b[n++] = i;
			}
		}

		// 第二部分：打印奇数、偶数数组的数据
		// 4. 打印奇数、偶数数组
		System.out.println("奇数数组如下：");
		System.out.println("----------------------------------------");
		for (int i = 0; i < m; i++) {
			System.out.print(a[i] + "\t");
			// 每10个一换行
			if ((i + 1) % 10 == 0) {
				System.out.println();
			}
		}
		System.out.println("偶数数组如下：");
		System.out.println("----------------------------------------");
		for (int i = 0; i < n; i++) {
			System.out.print(b[i] + "\t");
			// 每10个一换行
			if ((i + 1) % 10 == 0) {
				System.out.println();
			}
		}
	}
```

> **案例二：**程序，用户输入10个整数，求数组中最大值及最小值。

```java
	/**
	 * 分析：
	 *   ① 假定第一个数为最大值或最小值
	 *   ② 求最大值：
	 *      将输入的第二个数以后每个数分别与这个最大值比较，如果比它大，此时最大值就换成这个数。
	 *   ③ 求最小值：
	 *      将输入的第二个数以后每个数分别与这个最小值比较，如果比它小，此时最小值就换成这个数。
	 */
	private static void test02() {
		// 1. 定义键盘扫描器对象
		Scanner scanner = new Scanner(System.in);
		// 2. 输入10个数
		System.out.println("请输入10个整数：");
		int max = scanner.nextInt();
		int min = max;
		// 3. 再输入其它九个数
		for (int i = 0; i < 9; i++) {
			// 3.1 得到输入的数：
			int num = scanner.nextInt();
			// 求最大值：
			// 3.2 将此数与前面最大值比较
			if(num > max){
				max = num;
			}
			// 求最小值：
			// 3.3 将此数与前面最小值比较
			if(num < min){
				min = num;
			}
		}
		// 4. 打印最大值与最小值
	
        System.out.println("min = " + min + ",max = " + max);
	}
```

> **案例三：**数组中的非重复元素。(在数组中只出现了一次)

```java
/**
	 * 案例四：编写程序，写一个程序实现找到数组中的非重复元素。(在数组中只出现了一次)
	 * 分析：
	 *  1、准备两层循环、
	 *  2、外层循环在定义一个计数器，代表是否有重复元素（每次比较相等计数器count就加1）
	 *  3、内层循环完成将外层循环变量i分别与这个数组每个元素进行对比的功能，对比相等就累加计数器count
	 *  4、在内层循环完成后，比较count是否为1，如果为1证明此元素在数组中和重复。将其放在一个新数组中。
	 *  5、新数组的长度，可以定义成原数组的长度
	 *  6、新数组的下标，可以使用一个计数器同时充当下标
	 *
	 *  大致推算过程如下：
	 *  [1,2,3,2,3,5,6,8]
	 *  count = 0;
	 *  [1,2,3,2,3,5,6,8]
	 *
	 *  [1,5,6,8]--->count=1
	 */
	@Test
	public void test03(){
		// 1. 定义一个数组
		int[] a = {1,2,3,2,3,5,6,8};
		// 2. 定义一个存放非重复元素的新数组
		int[] b = new int[a.length];
		// 3. 定义一个计数器同时充当新数组的下标
		int n = 0;
		// 4. 开始统计非重复元素并放到新数组中
		for (int i = 0; i < a.length; i++) {
			// 4.1 定义一个计数器代表元素是否重复
			int count = 0;
			// 4.2 开始逐个比较当前元素是否与数组中每个值比较是否相等
			for (int j = 0; j < a.length; j++) {
				if(a[i] == a[j]){
					count++;
				}
			}
			// 4.3 根据count的值判断是否有重复元素
			if(count == 1){
				b[n++] = a[i];
			}
		}
		// 5. 最后打印非重复元素
		System.out.println("原数组中非重复元素如下：");
		System.out.println("-----------------------------");
		for (int i = 0; i < n; i++) {
			System.out.print(b[i] + "\t");
		}
	}
```

> **案例四：**如何找到数组中的重复元素？ （出现了多次）

```java
	@Test
	public void test04(){
		// 1. 定义一个数组
		int[] a = {1,2,3,2,3,5,6,8};
		// 2. 定义一个存放非重复元素的新数组
		int[] b = new int[a.length];
		// 3. 定义一个计数器同时充当新数组的下标
		int n = 0;
		// 4. 开始统计非重复元素并放到新数组中
		for (int i = 0; i < a.length; i++) {
			// 4.1 定义一个计数器代表元素是否重复
			int count = 0;
			// 4.2 开始逐个比较当前元素是否与数组中每个值比较是否相等
			for (int j = 0; j < a.length; j++) {
				if(a[i] == a[j]){
					count++;
				}
			}
			// 4.3 根据count的值判断是否有重复元素
			if(count > 1 && !isExists(b,a[i])){
				b[n++] = a[i];
			}
		}
		// 5. 最后打印非重复元素
		System.out.println("原数组中非重复元素如下：");
		System.out.println("-----------------------------");
		for (int i = 0; i < n; i++) {
			System.out.print(b[i] + "\t");
		}
	}

	/**
	 * 判断数组中是否有指定元素？
	 * @param a     数组
	 * @param e     比较元素
	 * @return      true: 存在此元素 false：不存在此元素
	 */
	private boolean isExists(int[] a,int e){
		for (int i = 0; i < a.length; i++) {
			if(e == a[i]){
				return true;
			}
		}
		return false;
	}
}
```



> **案例五：**找出输入的10个数中比平均数要大的数字并打印输出。

```javA
public class Lesson4_04 {
	public static void main(String[] args) {
		test01();
	}
	/**
	 * 分析：
	 * 1、输出10个数，需要使用Scanner和for循环
	 * 2、定义一个求和变量，每次输入一个数累加进去，最后计算平均数
	 * 3、可以将10个数放到数组中，然后，再每个元素与平均数进行比较，如果比平均数大，就输出。
	 */
	private static void test01() {
		// 第一部分：求平均数并将输入的整数放入数组中
		// 1. 定义一个扫描器对象
		Scanner scanner = new Scanner(System.in);
		// 2. 定义求和变量
		int sum = 0;
		// 3. 声明一个数组用于存放大于平均数的变量
		int[] a = new int[10];
		// 4. 定义计数器代表数组的下标
		int count = 0;
		// 5. 输入10个数累加到sum中
		System.out.println("请输入10个整数：");
		for (int i = 0; i < 10; i++) {
			// 5.1 得到输入的整数
			int num = scanner.nextInt();
			// 5.2 将输入的整数累加到sum变量中
			sum += num;
			// 5.3 将输入的整数放到数组中
			a[count++] = num;
		}
		// 6. 求平均数
		double avg = sum / 10.0;
		System.out.println("avg = " + avg);

		// 第二部分：遍历数组找到比平均数大的数字并打印
		System.out.println("比平均数大的数字如下：");
		System.out.println("----------------------------------");
		for (int i = 0; i < count; i++) {
			if(a[i] > avg) {
				System.out.print(a[i] + "\t");
			}
		}
	}

```

> **案例六：**一个长度为n的整型数组，处理后将奇数在前，偶数在后。

```java
	/**
	 * 分析：
	 *  1、定义一个原始数组，里面存放的是我们需要的所有数据。
	 *  2、定义一个奇数和偶数数组，
	 *    2.1 奇数和偶数的长度都是原数组的长度。
	 *    2.2 定义两个计数器m=0,n=0，分别奇数和偶数数组的个数，同时充当数组的下标
	 */
	@Test
	public void test02(){
		// 第一部分：将原数组中的奇数和偶数分别存放到两个小数组中
		// 2.1 定义一个原始数组
		int[] a = {3,1,0,19,5,2,19,23,18,34};
		// 2.2 定义一个奇数和偶数数组，分别存放原数组中的奇数和偶数
		int[] b = new int[a.length];                // 奇数数组
		int[] c = new int[a.length];                // 偶数数组
		// 2.3 定义代表奇数和偶数个数的计数器
		int m = 0,n = 0;
		// 2.4 开始将原始数组中的数据分别存放到b,c两个数组中
		for (int i = 0; i < a.length; i++) {
			//2.4.1 存放奇数数组
			if(a[i] % 2 == 1){
				b[m++] = a[i];
			}else{  //2.4.2 存放偶数数组
				c[n++] = a[i];
			}
		}

		// 第二部分：展示b，c两个小数组
		System.out.println("奇数数组如下：");
		System.out.println("------------------------------");
		for (int i = 0; i < m; i++) {
			System.out.print(b[i] + "\t");
		}
		System.out.println("\n偶数数组如下：");
		System.out.println("------------------------------");
		for (int i = 0; i < n; i++) {
			System.out.print(c[i] + "\t");
		}
	}
```

> **案例七**一个长度为n的整型数组，处理后将奇数在前，偶数在后。

```java
@Test
public void test02_1() {
    // 第一部分：将原数组中的奇数和偶数分别存放到两个小数组中
    // 2.1 定义一个原始数组
    int[] a = {3,1,0,19,5,2,19,23,18,34};
    // 2.2 定义一个新数组，将奇数放在前面，再将偶数放在后面
    int[] b = new int[a.length];
    int count = 0;
    // 2.3 开始遍历存放奇数到b数组中
    for (int i = 0; i < a.length; i++) {
        if(a[i] % 2 == 1){
            b[count++] = a[i];
        }
    }
    // 2.4 开始遍历存放偶数到b数组中
    for (int i = 0; i < a.length; i++) {
        if(a[i] % 2 == 0){
            b[count++] = a[i];
        }
    }
    // 2.5 将b数组打印出来
    System.out.println("将原数组重新组织后的数据如下：");
    System.out.println("--------------------------------------");
    for (int i = 0; i < count; i++) {
        System.out.print(b[i] + "\t");
    }
}
```

> **案例八**：快速找出一个数组中的最大数、第二大数。

```java
	/**
	 * 分析：
	 * 1、第一步，根据在数组中找最大值的思想，找到最大数。
	 * 2、第二步：在找到最大值后，将除了最大值外的其它元素放在一个新数组中，再找新数组的最大值。
	 */
	@Test
	public void test03(){
		// 第一步：找出原数组中的最大值
		// 1.1 声明一个数组
		int[] a = {3,1,0,19,5,2,19,23,18,12};
		// 1.2 假设第一个值最大
		int max = a[0];
		// 1.3 开始循环找最大值
		for (int i = 0; i < a.length; i++) {
			if(a[i] > max){
				max = a[i];
			}
		}
		System.out.println("max = " + max);

		// 第二步：将除了最大值外的其它元素放在一个新的数组中，找出新数组的最大值即为第二大值
		// 2.1 定义一个新数组
		int[] b = new int[a.length];
		// 2.2 定义数组个数充当下标
		int count = 0;
		// 2.3 将除了最大值外的其它值放入b数组中
		for (int i = 0; i < a.length; i++) {
			if(a[i] != max){
				b[count++] = a[i];
			}
		}
		// 2.4 在新的数组中找最大值
		// 2.4.1 假设b数组的第一个值就是最大值
		int secondMax = b[0];
		for (int i = 0; i < count; i++) {
			if(b[i] > secondMax){
				secondMax = b[i];
			}
		}
		// 2.4.2 打印第二大值
		System.out.println("secondMax = " + secondMax);
	}
}

```

> **冒泡排序实现过程分析：**

```java
public class Lesson4_05 {

	/**
	 * 冒泡排序：
	 * {11,1,19,2,5,3,7,6}--->N: 代表数组的长度
	 * i=0第一轮：1 11 2 5 3 7 6 19 确定了19的位置（内层循环：7次）
	 * 结果：1 2 5 3 7 6 11 19
	 * i=1第二轮：1 2 5 3 7 6 11  确定了11的位置（内层循环：6）
	 * 1 2 3 5 6 7 11
	 * i=2第三轮：1 2 3 5 6 7 确定了7的位置（内层循环：5）
	 * 1 2 3 5 6 7
	 * i=3第四轮：1 2 3 5 6 确定了6的位置（内层循环：4）
	 * 1 2 3 5 6
	 * i=4第五轮：1 2 3 5 确定了5的位置（内层循环：3）
	 * 1 2 3 5
	 * i=5第六轮：1 2 3 确定了3的位置（内层循环：2）
	 * 1 2 3
	 * i=6第七轮：1 2确定了2的位置（内层循环：1）
	 * 1 2
	 * 循环次数公式：
	 * 外层： N - 1  内层：N - 1 - i
	 */
	@Test
	public void test01() {
		// 1. 定义数组
		int[] a = {11, 1, 19, 2, 5, 3, 7, 6};
		// 2. 对数组进行排序
		sortArray(a, false);
		// 3. 打印最后的结果
		System.out.println("对数组进行升序排序后：");
		System.out.println("---------------------------------");
		for (int i = 0; i < a.length; i++) {
			System.out.print(a[i] + "\t");
		}
	}

	/**
	 * 对指定数组进行排序
	 *
	 * @param a    要排序的数絠
	 * @param flag true: 代表升序 false：降序
	 */
	private void sortArray(int[] a, boolean flag) {
		// 得到数组的长度
		int N = a.length;
		for (int i = 0; i < N - 1; i++) {           // 外层循环N-1
			for (int j = 0; j < N - 1 - i; j++) {   // 内层循环N-1-i
				if (flag) {   // 此时代表升序
					if (a[j] > a[j + 1]) {                  // 如果前面一个数比后面的数大就交换两个数 (升序排序)
						a[j] = a[j] + a[j + 1];
						a[j + 1] = a[j] - a[j + 1];
						a[j] = a[j] - a[j + 1];
					}
				} else {      // 此时代表降序
					if (a[j] < a[j + 1]) {                  // 如果前面一个数比后面的数大就交换两个数 (降序排序)
						a[j] = a[j] + a[j + 1];
						a[j + 1] = a[j] - a[j + 1];
						a[j] = a[j] - a[j + 1];
					}
				}
			}
		}
	}
}

```

> **数组常见API**：

```java
/**
	 * 数组相关的API函数:
	 */
	@Test
	public void test02(){
		// 1. 定义数组
		int[] a = {11, 1, 19, 2, 5, 3, 7, 6};
		// 2. Arrays类进行数组的排序
		// Arrays.sort(a,0,3);         // 将原数组的前三个元素进行排序，共它不动
		Arrays.sort(a);                             // 将原数组所有内容进行排序
		// 3. 打印数组
		System.out.println("排序后：");
		System.out.println("--------------------------");
		for (int i = 0; i < a.length; i++) {
			System.out.print(a[i] + "\t");
		}
		System.out.println("\n--------------------------");
		// 略过（JDK8的流式编程结合lamba表达式） 【了解】
		// Arrays.stream(a).sorted().forEach(r -> {
		// 	System.out.print(r + "\t");
		// });
		//

		// 4. 查找元素，要注意，必须要对查找元素的数组进行排序
		int e = 15;
		int index = Arrays.binarySearch(a, e);      // 返回值：存在：就是元素e在排序后的数组中的下标,不存在：返回在：-插入点-1的位置，插入点的确认在数组元素与要查找的元素之间判断
		System.out.println("index = " + index);
	}
```

