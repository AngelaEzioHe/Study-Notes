# Java 笔记

## 快速入门

**第一个程序：**

```java
//1.public class test表示Hello是个类，是一个public共有的类
//2.Hell0{ }表示一个类的开始和结束
//3.public static void main(String[] args) 表示一个主方法，即我们程序的入口
//4.main{ }表示方法的开始和结束
//5. System.out.printIn(""); 表示输出双引号内的东西到屏幕上
//public类只能有一个
public class Hello     //注意，这块儿的“Hello”要和文件名一致
{
    public static void main(String[] args)
    {
        System.out.printIn("hello world~");    //注意，println是小写的L不是大写的I
	}
}
```



## +号使用

```java
System.out.println(100+98); //198
System.out.println("100"+98); //10098
System.out.println(100+3+"hello"); //103hello
System.out.println("hello"+100+3); //hello1003
```

**注意：**

1. 从左到右，依次运算
2. 左右两方，有一方为字符串时，做拼接运算
3. 左右两方都是数值时，做四则运算



## 整型细节

```java 
int n1 =1;
long n2 = 1L;//定义long型常量为其赋值时要在常量后加"l"或"L"。
```



## 浮点数细节

```java
float	f1 = 1.1; //写法错误，java中，小数默认为double型，若为float型常量赋值，应在常量后加上“F”。
float	f2 = 1.1F;//正确
double	f3 = .123; //正确写法，0.123可以省略小数点前的0，但小数点不可省略
double	f4 = 5.12e2; //意为5.12*(10^2)
double	f5 = 2.7;
double	f6 = 8.1 /3; //结果为2.6999997
```

*对运算结果是小数的进行判断时，要小心。应该是以两个数的差值的绝对值在某个精度范围内进行判断*

```java
if(Math.abs(f5-f6) < 0.00001)
{
    System.out.println("差值非常小，到我的规定精度，认为相等");
}
```

## 字符型细节

**java中，char类型的本质是一个整数，再默认输出时，是unicode码对应的字符**

```java
char c1 ='何';
System.out.println((int)c1); //“何”对应的unicode码为20309
char c2 = 20309;
System.out.println(c2);
```

```java
System.out.println('a' + 10); //结果为107。（编译器先将‘a’转换为97，再和10进行运算。
```



## bool类型细节

**布尔类型：boolean**		值只能为 true 或 false

不可以以0或非0的整数替代 false 和 true

**和C语言不同**

**和C语言不同**

**和C语言不同**



## 基本数据类型转换

char -> int -> long -> float -> double

byte -> short -> int -> long -> float -> double

**所以，以下代码正确**

```java
int a = 'c';
double d = 80;
```



### 强制类型转换

**注意：**

- 会有精度损失
- 会有溢出

byte 和 char、short进行运算时，都先转换成int处理

### String类型基本转换

**基本数据类型 + " "就转换成字符串格式了**

```java
//基本数据类型->String
int n1 = 100;
float f1 = 1.1F;
double d1 = 4.5;
boolean b1 = true;
String s1 = n1 + "";
String s2 = f1 + "";
String s3 = d1 + "";
String s4 = b1 + "";
System.out.println(s1 + " " + s2 + " " + s3 + " " + s4);
```

 

**用特定的类将字符串转换成对应的基本数据类型：**

```java
//String->对应的基本数据类型
String s5 = "123";
int num1 = Integer.parseInt(s5);
double num2 = Double.parseDouble(s5);
float num3 = Float.parseFloat(s5);
long num4 = Long.parseLong(s5);
byte num5 = Byte.parseByte(s5);
boolean b = Boolean.parseBoolean("true");
short num6 = Short.parseShort(s5);

System.out.println(num1);
System.out.println(num2);
System.out.println(num3);
System.out.println(num4);
System.out.println(num5);
System.out.println(num6);
System.out.println(b);
```



## 算术运算符

### 练习一

```java
int i=1;
i=i++;
System.out.println(i); //结果为1
```

计算机实际过程：

```java
(1)temp = i;
(2)i = i +1;
(3)i = temp;
```

### 练习二

```java
int i = 1;
i = ++i;
System.out.println(i); //结果为2
```

计算机实际过程为：

```java
(1)temp = i;
(2)i = i + 1;
(3)i = temp;
```



## 逻辑运算符

-  && 和 &的区别
  - &&(短路与)：如果第一个条件为false，则第二个条件不会判断，最终结果为false，效率高。
  - &   (逻辑与)：不管第一个条件是否为false，第二个条件都要判断，效率低。

**开发中，我们使用的基本上是短路与&&，效率高。**

- ||和|的区别类似于&&和&。一个效率高一个效率低。
- ^ 和 ! 表示的含义与C语言相同。



## 赋值运算符

**有时候复合赋值运算会进行类型转换**

```java
byte b =3;
b +=2; //等价于 b = (byte)(b +2);
//但是 b = b + 2;这样编译会报错。
```



## 三元运算符

**经典案例：**实现三个数最大值

```java
int n1=55;
int n2=33;
int n3=123;
int max1 = n1 > n2 ? n1 : n2;
int max2 = max1 > m3 ? max1 : n3;
System.out.println(max2);
```



## 键盘输入

```java
import java.util.Scanner;
public class Input
{
    public static void main(String[] args)
    {
        //接收用户的输入
        //1.引入Scanner所在的包
        //2.创建 Scanner 对象，new创建一个对象
		//myScanner就是Scanner类的对象
        Scanner myScanner = new Scanner(System.in);
        //3.接收用户输入
        System.out.println("请输入名字");
        String name = myScanner.next(); //接收用户输入
        System.out.println("请输入年龄");
        int age = myScanner.nextInt(); //接收用户输入
        System.out.println("请输入薪水");
        double sal = myScanner.nextDouble(); //接收用户输入
        System.out.println("人的信息如下");
        System.out.println("名字：" + name +" 年龄：" + age +" 薪水：" +sal);
        char letter = myScanner.next().charAt(0);
    }    
}

```



## 进制

**整数有四种表示方式：**

1. 二进制：0,1，满2进1，以0b或0B开头；
2. 十进制：略；
3. 八进制：0-7，满8进1，以数字 0 开头；
4. 十六进制：0-9及A-F，满16进1，以0x或0X开头表示 （A-F不区分大小写）



## 跳转控制语句

- break语句出现在多层嵌套的语句块中时，可以通过标签指明要终止的是哪一层语句块

 ```java
 public class BreakDetail
 {
     public static void main(String[] args)
     {
         abc1://标签一
         for(int j=0;j<4;j++)
         {
             abc2://标签二
             for(int i=0;i<10;i++)
             {
                 if(i == 2)
                 {
                     break abc1;//从abc1中跳出去
                 }
                 System.out.println("i = " + i);
             }
         }
     }
 }
 ```

## 字符串的比较函数

字符串的比较一般不用 **==** 来比较，一般会使用  **.equals( )** 函数来比较。

**一般形式：**

```java
String str1;
String str2;
str.equals(str2);
```

- 如果相等，返回true
- 如果不相等，返回false

当比较 **“林黛玉”** 和 **str** 时，有两种方式：

```java
str.equals("林黛玉");
"林黛玉".equals(str);//推荐这个写法，可以避免空指针
```



## 数组的使用

### 方式一：动态初始化(一步到位)

数组的定义：

```java
数据类型[ ] 数组名 = new 数据类型 [大小] ;
int[] a = new int[5]; //创建一个数组，名字是a，存放5个int
```

### 方式二：动态初始化(先声明再创建)

**先声明数组**

*语法：*

```java
数据类型 数组名[ ]; /*也可以*/ 数据类型[ ] 数组名;
int[] a; //此时 scores 是 null
```

**创建数组：**

*语法：*

```java
数组名=new 数据类型[大小];
a=mew int[10];
```

### 方式三：静态初始化

**初始化数组：**

*语法：*

```java
数据类型 数组名[ ]= {元素值，元素值...};
int a[]={2,5,6,8,89,};
```



## 数组赋值机制

- 基本类型数据赋值，这个值就是具体的数据，而且相互不影响

  ```java
  int n1=10;
  int n2=n1;
  n2=80;
  System.out.println("n1="+n1);
  System.out.println("n2="+n2);
  ```

- 数组在默认情况下是**引用传递**，赋的值是地址。

  ```java
  int[] arr1={1,2,3};
  int[] arr2=arr1;
  for(int i=0;i<3;i++)
  {
      System.out.print(arr1[i]+" ");
  }
  arr2[0]=10;
  for(int i=0;i<3;i++)
  {
      System.out.print(arr1[i]+" ");
  }
  ```
















