---
title: Java基础
pubDate: 2022-10-26
categories: ['Java']
description: '这篇笔记将涵盖Java的基本语法、数据类型、控制流程和面向对象编程等重要概念。无论你是初学者还是有一定经验的开发者，这些笔记都将为你提供一个扎实的Java基础知识基础'
slug: Java Basics
---

# Java基础


1. Java对大小写敏感。
2. 关键字class对意思是类。Java是面向对象的语言，所有代码必须放在class里面。
3. 编译后的源文件，得到相应的字节码文件，编译起为每个类生成独立的字节码文件。
4. main方法是Java应用程序的入口方法 固定格式: **Public static void (String[] args) { }**
5. 一个源文件可以包含多个类。
6. 每个语句必须以分号结束，回车不是语句的结束标志。

:::details Click to see more

建议：
1. 编程是一定要注意缩进规范
2. 在写括号、引号时，一定要成对敲出来后再往里面写代码	



:::



## 创建第一个Java程序

​	在桌面创建一个java文本文件，命名为 **test**（test.java），然后编辑**test.java**文件，写入代码如下：

```java
public class test {	//class的名字一定要和java文本文件名一致！！！
    public static void main(String[] args) {	//开头固定搭配！！！
        System.out.println("Chan_Honman,你好！");
        System.out.println("this is a test!");
        System.out.println("这是第三行代码");
    }
}

```

​	写完代码后记得保存（⌘ + s / Ctrl + s ），然后打开终端输入命令如下：

```bash
#	将test.java文件编译成字节码文件 
javac test.java
#	运行程序
java test
```

​	其中 javac 命令的作用是：启动java的编译器程序。对指定扩展名的.java文件进行编译。 生成了jvm可以识别的字节码文件。也就是class文件，也就是java的运行程序。

​	而 java 命令的作用是：负责运行的部分.会启动jvm.加载运行时所需的类库,并对class文件进行执行.一个文件要被执行,必须要有一个执行的起始点,这个起始点就是main函数.

​	工作原理如下：

![java工作原理](/images/Java/Java工作原理.png)



## 最常用DOS命令

磁盘操作系统（Disk Operating System）是早期个人电脑上的一类操作系统。

常用命令：

| 命令    | 说明                           |
| ------- | ------------------------------ |
| cd      | 进入一个目录                   |
| cd ..   | 进入父级目录                   |
| dir     | 查看本目录下的文件和子目录列表 |
| cls     | 清楚屏幕命令 现在是（clear）   |
| 上下键  | 查找之前敲过的命令             |
| Tab键盘 | 自动补全命令                   |



## 十进制和二进制转换

### 1.十进制转二进制

​	十进制整数转换为二进制整数采用 **“除2取余 逆序排序”** 法。

将十进制的(43)D转换为二进制的步骤如下：

1. 将商43除以2，商21余数为1；

2. 将商21除以2，商10余数为1；

3. 将商10除以2，商5余数为0；

4. 将商5除以2，商2余数为1；

5. 将商2除以2，商1余数为0； 

6. 将商1除以2，商0余数为1； 

7. 读数，因为最后一位是经过多次除以2才得到的，因此它是最高位，读数字从最后的余数向前读，101011，即(43)D=(101011)B。

### 2.二进制转十进制

​	采用 **“权位相加”** 法

将二进制的(101011)B转换为十进制的步骤如下：

1. 第0位 1 x 2^0 = 1；

2. 第1位 1 x 2^1 = 2；

3. 第2位 0 x 2^2 = 0；

4. 第3位 1 x 2^3 = 8；

5. 第4位 0 x 2^4 = 0；

6. 第5位 1 x 2^5 = 32；

7. 读数，把结果值相加，1+2+0+8+0+32=43，即(101011)B=(43)D。



## Java注释

​	注释不会出现在字节码文件中，也就是说编译器是会跳过注释的语句。在Java中注释分为三种。

### 1.单行注释

```java
public class Welcome {

    //这是单行注释 main（）方法是程序的入口
    public static void main(String[] args) {
        System.out.println("Chan_Honman,你好！");
    }
}

```



### 2.多行注释

```java
public class Welcome {

    /*
        这是多行注释
        这是多行注释
        这是多行注释
    */
    public static void main(String[] /*行内注释： arguments的缩写是args */args) {
        System.out.println("Chan_Honman,你好！");
    }
}

```



### 3.文档注释

```java

/**
 * 这是文档注释 主要用于开发环境 IDEA、Eclipse、VScode
 * @author chan_honman
 * @version 1.0
*/
public class Welcome {
    public static void main(String[] args) {
        System.out.println("Chan_Honman,你好！");
    }
}

```



## 标识符和关键字



### 1.标识符

​	**标识符**是用来给变量、类、方法和包进行命名的。

标识符4大规则：

1. 必须以字母、下划线_ 、美元符号$ 开头。
2. 其他部分可以是字母、下划线_ 、美元符号$ 和数字任意组合。
3. 大小写敏感，且长度无限制。
4. 不可用Java的**关键字**。

:::tip

表示类名的标识符：每个单词的首字母大写，如：Boy、GoodBoy

表示方法和变量的标识符：第一个字母小写，从第二个单词开始首字母大写（**驼峰原则**）如：eat()、eatFood()

​	Java不采用ASCII字符集，而是用Unicode字符集。所以这里字母的含义不仅仅是英文，还包括汉字等等。但是**不建议使用汉字来定义标识符**！因为不够高级，不够酷，**不够官方**。



:::



### 2.关键字

​	**48个关键字**：abstract、assert、**boolean**、**break**、byte、case、catch、**char**、**class**、continue、default、do、**double**、else、enum、extends、final、finally、**float**、**for**、**if**、implements、**import**、**int**、interface、instanceof、**long**、native、**new**、package、private、protected、**public**、**return**、**short**、**static**、strictfp、super、**switch**、synchronized、**this**、throw、throws、transient、**try**、**void**、volatile、**while**。



## 变量的分类和作用域

变量有三种类型：

1. 局部变量
2. 成员变量（实例变量）
3. 静态变量

| 类型                 | 声明位置           | 从属于      | 生命周期（作用域）                                         |
| -------------------- | ------------------ | ----------- | ---------------------------------------------------------- |
| 局部变量             | 方法或语句内部     | 方法/语句块 | 从声明位置开始。知道方法或语句块执行完毕。局部变量消失     |
| 成员变量（实例变量） | 类内部，方法外部   | 对象object  | 对象创建，成员变量页跟着创建。对象消失，成员变量也跟着消失 |
| 静态变量（类变量）   | 类内部，static修饰 | 类class     | 类被加载，静态变量就有效。类被卸载，静态变量消失           |

```java
public class test {

    int a = 3;  //成员变量
    static int b = 4;   //静态变量

    public static void main(String[] agrs) {
        //局部变量
        int age = 18;
        int b;  //只是声明了变量b 还没有初始化
        int x = 0, y = 0, z = 1;

        System.out.println(age);    //输出：18
        b = 0;  //变量使用之前必须初始化
        System.out.println(b);  //输出：0
        System.out.println(z);  //输出：1
    }
}

```

:::tip

**下面代码哪个是正确的？？？**

A代码如下：

```java
public void test(){
        int i;
        int j = i + 5; 
    }
```

B代码如下：

```java
public void test(){
        int i;
        i = 5;
        int j = i + 5; 
    }
```



:::

:::details Click to see the answer

答案：B

因为 A 代码中的错误如下：

```java
public void test(){
        int i;
        int j = i + 5;  //编译出错 变量 i 没有被初始化
    }
```

**变量 i 没有被初始化**



:::



## 常量 和 final

​	在Java中，用关键字 **final** 来定义一个常量。常量**一旦被初始化后就不能再更改**。

声明格式：**final** type varName = value;

```java
public class TestConstant {
    public static void main(String[] args) {
        final double pi = 3.14;
        //pi = 3.1415;    //Cannot assign a value to final variable 'pi'
        System.out.println(pi);
    }
}
```

> 一般将1、2、3、'a'、'b'、'c'、true、false、"helloWorld"等称为**字符常量**，而使用final修饰的 pi 等称为**符号常量**。

:::tip

**变量和常量的命名规范**

1. 大写字母和下划线：MAX_VALUE
2. 类成员变量：首字母小写、驼峰原则
3. 类名：首字母大写、驼峰原则（ Man、GoodMan ）
4. 方法名：首字母小写、驼峰原则( play()、playComputer() )

**练习题：圆的半径r为4 π约为3.14 计算该圆的面积area和周长perimeter**



:::

:::details Click to see the answer

```java
/**
 * 圆的半径r为4 π约为3.14 计算该圆的面积area和周长perimeter
 */
public class TestConstant {
    public static void main(String[] args) {
        final double pi = 3.14; //π
        int r = 4;  //半径为4
        double area = pi * r * r;
        double perimeter = 2 * pi * r;
        System.out.println("圆的面积：" + area); //输出：圆的面积：50.24
        System.out.println("圆的周长：" + perimeter);    //输出：圆的周长：25.12
    }
}

```



:::



## 基本数据类型 Primitive data type

![](/images/Java/基本数据类型.png)

### 整数类型

一共有**四种类型**：

| 类型      | 占用存储空间 | 范围              |
| --------- | ------------ | ----------------- |
| **byte**  | 1字节        | -2^7 —  2^7 - 1   |
| **short** | 2字节        | -2^15 —  2^15 - 1 |
| **int**   | 4字节        | -2^31 —  2^31 - 1 |
| **long**  | 8字节        | -2^63 —  2^63 - 1 |



> Java语言整型常量的四种表示形式：
>
> 1. 十进制整数：如：99、-500、0
> 2. 八进制整数：要求以 0 开头，如：014
> 3. 十六进制整数：要求以 0x 开头 或 0X 开头，如：0x14
> 4. 二进制整数：要求 0b 或 0B 开头，如：0b01110011

```java
public class TestInt {
    public static void main(String[] args) {

        int a = 100;    //十进制
        int b = 022;    //八进制
        int c = 0xff;    //十六进制
        int d = 0b10;    //二进制

        byte e = 50;
        short f = 300;

        long salary = 3000000000L;  //整型常量定义为long类型

        System.out.println(a);  //100
        System.out.println(b);  //18    输出自动转为十进制
        System.out.println(c);  //255   输出自动转为十进制
        System.out.println(d);  //2     输出自动转为十进制

        System.out.println(salary); //3000000000

        System.out.println(e);  //50
        System.out.println(f);  //300
    }
}

```



### 浮点型

**Floating Point Number**

一共有**两种类型**：

| 类型       | 占用空间 | 范围                            |
| ---------- | -------- | ------------------------------- |
| **float**  | 4字节    | -3.403**E**38 — 3.403**E**38    |
| **double** | 8字节    | -1.798**E**308 —  1.798**E**308 |

>1. float类型aka单精度类型 尾数可以精确到7位有效数字
>
>2. double类型aka双精度 **绝大部分应程序都采用double类型**
>3. Java浮点类型常量有两种表达形式： 1.十进制数形式 **3.14 、314.0、 0.314** 2.科学记数法形式 **3.14E0、 3.14E2、 3.14E-1**
>4. 浮点型不精确的 不建议用来作运算比较 若精度要求非常高用于商业计算**可使用BigDecimal进行运算比较**
>5. 浮点型常量默认是double 若改成float可以在后面加个F或f



### 字符型

​	**字符型在内存中占2个字节**，在Java中使用单引号来表示字符常量。例如'A'是一个字符，它与"A"是不同的，"A"表示含有**一个字符的字符串**。

​	**char类型**用来表示在**Unicode**编码表中的字符。Unicode编码被设计用来处理各种语言的文字，它占2个字节，可允许有65536个字符。

| 转义符 | 含义              | Unicode值 |
| ------ | ----------------- | --------- |
| \b     | 退格（backspace） | \u0008    |
| \n     | 换行              | \u000a    |
| \r     | 回车              | \u000d    |
| \t     | 制表符（tab）     | \u0009    |
| \ "    | 双引号            | \u0022    |
| \ '    | 单引号            | \u0027    |
| \\\    | 反斜杠            | \u005c    |

> **String类其实是字符序列（char sequence），本质是char字符组成的数组。**



```java
/**
 * char类型的使用
 * @author chan_honman 
 * @version 1.0
 */
public class TestChar {
    public static void main(String[] args) {
        char c1 = 'a';  //a
        char c2 = '中';  //中
        char c3 = '\u0061'; //a

        System.out.println(c1);
        System.out.println(c2);
        System.out.println(c3);

        String str = "My name is Chan_Honman!";
        System.out.println(str);

        char c5 = '\n';
        System.out.println("a\nb\nc\nd\ne\nf\ng");  //没输出一个字母就换一次行
    }
}

```



### 布尔型 boolean

1. boolean类型只有两个常量值 **true** 和 **false**。
2. **内存中占用一个字节或4个字节** 不可以使用0或非0的整数代替 ture 和 false。（与c语言不同）

```java
/**
 * @author chan_honman 
 * @version 1.0
 */

public class TestBoolean {
    public static void main(String[] args) {
        boolean b1 = true;
        boolean b2 = false;

        if (b1){
            System.out.println("b1是true！");
        }else{
            System.out.println("b1是false！");
        }
    }
}

```



## 运算符 operator

计算机的基本用途就是执行数学运算，Java提供了一套丰富的运算符来操作变量。



### 算数运算符

1. **＋, －, *, /, %** 属于二元运算符。**%**是取模运算符，就是我们常说的**求余数操作。**
2. 算数运算符中**++**（**自增**），**--**（**自减**）属于一元运算符。

```java
/**
 * @author chan_honman
 * @version 1.0
 */

public class TestOperator01 {
    public static void main(String[] args) {
        int a = 3;
        long b = 4;
        long c = a + b;

        double d = 3 + 3.14;
        int d2 = 32 / 3;    //两个整数相除 直接保留结果的整数部分 没有四舍五入
        System.out.println(d2); //输出10

        //取余数
        int e = 10 % 3;
        System.out.println(e);  //输出1

        //自增 自减
        int g = 30;
        g++;    //相当于 g = g + 1
        g--;    //相当于 g = g - 1

        g = 10;
        int h = g++;    //g++先赋值给h 后g自增
        System.out.println("这时候的g = " + g); //输出11
        g = 10;
        int i = ++g;    //++g先自增后 赋值给i

        System.out.println(h);  //输出10
        System.out.println(i);  //输出11
    }
}

```



### 二元运算符的运算规则

**整数运算**：

1. 如果两个操作数**有一个为long类型**，则**结果也为long类型。**
2. **没有long类型时**，结果为int类型。**就算操作数全为short、byte类型，结果也是int类型。**

**浮点运算**：

1. 如果两个操作数有**一个为double类型，则结果也是double类型。**
2. **只有两个操作数都是float类型**，则**结果才为float类型。**

**取模运算**：

其余作数可以为浮点数，一般使用整数，结果是”余数“，**”余数“符号和左边操作数相同**，如：7 % 3 = 1， -7 % 3 = -1， 7 % -1 = 1。



### 赋值及其扩展赋值运算符

| 运算符 | 用法举例 | 等效表达式 |
| ------ | -------- | ---------- |
| +=     | a += b   | a = a + b  |
| -=     | a -= b   | a = a - b  |
| *=     | a *= b   | a = a * b  |
| /=     | a /= b   | a = a / b  |
| %=     | a %= b   | a = a % b  |

```java
/**
 * @author chan_honman
 * @version 2.0
 */

public class TestOperator02 {
    public static void main(String[] args) {
        int a = 3;
        int b = 4;
        a += b;     //相当于 a = a + b
        System.out.println(a);  //输出7

        a = 3;
        a *= b + 3;   //相当于 a = a * (b + 3)
        System.out.println(a);  //输出21
    }
}

```



### 关系运算符

**关系运算符用来进行比较运算。关系运算的结果是布尔值：true 或者 false。**

| 运算符 | 含义       | 示例   |
| ------ | ---------- | ------ |
| ==     | 等于       | a == b |
| !=     | 不等于     | a != b |
| >      | 大于       | a > b  |
| <      | 小于       | a < b  |
| >=     | 大于或等于 | a >= b |
| <=     | 小于或等于 | a <= b |

:::tip

**注意事项**

1. **= 是赋值运算符 而真正的判断两个操作数是否相等的运算符是 ==。**
2. **== 、 != 、 是所有（基本和引用）数据类型都可以使用。**
3. **（> 、 >=、 <、 <=）仅针对数值类型（byte short int long float double char）。**

:::

```java
/**
 * @author chan_honman
 * @version 3.0
 */

public class TestOperator03 {
    public static void main(String[] args) {
        int a = 3;
        int b = 4;
        boolean c = a > b;
        System.out.println(c);  //输出false

        char d = 'h';
        //char值位于0-65536之间 可以通过（int）强转成数字
        System.out.println(d);  //输出h
        System.out.println((int) d);    //输出104 h对应的十进制数是104
        boolean e = d > 100;
        System.out.println(e);
    }
}

```



### 逻辑运算符

| 名称   | 符号     | 说明                        |
| ------ | -------- | --------------------------- |
| 与     | &        | 只要有一个为false 则为false |
| 短路与 | **&&**   | 只要有一个为false 则为false |
| 或     | \|       | 只要有一个为true 则为true   |
| 短路或 | **\|\|** | 只要有一个为true 则为true   |
| 非     | !        | 取反                        |
| 异或   | ^        | 相同为false 不同为true      |

:::tip

**短路与和短路或采用短路的方式。从左到右计算，如果通过运算左边的操作数就能够确定逻辑表达式的值，则不会继续计算运算符右边的操作数，提高效率。**

:::

```java
/**
 * @author chan_honman
 * @version 4.0
 */

public class TestOperator04 {
    public static void main(String[] args) {
        boolean b1 = true;
        boolean b2 = false;
        System.out.println(b1 & b2);    //与 有一个false 输出false
        System.out.println(b1 | b2);    //或 有一个true 输出true
        System.out.println(!b2);        //取反
        System.out.println(b1 ^ b2);    //异或 相同false 不同所以输出 true

        //短路与 短路或
        //int b3 = 3/0 会报错 不能除以0
        boolean b3 = 1 > 2 && (4 < 3 / 0);  //短路只要前面符合要求 后面就不会判断了
        System.out.println(b3); //输出false
    }
}

```



### 位运算符

**位运算指的是进行二进制的运算。**

| 位运算符 | 说明                              |
| -------- | --------------------------------- |
| **~**    | 取反                              |
| **&**    | 按位与                            |
| **\|**   | 按位或                            |
| **^**    | 按位异或                          |
| **<<**   | 左移运算符 左移动1位相当于乘2     |
| **>>**   | 右移运算符 右移动1位相当于除2取商 |

```java
/**
 * @author chan_honman
 * @version 4.0
 */

public class TestOperator04 {
    public static void main(String[] args) {
        int a = 7;  //0 1 1 1
        int b = 8;  //1 0 0 0
        System.out.println(a & b);    //按位或 0
        System.out.println(a | b);    //按位与 15
        System.out.println(a ^ b);    //按位异或 15
        System.out.println(~b);       //取反  -9

//      位移 乘以2 除以2 使用位移操作 最快！！！！
        int c = 5 << 2;   //5*2*2
        System.out.println(c);
        int d = 40 >> 3;    //40/8

    }
}

```

**乘除2 使用位移操作 最快！！！！**



### 字符串连接符

```java
/**
 * 测试字符串连接符的用法
 */

public class TestOperator05 {

    public static void main(String[] args) {
        String a = "3";
        int b = 4;
        System.out.println(a + b);  //34

//      条件是String 不是char 若是char 则仍然是加法
        char c1 = 'h';
        char c2 = 'i';
        System.out.println(c1 + c2);    //209
        System.out.println("" + c1 + c2);   //hi
    }
}

```



### 条件运算符

![](/images/Java/条件运算符.png)

```java
/**
 * 测试条件（三元）运算符的用法
 */

public class TestOperator06 {

    public static void main(String[] args) {
        int score = 90;
        String a = score < 60 ? "不及格" : "及格";
        System.out.println(a);  //及格

        if (score < 60) {
            a = "不及格";
        } else {
            a = "及格";
        }
        System.out.println(a);  //及格

        int x = -100;
        int flag = x > 0 ? 1 : (x == 0 ? 0 : 1);    //x是否大于0 不是的话执行冒号后的 判断x是否等于0 不是的话 执行冒号后面赋值
        System.out.println(flag);   //1

    }
}

```



## 运算符优先级问题

1. **逻辑与&& > 逻辑或|| > 逻辑非	a || b && c 的运行结果是 a || ( b && c )**
2. **括号运算符 > 算术运算符 > 关系运算符 > 位运算符 > 逻辑运算符**



## 数据类型的转换

**自动类型转换指的是容量小的数据类型可以自动转为容量大的数据类型 如下图所示：**

![](/images/Java/数据类型的转换.png)

> **红色线条表示转换无数据丢失 虚线表示在转换时可能会丢失精度**



## 数据强制转换

**强制转换类型 又称为造型（cast） 用于强制转换数值的类型 可能会损失精度**

语法格式如下：

（type）var



```java
/**
 * 测试类型强制转换
 */

public class TestTypeCast {

    public static void main(String[] args) {
        double a = 3.94152;
        int b = (int) a;
        System.out.println(b);  //3 浮点数强转为整数 直接丢失小数部分

        int c = 97;
        char d = (char) c;
        System.out.println(c);  //97

        //强制转换超过了表数范围会丢失精度（完全不同的值）
        byte e = (byte) 300;
        System.out.println(e);  //44
    }
}

```



## 基本类型转化时常见错误和问题

1. **操作比较大的数时 要留意是否溢出 尤其是整数操作时**
2. **L 和 l 的问题：（1）不要命名为 l 的变量 字母 l 容易和数字 1 混淆 （2）long类型使用大写L 不要用小写 l** 



## Scanner处理键盘输入

**Scanner让程序和用户通过键盘交互**

```java
import java.util.Scanner;

/**
 * 测试键盘输入：Scanner用法
 */

public class TestScanner {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入用户名：");
        String uname = sc.nextLine();
        System.out.println("你好，" + uname);
    }
}

```

请输入用户名：
Chan_Honman	**(键盘输入)**
你好，Chan_Honman

Process finished with exit code 0



## 控制语句

1. **顺序结构：先执行a，再执行b的逻辑**
2. **条件判断结构：如果。。。则。。。的逻辑**
3. **循环结构：如果。。。则重复执行。。。的逻辑**



## 条件判断结构（选择结构）

![](/images/Java/条件判断结构.png)



### if单分支结构



![](/images/Java/if单分支结构.png)

> 语法结构：
>
> ```java
> if(布尔表达式){
> 	语句块
> }
> ```
>
> 

> **【示例】掷色子🎲游戏** 
>
> Math类的使用
>
> Math.random()该方法用于产生 0 到 1 区间 double 类型的随机数，但是不包括1。
>
> ```java
> int i = (int) (6 * Math.random()); //产生【0,5】之间的随机数
> ```
>
> 

```java
/**
 * 写个掷色子游戏
 * 1.如果三次加起来一共大于15        不错
 * 2.如果三次加起来在 10-15 之间     一般
 * 3.如果三次加起来在 10-3之间       不好
 */

public class TestIf01 {

    public static void main(String[] args) {
        int i = (int) (Math.random() * 6) + 1;
        int j = (int) (Math.random() * 6) + 1;
        int k = (int) (Math.random() * 6) + 1;

        int count = i + j + k;

        if (count > 15) {
            System.out.println("运气不错！");
        }

        if (count < 10) {
            System.out.println("运气不好！");
        }

        if (10 <= count && count <= 15) {
            System.out.println("运气一般！");
        }

    }
}

```



### if-else双分支结构



![](/images/Java/ifelse双分支结构.png)



> **语法结构：**
>
> ```java
> if (布尔表达式) {
> 	语句块1
> } else {
> 	语句块2
> }
> ```
>
> 

**小练习：**

```java
/**
 * 测试if-else双分支结构
 */

public class TestIf02 {

    public static void main(String[] args) {
        double r = 4 * Math.random();
        double area = Math.PI * r * r;
        double circle = 2 * r * Math.PI;
        System.out.println("半径=" + r + " 面积=" + area + "， 周长=" + circle);
        if (area >= circle) {
            System.out.println("面积的数值大于周长");
        }else {
            System.out.println("面积的数值小于周长");
        }
    }
}

```



### If-elseif-else多分支结构

![](/images/Java/多分支结构.png)

>**语法结构**
>
>```java
>if (布尔表达式1) {
>    语句块1;
>	} else if (布尔表达式2) {
>    语句块2;
> 	}.....
>```
>
>

**小练习：**

```java
/**
 * 测试多分支结构
 */

public class TestIf03 {

    public static void main(String[] args) {
        int age = (int) (120 * Math.random());
        System.out.println("年龄是： " + age);

        //15以下儿童 15-24青年 25-44中年 45-64中老年 65-84老年 85-99老寿星
        //100-109百岁老人 110以上申请国家纪录
        if (age < 15) {
            System.out.println("儿童");
        } else if (age < 25) {
            System.out.println("青年");
        } else if (age < 45) {
            System.out.println("中年");
        } else if (age < 65) {
            System.out.println("中老年");
        } else if (age < 85) {
            System.out.println("老年");
        } else if (age < 100) {
            System.out.println("老寿星");
        } else if (age < 110) {

        } else {
            System.out.println("百岁老人");
        }
    }

}

```



## switch语句

1. **switch会根据表达式的值从相匹配的case标签处开始执行，一直执行到break处或者是switch的末尾。如果表达式的值与任一case值不匹配，则进入default语句。**
2. **switch中表达式的值是int（byte、short、char也可。但是long不行）、枚举、字符串。**

![](/images/Java/switch多分支结构.png)



**练习题：**

```java
public class TestSwitch01 {

    public static void main(String[] args) {
        int grade = (int) (Math.random() * 4) + 1;   //大学年级

        switch (grade) {
            case 1:
                System.out.println("大一新生");
                break;
            case 2:
                System.out.println("大二");
                break;
            case 3:
                System.out.println("大三");
                break;
            default:
                System.out.println("大四");
                break;
        }
    }
}

```



## 循环结构

**循环结构 分两大类，一类是当型，一类是直到型。**

* **当型：**

  **当布尔表达式条件位true时，反复执行某语句，当布尔表达式的值为false时才停止循环，比如while与for循环。**

* **直到型：**

  **先执行某语句，再判断布尔表达式，如果true再执行语句，如此反复，直到布尔表达式条件为false时才停止循环，比如do-while循环。**



### while循环♻️

![](/images/Java/while循环结构.png)

> **语法结构：**
>
> ```java
> while (布尔表达式)	{
> 		循环体;
> }
> ```
>
> 

练习题：

```java
public class TestWhile {

    public static void main(String[] args) {
        int a = 0;
        while (a < 3) {
            System.out.println("I love U! " + a);
            a++;
        }
    }
}

```



### for循环♻️

![](/images/Java/for循环结构.png)

> 语法结构：
>
> ```java
> for (初始表达式;布尔表达式;迭代因子) {
> 	循环体；
> }
> ```
>
> 

* 初始化部分设置：循环变量的初值
* 条件判断部分为：布尔表达式
* 迭代因子：控制循环变量的增减

**练习题：**

累加 0+1+2+3+4+...+100

```java
public class TestFor {

    public static void main(String[] args) {
        int sum = 0;
        for (int i = 0; i <= 100; i++) {
            sum += i;
        }
        System.out.println(sum);    //5050
    }
}

```

输出90-1之间能被3整除的数

```java
public class TestFor {

    public static void main(String[] args) {
        for (int i = 90; i >= 1; i--) {
            if (i % 3 == 0) {
                System.out.println(i + "\t");
            }
        }
    }
}

```



### do-while循环♻️

![](/images/Java/dowhile循环结构.png)

> 语法结构：
>
> ```java
> do{
> 	循环体;
> }while(布尔表达式);
> ```
>
> 

## 嵌套循环♻️

1⃣️执行结果如下所示：

```java
1 1 1 1 1
2 2 2 2 2
3 3 3 3 3
4 4 4 4 4
5 5 5 5 5
```

```java
public class TestLoop2 {

    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= 5; j++) {
                System.out.print(i + "\t");
            }
            System.out.println();
        }
    }
}

```

2⃣️输出9*9乘法口诀表:

```java
1 * 1 = 1	
1 * 2 = 2	2 * 2 = 4	
1 * 3 = 3	2 * 3 = 6	3 * 3 = 9	
1 * 4 = 4	2 * 4 = 8	3 * 4 = 12	4 * 4 = 16	
1 * 5 = 5	2 * 5 = 10	3 * 5 = 15	4 * 5 = 20	5 * 5 = 25	
1 * 6 = 6	2 * 6 = 12	3 * 6 = 18	4 * 6 = 24	5 * 6 = 30	6 * 6 = 36	
1 * 7 = 7	2 * 7 = 14	3 * 7 = 21	4 * 7 = 28	5 * 7 = 35	6 * 7 = 42	7 * 7 = 49	
1 * 8 = 8	2 * 8 = 16	3 * 8 = 24	4 * 8 = 32	5 * 8 = 40	6 * 8 = 48	7 * 8 = 56	8 * 8 = 64	
...
```

```java
public class TestLoop2 {

    public static void main(String[] args) {
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(j + " * " + i + " = " + i * j + "\t");
            }
            System.out.println();
        }
    }
}

```



## break语句和continue语句



* **break语句用于强行退出整个循环♻️**
* **continue语句用于结束本次循环，继续下一次循环**



![](/images/Java/break和continue.png)



> 练习题：
>
> ```java
> /**
>  * 测试breal语句
>  * 产生100以内的随机数 知道随机数为88 终止循环
>  */
> 
> public class TestBreak {
> 
>     public static void main(String[] args) {
>         int total = 0;
>         while (true) {
>             total++;
>             int i = (int) (Math.random() * 100);
>             System.out.println(i);
>             if (i == 88) {
>                 break;
>             }
>         }
>         System.out.println("循环次数：" + total);
>     }
> }
> 
> ```
>
> ```java
> /**
>  * 测试continue语句
>  * 把100-150之间不能被3整除的数输出，并且每行输出5个
>  */
> 
> public class TestContinue {
> 
>     public static void main(String[] args) {
>         int count = 0;
> 
>         for (int i = 100; i <= 150; i++) {
>             if (i % 3 == 0) {
>                 continue;
>             }
>             System.out.print(i + "\t");
>             count++;
>             if (count == 5) {
>                 System.out.println();
>                 count = 0;
>             }
>         }
>     }
> }
> 
> ```
>
> 



## 带标签的continue

“标签”是指后面跟一个冒号的标识符 例如 **label** 。 对Java来说唯一用到标签的地方是循环语句之前。

“**go to 有害**”论中，最多有问题的就是变迁，而非 **to go**。随着标签在一个程序里数量的增多，产生错误的机会也越来越多。但Java标签不会造成这方面的问题，因为它们的活动产所已被限制死，不可通过特别的方式到处传递程序的控制权。

```java
/**
 * 打印101-150之间的所有质数
 */

public class TestCountinue02 {

    public static void main(String[] args) {
        outer:
        for (int i = 101; i < 150; i++) {
            for (int j = 2; j < i / 2; j++) {
                if (i % j == 0) {
                    continue outer; //符合条件跳到外部循环继续
                }
            }
            System.out.print(i + " ");
        }
    }
}

```



## ❓年薪计算器程序

1. 通过键盘输入用户的月薪，每年是几个月薪水。
2. 输出用户的年薪。
3. 如果年薪超过10万则恭喜超过90%的国人，如果年薪超过20万则恭喜超过98%的国人。
4. 直到键盘输入数字88，则退出程序（使用break退出循环）。
5. 键盘输入66，则这个用户退出计算不显示恭喜...，直接显示“重新开始计算...”，然后计算下一个用户的年薪。

```java
import java.util.Scanner;

/**
 * 年薪计算器程序
 *
 * @author chan_honman
 * @version 1.0
 */

public class SalaryCalculator {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);


        outer:
        while (true) {

            System.out.println("请输入您的月薪：");
            int monthlySalary = sc.nextInt();
            if (monthlySalary == 88) {
                break;
            }

            System.out.println("请输入您每年是有几个月薪水：");
            int month = sc.nextInt();
            if (month == 66) {
                System.out.println("重新开始计算...\n");
                continue outer;
            }

            int annualSalary = monthlySalary * month;
            System.out.println("您的年薪为：" + annualSalary + "元");

            if (annualSalary > 200000) {
                System.out.println("恭喜您的年薪超过98%的国人！！！\n");
            } else if (annualSalary > 100000) {
                System.out.println("恭喜您的年薪超过90%的国人！！！\n");
            } else {
                System.out.println("继续加油争取年薪过10万吧！！！\n");
            }
        }


    }
}

```





















**updating..........**
