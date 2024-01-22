---
title: java-note
date: 2024-01-21 17:30:49
tags: [java]
---

# day01

## HelloWorld

```java
public class HelloWorld {
	public static void main (String[] args) {
		System.out.println("HelloWorld");
	}
}
```

## 注释

```java
注释
	含义:
		在程序中用来解释说明的文字
	分类:
		单行注释
		多行注释
		文档注释

单行注释:
	含义:
		用来解释说明单行文字的注释
	格式:
		//注释内容 

多行注释:
	含义:
		用来解释说明多行文字的注释
	格式:
		/*
			注释内容
		*/
	注意:
		多行注释以/*作为注释的开始,以遇到的第一个*/作为注释的结束

文档注释:
	含义:
		用来解释说明多行文字并备注代码的相关信息的注释
	格式:
		/**
			@ClassName 类名
			@Description 该类的描述
			@Author 作者
			@DateTime 日期时间
			@Version 版本
		*/
	注意:
		多行注释以/**作为注释的开始,以遇到的第一个*/作为注释的结束

```

## 关键字

```java
/*
	关键字:
		含义:
			在程序中被赋予特殊含义的英文单词
		特点:
			1.每个关键字都被赋予了特殊含义
			2.关键字必须全部小写
		注意:
			1.关键字一共53个,其中常用关键字51个,保留关键字2个
			2.main,args不是关键字
			3.在Editplus工具中,关键字呈蓝色字体
*/
public class BasicDemo02 {
	public static void main (String[] args) {
		System.out.println();
	}
}
```

## 变量

```java
/*
	变量:
		含义:
			在程序中其值可以发生改变的量
		前提:
			数据类型
			变量名
			初始化值
		格式:
			直接声明初始化:
				数据类型 变量名 = 初始化值;
			先声明后初始化
				数据类型 变量名;
				变量名 = 初始化值;
*/
```

## 数据类型

```java
/*
	数据类型:
		含义:
			Java语言是一门强类型的语言,每个数据都有对应的数据类型
		分类:
			基本数据类型:
				整数型
					含义:
						存储整数数据的数据类型
					关键字:
						byte,short,int(默认),long
					注意:
						每创建一个byte类型变量,占内存1个字节
						每创建一个short类型变量,占内存2个字节
						每创建一个int类型变量,占内存4个字节
						每创建一个long类型变量,占内存8个字节
				浮点型
					含义:
						存储浮点数据的数据类型,可以理解为小数,本质上与小数不同
					关键字:
						float,double(默认)
					注意:
						float和double并不是精确的小数,目前将其理解为小数
						每创建一个float类型变量,占内存4个字节
						每创建一个double类型变量,占内存8个字节
				字符型
					含义:
						存储单个字符的数据类型,单个字符可以是:字母,数字,汉字,标点......
					关键字:
						char
					注意:
						每创建一个char类型变量,有两种占内存规则,分别为内码和外码
						内码规则:
							char类型变量由底层源码进行创建,每创建一个char类型变量,占内存2个字节
						外码规则:
							char类型变量由程序员手动进行创建,每创建一个char类型变量,根据当前开发环境的编码占用内存
							如果编码是GBK,每创建一个char类型变量,占内存2个字节
							如果编码是UTF-8,
								每创建一个字母,数字,英文标点,占内存1个字节
								每创建一个汉字,占内存3个字节
				布尔型
					含义:
						存储"真","假"值的数据类型
					关键字:
						boolean
					注意(了解):
						每创建一个boolean类型基本类型变量,占内存4个字节
						创建一个boolean类型的数组,数组中的每个boolean元素占内存1个字节
			引用数据类型:
				数组,类,接口
*/
```

## 标识符

```java
/*
	标识符:
		含义:
			在程序中,给包,类,接口,方法,变量等起的名字
		特点(硬性规则):
			1.标识符可以由英文大小写字母,0-9数字,美元符$,下划线_,Unicode码表中的中文字符组成;
			2.标识符中0-9数字不能开头
			3.标识符不可以是Java中的关键字
		注意(软性规范):
			1.标识符可以声明中文,但是不推荐
			2.声明标识符的时候,做到"见名知意"
			3.给不同的内容声明标识符要遵循不同的命名规范
				类的命名规范:
					一个单词:单词的首字母大写
					多个单词:每个单词的首字母大写
				方法的命名规范:
					一个单词:单词全部小写
					多个单词:第一个单词全部小写,第二个单词开始每个单词的首字母大写
				变量的命名规范:
					一个单词:单词全部小写
					多个单词:第一个单词全部小写,第二个单词开始每个单词的首字母大写					
*/
public class BasicDemo05 {
	public static void main (String[] args) {
		
	}
}
```

## 初始化值

```java
/*
	初始化值:
		含义:
			在程序中,声明变量时给变量赋的值;
		分类:
			数据值
			地址值(暂不涉及)
		注意:
			1.在程序中所有的变量使用前必须进行初始化赋值操作
			2.在程序中所有的初始化必须在其数据类型的取值范围内
			3.在声明初始化long类型变量时,初始化值后面需要追加字母L或l,推荐L
			4.在声明初始化float类型变量时,初始化值后面需要追加字母F或f
			5.在声明初始化double类型变量时,初始化值后面需要追加字母D或d,推荐不写
			6.在声明初始化char类型变量时,初始化值需要使用''进行表示,''中有且仅有一个字符
			7.在声明初始化char类型变量时,初始化值除了单字符表示法外,还有一种较为常用的数字表示法(0~65535)
			8.在声明初始化booelan类型变量时,初始化值只有两个:true和false
			9.在给变量进行初始化赋值时,初始化值也可以是一个变量名(将该变量的初始化赋值给另外一个变量)


	补充:
		编码表:十进制数字和字符进行一一对应的码表
		ASCII编码表:世界上第一张编码表,将大小写字母,数字,标点和0~127进行一一对应的编码表
			字符0		数字48
			字符A		数字65
			字符a		数字97
		Unicode编码表:将各个国家常用的文字收集后的编码表(0~65535)
*/

public class BasicDemo06 {
	public static void main (String[] args) {
		char var = 48;
		System.out.println(var);

		boolean var1 = true;

		int a = 3;
		int b = a;//将变量a的3的值赋值给int类型的变量b
		System.out.println(a);
		System.out.println(b);
	}
}
```

```java
/*
	声明并初始化8个基本数据类型变量和字符串变量,并打印
*/

public class BasicDemo07 {
	public static void main (String[] args) {
		//声明初始化整数型变量
		byte var1 = 123;
		short var2 = 12345;
		int var3 = 1234567890;
		long var4 = 12345678900L;

		System.out.println(var1);
		System.out.println(var2);
		System.out.println(var3);
		System.out.println(var4);

		System.out.println("=======================");

		//声明并初始化浮点型变量
		float var5 = 12.34F;
		double var6 = 67.89;
		System.out.println(var5);
		System.out.println(var6);

		System.out.println("=======================");

		//声明初始化字符型变量
		char var7 = 'a';
		System.out.println(var7);

		System.out.println("=======================");

		//声明并初始化布尔类型变量
		boolean var8 = true;
		System.out.println(var8);

		System.out.println("=======================");

		//声明并初始化字符串类型变量
		String var9 = "HelloWorld";
		System.out.println(var9);
	}
}
```

```java
/*
	变量声明初始化的注意事项:
		1.遵循数据类型,标识符,初始化值的注意事项
		2.在同一作用域内,不可以声明同名的变量
			作用域:变量所属的那对大括号
		3.变量的使用只在所属的作用域内有效
		4.声明多个变量,且多个变量还是同一种数据类型的时候,可以将其在同一行上进行声明初始化
*/
public class BasicDemo08 {
	public static void main (String[] args) {
		//两个变量分别直接声明初始化(推荐)
		int a1 = 3;
		int b1 = 4;
		System.out.println(a1);
		System.out.println(b1);

		System.out.println("===============================");

		//两个变量分别先声明后初始化(推荐)
		int a2;
		a2 = 3;
		int b2;
		b2 = 4;
		System.out.println(a2);
		System.out.println(b2);

		System.out.println("===============================");

		//两个变量一起直接声明初始化(笔试)
		int a3 = 3 , b3 = 4;
		System.out.println(a3);
		System.out.println(b3);

		System.out.println("===============================");

		//两个变量一起先声明后初始化(笔试,源码)
		int a4 , b4;
		a4 = 3;
		b4 = 4;
		System.out.println(a4);
		System.out.println(b4);

		System.out.println("===============================");

		//两个变量一起混合初始化(笔试)
		int a5 = 3, b5;
		b5 = 4;
		System.out.println(a5);
		System.out.println(b5);
	}
}
```

## 进制转换

![](java-note/image.png)

# day02

## 类型的转换

```java
/*
	类型的转换
		含义:
			将一种数据类型的数据转换为另外一种数据类型的数据
		分类:
			基本类型的类型转换
			引用类型的类型转换(暂不涉及)
			基本类型和包装类型的类型转换(暂不涉及)
			基本类型和字符串类型的类型转换(暂不涉及)

	基本类型的类型转换
		含义:
			将一种基本类型的数据转换为另外一种基本类型的数据
		分类:
			自动转换(隐式转换)
			强制转换(显式转换)
		格式:
			数据类型1 变量名 = (数据类型1)数据类型2的变量值;
*/
```

### 自动转换(隐式转换)

```java
/*
	自动转换(隐式转换)
		含义:
			将取值范围较小的数据类型转换成取值范围较大的数据类型
		关系:
			基本类型取值范围从小到大的关系:
				byte < short < int < long < float < double
						char < int < long < float < double
		注意:
			1.基本类型间的转换是七种数值类型间的转换,boolean类型无法进行转换
			2.自动转换也可以使用类型转换的格式,往往将(数据类型)省略不写
*/

public class BasicDemo02 {
	public static void main (String[] args) {
		byte var1 = 123;
		int var2 = 123;

		//var1 = var2;//错误: 不兼容的类型: 从int转换到byte可能会有损失
		var2 = var1;

		long var3 = 123L;
		float var4 = 12.34F;

		//var3 = var4;//错误: 不兼容的类型: 从float转换到long可能会有损失
		var4 = var3;

		char var5 = 'a';
		var2 = var5;
		//var5 = var2;//错误: 不兼容的类型: 从int转换到char可能会有损失

		short var6 = 123;
		//var5 = var6;//错误: 不兼容的类型: 从short转换到char可能会有损失
		//var6 = var5;//错误: 不兼容的类型: 从char转换到short可能会有损失
	}
}
```

```java
/*
	在内存中,每创建一个float类型变量,占内存4个字节,每创建一个long类型变量,占内存8个字节,
	为什么float类型可以存储long类型数据?
		1.基本类型的类型转换只与数据类型的取值范围有关,和所在内存大小无关
		2.float类型之所有可以用更少的字节存储更大或更小的数据,因为float或double底层不是十进制小数,而是一套IEEE754浮点计数标准
		3.证明long的取值范围小于float的取值范围
			long的取值范围中最大的整数 < 2^63
			float的取值范围中最大的整数 > 3.4*10^38 > 2*10^38 > 2*8^38 = 2*(2^3)^38 = 2*2^114 = 2^115 > 2^63

*/
```

### 强制类型(显式转换)

```java
/*
	基本类型的强制类型(显式转换)
		含义:
			将取值范围较大的数据类型转换成取值范围较小的数据类型
		格式:
			取值范围较小的数据类型 变量名 = (取值范围较小的数据类型)取值范围较大数据类型的变量值;
		注意:
			在实际应用中尽量避免使用基本类型的强制转换,可能会发生数据的精度损失或数据溢出
*/
public class BasicDemo04 {
	public static void main (String[] args) {
		int var = (int)3.99;
		System.out.println(var);

		System.out.println("=============================");

		byte num = (byte)130;// 130 = 127 + 3  -128 -127 -126
		System.out.println(num);
	}
}
```

### 类型转换注意事项

```java
/*
	基本类型的类型转换注意事项
		1.类型类型的自动转换和强制转换都可以使用基本类型转换的格式,自动转换可以省略不写(数据类型);
		2.基本类型间的转换是七种数值类型间的转换,boolean类型无法进行转换
		3.在实际应用中尽量避免使用基本类型的强制转换,可能会发生数据的精度损失或数据溢出
		4.byte,short,char这三种基本类型只要参与数学运算,先自动提升成int类型,再参与数学运算;如果没有数学运算,依旧按照基本类型的自动转换关系进行转换
*/

public class BasicDemo05 {
	public static void main (String[] args) {
		float var1 = 3.3F;
		float var2 = 4.4F;
		float var3 = var1 + var2;
		System.out.println(var3);

		byte num1 = 3;
		byte num2 = 4;
		//byte num3 = num1 + num2;
		//System.out.println(num3);

		short s = num1;
	}
}
```

## 两种常见的输出语句

```java
/*
	两种常见的输出语句:
		换行输出语句:
			含义:
				将内容进行输出打印,并进行回车换行操作
			格式:
				System.out.println(内容);
			注意:
				当换行输出语句没有任何输出内容时,直接进行换行处理
		直接输出语句
			含义:
				将内容进行输出打印,不进行其它操作
			格式:
				System.out.print(内容);
			注意:
				当直接输出语句没有任何输出内容时,程序"编译报错"
*/

public class BasicDemo06 {
	public static void main (String[] args) {
		System.out.println("Hello");

		System.out.print();

		System.out.println("World");

		System.out.println("====================");

		System.out.print("Hello");
		System.out.print("World");
	}
}
```

## 常量

```java
/*
	常量:
		含义:
			在程序执行的过程中,其值不可以发生改变的量
		分类:
			自定义常量(暂不涉及)
				含义:由开发人员定义的常量,并且有final关键字进行修饰
			字面值常量
				含义:单独的数据值,无法直接进行使用,需要结合其它语句进行使用
				分类:
					整数字面值常量
					浮点字面值常量
					字符字面值常量
					布尔字面值常量
					字符串字面值常量
					空常量(暂不涉及)
						null
				注意:
					字面值常量无法单独使用,需要结合其它语句进行使用
					null无法在输出语句中进行打印

*/

public class BasicDemo07 {
	public static void main (String[] args) {
		//直接打印字面值常量
		System.out.println(123);
		System.out.println(3.14);
		System.out.println('a');
		System.out.println(true);
		System.out.println("HelloWorld");
		//System.out.println(null);
	}
}
```

```java
/*
	常量的注意事项:
		1.在给byte,short,char这三种数据类型进行整数赋值操作时,初始化值如果是字面值常量,且该初始化值还在其数据类型的取值范围内,JVM中的存储常量的内存区域会将其自动优化为该数据类型,将这一过程称之为"常量优化机制"
		2.在给变量进行初始化赋值操作时,如果初始化值是一个表达式,运算符号两边的数据都是字面值常量,且运算的结果还在其数据类型的取值范围内,JVM中的编译器在编译器自动将其运算完毕,将这一过程称之为"常量优化机制"
*/

public class BasicDemo08 {
	public static void main (String[] args) {
		byte var1 = 123;
		int var2 = 123;

		//var1 = var2;

		System.out.println("=====================");

		byte b1 = 3;
		byte b2 = 4;
		byte b3 = 3 + 4;
	}
}
```

## 运算符

```java
/*
	运算符:
		含义:
			在程序中用来连接常量或变量的运算符号
		
	表达式:
		含义:
			在程序中用运算符连接起来的式子

	常见的运算符:
		算术运算符
		赋值运算符
		关系运算符
		逻辑运算符
		三元运算符
		位运算符
*/
```

### 算术运算符

```java
/*
	算术运算符:
		含义:
			进行常量或变量算术操作的运算符
		分类:
			四则运算符
				+ - * /
			取余运算符
				%
			自增运算符
				++
			自减运算符
				--

	四则运算符和取余运算符
		含义:
			针对常量或变量进行数学运算的运算符
		注意:
			/是获取两个数相除的商
			%是获取两个数相除的余数

*/

public class OperatorDemo02 {
	public static void main (String[] args) {
		int a = 3;
		int b = 4;

		System.out.println(a + b);
		System.out.println(a - b);
		System.out.println(a * b);
		System.out.println(a / b);
		System.out.println(a % b);
	}
}
```

### 四则运算符和取余运算符的练习

```java
/*
	四则运算符和取余运算符的练习

	需求:获取指定四位数中各个位上的数字
*/

public class OperatorDemo03 {
	public static void main (String[] args) {
		//声明并初始化四位整数
		int num = 4396;

		//获取该四位整数中各个位上的数字
		int ge = num % 10;
		int shi = num / 10 % 10;
		int bai = num / 100 % 10;
		int qian = num / 1000 % 10;

		//打印各个位上的数字
		System.out.println(qian);
		System.out.println(bai);
		System.out.println(shi);
		System.out.println(ge);
	}
}
```

```java
/*
	+号的多种用法:
		1.加法运算符
		2.字符串连接符
			当+号两边中的任意一边出现了字符串时,+号不再起到加法运算符的作用,而是变成了字符串连接符,将运算符两边的内容进行连接操作
*/

public class OperatorDemo04 {
	public static void main (String[] args) {
		String str1 = "Hello";
		String str2 = "World";
		String str3 = str1 + str2;

		System.out.println(str3);
	}
}
```

```java
public class OperatorDemo05 {
	public static void main (String[] args) {
		System.out.println("Hello" + 5 + 20);//Hello520
		System.out.println(5 + 20 + "Hello");//25Hello

		System.out.println("=================================");

		System.out.println('a' + 1);//98
		System.out.println("a" + 1);//a1
		System.out.println("" + 'a' + 1);//a1
	}
}
```

### 自增自减运算符

```java
/*
	自增自减运算符
		含义:
			在变量的自身数据基础上进行+1或-1的运算符
		注意:
			自增自减运算符只能变量进行使用,常量无法进行使用
		格式(以++为例):
			++变量名 或者 变量名++
		分类:
			单独使用
				++在前和++在后的结果是一样的
			复合使用
				如果++在前,先自增,再使用
				如果++在后,先使用,在自增
*/

public class OperatorDemo06 {
	public static void main (String[] args) {
		int a = 3;
		int b = 4;

		//a++;
		//++a;
		//b = ++a;
		b = a++;


		System.out.println("a = " + a);
		System.out.println("b = " + b);
	}
}
```

```java
/*
	自增自减运算符的练习
*/

public class OperatorDemo07 {
	public static void main (String[] args) {
		int a = 3;
		//int b = ++a + a++;
		//分析:4(a=4) + 4(a=5) = 8(a=5)


		//int b = a++ + ++a;
		//分析:3(a=4) + 5(a=5) = 8(a=5)


		//int b = a++ + a++;
		//分析:3(a=4) + 4(a=5) = 7(a=5)

		int b = ++a + ++a;
		//分析:4(a=4) + 5(a=5) = 9(a=5)

		System.out.println("a = " + a);
		System.out.println("b = " + b);

		System.out.println("==================================");

		/*
			思考题1:x=3,x=x++,++在后,先将x=3的值赋值给x,在进行自增,x变成4,但实际结果执行3,为什么?
		*/
		int x = 3;
		x = x++;
		System.out.println("x = " + x);//3

		System.out.println("==================================");

		/*
			思考题2:按照运算符的优先级,有括号先算括号,先执行i++ + 1,结果2,i变成2,再计算i++ * 2,结果4,i变成3,但是实际结果打印3和3,不是3和4,为什么?
		*/

		int i = 1;
		int j = i++ * (i++ + 1);

		System.out.println("i = " + i);//3
		System.out.println("j = " + j);//3
	}
}
```

### 赋值运算符

```java
/*
	赋值运算符:
		含义:
			针对变量或操作进行赋值操作的运算符
		分类:
			直接赋值运算符
				=
			复合赋值运算符
				+= -= *= /= %= ......
				含义:将运算符两边的结果进行运算操作(取决于=之外的符号),再将运算的结果赋值给左边的变量
		注意:
			复合的赋值运算符再将左右两边运算的结果赋值给左边的变量之前,会根据左边变量的数据类型隐藏做了一步强制转换

*/
public class OperatorDemo08 {
	public static void main (String[] args) {
		//声明并初始化变量
		int var = 3;//将整数3赋值给int类型的变量var


		int a = 3;
		int b = 4;

		a += b;//相当于 a = a + b 
		System.out.println("a = " + a);
		System.out.println("b = " + b);

		System.out.println("==========================");

		byte b1 = 3;
		byte b2 = 4;

		b2 += b1;//b2 = b1 + b2;
	}
}
```

### 关系运算符

```java
/*
	关系运算符:
		含义:
			比较变量或常量之间关系的运算符
		分类:
			< <= > >= == !=
		注意:
			关系表达式的结果一定是boolean值
	
	==:比较基本类型数据值是否相等
	!=:比较基本类型数据值是否不等

		
*/

public class OperatorDemo09 {
	public static void main (String[] args) {
		int a = 3;
		int b = 4;
		int c = 4;

		System.out.println(a < b);//true
		System.out.println(a <= b);//true
		System.out.println(b < c);//false
		System.out.println(b <= c);//true

		System.out.println("===========================");

		System.out.println(a > b);//false
		System.out.println(a >= b);//false
		System.out.println(b > c);//false
		System.out.println(b >= c);//true

		System.out.println("===========================");

		System.out.println(a == b);//false
		System.out.println(b == c);//true

		System.out.println("===========================");

		System.out.println(a != b);
		System.out.println(b != c);
	}
}
```

### 逻辑运算符

```java
/*
	逻辑运算符
		含义:
			用来连接结果是boolean值表达式的运算符
		分类:
			单独逻辑运算符
				&	|	^	!
			短路逻辑运算符
				&&	||

	单独逻辑运算符
		运算符&:
			含义:
				与,且
			特点:
				有false则false
			场景:
				判断多个条件是否同时满足

		运算符|:
			含义:
				或
			特点:
				有true则true
			场景:
				判断多个条件是否至少满足其中一条

		运算符^:
			含义:
				异或
			特点:
				相同则false,不同则true
			场景:
				判断多个条件结果是否不一致

		运算符!:
			含义:
				非
			特点:
				非true则false,非false则true
			场景:
				针对boolean值结果进行取反
*/
public class OperatorDemo10 {
	public static void main (String[] args) {
		int a = 3;
		int b = 4;
		int c = 5;

		//运算符&
		System.out.println(a > b & a > c);//false & false
		System.out.println(a > b & a < c);//false & true
		System.out.println(a < b & a > c);//true & false
		System.out.println(a < b & a < c);//true & true

		System.out.println("==============================");

		//运算符|
		System.out.println(a > b | a > c);//false | false
		System.out.println(a > b | a < c);//false | true
		System.out.println(a < b | a > c);//true | false
		System.out.println(a < b | a < c);//true | true

		System.out.println("==============================");

		//运算符&
		System.out.println(a > b ^ a > c);//false ^ false
		System.out.println(a > b ^ a < c);//false ^ true
		System.out.println(a < b ^ a > c);//true ^ false
		System.out.println(a < b ^ a < c);//true ^ true

		System.out.println("==============================");

		//运算符!
		System.out.println(!true);
		System.out.println(!false);

		System.out.println(!!!true);
	}
}
```

### 短路逻辑运算符

```java
/*
	短路逻辑运算符
		&& ||

	&和&&的区别:
		&和&&的结果是一样的;&&具有短路效果,当&&前面表达式的结果为false时,后面的表达式不会被执行;&无论前面表达式结果的值是true还是false,后面表达式都会被执行

	|和||的区别:
		|和||的结果是一样的;||具有短路效果,当||前面表达式的结果为true时,后面的表达式不会被执行;|无论前面表达式结果的值是true还是false,后面表达式都会被执行
*/

public class OperatorDemo11 {
	public static void main (String[] args) {
		int a = 3;
		int b = 4;
		int c = 5;

		//运算符&
		System.out.println(a > b & a > c);//false & false
		System.out.println(a > b & a < c);//false & true
		System.out.println(a < b & a > c);//true & false
		System.out.println(a < b & a < c);//true & true

		System.out.println("========================");

		//运算符&&
		System.out.println(a > b && a > c);//false && false
		System.out.println(a > b && a < c);//false && true
		System.out.println(a < b && a > c);//true && false
		System.out.println(a < b && a < c);//true && true

		System.out.println("========================");

		int x = 3;

		System.out.println(false && ++x > 3);

		System.out.println("x = " + x);
	}
}
```

### 三元运算符

```java
/*
	三元运算符:
		含义:
			含有三个未知量的运算符
		格式:
			关系表达式 ? 结果值1 :结果值2
		流程:
			1.先确认关系表达式的结果是true还是false;
			2.在获取关系表达式结果的同时,统一结果值1和结果值2的数据类型
			3.如果是true,执行"统一数据类型后的"结果值1;
			  如果是false,执行"统一数据类型后的"结果值2;

	需求:
		获取两个整数的较大值
*/

public class OperatorDemo12 {
	public static void main (String[] args) {
		int a = 3;
		int b = 4;
		System.out.println(a > b ? a : b);

		System.out.println("=====================");

		System.out.println(false ? 3.6 : 5);
	}
}
```

### 位运算符

```java
/*
	原码,反码,补码:
		相同点:
			1.原码,反码,补码都是特殊的二进制形式表示法
			2.原码,反码,补码在二进制数据中规定的符号位,最高位即为符号位,正数为0,负数为1
			3.原码,反码,补码在二进制数据中根据在内存中占用字节大小进行足位存储,不足位数通过补0进行占位
				例如:int num = 2;
					普通二进制:10
					特殊二进制:
						00000000 00000000 00000000 00000010
		不同点:
			原码:计算机中显示数据的二进制特殊表示形式
			补码:计算机中底层进行数据运算的二进制特殊表示形式
			反码:进行原码和补码相互转换的中间量

	底层存储和操作数据的过程分析:
		1.显示数据==>数据原码
			(1)根据显示数据占用字节数确定二进制的总位数
			(2)根据显示数据的正负确定二进制原码的符号位
		2.数据原码==>数据反码
			如果符号位是0,数据反码与其原码相同
			如果符号位是1,数据反码在其原码的基础上进行逐位取反,符号位保持不变
		3.数据反码==>数据补码
			如果符号位是0,数据补码与其反码相同
			如果符号位是1,数据补码在其反码的基础上进行+1运算
		4.操作补码==>结果补码
			根据实际需求进行运算操作
		5.结果补码==>结果反码
			如果符号位是0,结果反码与其补码相同
			如果符号位是1,数据反码在其补码的基础上进行-1运算
		6.结果反码==>结果原码
			如果符号位是0,结果原码与其反码相同
			如果符号位是1,数据原码在其反码的基础上进行逐位取反,符号位保持不变
		7.结果原码==>结果数据
			(1)将除符号位外,所有二进制数进行将十进制的转换
			(2)如果符号位是1,在十进制结果数据的前面补上负号

	将int类型的130强制转换成byte类型后,结果为-126的存储操作过程:
		1.显示数据==>数据原码
			数据原码:00000000 00000000 00000000 10000010
		2.数据原码==>数据反码
			数据反码:00000000 00000000 00000000 10000010
		3.数据反码==>数据补码
			数据补码:00000000 00000000 00000000 10000010
		4.操作补码==>结果补码
			结果补码:10000010
		5.结果补码==>结果反码
			结果反码:10000001
		6.结果反码==>结果原码
			结果原码:11111110
		7.结果原码==>结果数据
			结果数据:-126
*/
```

```java
/*
	位运算符:
		含义:
			直接针对二进制位进行操作的运算符
		分类:
			按位运算符
				& | ^ ~
			移位运算符
				<< >> >>>

	按位运算符:
		运算符&:
			含义:
				按位与
			特点:
				当两位相同时为1时才返回1,包括符号位

		运算符|:
			含义:
				按位或
			特点:
				当两位有一位为1即可返回1,包括符号位

		运算符^:
			含义:
				按位异或
			特点:
				当两位相同时返回0,不同时返回1,包括符号位

				^:按位异或,当两位相同时返回0,不同时返回1
*/
public class OperatorDemo14 {
	public static void main (String[] args) {
		//按位与
		System.out.println(6 & 23);
		System.out.println(-6 & -23);

		System.out.println("==============================");

		//按位或
		System.out.println(6 | 23);
		System.out.println(-6 | -23);

		System.out.println("==============================");

		//按位异或
		System.out.println(6 ^ 23);
		System.out.println(-6 ^ -23);

		System.out.println("==============================");

		//按位非
		System.out.println(~6);
		System.out.println(~-6);
	}
}
```
![Alt text](java-note/image-1.png)
### 移位运算符

```java
/*
	移位运算符
		含义:
			移动二进制位操作的运算符
		分类:
			<< >> >>>

	左移运算符:
		含义:
			将二进制位往左移动指定的位数,包含符号位
		格式:
			数据 << 位数
		特点:
			将二进制位往左移动指定的位数,符号位也随之移动,如果低位出现了空位,补0进行占位操作
			
	右移运算符:
		含义:
			将二进制位往右移动指定的位数,包含符号位
		格式:
			数据 >> 位数
		特点:
			将二进制位往右移动指定的位数,符号位也随之移动,如果高位出现了空位,补和符号位相同的数字进行占位操作

	无符号右移运算符:
		含义:
			将二进制位往右移动指定的位数,无需关注符号位
		格式:
			数据 >>> 位数
		特点:
			将二进制位往右移动指定的位数,符号位也随之移动,如果高位出现了空位,补0进行占位操作
*/

public class OperatorDemo15 {
	public static void main (String[] args) {
		System.out.println(6 << 2);
		System.out.println(-6 << 2);

		System.out.println(6 << 29);
		System.out.println(-6 << 29);

		System.out.println("==================================");

		System.out.println(6 >> 2);
		System.out.println(-6 >> 2);

		System.out.println("==================================");

		System.out.println(6 >>> 2);
		System.out.println(-6 >>> 2);
	}
}
```

# day03

### 运算符的优先级

```java
/*
	运算符的优先级
		1.Java中运算符的优先级和数学中的符号的优先级不同,数学中符号的优先级,谁优先级高就优先执行谁,但程序中的优先级是程序从左到右依次执行,如果碰到比执行运算符优先级更高的运算符,先将其作为一个整体进行计算
		2.当表达式中出现了自增自减运算符,且同时出现了(),需要注意运算符优先级问题
		3.当赋值运算符左右两边出现了相同的变量,需要注意运算符优先级问题
		4.如果在程序中出现了复合的赋值运算符,先进行拆分,再进行运算,在拆分的时候需要注意:复合的赋值运算符,将左边的变量和右边的式子进行运算操作,再根据左边变量的数据类型进行强制转换后赋值给左边的变量,而不是将右边的式子和左边的变量进行运算操作
		5.在程序中()只作为一个整体进行运算
		6.不要把一个表达式写得过于复杂，如果一个表达式过于复杂，则把它分成几步来完成；
		7.不要过多的依赖运算的优先级来控制表达式的执行顺序，这样可读性太差，尽量使用()来控制表达式的执行顺序

*/

public class OperatorDemo {
	public static void main (String[] args) {
		int i = 1;
		int j = i++ * (i++ + 1);//1(i=2) * 3(i=3) = 3
		System.out.println("i = " + i);//3
		System.out.println("j = " + j);//3

		System.out.println("======================================");

		int x = 3;//3==>4==>3
		x = x++;//先使用,后自增:先3的值存储在内存中的临时数据区
		System.out.println("x = " + x);

		System.out.println("======================================");

		int a = 2;
		int b = 5;
		//a *= b + 5;
		//a = a * (b + 5);
		a *= a++;
		//a = a * a++;//4,2==>3==>4
		//a = a++ * a;//6,2==>3==>6
		System.out.println("a = " + a);
		//System.out.println("b = " + b);
	}
}
```

## 流程控制

```java
/*
	所有编程语言都会遵循最基础的结构:顺序结构,代码从上至下依次执行
	
	流程控制:
		含义:
			针对程序中的代码进行逻辑执行,整体遵循顺序结构和自身流程控制执行
		分类:
			流程控制语句:
				含义:
					进行流程控制的语句,编写在代码块中
				分类:
					分支结构语句
						条件判断语句:if语句
						条件选择语句:switch语句
					循环结构语句
						for语句
						while语句
						dowhile语句

			流程控制代码块
				含义:
					进行流程控制的代码块,编写在类文件中
				分类:
					调用结构:
						普通方法
						构造器
						构造器代码块
						......

	学习流程控制的小技巧:
		1.记住流程控制的基本格式
		2.记住流程控制的执行流程
		3.精通流程控制的实际应用
*/
```

### if语句格式

```java
/*
	if语句第一种格式:
		if (条件判断语句) {
			语句体
		}

	执行流程:
		1.先确认条件判断语句的结果是true还是false;
		2.如果是true,执行语句体;
		  如果是false,if语句结束,继续往下执行;
	
	应用场景:
		只有一种选择情况

	需求:
		判断指定整数是否为偶数,如果是执行打印;
*/

public class IfDemo01 {
	public static void main (String[] args) {
		System.out.println("开始");

		//声明并初始化指定整数
		int num = 624;

		if (num % 2 == 0) {
			System.out.println(num + "是偶数");
		}

		System.out.println("结束");
	}	
}
```

```java
/*
	if语句的第二种格式:
		if (条件判断语句) {
			语句体1
		} else {
			语句体2
		}

	执行流程:
		1.先确认条件判断语句的结果是true还是false
		2.如果是true,执行语句体1,if语句结束;
		  如果是false,执行语句体2,if语句结束;

	应用场景:
		解决有两种选择情况

	注意事项:
		if语句的第二种格式和三元运算符相比,在实际开发中,更推荐使用if语句的第二种格式,三元运算符可以解决的问题,if语句的第二种格式都可以解决,但是if语句的第二种格式可以解决的问题,三元运算符不一定可以解决

	
	需求:判断指定整数的奇偶性并打印
*/

public class IfDemo02 {
	public static void main (String[] args) {
		//声明并初始化指定整数
		int num = 456;

		//进行num的奇偶性判断
		if (num % 2 == 0) {
			System.out.println(num + "是偶数");
		} else {
			System.out.println(num + "是奇数");
		}

		System.out.println("================================");

		String result = num % 2 == 0 ? num + "是偶数" : num + "是奇数";

		System.out.println(result);
	}
}
```

```java
/*
	if语句的第三种格式:
		if (条件判断语句1) {
			语句体1
		} else if (条件判断语句2) {
			语句体2
		}
		......
		else if (条件判断语句n) {
			语句体n
		} else {
			语句体n+1
		}

	执行流程:
		1.先确认条件判断语句1的结果是true,还是false
		2.如果是true,执行语句体1,if语句结束;
		  如果是false,确认条件判断语句2的结果是true,还是false
		......
		3.当所有的条件判断语句的结果是false时,执行else中的语句体n+1;

	应用场景:解决三种及三种以上的选择情况
	
	注意事项:
		if语句第三种格式中的else语句可以省略不写,但是建议写上,因为在特殊场景中不写可能编译报错

	需求:判断两个整数的关系
*/

public class IfDemo03 {
	public static void main (String[] args) {
		int a = 3;
		int b = 4;

		//判断a和b之间的关系
		if (a > b) {
			System.out.println("a > b");
		} else if (a < b) {
			System.out.println("a < b");
		} else {
			System.out.println("a = b");
		}
	}
}
```

```java
/*
	x和y的关系满足如下：
		x>=3 y = 2x + 1;
		-1<x<3 y = 2x;
		x<=-1 y = 2x - 1;
	根据给定的x的值，计算出y的值并输出。
*/
public class IfDemo04 {
	public static void main (String[] args) {
		//声明并初始化x变量
		int x = 5;

		//声明变量y
		int y;

		//针对x进行判断
		if (x >= 3) {
			y = 2 * x + 1;
		} else if (x > -1 && x < 3) {
			y = 2 * x;
		} else {
			y = 2 * x - 1; 
		}

		//打印变量y
		System.out.println("y = " + y);
	}
}
```

```java
/*
	通过指定考试成绩，判断学生等级
		90-100      优秀
		80-89        好
		70-79        良
		60-69        及格
		60以下    不及格
*/

public class IfDemo05 {
	public static void main (String[] args) {
		//声明并初始化学生的考试成绩
		int score = -1;

		if (score >= 90 && score <= 100) {
			System.out.println("优秀");
		} else if (score >= 80 && score <= 89) {
			System.out.println("好");
		} else if (score >= 70 && score <= 79) {
			System.out.println("良");
		} else if (score >= 60 && score <= 69) {
			System.out.println("及格");
		} else if (score >= 0 && score <= 59) {
			System.out.println("不及格");
		} else {
			System.out.println("成绩有误");
		}

		System.out.println("================================");

		if (score >= 0 && score <= 100) {
			if (score >= 90 && score <= 100) {
				System.out.println("优秀");
			} else if (score >= 80 && score <= 89) {
				System.out.println("好");
			} else if (score >= 70 && score <= 79) {
				System.out.println("良");
			} else if (score >= 60 && score <= 69) {
				System.out.println("及格");
			} else {
				System.out.println("不及格");
			}
		} else {
			System.out.println("成绩有误");
		}
	}
}
```

### switch语句的格式

```java
/*
	switch语句的格式:
		switch (数据值) {
			case 待选数据值1:
				语句体1
				break;

			case 待选数据值2:
				语句体2
				break;

			......

			case 待选数据值n:
				语句体n
				break;
			
			default:
				语句体n+1
				break;
		}

	执行流程:
		1.确认switch()中的数据值具体是多少
		2.选择"待选数据值1"和数据值进行匹配,看是否匹配条件;
		3.如果和数据值匹配成功,执行语句体1,执行break,switch语句结束;
		  如果和数据值匹配失败,选择"待选数据值2"和数据值进行匹配,看是否匹配条件;
		......
		4.当所有的待选数据值都和数据值匹配失败,执行default中语句体n+1,执行break,switch语句结束
*/

public class SwitchDemo01 {
	public static void main (String[] args) {
		//声明并初始化数字变量
		int weekday = 8;

		switch (weekday) {
			case 1:
				System.out.println("星期一");
				break;
			case 2:
				System.out.println("星期二");
				break;
			case 3:
				System.out.println("星期三");
				break;
			case 4:
				System.out.println("星期四");
				break;
			case 5:
				System.out.println("星期五");
				break;
			case 6:
				System.out.println("星期六");
				break;
			case 7:
				System.out.println("星期日");
				break;
			default:
				System.out.println("哥们你是火星来的吧,地球上没有这个星期");
				break;
		}
	}
}
```

```java
/*
	switch语句的注意事项:
		1.switch语句()中数据值的数据类型:
			基本类型:只支持int类型,根据基本类型转换,间接支持byte,short,char
			引用类型:
				在JDK5.0(包含)以后,可以支持枚举(Enum)类型
				在JDK7.0(包含)以后,可以支持字符串(String)类型
		2.switch语句中default可以省略不写,推荐写上
		3.switch语句中case和default位置可以互换,但不影响执行流程
		4.switch语句中break可以省略不写,如果不写会出现case穿透效果
			
*/

public class SwitchDemo02 {
	public static void main (String[] args) {
		int num = 1;

		switch (num) {
			case 1:
				System.out.println("你好");
				//break;
			default:
				System.out.println("苗苗老师好");
				//break;
			case 2:
				System.out.println("我好");
				//break;
			case 3:
				System.out.println("大家好");
				//break;
		}
	}
}
```

```java
/*
  需求：定义一个月份，输出该月份对应的季节。
  		一年有四季`````
  		3,4,5	春季
  		6,7,8	夏季
  		9,10,11	秋季
  		12,1,2	冬季
  
  分析：
  		A:指定一个月份
  		B:判断该月份是几月,根据月份输出对应的季节
  			if
  			switch

	if语句和switch语句的区别:
		底层处理阶段,switch语句的执行效率更高,在硬件过剩的今天,这点效率可以忽略不计,在实际开发中,更推荐使用if语句
*/

public class SwitchDemo03 {
	public static void main (String[] args) {
		//声明并初始化月份变量
		int month = 6;

		if (month == 1) {
			System.out.println("冬季");
		} else if (month == 2) {
			System.out.println("冬季");
		} else if (month == 3) {
			System.out.println("春季");
		} else if (month == 4) {
			System.out.println("春季");
		} else if (month == 5) {
			System.out.println("春季");
		} else if (month == 6) {
			System.out.println("夏季");
		} else if (month == 7) {
			System.out.println("夏季");
		} else if (month == 8) {
			System.out.println("夏季");
		} else if (month == 9) {
			System.out.println("秋季");
		} else if (month == 10) {
			System.out.println("秋季");
		} else if (month == 11) {
			System.out.println("秋季");
		} else if (month == 12) {
			System.out.println("冬季");
		} else {
			System.out.println("月份有误");
		}

		System.out.println("========================");

		if (month == 3 || month == 4 || month == 5) {
			System.out.println("春季");
		} else if (month == 6 || month == 7 || month == 8) {
			System.out.println("夏季");
		} else if (month == 9 || month == 10 || month == 11) {
			System.out.println("秋季"); 
		} else if (month == 12 || month == 1 || month == 2) {
			System.out.println("冬季");
		} else {
			System.out.println("月份有误");
		}

		System.out.println("========================");

		switch (month) {
			case 1:
				System.out.println("冬季");
				break;
			case 2:
				System.out.println("冬季");
				break;
			case 3:
				System.out.println("春季");
				break;
			case 4:
				System.out.println("春季");
				break;
			case 5:
				System.out.println("春季");
				break;
			case 6:
				System.out.println("夏季");
				break;
			case 7:
				System.out.println("夏季");
				break;
			case 8:
				System.out.println("夏季");
				break;
			case 9:
				System.out.println("秋季");
				break;
			case 10:
				System.out.println("秋季");
				break;
			case 11:
				System.out.println("秋季");
				break;
			case 12:
				System.out.println("冬季");
				break;
			default:
				System.out.println("月份有误");
				break;
		}

		System.out.println("========================");

		switch (month) {
			case 3:
			case 4:
			case 5:
				System.out.println("春季");
				break;

			case 6:
			case 7:
			case 8:
				System.out.println("夏季");
				break;

			case 9:
			case 10:
			case 11:
				System.out.println("秋季");
				break;

			case 12:
			case 1:
			case 2:
				System.out.println("冬季");
				break;
			default:
				System.out.println("月份有误");
				break;
		}
	}
}
```

### for语句的格式

```java
/*
	for语句的格式:
		for (初始化语句;循环条件语句;迭代语句) {
			循环体语句
		}

	执行流程:
		1.先执行初始化语句;
		2.确认循环条件语句的结果是true还是false
		3.如果是true,执行循环体语句;
		  如果是false,for语句结束;
		4.执行迭代语句
		5.跳回第2步,继续执行

	需求:打印10遍HelloWorld
*/

public class ForDemo01 {
	public static void main (String[] args) {
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");

		System.out.println("==============================");
		
		for (int i = 1; i <= 10 ; i++ ) {
			System.out.println("HelloWorld");
		}
	}
}
```

```java

public class ForDemo02 {
	public static void main (String[] args) {
		System.out.println(1);
		System.out.println(2);
		System.out.println(3);
		System.out.println(4);
		System.out.println(5);

		System.out.println("=============================");

		for (int i = 1; i <= 5 ; i++) {
			System.out.println(i);
		}

		System.out.println("=============================");

		for (int i = 5; i >= 1 ; i-- ) {
			System.out.println(i);
		}
	}
}
```

```java
/*
	通过for语句计算1-5之间的累加和

*/

public class ForDemo03 {
	public static void main (String[] args) {
		//声明并初始化求和变量
		int sum = 0;

		/*
		sum = sum + 1;
		sum = sum + 2;
		sum = sum + 3;
		sum = sum + 4;
		sum = sum + 5;
		*/

		for (int i = 1; i <= 5 ; i++ ) {
			sum += i;//sum = sum + i;
		}

		System.out.println("sum = " + sum);
	}
}
```

```java
/*
	通过for语句获取1-100之间的偶数之和
*/

public class ForDemo04 {
	public static void main (String[] args) {
		//声明并初始化求和变量
		int sum = 0;

		//遍历1-100之间所有整数
		for (int i = 1; i <= 100 ; i++ ) {
			//判断每个整数是否为偶数
			if (i % 2 == 0) {
				sum += i;
			}
		}

		System.out.println("sum = " + sum);
	}
}
```

```java
/*
  练习：打印所有的水仙花数
  
  分析：
  		什么是水仙花数呢?
  			所谓的水仙花数是指一个三位数，其各位数字的立方和等于该数本身。
 			举例：153就是一个水仙花数。
 			153 = 1*1*1 + 5*5*5 + 3*3*3
 
 		1.三位数其实就告诉了我们水仙花数的范围
 			100-999
 		2.如何获取一个数据的每一个位上的数呢?
 			举例：我有一个数据153，请问如何获取到个位，十位，百位
 			个位：153%10 = 3;
 			十位：153/10%10 = 5;
 			百位：153/10/10%10 = 1;
 			千位：...
 			万位：...
 		3.让每个位上的立方和相加，并和该数据进行比较，如果相等，就说明该数据是水仙花数，在控制台输出
*/

public class ForDemo05 {
	public static void main (String[] args) {
		//遍历所有的三位数
		for (int i = 100; i < 1000; i++) {
			//获取每个三位数的个位,十位,百位
			int ge = i % 10;
			int shi = i / 10 % 10;
			int bai = i / 100 % 10;

			//进行数据的筛选
			if (i == bai*bai*bai + shi*shi*shi + ge*ge*ge) {
				System.out.println(i);
			}
		}
	}
}
```

```java
/*
	打印所有的水仙花数共有多少个
*/

public class ForDemo06 {
	public static void main (String[] args) {
		//声明并初始化水仙花数的计数器变量
		int count = 0;

		//遍历所有的三位数
		for (int i = 100; i < 1000 ;i++ ) {
			//获取每个三位数的个位,十位,百位
			int ge = i % 10;
			int shi = i / 10 % 10;
			int bai = i / 100 % 10;

			//针对数据进行筛选
			if (i == bai*bai*bai + shi*shi*shi + ge*ge*ge) {
				//符合要求,计数器变量累加
				count++;
			}
		}

		//打印计数器变量
		System.out.println("count = " + count);
	}
}
```

```java
/*
	分析以下需求，并用代码实现：
	(1)打印出四位数字中个位+百位=十位+千位并且个位数为偶数，千位数为奇数的数字,并打印符合条件的数字的个数
	(2)符合条件的数字,每行显示5个,用空格隔开,打印格式如下:
		1012 1034 1056 1078 1100 
		1122 1144 1166 1188 1210
		//......
		符合条件的数字总共有: 165个
*/

public class ForDemo07 {
	public static void main (String[] args) {
		//声明并初始化计数器变量
		int count = 0;

		//遍历四位数
		for (int i = 1000; i < 10000 ; i++ ) {
			//获取每个四位数字的各个位上的数字
			int ge = i % 10;
			int shi = i / 10 % 10;
			int bai = i / 100 % 10;
			int qian = i / 1000 % 10;

			//进行数据的筛选
			if ((ge + bai == shi + qian) && (ge % 2 == 0) && (qian % 2 == 1)) {
				//符合条件,计数器累加
				count++;


				//按照规则打印符合要求数据
				if (count % 5 == 0) {
					System.out.println(i);
				} else {
					System.out.print(i + " ");
				}
			}
		}

		//打印计数器变量
		System.out.println("符合条件的数字总共有: " + count + "个");
	}
}
```

### while语句的格式

```java
/*
	while语句的格式:
		while (循环条件语句) {
			循环体语句
		}

	执行流程:
		1.确认循环条件语句的结果是true还是false
		2.如果是true,执行循环体语句;
		  如果是false,while语句结束;
		3.跳回第1步,继续执行

	为了和for循环进行转换,衍生出while的扩展格式:
		初始化语句
		while (循环条件语句) {
			循环体语句
			迭代语句
		}
*/

public class WhileDemo01 {
	public static void main (String[] args) {
		for (int i = 1; i <= 10 ; i++ ) {
			System.out.println("HelloWorld");
		}

		System.out.println("====================");

		int i = 1;
		while (i <= 10) {
			System.out.println("HelloWorld");
			i++;
		}
	}
}
```

```java
/*
 	练习：趣味折纸
  	
 	题目：
 		世界最高山峰是珠穆朗玛峰，它的高度是8848.86米，假如我有一张足够大的纸，它的厚度是0.1毫米请问，折叠多少次，不低于珠穆朗玛峰的高度?
 */

 public class WhileDemo02 {
	public static void main (String[] args) {
		//变量的声明并统一单位
		int zf = 88488600;
		int zhi = 1;

		//声明并初始化计数器变量
		int count = 0;

		//考虑不知道折叠多少次,选择while循环
		while (zhi < zf) {
			//计数器累加
			count++;

			//折叠将原有的厚度*2
			zhi *= 2;
		}

		//打印计数器变量
		System.out.println("count = " + count);
	}
 }
```

### dowhile语句的格式

```java
/*
	dowhile语句的格式
		do {
			循环体语句
		} while (循环条件语句);

	执行流程:
		1.先执行循环体语句
		2.再确认循环条件语句的结果是true还是false;
		3.如果是true,跳回第1步继续执行
		  如果是false,dowhile语句结束

	为了和for语句进行转换,衍生出dowhile语句的扩展格式:
		初始化语句
		do {
			循环体语句
			迭代语句
		} while (循环条件语句); 
*/

public class DoWhileDemo {
	public static void main (String[] args) {
		for (int i = 1; i <= 10 ; i++ ) {
			System.out.println("HelloWorld");
		}

		System.out.println("====================");

		int i = 1;
		do {
			System.out.println("HelloWorld");
			i++;
		} while (i <= 10);
	}
}
```

### 三种循环的区别

```java
/*
	三种循环的区别:
		1.判断和循环的先后顺序
			for语句先判断,后循环
			while语句先判断,后循环
			dowhile语句先循环,后判断
		2.当循环条件语句结果为false时,循环体语句至少执行次数
			for语句至少执行零次
			while语句至少执行零次
			dowhile语句至少执行一次
		3.实际开发中选择:
			有明显的循环次数(范围),选择for语句
			没有明显的循环次数(范围),选择while语句
			不会选择dowhile语句
	
*/
```

```java
/*
	流程控制语句的注意事项
		当流程控制语句{}中有且仅有一行代码时,{}可以省略不写,建议写上
*/

public class BasicDemo03 {
	public static void main (String[] args) {
		if (false) {
			System.out.println("Hello");
			System.out.println("World");
		}


		for (int i = 1; i <= 10 ; i++) {
			System.out.println("Hello");
			System.out.println("World");
		}
	}
}
```

### 控制语句

```java
/*
	控制语句:
		含义:
			控制部分"流程控制语句"和"流程控制代码块"的关键字
		分类:
			break
			continue
			return(暂不涉及)

	break关键字:
		场景:
			1.switch语句中
			2.循环语句中
		含义:
			1.结束所在的switch语句
			2.结束所在的循环语句

	continue关键字:
		场景:
			循环语句中
		含义:
			结束本次循环,继续下一次循环
			
*/
public class BasicDemo04 {
	public static void main (String[] args) {
		
		
		
		for (int i = 1; i <= 10 ; i++) {
			if (i == 3) {
				//break;
				continue;
			}

			System.out.println(i);
		}
	}
}
```

```java
/*
	控制语句的注意事项:
		在同一个作用域中,控制语句的后面不能编写其它代码,否则编译报错,因为永远无法执行
*/

public class BasicDemo05 {
	public static void main (String[] args) {
		for (int i = 1; i <= 10 ; i++) {
			if (i == 3) {
				//break;
				continue;
				System.out.println("HelloWorld");
			}

			System.out.println(i);
		}
	}
}
```

### 死循环语句

```java
/*
	死循环语句:
		含义:
			当循环条件语句的结果永远为true的循环语句
		分类:
			for语句的死循环
			while语句的死循环
			dowhile语句的死循环(忽略)

	for语句的死循环格式
		for (;;) {
			循环体语句
		}

	while语句的死循环格式:
		while (true) {
			循环体语句
		}

	for语句的死循环格式和while语句的死循环格式的区别:
		1.在实际开发中,更推荐使用while的死循环格式,该格式浅显易懂;
		2.如果开发的项目不是业务系统,而是算法,设计模式,框架,编程语言的源码,更推荐使用for语句的死循环,因为执行效率更高
*/
public class BasicDemo01 {
	public static void main (String[] args) {
		/*
		for (;;) {
			System.out.println("HelloWorld");
		}
		*/

		while (true) {
			System.out.println("HelloWorld");
		}
	}
}
```

### 循环嵌套语句

```java
/*
	循环嵌套语句:
		含义:
			在循环语句中存在另外一个循环语句(指代for语句的嵌套)
		解释:
			外层循环语句:声明在外面的循环语句
			内层循环语句:声明在外层循环语句的循环体位置上的循环语句
			外层循环语句和内层循环语句是一组相对的概念
		格式:
			for (外层循环的初始化语句;外层循环的循环条件语句;外层循环的迭代语句) {
				for (内层循环的初始化语句;内层循环的循环条件语句;内层循环的迭代语句) {
					内层循环的循环体语句
				}
			}
		执行流程:
			1.先执行外层循环的初始化语句;
			2.再确认外层循环的循环条件语句的结果是true还是false
			3.如果是false,循环嵌套语句结束;
			  如果是true,执行外层循环的循环体语句;
			  a.执行内层循环的初始化语句
			  b.确认内层循环的循环条件语句的结果是true还是false
			  c.如果是false,内层循环语句结束,继续执行第4步;
			    如果是true,执行内存循环的循环体语句;
			  d.执行内层循环的迭代语句;
			  e.跳回第b步,继续执行
			4.执行外层循环的迭代语句
			5.跳回第2步继续执行

	需求:按照固定的格式打印一天中的时间
		格式:
			XX时XX分
*/
public class BasicDemo02 {
	public static void main (String[] args) {
		//外层循环:控制小时
		for (int h = 0; h < 24 ; h++) {
			//内层循环:控制分钟
			for (int m = 0; m < 60 ; m++) {
				System.out.println(h + "时" + m + "分");
			}
		}
	}
}
```

```java
/*
	循环嵌套语句的注意事项:
		1.循环嵌套语句中外层循环的初始化语句执行了1次
		2.循环嵌套语句中内层循环的初始化语句执行了"外层循环的循环次数"次
		3.循环嵌套语句中内层循环的循环体语句执行了"外层循环的循环次数 * 内层循环的循环次数"次
		4.循环嵌套语句嵌套的层数越多,循环次数越多,执行效率越低,在实际应用中,尽量避免使用过程层数的循环嵌套语句,一般情况下,使用到双层循环嵌套即可,三层及以上肯定有简化方式
*/
public class BasicDemo03 {
	public static void main (String[] args) {
		for (int bai = 1; bai < 10 ; bai++ ) {
			for (int shi = 0; shi < 10 ; shi++ ) {
				for (int ge = 0; ge < 10 ; ge++ ) {
					System.out.println(bai*100 + shi*10 + ge*1);
				}
			}
		}

		System.out.println("================================");

		for (int i = 100; i < 1000 ; i++ ) {
			System.out.println(i);
		}
	}
}
```

```java
/*
	花100文钱买100只鸡
	公鸡5文1只
	母鸡3文1只
	小鸡1文3只
	花100文钱正好买100只鸡

	思路:
		一种一种的可能性进行尝试
*/
public class BasicDemo04 {
	public static void main (String[] args) {
		for (int gong = 0; gong <= 100 ; gong++ ) {
			for (int mu = 0; mu <= 100 ; mu++) {
				for (int xiao = 0; xiao <= 100 ; xiao++ ) {
					//进行数据筛选
					if ((gong + mu + xiao == 100) && (5*gong + 3*mu + xiao/3 == 100) && (xiao % 3 == 0)) {
						System.out.println("公鸡有"+gong+"只，母鸡有"+mu+"只，小鸡有"+xiao+"只");
					}
				}
			}
		}
	}
}
```

```java
/*
	百钱买百鸡的优化
*/

public class BasicDemo05 {
	public static void main (String[] args) {

		//循环次数:1030301
		for (int gong = 0; gong <= 100 ; gong++ ) {
			for (int mu = 0; mu <= 100 ; mu++) {
				for (int xiao = 0; xiao <= 100 ; xiao++ ) {
					//进行数据筛选
					if ((gong + mu + xiao == 100) && (5*gong + 3*mu + xiao/3 == 100) && (xiao % 3 == 0)) {
						System.out.println("公鸡有"+gong+"只，母鸡有"+mu+"只，小鸡有"+xiao+"只");
					}
				}
			}
		}

		System.out.println("=================================");

		//循环次数:72114
		for (int gong = 0; gong <= 20 ; gong++ ) {
			for (int mu = 0; mu <= 33 ; mu++) {
				for (int xiao = 0; xiao <= 100 ; xiao++ ) {
					//进行数据筛选
					if ((gong + mu + xiao == 100) && (5*gong + 3*mu + xiao/3 == 100) && (xiao % 3 == 0)) {
						System.out.println("公鸡有"+gong+"只，母鸡有"+mu+"只，小鸡有"+xiao+"只");
					}
				}
			}
		}

		System.out.println("=================================");

		//循环次数:24276
		for (int gong = 0; gong <= 20 ; gong++ ) {
			for (int mu = 0; mu <= 33 ; mu++) {
				for (int xiao = 0; xiao <= 100 ; xiao+=3 ) {
					//进行数据筛选
					if ((gong + mu + xiao == 100) && (5*gong + 3*mu + xiao/3 == 100)) {
						System.out.println("公鸡有"+gong+"只，母鸡有"+mu+"只，小鸡有"+xiao+"只");
					}
				}
			}
		}

		System.out.println("=================================");

		//循环次数:714
		for (int gong = 0; gong <= 20 ; gong++ ) {
			for (int mu = 0; mu <= 33 ; mu++) {
				int xiao = 100 - gong - mu;
				//进行数据筛选
				if ((5*gong + 3*mu + xiao/3 == 100) && (xiao % 3 == 0) && (xiao >= 0)) {
					System.out.println("公鸡有"+gong+"只，母鸡有"+mu+"只，小鸡有"+xiao+"只");
				}
			}
		}

		System.out.println("=================================");

		//循环次数:714
		for (int gong = 0; gong <= 20 ; gong++ ) {
			for (int xiao = 0; xiao <= 100 ; xiao+=3 ) {
				int mu = 100 - gong - xiao;
				//进行数据筛选
				if ((5*gong + 3*mu + xiao/3 == 100) && (mu >= 0)) {
					System.out.println("公鸡有"+gong+"只，母鸡有"+mu+"只，小鸡有"+xiao+"只");
				}
			}
		}
	}
}
```

```java
/*
	打印1-100之间所有质数
		
	质数:也叫素数,只能被1或者本身进行整除的正整数,1不是质数
	特点:有且仅有两个因数

	思路:
		判断1-100之间每个整数因数的个数
*/

public class BasicDemo06 {
	public static void main (String[] args) {
		for (int i = 1 ; i <= 100 ; i++) {
			//针对每个被除数声明因数统计计数器变量
			int count = 0;

			for (int j = 1; j <= i ; j++) {
				//进行整除判断
				if (i % j == 0) {
					count++;
				}
			}

			if (count == 2) {
				System.out.println(i);
			}
		}
	}
}
```

```java
/*
	质数的优化
*/

public class BasicDemo07 {
	public static void main (String[] args) {
		for (int i = 2 ; i <= 100 ; i++) {
			//针对每个质数设置标记变量,true为质数,false为非质数
			boolean flag = true;

			for (int j = 2; j < i ; j++) {
				//进行整除判断
				if (i % j == 0) {
					flag = false;
					break;
				}
			}

			if (flag) {
				System.out.println(i);
			}
		}

	}
}
```

## 方法

```java
/*
	方法:
		含义:
			在程序中封装特殊功能的代码
		好处:
			1.提高程序的复用性,从而提高开发效率
			2.降低代码的耦合性
				耦合性:程序与程序之间的关联,耦合性越大程序越不方便维护
			
*/
public class MethodDemo01 {
	public static void main (String[] args) {
		method(13);

		System.out.println("打印水仙花数");

		method(5);

		System.out.println("趣味折纸");

		method(7);

		System.out.println("百钱买百鸡");

		method(11);
	}

	public static void method (int num) {
		for (int i = 1; i <= num ; i++) {
			System.out.println("HelloWorld");
		}
	}
}
```

### 方法的特点

```java
/*
	方法的特点:
		1.在程序中方法与方法之间的关系:调用关系(调用结论)
		2.方法特点核心:不调用,不执行
		3.在方法调用的过程中有两个重要的关键性动作:传递参数(传参)和返回结果(返回)
			传参:
				含义:
					在调用方法时,将实际参数传递给形式参数的过程
				解释:
					实际参数(实参):
						方法调用时()参数列表中的参数,是具体的数据值或地址值
					形式参数(形参):
						方法声明时()参数列表中的参数,是具体数据值或地址值类型的声明
				目的:
					在调用者方法中调用了另外一个方法,调用者方法中数据另外一个方法无法直接进行使用,需要通过参数传递形式让另外一个方法可以使用调用者方法中的数据
			返回:
				含义:
					在调用方法结束时,将方法的结果数据返回给调用者的过程
				目的:
					当调用者方法需要另外一个方法中的结果数据时,无法直接进行获取,需要通过返回结果的方式将结果数据返回给调用者方法
*/

public class MethodDemo02 {
	public static void main (String[] args) {
		
	}
}
```

### 方法声明的格式

```java
/*
	方法声明的格式:
		修饰符 返回类型 方法名 (形参类型1 形参名1,形参类型2 形参名2,......形参类型n 形参名n) {
			方法体语句
			return 返回值;
		}

	方法声明格式的解释:
		修饰符:修饰Java程序的语法关键字,目前阶段使用public static进行替代
		返回类型:返回结果数据的数据类型
			分类:无返回类型,基本类型,引用类型
		方法名:给方法起的名字,做到"见名知意"
		():形参列表
			分类:没有形参,基本类型,引用类型
		方法体语句:特殊功能的代码片段
		return:控制语句,(1)结束方法(2)返回结果数据
		返回值:方法的结果数据
			
*/

public class MethodDemo03 {
	public static void main (String[] args) {
		
	}
}
```

```java
/*
	方法声明前的两个明确:
		返回类型:
			明确方法结果数据的数据类型
		形参列表:
			明确需要使用调用者方法中几个数据
			明确每个数据的数据类型和变量名

	需求:通过方法获取两个整数的求和操作
*/

public class MethodDemo04 {
	public static void main (String[] args) {
		
	}

	/*
		两个明确:
			返回类型:int
			形参列表:int a, int b
	*/

	public static int getSum (int a , int b) {
		int sum = a + b;
		return sum;
	}
}
```

### 方法的调用格式

```java
/*
	方法的调用格式:
		如果方法归属于"对象",需要使用对象名进行调用(暂不涉及)
			单独调用(直接调用)
				格式:对象名.方法名(实参);
			输出调用(打印调用)
				格式:System.out.println(对象名.方法名(实参));
			赋值调用
				格式:数据类型 变量名 = 对象名.方法名(实参);

		如果方法归属于"类",需要使用类名进行调用(暂不涉及)
			单独调用(直接调用)
				格式:类名.方法名(实参);
			输出调用(打印调用)
				格式:System.out.println(类名.方法名(实参));
			赋值调用
				格式:数据类型 变量名 = 类名.方法名(实参);

		如果调用同一个类中(或父类中非重写方法)的方法
			单独调用(直接调用)
				格式:方法名(实参);
			输出调用(打印调用)
				格式:System.out.println(方法名(实参));
			赋值调用
				格式:数据类型 变量名 = 方法名(实参);

*/

public class MethodDemo05 {
	public static void main (String[] args) {
		//单独调用(直接调用)
		//getSum(3,4);
		//输出调用(打印调用)
		//System.out.println(getSum(3,4));
		//赋值调用
		int sum = getSum(3,4);
		System.out.println("sum = " + sum);
	}

	/*
		两个明确:
			返回类型:int
			形参列表:int a, int b
	*/

	public static int getSum (int a , int b) {
		int sum = a + b;
		return sum;
	}
}
```

```java
/*
	栈内存(本地方法栈)
		含义:
			JVM内存中存储"正在运行方法"的内存区域
		解释:
			进栈(压栈):方法进行栈内存的过程
			出栈(弹栈):方法在栈内存中消失的过程
		特点:
			1.方法的出栈是立即出栈
			2.方法进栈和出栈遵循"先进后出,后进先出"规则
*/

public class MethodDemo06 {
	
}
```

```java
/*
	需求:通过方法实现两个整数比较是否相同功能
*/

public class MethodDemo07 {
	public static void main (String[] args) {
		boolean result = compare(3,4);

		System.out.println(result);
	}

	/*
		两个明确:
			返回类型:boolean
			形参列表:int a,int b
	*/
	public static boolean compare (int a,int b) {
		/*
		if (a == b) {
			return true;
		} else {
			return false;
		}
		*/
		//return a == b ? true : false;

		return a == b;
	}
}
```

```java
/*
	通过方法实现1到100的累加和
*/

public class MethodDemo08 {
	public static void main (String[] args) {
		int sum = getSum();
		System.out.println("sum = " + sum);

		System.out.println("==========================");

		sum = getSum(1,100); 
		System.out.println("sum = " + sum);
	}

	/*
		两个明确:
			返回类型:int
			形参列表:int start , int end
	*/
	public static int getSum (int start , int end) {
		//声明并初始化求和变量
		int sum = 0;

		for (int i = start; i <= end ; i++) {
			sum += i;
		}

		return sum;
	}

	/*
		两个明确:
			返回类型:int
			形参列表:没有形参
	*/
	public static int getSum () {
		//声明并初始化求和变量
		int sum = 0;

		for (int i = 1; i <= 100 ; i++ ) {
			sum += i;
		}

		return sum;
	}
}
```

```java
/*
	需求:通过方法实现打印指定次数的HelloWorld

	void关键字:
		含义:
			方法没有返回值
		作用:
			当方法没有返回值时,返回类型的位置也不能空着,需要使用void关键字进行占位
		注意:
			1.当方法的返回类型为void时,调用方式只能使用单独调用(直接调用)
			2.当方法的返回类型为void时,方法的return关键字可以省略不写
*/

public class MethodDemo09 {
	public static void main (String[] args) {
		printHW(10);
	}

	/*
		两个明确:
			返回类型:没有返回类型
			形参列表:int num
	*/
	public static void printHW (int num) {
		for (int i = 1; i <= num ; i++ ) {
			System.out.println("HelloWorld");
		}

		//return;
	}
}
```

### 方法的小结

```java
/*
	方法的小结:
		1.方法的声明位置必须在类中方法外,不能形成方法的嵌套
		2.当方法没有返回值的时候,返回类型的位置也不能空着,需要使用void关键字进行占位
		3.当方法的返回类型是void时,方法的return关键字可以省略不写
		4.方法核心特点:不调用,不执行
		5.进行方法调用的时候,实参列表和形参列表必须一一进行对应
		6.当方法的返回类型不是void时,调用方式推荐使用赋值调用
		7.当方法的返回类型为void时,调用方式只能使用单独调用(直接调用)
*/
```

### 方法的重载

```java
/*
	方法的重载:
		含义:在同一个类中(或子父类继承关系中),出现了方法名相同,形参列表不同的现象

	方法重载的前提条件:
		1.必须在同一个类中(或子父类继承关系中)
		2.方法名必须相同
		3.形参列表必须不同(至少满足以下一点)
			(1)形参个数不同
			(2)形参的数据类型不同
			(3)形参数据类型的顺序不同
*/

public class MethodDemo11 {
	
	//声明打印两个整数之和的方法
	public static void printSum (int a, int b) {}

	//声明打印两个浮点数之和的方法
	public static void printSum (double a, double b) {}

	//声明打印三个整数之和的方法
	public static void printSum (int a, int b, int c) {}

	//声明打印一个整数和一个浮点数之和的方法
	public static void printSum (int a, double b) {}

	//声明打印一个浮点数和一个整数之和的方法
	public static void printSum (double a, int b) {}
}
```

```java
/*
	方法重载的注意事项:
		执行重载方法时,具体执行哪个方法取决于调用方法时的实参
*/

public class MethodDemo12 {
	public static void main (String[] args) {
		//method((byte)123);
		method(3,4);
	}

	public static void method (double a , int b) {
		System.out.println("double,int");
	}

	public static void method (int a , double b) {
		System.out.println("int,double");
	}

	/*
	public static void method (byte num) {
		System.out.println("byte");
	}
	*/

	public static void method (short num) {
		System.out.println("short");
	}

	public static void method (int num) {
		System.out.println("int");
	}

	public static void method (long num) {
		System.out.println("long");
	}
}
```

### 方法的递归

```java
/*
	方法的递归:
		含义:
			在程序中,方法自身调用自身的现象
		分类:
			直接递归:
				在a方法中调用a方法
			间接递归:
				在a方法中调用b方法,在b方法中调用c方法,在c方法中调用a方法
		注意:
			1.使用递归需要给递归添加结束条件,否则会发生栈内存溢出(StackOverflowError)
			2.使用递归即使添加了结束条件,也不能递归层数过多,否则会发生栈内存溢出(StackOverflowError)
		好处:
			方法的递归和循环类似,可以帮助我们解决一些循环语句无法解决的问题
			例如:
				遍历多级文件夹
	
*/

public class MethodDemo13 {
	static int num = 1;

	public static void main (String[] args) {
		method();
	}

	public static void method () {
		System.out.println(num++);

		if (num == 100000) {
			return;	
		}

		method();
	}
}
```

```java
/*
	需求:通过方法的递归实现1到指定数的求和运算
*/

public class MethodDemo14 {
	public static void main (String[] args) {
		int value = getValue(5);
		System.out.println("sum = " + value);

		System.out.println("============================");

		int sum = getSum(5);
		System.out.println("sum = " + sum);
	}

	/*
		两个明确:
			返回类型:int
			形参列表:int num
	*/
	public static int getSum(int num) {
		//给递归添加限定的条件
		if (num == 1) {
			return 1;
		}

		return num + getSum(num - 1);
	}


	/*
		两个明确:
			返回类型:int
			形参列表:int num
	*/
	public static int getValue(int num) {
		//声明并初始化求和变量
		int sum = 0;

		//累加求和
		for (int i = 1; i <= num ; i++) {
			sum += i;
		}

		return sum;
	}
}
```

```java
/*
  需求：
  		有一对兔子，从出生后第3个月起每个月都生一对兔子，小兔子长到第三个月后每个月又生一对兔子，
  		假如兔子都不死，问指定月份的兔子对数为多少？ 
  
  规律：
  		第一个月：1
  		第二个月：1
  		第三个月：2
  		第四个月：3
  		第五个月：5
  		第六个月：8
  		...
  
  		规律：从第三个月开始，每个月的兔子对数是前两个月的兔子对数之和
           第一个月和第二个月的兔子对数都是1
*/

public class MethodDemo15 {
	public static void main (String[] args) {
		long num = getNum(7);
		System.out.println("兔子的总对数:" + num);
	}

	/*
		两个明确:
			返回类型:long
			形参列表:int month
	*/
	public static long getNum (int month) {
		//给递归添加限定的条件
		if (month == 1 || month == 2) {
			return 1;
		}

		return getNum(month - 1) + getNum(month - 2);
	}
}
```

```java
/*
	方法递归的弊端:
		递归层数越多程序的执行效率越低
*/

public class MethodDemo16 {
	//声明并初始化方法调用次数的计数器变量
	static long count = 0;

	public static void main (String[] args) {

		//获取此时的纳秒时间
		long start = System.nanoTime();

		long num = getNum(50);

		//获取此时的纳秒时间
		long end = System.nanoTime();

		System.out.println("兔子的总对数:" + num);
		System.out.println("方法调用次数:" + count);
		System.out.println("程序运算时间:" + (end - start));
	}

	/*
		动态规划:
	*/
	public static long getNum (int month) {
		//方法调用次数的计数器累加
		count++;

		//给递归添加限定的条件
		if (month == 1 || month == 2) {
			return 1;
		}

		//声明并初始化当前月份兔子对数变量
		long num = 0;
		//声明并初始化上个月份兔子对数变量
		long a = 1;
		//声明并初始化上上个月份兔子对数变量
		long b = 1;

		//遍历月份
		for (int i = 3; i <= month ; i++) {
			num = a + b;
			//为下次循环操作进行准备
			b = a;
			a = num;
		}

		return num;
	}

	/*
		两个明确:
			返回类型:long
			形参列表:int month

		兔子的总对数:125.86269025
		方法调用次数:251.72538049
		程序运算时间:32.731882900
	
	public static long getNum (int month) {
		count++;

		//给递归添加限定的条件
		if (month == 1 || month == 2) {
			return 1;
		}

		return getNum(month - 1) + getNum(month - 2);
	}
	*/
}
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```

```java
```
