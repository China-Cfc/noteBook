# JavaSE

# 计算机基础

## 计算机硬件

- 一些物理装置按照系统结构的要求构成一个有机整体的为计算机软件运行提供物质基础

- 计算机硬件的组成：**CPU**、**主板**、**内存**、硬盘、电源、主机箱、显卡、键盘、鼠标、显示器等

- IO设备：input and output 输入输出设备

- 冯.诺依曼体系结构

<img src="D:\学习资料\Typora学习文件\tuxiang/冯诺依曼.png" alt="如图" style="zoom:60%;" />

---

## 计算机软件

- 计算机软件可以使计算机按照事先设定好的顺序实现特定的功能
- 计算机软件按照功能分为系统软件和应用软件
  - 系统软件:DOS(Disk Operating System),**Windows**,**Liunx**,Unix,Mac,Android,iOS
  - 应用软件:qq,微信,LOL等
- 软件,开发,软件开发(Intellij IDEA软件)
  - 人机交互(图形化界面,命令行)

---

  

## 计算机快捷键

- Shift+Del 永久删除
- Win+e 打开我的电脑
- Ctrl+Shif+Esc  打开任务管理器
  - 打开运行,输入mstsc 打开远程桌面

---

## Dos命令

**打开CMD的方式**

1. 开始+系统+命令提示符
2. Win+R 输入cmd
3. 在任意文件夹下面,按住shift+右键 选择在此处打开命令行窗口
4. 在资源管理器的地址栏前面加上cmd+空格

以管理员方式运行：右击

常用的DOS命令

```bash
#盘符切换 D:
#查看当前目录下的所有文件 dir
#切换目录 cd change direcory(目录)
#/d 跨盘切换   # cd.. 回到上一层目录
#清理屏幕 cls     (clear screen)
#退出 exit
#查看ip ipconfig
#也可以直接打开程序 calc 计算器 mspaint 画图 notepad 记事本
#ping 命令
#文件操作
md (make directory-目录)创建文件夹
cd >a.txt 创建文件
del a.txt  删除文件
rd (remove directory ) 移除删除目录
```

---

## 计算机语言发展史

- 二进制语言：不需要转换直接输入给计算机使用的
- 汇编语言：人能读懂的单词指令代替二进制 应用于：逆向工程，机器人，病毒等

- 高级语言

  - 面向过程:C
  - 面向对象:C++,Java
  - C++语言 :C的升级;C#(shapo);Python;PHP;JavaScript

  Java 2 标准版（J2SE）：占领桌面

  Java 2 移动版（J2ME）：占领手机

  Java 2 企业版（J2EE）：占领服务器

  **Java发展**

  - 构建工具：Ant，**Maven**，Jekins
  - 应用服务器：**Tomcat**，Jetty，Jboss，Webspher,weblogic
  - Web开发：Struts，**Spring**，Hibernate，myBatis
  - 开发工具：Eclipse，Netbean，intellij idea，Jbuilder

## java特性和优势

- 简单性
- 面向对象
- **可移植性**
- 高性能
- **分布式**
- **动态性**:反射机制
- **多线程**
- 安全性
- 健壮性

---

## Java 三大版本

- **JavaSE：标准版（桌面程序，控制台开发。。）**
- JavaME：嵌入式开发（手机，小家电。。）
- **JavaEE：E企业级开发（web开发，服务器开发）**：先学习标准版

---

## JDK,JRE,JVM

- JDK：Java Development Kit， Java开发者工具
- JRE：Java Runtime Environment，Java运行时环境
- JVM：Java Virtual Machine，Java虚拟机（跨平台核心）

![](../../tuxiang/JDK,JRE,JVM.png)



---

## Java开发环境搭建

**JDK（JDK7、8）**

**配置环境变量：**

- 系统变量：JAVA_HOME
- 系统变量：PATH中：新建 %JAVA_HOME%bin；新建 %JAVA_HOME%jre\bin

**文件作用**

bin：放一些可执行的程序

include：引入c语言的头文件

**jre：Java运行时环境**

**lib：Java类库文件**

src.zip：资源类文件，类资源



---

## hello world

1. 新建java文件

新建txt文件，命名hello.java，输入以下代码

```java
public class hello{//hello要和文件名称一样
    public static void main(String[] args){//String首字母要大写，下方System一样
        System.out.pring("hello world!")
    }
}
//punlic class 表示类；main 表示方法；String[] args 是一个参数；System.out.pring("hello world!")输出
```

2. 生成class文件

cmd进入dos窗口，找到 .java 文件在的目录，输入  javac hello.java

3. 执行class文件

cmd进入ods窗口，进入对应目录，输入 java hello  #不需要加  .class



### 注意

1. 单词大小写敏感
2. 使用英文，避免乱码
3. 文本使用""



---

### java程序运行机制

* 编译型：翻译，速度更快 -- 开发操作系统等
* 解释性：网页对于速度要求不高，

区别在于翻译的时机不同！

> java属于以上两种



## IDEA安装

### 1，什么是IDE

> Eclispe。。。IDEA 软件

就是集成开发环境，百度百科



```java
#在idea中创建文件的时候在source文件夹下创建，打开项目结构可以看到
# file --Project Structure
#    打开Project，调整jdk和语言 语言调整为8
```



---



# 基础知识

## 壹，注释、标识符、关键字

### 1，注释

* 单行注释

```java
//单行注释
```



* 多行注释

```java
/*
sdfsdfsdfsdfsdgdsg
sfefdfdgdfsgd
*/
public class demo{}
```



* 文档注释:在JavaDoc里讲解

```java
//文档注释 /**   */（可以识别其中的参数）
/**
*@Author 春风吹
*/
```



---

---

示例：

```java
public class demo{
    public static void main(String[] args){
        System.out.println("Hello World!");
    }
}
```

> psvm快捷键是 public static void main（）
>
> sout 快捷键是 System.out.println();

### 2，标识符

<!--上面的输入代码中，在IDEA中sout快捷键是``System.out.println()``，这个就是一个打印输入的语句 `println`代表的是打印并换行,`print`代表的是打印不换行,`printf`继承了C语言的的一些特性,能够格式化输出​-->

<img src="../../tuxiang/Java关键字.png" style="zoom:60%;" />

**关键字:系统定义好的**

*==Java所有的组成部分都需要名字。类名、变量名和方法名都被称为标识符==*

标识符命名注意点：

* **所有的标识符都应该以大小写字母、`$`或者下划线`_`为开头命名**
* 首字符之后可以是字母，‘$’，‘_’ 或数字的任意字符组合,不包括其他特殊符号
* **==不能使用系统的关键字作为变量名和方法名包括类名==**
* 标识符是大小写敏感的，所以`A`和`a`是两个不同的变量
* ~~可以使用中文命名，不推荐使用~~

```java
public class demo1/*类名使用class就会报错*/{
    public static void main(String[] args){
        String name = "qq";//变量名可以为 Name,$name,_name   //不能为特殊符号开头，数字开头以及定义的关键字作为名字       
        System.out.println(name);
    }
}
```

---

---

---



## 贰，**数据类型**

 **1，数据类型分为：**

* 强类型语言

  * **要求变量的使用要严格符合规定，所有的变量要在定义之后才能使用**

    <!--因为严格所以安全，因为安全所以速度慢-->

* 弱类型语言：Javascript等

**2，Java的数据类型分为两大类**

* **基本类型（primitive type）**

![基本类型](../../tuxiang/基础数据类型（Primitive Type）.png)

```java
public class demo1{
    public static void main(Sting[] args){
        //整数类型
        byte num1 = 12;
        short num2 = 12;
        int num3 = 12;
        long num4 = 12L;//会在后面加 L/l 进行标识 l容易和数字 1 混淆 使用L
        //浮点数
        float fnum1 = 0.23F;//float 类型在后面加上 F/f
        double fnum2 = 3.1415926;//可以在后面加上 D/d
        //字符
        char name = 'A';//char name = 'AA'会报错，只能由一个字符组成
        //String,字符串不是关键字，他是一个类
        //String name1 = '山东';
        //布尔类型：是非
        boolean flag = true;//false
    }
}
```

**==注意的是byte类型范围只有 -128-127；short类型只有 -32768-32767；int类型正负接近二十一亿多**

---



* **引用类型（reference type）**

引用类型分为：（除了基础类型都是引用类型）

​	类、接口、数组

---

***扩展***

<!--数字十进制和二进制转换：-->

```java
//1101.01 相当于2的3次方加2的2次方加0×2的1次方加0×2的-1次方加2的-2次方
//十进制转二进制 不断地除以2先后的余数就是二进制
```



**什么是字节**

* 位 bit ：是计算机内部数据存储的最小单位，11001100 是一个八位二进制数。一个1/0就是一位
* 字节 byte ：是计算机中数据处理的基本单位，习惯上用大写B来表示，1B（byte，字节）= 8bit（位） 
* 字符：是指计算机中使用的字母、数字、字和符号



**扩展**

*整数扩展*

二进制数字以`0b`开头，八进制数字以`0`,十六进制以`0x`

```java
public class demo1 {
    public static void main(String[] args) {
        int i = 0b10;//二进制
        int i1 = 010;//八进制
        int i2 = 0x10;//十六进制
        System.out.println(i);
        System.out.println(i1);
        System.out.println(i2);
    }
}
```

---

*浮点数拓展* 

`float`类型和`double`类型

```java
public class demo1 {
    public static void main(String[] args) {
        float i = 0.1f;
        double d = 0.1d;
        float i1 = i+1;
        System.out.println(i==d);//false 在底层存储的时候，不同类型的数据存储的位置不一样，当比较的时候是比较的两个变量之间的存储位置，float和double存储的位置不同，所以false
        System.out.println(i==i1);//true float位数有限，有舍入误差，是一个大约数，接近但不相等
        System.out.println(d);

    }
}
```

**==重点：最好完全避免使用浮点数进行比较==**

 <!--银行业务怎样表示？使用BigDecimal 数学工具类-->

---

*字符拓展*

```java
public class demo1 {
    public static void main(String[] args){
        char c1 = 'a';
        char c2 = '中';
        System.out.println((int)c1);//强制转换
        //所有的字符本质都是数字（所有的字符在内存里存储的方式都是数字--待定）
        //涉及编码问题，Unicode 占两个字节 表示65536字符 2的16次方
        //如何表示：U0000-UFFFF
        char c3 = '\u0061';
        System.out.println(c3);//a
    }
}
```

```java
public class demo {
    public static void main(String[] args) {
        String a = new String("hello world");
        String b = new String("hello world");
        System.out.println(a == b);//false!
    }
}
```





---

*转义字符*

`\t`代表的是制表符；

`\n`代表的是换行  等

## 弎，类型转换

**由于java是强类型语言，所以进行运算的时候，会用到类型转换**

```java
低------------------------------------> 高
byte,short,char->int->long->float->double  //根据容量字节大小排，小数的优先级大于整数
```

*运算中，不同类型的数据需要转换成同一种类型才能运算*

**强制类型转换**：从高到低转换需要强制转换，例如：`int i=12;byte b=(byte)i`

**自动类型转换**：从低到高转换会自动转换，例如：`int i=12;double d=i`

```java
public class demo {
    public static void main(String[] args) {
        int i = 130;
        byte b = (byte) i;//byte的字节范围为 -128 -- 127 超过了这个范围叫做内存溢出
        System.out.println(i);//130
        System.out.println(b);//-126
        //强制转换 从高到低 ； 自动转换 从低到高
        System.out.println("========================================");
        double d = i;//自动转换
        System.out.println(d);
        /*注意点
        * 1，不能对布尔类型进行转换
        * 2，不能将对象类型转换成不相干的类型
        * 3，在把高容量转换为低容量的时候，需要强制转换，可能会出现内存溢出情况
        * 4，在对小数进行准换的时候会出现，精度问题，如下
        * */
        System.out.println("=================================");
        System.out.println((int)23.1);//23
        System.out.println((int)23.9);//23
        System.out.println((int)-23.1);//23
        System.out.println((int)-23.9);//23  小数点后直接消失，不进行四舍五入

        System.out.println("=================================");
        char c = 'a';
        int ic = c+1;
        System.out.println(ic);//98  unicode码
        System.out.println((char)ic);//b
    }
}

```

**常见的问题**

```java
public class demo {
    public static void main(String[] args) {
        //操作比较大的数字的时候，注意内存溢出问题
        //java7 数字之间可以使用下划线分割  100_000
        int i = 1_0_0000_0000;
        int year = 20;
        int total = i*year;
        System.out.println(total);//-1474836480 结果为200亿 超过int的字节范围21亿多 ，内存溢出
        long l = i*year;
        System.out.println(l);//-1474836480  依然溢出，原因在于，先运算后转换，运算时出现错误，所以仍然溢出
        //将其中一个转换为高容量即可
        long l1 = (long)i *year;
        System.out.println(l1);//20000000000
        //long i = 10000L;后面L进行使用大写L，小写l可以实现用，可能会错认为1

    }
}
```



## 肆，变量、常量

### 变量

<!--通过变量可以操作内存中的数据，声明变量会在内存中开放一个空间，变量指的就是这个空间，赋予的值就是存放于这个空间内，不是放空间，变量的地址不会改变-->

#### 变量名，变量类型

* 定义：可以变换的量（就像是一元二次方程中的x和y）
* Java是种强类型语言，每个变量必须声明类型
* 变量是程序中最基本的存储单元，他的要素包括变量名，变量类型和作用域

```java
type varName [=value] [{,varName[=value]}]
//数据类型 变量名 = 值；可以使用逗号隔开来声明多个相同类型的变量
```



* 注意事项
  * 每个变量都有类型，类型可以是基本类型，也可以是引用类型
  * 变量名必须是合法的标识符（标识符命名规则）
  * 变量声明必须是一个完整的语句，因此每个声明都必须使用`;`分号结束



```java
public class demo {
    public static void main(String[] args) {
        char a='c',c='a';
        int i = 1;
        double d = 3.14d;
        String s = "Java";//''代表字符，""代表字符串
    }
}
```

### 变量的作用域

* 类变量：写在类里面的变量，需要关键字static（静态）
* 实例变量：写在类中变量，没有static
* 局部变量：写在方法中的变量

示例：

```java
public class Demo1 {
    static int salaries; //类变量：通过static形成静态，隶属于类
    String str = "Java";//实例变量
    public static void main(String[] args) {
        int i = 0;//局部变量        
    }
}
```

---

```java
public class Demo1 {//类中有 属性：变量，方法

    //实例对象：从属于对象即类对象;如果不初始化，输出类型的默认值 数字型输入0/0.00，char输出 空格；除了基本类型都输出为null
    //布尔类型的默认值为false
    String name;
    char ch;
    int age;//使用麻烦

    //类变量 static 可以直接在方法中调用,从属于类，随着类出现而出现，消失而消失
    static double salaries = 2500d;

    //main方法，主程序方法
    public static void main(String[] args) {
        //写在方法中的是局部变量，必须声明和初始化值
        //int i;会报错需要初始化值-赋值

        //在方法中使用实例对象  变量类型 变量类型 = new Demo1();
        Demo1 demo1 = new Demo1();
        System.out.println(demo1.age);//0
        System.out.println(demo1.name);//null
        System.out.println(demo1.ch);//空格
        System.out.println("===========类变量==================");
        System.out.println(salaries);
    }
    //其他方法
    public void add(){
    }
}
```

### 常量

* 常量（constant）：初始化（initialize）后不能改变值！不会变动的值；

* 常量可以理解为一种特殊的变量，他的值设定好后，在程序运行过程中无法改变

  ```java
  final  类型 常量名 = 值;//finaly
  final double PI = 3.14d;
  ```

  

* 常量名一般使用全部大写字符（规范）

---

### 变量的命名规范

* 所有变量、方法、类名：简单明了
* 类成员变量：首字母小写和驼峰原则：monthSalary
* 局部变量：首字母小写和驼峰原则
* 常量：大写字母和下划线：MAX_VALUE
* 类名：首字母大写和驼峰原则：Man_Value
* 方法名：首字母小写和驼峰原则：run(),runRun()



## 伍， 运算符

### 优先级

()  > 一元运算符 > 二元运算符 > 三元运算符

二元运算符：乘除大于加减



---



```java
public class Demo1 {//定义方法来获取变量的类型
    public static void main(String[] args) {
        short a = 1;
        byte b =2;
        System.out.println(getType(a+b));//int
        System.out.println(getType(a));//short
        System.out.println(getType(b));//byte
    }
    public  static String getType(Object obj){
        return obj.getClass().getName();
    }
}
```

---

* Java支持以下运算符：

  * 算数运算符：+，-，*，/，%，++，--

    **算数运算符操作数必须为数值类型。分为一元运算符（只有一个操作数）和二元运算符（有两个操作数，运算符在两个数之间）**

    * 一元运算符：+（正），-（负），++（自加），--（自减）

    

  * 赋值运算符：=

  * 关系运算符：>,<,>=,<=,==,!=,instanceof

  * 逻辑运算符：&&，||，！（与，或，非）

  * 位运算符：&，|，^, ~, >>, <<, >>>（二进制）

  * 条件运算符：  ？，：（偷懒）

  * 扩展赋值运算符：+=，-=，*=，/=（赋值时使用`a+=1`等同于`a=a+1`）

---

### 算数运算符

```java
package operator;//算数运算符

public class Demo1 {
    public static void main(String[] args) {
        int a = 5;
        int b,c,d,e,f,g;
        b = +a;
        System.out.println(b);
        c = -a;
        System.out.println(c);
        d = ++a;//先 a=a+1；再d = a
        System.out.println(d);
        int h = 5;
        e = h++;//先e=h，再h=h+1
        int ee = h;
        System.out.println(e);
        System.out.println(ee);
        int j =5;
        f = --j;//先 j=j-1,再f=j
        System.out.println(f);
        int k = 5;
        g = k--;//先 g=k,再k=k+1
        int gg = k;
        System.out.println(g);
        System.out.println(gg);

    }
}
```

```java
package operator;//%

public class Demo1 {
    public static void main(String[] args) {
        int a = 10;
        int c = 3;
        System.out.println(a%c);//1
    }
}
```



```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        long a = 12121212313113L;
        int b = 123;
        short c = 10;
        byte d = 8;
        //当操作数中有double类型结果为double，有long类型，结果为long，其余的结果为int类型
        System.out.println(a+b+c+d);//long
        System.out.println(b+c+d);//int
        System.out.println(c+d);//int
    }
}
```



### 关系运算符

```java
package operator;//关系运算符

public class Demo1 {
    public static void main(String[] args) {
        //关系运算符返回的结果只有：false和true 布尔类型
        int a = 10;
        int b = 20;
        System.out.println(a==b);
        System.out.println(a>b);
        System.out.println(a<b);
        System.out.println(a!=b);
        }
}
```

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        //幂运算 使用Math工具类实现各种数学运算
        double d = Math.pow(3, 2);
        System.out.println(d);
    }
}
```



### 逻辑运算符

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        //逻辑运算符，常与判断相结合 &&与，||或，! 非
        int a = 1;
        int b = 2;
        int c = 1;
        System.out.println(a==b&&a==c);//false 其中a==b为false，a==c为true，由此得出 && 中一方判断为false，结果便为false
        System.out.println(a==b||a==c);//true  可以得出 || 中其中一方为true便为true
        System.out.println(!(a==b));//true 取了相反判断
        System.out.println(!(a==c));//false 同理
        //以上可以综合理解为 &&：和 a和b都是true便是true  ||：或者 a或者b为true便是true  ！：非 ()里面的说对我就说不对，说错我就说对 杠精！！！
        //以上逻辑运算中有一种叫做短路运算，即没有执行完全部代码就得到了答案
        int d =5;
        boolean e = (d<1)&&(d++>0);
        System.out.println(e);//false
        System.out.println(d);// 5  由此得出d++没有运行，
    }
}

```

### 位运算符

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        /*位运算符 & 两者对应的位上都是1结果为1，否侧为0
        | 两者对应的位上都是0结果为0，否则为1
        ^ 两者对应的位上数字相同为0，否则为1
        ~ 取反值,Java中正负数为相反值，负数的二进制为整数的二进制反值低位加1 即  1 = 0001 ; -1 = 1111 1111 1111 1111 1111 1111 1111 1111
        >>：二进制的位整体右移动 /2  效率最高
        <<: 二进制的位整体左移动 *2
        >>>:忽略正负号向右移动 结果输出为正码：正数
        a =  0011 1100
        b =  0000 1101
        ------------------------------------
        a&b= 0000 1100
        a|b= 0011 1101
        a^b= 0011 0001
        ~b = 1111 0010
        例题：2*8如何最快速度运算 2*8 = 2*2*2*2
        
        0000 0000 0
        0000 0001 1  1*2^0           1
        0000 0010 2  1*2^1           2
        0000 0011 3  1*2^1+1*2^0     2+1
        0000 0100 4  1*2^2           2*2
        0000 1000 8  1*2^3           2*2*2
        0001 0000 16 1*2^4           2*2*2*2
        以上得出 << 左移一位代表 十进制数字*2
        >> 右移一位代表 十进制数字/2
         */
        System.out.println(30>>2);
        System.out.println(-30>>2);
        System.out.println(-1>>>1);
    }
}

```





### 条件运算符

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        //条件运算符 x ？y ：z
        //如果x == true 就输出y，否侧输出z
        int a = 70;
        System.out.println(a<60?"不及格":"及格");
    }
}

```





### 扩展赋值运算符

```java
a +=b  就是 a = a+b
```

### 字符串拼接符号 +

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        //字符串拼接 +
        //从左右运算，遇到String类型会进行字符串的拼接，字符串之后的运算不进行直接拼接，字符串之前的运算可以进行
        int a = 10;
        int b = 20;
        int c = 30;
        System.out.println(a+b);
        System.out.println(""+a+b);
        System.out.println(a+b+"");
        System.out.println(a+b+""+c);
    }
}package operator;

public class Demo1 {
    public static void main(String[] args) {
        //条件运算符 x ? y : z
        //如果 x == ture 输出y，否则输出z
        int a = 20;
        String type = a<60?"No":"Yes";
        System.out.println(type);
        //if中经常使用，与sql中的case when类似
    }
}
```



## 陆，包机制、JavaDoc

### 包机制

* 为了更好的组织类，Java提供了包机制，用于区别类名的命名空间

* 包语法格式为：

  `package pkg1[.pkg2[.pkg3....]]`

* 一般使用公司域名倒置作为包名`com.baidu.www`

* 为了使用某一个包的成员，我们需要在Java程序中明确导入包。使用import：

  `import pkg1[.pkg2...].(classname|*)`

```java
package operator;

import com.company.Main;
import com.company.*;
//当包中的类太多了，不想一个一个导入的时候使用 *
public class Demo1 {
    public static void main(String[] args) {
        
    }
}
//查看阿里巴巴开发手册
```

---

### JavaDoc

* javadoc命令是用来生成自己API文档的

* 参数信息：

  * @author 作者名
  * @version 版本号
  * @since 指明需要最早使用的jdk版本
  * @param 参数名
  * @return 返回值情况
  * @throws 异常抛出情况

  [jdk8的API官网文档](https://docs.oracle.com/javase/8/docs/api/)

```java
package operator;

/**在这里添加参数
 * @author 阿常
 * @version 1.0
 * @since 1.8
 */
public class Demo1 {    
    String name;    
    int num = 100;//只有在属性和方法之间加/** 回车才会自动弹出

    /**
     * @param name
     * @return
     * @throws Exception
     */
    public String test(String name)throws Exception {
        return name+num;

    }
}
```

**生成API文档**

1，进入所写的类文件所在的目录，打开cmd；

2，使用javadoc 参数 类文件名  方式生成API文档；

![生成API文档](D:\学习资料\Typora学习文件\tuxiang\API.png)

其中 `-encoding UTF-8 -charser UTF-8`是编码为UFT-8,字符集也变为UTF-8;

3，在原本的类文件所在的目录下会生成很多HTML的文件，可以打开index.html文件查看

---



第二种：

在IDEA中打开文件所在的终端，执行以上代码





## 柒，类变量，实例变量补充

### [java中的类变量和实例变量](https://www.cnblogs.com/ghlz/p/13535397.html)

### java中的变量分为

1.局部变量；
2.成员变量: 分为**a.类变量, b.实例变量**。



**1.局部变量：**

- 局部变量声明在方法、构造方法或者语句块中；

- 局部变量在方法、构造方法、或者语句块被执行的时候创建，当它们执行完成后，变量将会被销毁；

- 访问修饰符不能用于局部变量；

- 局部变量只在声明它的方法、构造方法或者语句块中可见；

- 局部变量是在栈上分配的。

- 局部变量没有默认值，所以局部变量被声明后，必须经过初始化，才可以使用。

  

**2.成员变量**
成员变量是定义在类中，方法体之外的变量。这种变量在创建对象的时候实例化。成员变量可以被类中方法、构造方法和特定类的语句块访问。

**a.类变量:**

- 类变量也称为静态变量，在类中以 static 关键字声明，但必须在方法之外。
- 无论一个类创建了多少个对象，类只拥有类变量的一份拷贝。
- 静态变量除了被声明为常量外很少使用。常量是指声明为public/private，final和static类型的变量。常量初始化后不可改变。
- 静态变量储存在静态存储区。经常被声明为常量，很少单独使用static声明变量。
- 静态变量在第一次被访问时创建，在程序结束时销毁。
- 与实例变量具有相似的可见性。但为了对类的使用者可见，大多数静态变量声明为public类型。
- 默认值和实例变量相似。数值型变量默认值是0，布尔型默认值是false，引用类型默认值是null。变量的值可以在声明的时候指定，也可以在构造方法中指定。此外，静态变量还可以在静态语句块中初始化。
- 静态变量可以通过：ClassName.VariableName的方式访问。
- 类变量被声明为public static final类型时，类变量名称一般建议使用大写字母。如果静态变量不是public和final类型，其命名方式与实例变量以及局部变量的命名方式一致。

**b.实例变量：**

- 实例变量声明在一个类中，但在方法、构造方法和语句块之外；
- 当一个对象被实例化之后，每个实例变量的值就跟着确定；
- 实例变量在对象创建的时候创建，在对象被销毁的时候销毁；
- 实例变量的值应该至少被一个方法、构造方法或者语句块引用，使得外部能够通过这些方式获取实例变量信息；
- 实例变量可以声明在使用前或者使用后；
- 访问修饰符可以修饰实例变量；
- 实例变量对于类中的方法、构造方法或者语句块是可见的。一般情况下应该把实例变量设为私有。通过使用访问修饰符可以使实例变量对子类可见；
- 实例变量具有默认值。数值型变量的默认值是0，布尔型变量的默认值是false，引用类型变量的默认值是null。变量的值可以在声明时指定，也可以在构造方法中指定；
- 实例变量可以直接通过变量名访问。但在静态方法以及其他类中，就应该使用完全限定名：ObejectReference.VariableName。



---



# 流程控制

## 壹，用户交互Scanner对象

### 1.1 Scanner对象

* Java提供的工具类，获取输入的内容，java.util.Scanner

* 基本语法：

  `Scanner s = new Scanner(System.in);`

* 通过Scanner类的`next()`与`nextLine()`方法获取输入的字符串,在读取前我们一般需要,使用`hasNext()`和`hasNextLine()`来判断是否有输入的数据

* 凡是属于IO流的类，如果不主动关闭，他不会自动关闭，一直占用资源



### 1.2 next()

* 一定要读取到有效字符后才可以结束输入
* 对输入有效字符之前遇到的空白,`next()`方法会自动将其去掉,省掉开头的空白
* 只有输入有效字符后才将后面输入的空白作为分隔符或者结束符,然后结束输入
* `next()`不能得到带有空格的字符串

### 1.3 nextLine()

* 以Enter为结束符,也就是说`nextLine()`方法返回的是输入回车之前的所有字符
* 可以获得空白

---

![next](../../tuxiang/image-20220318001703787.png)

```java
package operator;

import java.util.Scanner;

public class Demo1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String str = scanner.next();
        System.out.println(str);
        scanner.close;
    }
}
```

---

![nextLine](../../tuxiang/image-20220318001936787.png)

```java
package operator;

import java.util.Scanner;

public class Demo1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String str = scanner.nextLine();
        System.out.println(str);
        scanner.close;
    }
}

```

### 1.4 与`if`结构使用

```java
package operator;

import java.util.Scanner;

public class Demo1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int i =0;
        float f = 0.0f;
        //判断输入的是否为整数
        System.out.println("请输入整数：");
        if (scanner.hasNextInt()){
            i = scanner.nextInt();
            System.out.println(i);
        }
        else {
            System.out.println("非整数！");
        }
        //判断输入的是否为小数
        System.out.println("请输入小数：");
        if (scanner.hasNextFloat()){
            f = scanner.nextFloat();
            System.out.println(f);
        }else {
            System.out.println("非小数！");
        }
        scanner.close();
    }
}
```



* 使用ctrl点击Scanner进入类的源码中可以查看很多；
  * 也可以点击左下边框的结构选项查看本类的结构

```java
package operator;

import java.util.Scanner;
//输入多个数字，求其和和平均数，输入非数字结束，输出结果
//分析：多个数字需要定义几个数字的变量；和 的变量；平均数 = 和 / 数量
public class Demo1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double sum = 0d;
        int count = 0;
        System.out.println("输入第"+(count+1)+"个数字");
        while (scanner.hasNextDouble()){

            double d = scanner.nextDouble();
            count +=1;
            sum += d;
            System.out.println("已有"+count+"个数字");
            System.out.println("和为"+sum+"\n平均数为"+(sum/count));
        }
        System.out.println("共"+count+"个数字"+"\n总和为"+sum+"\n总平均数为"+(sum/count));
        scanner.close();
    }
}

```



---

## 贰，顺序结构

* Java的基础结构就是顺序结构，除非特别指明，否则就按照顺序一句一句执行。

* 顺序结构是最简单的算法结构

  ![122](../../tuxiang/image-20220320002744360.png)

  * 语句和语句之间，框和框之间是按从上到下的顺序进行的，它是由若干个依次执行的处理步骤组成的，它是任何一个算法都离不开的一种基础算法结构

## 弎，选择结构 struct

<!--if中的布尔表达式中可以使用逻辑运算符：&&，||，！-->

* str.equals("str") 它是判断String类型str中的字符串是不是str，是返回true

### 3.1 if单选择结构

```java
if(布尔表达式){
    //布尔表达式为true时执行的代码
}
```

```java
package operator;

import java.util.Scanner;

public class Demo1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入字符串：");
        String s = scanner.nextLine();
        if(s.equals("Hello")){
            System.out.println(s);
        }
        scanner.close();
    }
}

```



### 3.2 if双选择结构

```java
if(布尔表达式){
    //布尔表达式为true时执行的代码
}
else{//条件不满足的时候
    //除了以上的结果其他的情况下执行的代码
}
```



### 3.3 if多选择结构

```java
if(条件1){
    //条件满足时执行代码
}
else if(条件2){
    //条件1不满足，但满足条件2执行代码
}
else if(条件3){
}
else{
    //以上情况都不满足时执行
}
```

java if结构 执行顺序时从上往下

### 3.4 嵌套的if结构

```java
if(条件1){//满足条件1进入以下代码
    if(条件2){//代码为if判断,如果满足1又满足2进入第二层判断里并执行代码
        if(条件3){//满足1满足2又满足3进入执行代码            
        }
        else{}
    }
    else{}
}
else{}
```



### **3.5 switch**多选择结构

* 多选择结构另一种实现方式`switch case`语句

* switch case 语句判断一个变量与一系列值中的某个值是否相等，每个值称为一个分支（相当于sql种的decode函数（java种没有函数定义，都是方法））

  ```java
          switch (expression){
              case value:
                  //语句
                  break;//可选  当break不存在的时候，会执行下面所有的代码，知道遇到break或者全部执行完
              case value:
                  //语句
                  break;//可选
              //你可以有任意数量的case语句
              default://可选
                  //语句
          }
  ```

  > 上面的情况叫做case贯穿；
  >
  > **IDEA可实现java的反编译**

* switch 语句中变量类型：

  * byte、short、int或者char **不支持float、double、long 类型**
  * Java SE7 开始，支持字符串String类型。同事case标签必须为字符串常量或字面量

## 肆，循环结构

### 4.1 while循环

**基本结构：**

```java
while(布尔表达式){
    //执行代码
}
```

**0.0注意点：**

- 只要是布尔表达式为true，循环就一直进行
- 大多是情况是有结束循环的方式
- 少部分需要一直进行，如服务器的请求响应监听等；
- 避免死循环，影响性能或程序崩溃。

### 4.2 do...while 循环

- 对于while语句而言，如果不满足条件，则不能进入循环，有时候我们需要不满足条件，也至少执行一次。
- `do...while`循环和`while`循环相似,不同的是,`do...while`循环至少会执行一次

```java
do {
    //代码语句
}while (布尔表达式)
```

- `while`和`do...while`的区别
  - `while`先判断后执行,`do...while`先执行后判断
  - `do...while`总是保证循环体会被至少执行一次!

### 4.3 for 循环

> Java5中引入了一种主要用于数组的增强型`for`循环

* 语法格式:

  ```java
  for(初始化;布尔表达式;更新){
      //代码
  }
  ```

* for循环语句是支持迭代的一种通用结构,是最有效,最灵活的循环结构.

练习:

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        //计算0到100的奇数和偶数和
        int oddSum = 0;//奇数和
        int evenSum = 0;//偶数和
        for (int i = 0; i <= 100; i++) {//100.for
            if (i%2!=0){//使用不等于效率更高
                oddSum += i;
            }else {
                evenSum += i;
            }
        }
        System.out.println("奇数和为："+oddSum+"\n偶数和为："+evenSum+"\n=============================");
        //用while和for输出1-1000之间被5整除的数，每行输入三个
        //while
        int i = 0;
        int num1 = 0;
        int num2 = 0;
        int num3 = 0;
        while (i<=1000){
            if (i%5!=0){
            }else{
                System.out.print(i+"\t");
            }
            if (i%(3*5)!=0){
            }else{
                System.out.println("");
            }
            i++;
        }
        System.out.println("\n=======================================");
        //for
        for (int r = 0; r <= 1000; r++) {
            if (r%5==0){
                System.out.print(r+"\t");
                if (r%15==0){
                    System.out.println("");
                }
            }
        }
        System.out.println("=====================================================================");
        //打印九九乘法表
        int sum = 0;
        for (int x = 1; x <= 9; x++) {
            for (int y = 1; y <= x; y++) {
                System.out.print(y+"*"+x+"="+x*y+"\t");
            }
            System.out.println();
        }
    }
}
```

### 4.4 增强for循环

<!--Java5引入的一种主要用于数组或集合的增强性for循环-->

**语法:**

```java
for(声明语句:表达式){
    //代码
}
```

- <u>声明语句:</u>声明新的局部变量,该变量的类型要和数组元素的类型匹配.作用域仅限于循环块中,他的值和此时数组元素的值相等
- <u>表达式:</u>表达式是要访问的数组名,或者是返回值为数组的方法

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        int [] numbers = {1,2,3,4,5};//定义一个数组
        System.out.println(numbers[0]);//numbers[0]代表取数组中的索引为0的元素，相当于python中的列表
        System.out.println("=================");
        for (int i = 0; i < 5; i++) {
            System.out.println(numbers[i]);
        }
        System.out.println("==========================");
        //增强for
        for (int i : numbers){
            System.out.println(i);
        }
    }
}
```





## 伍，break & continue

### 5.1 `break`和`continue`

**break**:在任何循环语句中的主体部分,都能用`break`强行退出循环.在`swith`语句中也用到

**continue:**在循环语句块中,用于终端某次循环,跳过这个循环块此次执行的语句,进行下一次判断是否执行循环;

> 就是break中断这个循环块,循环不在进行;  遇到break时,我不干了!!!
>
> continue是跳过循环块中的某次循环,此次循环不进行,会进入到下一次循环;  当遇到continue时，老子不喜欢这个不干，干下一个

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        for (int i = 0; i < 10; i++) {
            System.out.print(i);//正常循环
        }//0123456789  
        System.out.println("=============break============");
        for (int i = 0; i < 10; i++) {
            if (i==5){
                break;
            }
            System.out.print(i);//break
        }//01234   缺少5以后的数字,等于5时中断了循环,循环不在进行
        System.out.println("============continue=============");
        for (int i = 0; i < 10; i++) {
            if (i==5){
                continue;
            }
            System.out.print(i);
        }//012346789   缺少了数字5,当i=5 时,不执行System.out.print(i);,进入到了下一个循环 i=6;
    }
}
```

### 5.2 `goto`关键字

- `goto`关键字很早在程序设计语言中出现，尽管他是Java的保留字，未得到正式使用；Java没有`goto`，在`break`和`continue`还有影子---带标签的
- “标签”是指后面跟一个冒号：`label:`
- 对于Java来说唯一用的标签的是在循环语句之前，设立标签的理由：希望在循环体中嵌套循环体，由于`break`和`continue`，只能中断当前循环，如果随标签使用，他们可以终端到存在标签的位置

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        //求101-150之间的质数
        //质数：指在大于1的自然数中，除了1和本身不存在其他因数的自然数叫做质数，例如：7；7只能除了1或者7才能整除
        prime:for (int i =101;i<=150;i++){
            for (int x =2;x<=i/2;x++){//能够整除的自然数只能在1- x/2之间
                if (i%x==0){
                    continue prime;//没有标签的话，只能跳转到第二个循环体，无法跳转到第一个循环体
                }
            }
            System.out.print(i+" ");
        }
    }
}
```





## 陆，练习

```java
package operator;

public class Demo1 {
    public static void main(String[] args) {
        //使用 * 答应一个等边三角形
        //思路：等边三角形由两个直角三角形构成，在画面上的 - 是由两个倒直角三角形构成；
        //可分为左右半边，一个半边是由两部分组成的，在程序中 后方的 - 为空即可
        /*
        -----*-----
        ----***----
        ---*****---
        --*******--
        -*********-
         */
        for (int i = 1; i < 6; i++) {
            //确定 - 的形状 把 - 替换为空格
            for (int r = 5; r >= i; r--) {
                System.out.print(" ");
            }
            //确定左半边 * 的形状
            for (int r = 1; r <= i; r++) {
                System.out.print("*");
            }
            //确定右半边 * 的形状 第一行只有一个 所以第一行本循环不输出
            for (int r = 1; r < i; r++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```





---



# 方法

<!--参考python中的方法和其他应用记忆-->

## 壹，方法的概念

- Java方法事语句的集合，他们在一起执行一个功能。
  - 方法是解决一类问题的步骤的有序组合
  - 方法包含于类或对象中
  - 发法在程序中被创建，在其他地方被应用
- 设计方法的原则：方法的本意是功能块，就是实现某个功能的语句块的集合，我们设计方法的时候，最好保持方法的原子性，**就是一个方法只完成一个功能，有利于后期的扩展**
- 发放的命名规则：开头小写，驼峰原则

```java
//加法方法
public class Demo01{
    public static void main(String[] args){
        int sum = add(a:1,b:2);
        System.out.println(sum);//在其他地方被调用
    }
    public static int add(int a,int b){
        return a+b;
    }    
}
```





## 贰，方法的定义及调用

- Java的方法类似于其他语言的函数，是一段**用来完成特定功能的代码片段**，一般情况下，定义一个方法包含以下语法：
  - **方法包含一个方法头和一个方法体**。下面是一个方法的所有部分：
    - **修饰符：**修饰符，是可选的，告诉编译器如何调用这个方法。定义了这个方法的访问类型。
    - **返回值类型：**方法可能会返回值。returnValueType是方法的返回值的数据类型。有些方法执行所需要的操作，可能不会有返回值。在这种情况下，returnValueType的关键字是`void`。
    - **方法名**：是方法的实际名称。方法名和参数表共同构成方法签名。
    - **参数类型**：参数像是一个占位符，方法被调用的时候，传递值给参数，这个值被称为实参或变量。参数列表是指方法的参数类型、顺序、和参数的个数。参数是可选的，方法可以不包含任何参数。
      - 形式参数：在方法被调用时用于接受外界输入的数据。
      - 实参：调用方法时实际传给方法的数据。
    - **方法体**：方法体包含具体的语句，定义该方法的功能

```java
修饰符 返回值类型 方法名(参数类型 参数名){
    。。。
    方法体
    。。。
    return 返回值;
}
```







## 弎，方法重载

- 重载就是在一个类中，有相同的函数名称，但是形参不同的函数。
- 方法的重载的规则：
  - **方法名称必须相同**
  - **参数列表必须不同（个数不同、类型不同、参数排列顺序不同等）**
  - 方法的返回类型可以相同也可以不相同
  - 仅仅返回类型不同不足以成为方法的重载
- 实现理论：
  - 方法名称相同时，编译器会根据调用发放的参数个数，参数的数据类型等逐个去匹配，以选择对应的方法，如果匹配失败，则编译器报错

```java
package package_opertor;

public class study {
    //方法重载
    public static void main(String[] args) {
        int add = add(1, 2);
        double add2 = add(1.0,2.0);
        System.out.println(add);
        System.out.println(add2);
    }
    //定义加法
    public static int add(int a,int b){
        return a+b;
    }
    //定义加法2
    public static double add(double a,double b){
        return a+b;
    }
}
```



## 肆，命令行传参(了解)

- 运行一个程序的时候在传递给它消息。这要靠传递命令行参数main()来实现

```java
public class CommandLine{
    public static void main(String args[]){
        for(int i=0;i<args.length;i++){
            System.out.println("args["+i+"]:"+args[i]);
        }
    }
}
```





## 伍，可变参数

- 可以传递同类型的可变参数给一个方法
- 在方法声明中，在指定参数类型后加个省略号(...)。
- 一个方法只能指定一个可变参数，它必须是方法的最后一个参数。任何普通参数都必须在可变参数之前生命。

```java
package package_opertor;

public class study {
    //方法重载
    public static void main(String[] args) {
        printMax(1,2,3,4,657,65,7456,8);
    }

    public static void printMax(double... num) {
        if (num.length==0){
            System.out.println("No argument passed!");
            return;
        }
        double result = num[0];
        for (int i=1;i< num.length;i++){
            if (num[i]>result){
                result = num[i];
            }
        }
        System.out.println(result);
    }
}

```







## 陆，==递归（重要）面试题==

<!--自己调用自己-->

- 定义：递归就是A方法调用A方法
- 递归结构包含两个部分：
  - 递归头：什么时候不调用自身方法；没有头，将陷入死循环
  - 递归体：什么时候需要条用自身方法。

**举例**

设计阶乘功能

```java
package package_opertor;

public class study {
    //设计阶乘
    public static void main(String[] args) {

    }
    //1! 为1
    //2! 2*1
    //3! 3*2*1
    //4! 4*3*2*1
    //可以理解为 n! = n*(n-1)!
    public static int factorial(int n) {
        //定义一个头
        if (n==1){
            return 1;
        }else{//既然factorial方法是阶乘方法,那么调用阶乘方法来表示即可
            return n*factorial(n-1);
        }
    }
}
```

![阶乘递归](../../tuxiang/阶乘递归.png)



- 尽量不使用递归

---

# 数组arrays

## 壹，数组概述

<!--一组数-->

### 数组定义

- 数组是**相同类型**数据的有序集合
- 数组描述的是相同类型的若干数据,按照一定的先后顺序排列组成的
- 其中,每一个数据成为一个数组元素,每个数组元素可以**通过下标**访问它们 下标从零开始

## 贰，数组声明创建

- 首先必须声明数组变量

![](../../tuxiang/java数组.png)

```java
package package_opertor;
import java.util.Scanner;
public class study {
    public static void main(String[] args) {
        //声明数组
        int[] nums;
        int nums2[];
        //创建一个数组
        nums = new int[5];//5为分配给数组几个数组几个空间
        //声明并创建数组
        int nums3[] = new int[5];
        int[] nums4 = new int[5];
        //数组元素赋值
        nums[0]= 1;
        nums[1]= 2;
        nums[2]= 3;
        nums[3]= 4;
        nums[4]= 5;
        //访问数组中一个元素
        System.out.println(nums[3]);
        //计算数组元素的和
        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            sum +=nums[i];
        }
        System.out.println(sum);
    }
}

```



### 内存分析

![](../../tuxiang/Java内存.png)

- Java内存简单分析



![](../../tuxiang/数组内存理解.png)

### 数组的三种初始化

- 静态初始化

```java
int a[] = {1,2,3};
Man[] mans = {new Man(),new Man()};//Man是创建的一个类class
```

<!--理解：静态初始化是指在创建数组的同时，赋值，此时数组根据赋值的元素来分配大小-->

- 动态初始化（包含默认初始化）

```java
int a[] = new int[2];
a[0]=1;
a[1]=2;
```

<!--理解：动态初始化就是把数组创建出，分配大小后，再慢慢赋值-->

- 数组的默认初始化
  - 数组是引用类型，他的元素相当于类的实例变量，因此数组一经分配空间，其中的每个元素也被按照实例变量同样的方法被隐式初始化。





### 数组的四个基本特点

- 数组长度都是确定的、固定的。数组一旦被创建，它的大小不会改变。
- 数组元素必须是相同类型，不能出现混合类型。
- 数组中元素可以是任何数据类型，包含基本类型和引用类型。
- 数组变量属应用类型，数组也可以看成对象，数组的每个元素可以看成这个对象的成员变量。数组本身就是对象，Java中对象是在堆中，因为数组无论保存原始类型还是其他对象类型，数组对象本身是在堆中的。







## 弎，数组使用

- 普通for循环
- For-each 加强循环
- 数组作为方法入参（定义一个以方法，入参的数据类型为数组）
- 数组作为返回值（定义一个方法，返回值的数据类型为数组）

```java
package package_opertor;

public class study {
    public static void main(String[] args) {
        int arrays[] = {1,2,3,4,5};
        //For-each
        for (int array : arrays) {
            System.out.print(array+" ");//1 2 3 4 5
        }
        System.out.println("\n==============数组作为入参========================");
        //调用printArrays方法打印数组
        printArrays(arrays);
        System.out.println("\n==============数组作为返回值========================");
        //调用反转数组方法
        int[] reverse = reverse(arrays);
        printArrays(reverse);
        System.out.println("\n==============数组作为入参,使用方法组合调用========================");

        printArrays(reverse(arrays));


    }
    //数组作为方法入参（定义一个以方法，入参的数据类型为数组）
    public static void printArrays(int arrays[]){
        for (int array : arrays) {
            System.out.print(array+" ");
        }
    }
    //数组作为返回值（定义一个方法，返回值的数据类型为数组）
    //反转数组，数组元素调换
    public static int[] reverse(int arrays[]){
        int result[] = new int[arrays.length];
        for (int i = 0,j = arrays.length-1; i < arrays.length ; i++,j--) {
            result[i] = arrays[j];
        }
        return result;
    }

}

```





## 肆，多维数组

<!--可以理解为,数组的嵌套,一元数组中每个数组元素是数字,二维或多维数组中,数组中的数组元素存的也是数组-->

<!--遍历多维数组的时候需要对最底层的数组进行遍历,需要for循环的嵌套,不需要多维数组,二维够用-->

- 多维数组可以看成是数组的数组

- 二维数组

  ```java
  int a[][] = new int[2][5]
  ```

- 解析:以上二维数组 a 可以看成一个二行五列的数组

![](../../tuxiang/二维数组.png)

![](../../tuxiang/二维数组2.png)



```java
package package_opertor;

public class study {
    public static void main(String[] args) {
        int a[][] = {{1,2},{3,4}};
        System.out.println(a[0]);//[I@4554617c
        System.out.println(a[0][1]);//2
        System.out.println(a[1][1]);//4
        for (int aa[] : a ){
            for (int num : aa ){
                System.out.print(num+" ");
            }
        }
        //
        System.out.println("\n===============");
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                System.out.print(a[i][j]+" ");
            }
        }
    }

}

```







## 伍，Arrays类

### Arrays

<!--专门操作数组的类-->

- 数组的工具类java.util.Arrays
- 由于数组对象本身并没有方法供我们调用，但API中提供了一个工具类Arrays供我们使用，从而可以对数据对象进行一些基本的操作。
- **查看JDK帮助文档**。
- Arrays类中的方法都是`static`修饰的静态方法，在使用的时候可以直接使用类名进行调用，而“不用”使用对象来调用（是 不用 ，而不是 不能）。
- 具有以下常用功能
  - 给数组赋值：`fill`
  - 数组排序：`sort`升序
  - 比较数组：`equals` 比较数组中元素值是否相等
  - 查找数组元素：`binarySearch`对排序好的数组进行二分查找法。

### 冒泡排序

- 冒泡排序是最出名的排序算法之一，共有八大排序！

- 冒泡的代码简单，两层循环，外层循环轮数，里层依次比较

- **看到嵌套循环，就应该立马想到得出这个算法的==时间复杂度为O(n^2^)==**

```java
package package_opertor;
//冒泡排序
public class study {
    public static void main(String[] args) {
        int a[] = {1,23,2,4,23,4,32,5,45,21,3,2,5,4,53};
        int sort[] = sort(a);
        printArrays(sort);
    }
    public static int[] sort(int arrays[]){
        int c = 0;
        for (int i = 0; i < arrays.length-1; i++) {//判断走几次，因为内层比较，前面的数字都已经和后面的数字比较过了，最后一个数字不需要比较所以，控制在0-13，
            for (int j = 0; j < arrays.length-1-i; j++) {//控制上限，上限控制:j 和 i 的关系，i = 0，第一个元素需要循环比较到下标为14的元素，上限为 14 = 15 -1-0，依次类推为上限公式 = 15-1-i 
                if (arrays[j+1]<arrays[j]) {
                    c = arrays[j+1];
                    arrays[j+1] = arrays[j];
                    arrays[j] = c;
                }
            }
        }return arrays;

    }

    public static void printArrays(int arrays[]){
        for (int a:arrays) {
            System.out.print(a+",");
        }
    }

}

```





## 陆，稀疏数组

<!--数组结构-->

- 当一个数组中大部分元素为 0 ，或者为同一值的数组时，可以使用稀疏数组来保存该数组。
- 稀疏数组的处理方法是：
  - 记录数组一共几行几列，有几个不同值。
  - 把具有不同值的元素和行列及值记录在一个小规模数组中，从而压缩程序规模。
- 如下图：左边是原始数组，右边是稀疏数组。

![](../../tuxiang/稀疏数组.png)



![](../../tuxiang/五子棋.png)



```java
package package_opertor;

public class study {
    public static void main(String[] args) {
        int arrays1[][] = new int[11][11];
        arrays1[1][2] = 1;
        arrays1[2][3] = 2;
        //printArrays(arrays1);
        //创建稀疏数组
        //计算有效个数
        int sum = 0;
        for (int a[]:arrays1) {
            for (int b:a) {
                if (b!=0){
                    sum++;
                }
            }
        }
        System.out.println(sum);//打印有效个数
        int arrays2[][] = new int[sum+1][3];
        arrays2[0][0] = 11;//将数组行赋值
        arrays2[0][1] = 11;//将数组列赋值
        arrays2[0][2] = sum;//将数组有效数赋值
        //有效值赋值 计算有效值的行列
        int count = 0;//标记有效值个数，便于计算稀疏数组的行号
        for (int i = 0; i < arrays1.length; i++) {
            for (int j = 0; j < arrays1[i].length; j++) {
                if (arrays1[i][j]!=0){
                    count++;//此时存的是有效数的个数，起始值为1，这就是稀疏数组的行号
                    arrays2[count][0]=i;//存入数组有效数的行号
                    arrays2[count][1]=j;//存入数组有效数的列号
                    arrays2[count][2]=arrays1[i][j];//存入有效数的值
                }
            }
        }
        System.out.println("稀疏数组");
        printArrays(arrays2);
        //还原
        System.out.println("根据稀疏数组还原数组");
        int arrays3[][]= new int[arrays2[0][0]][arrays2[0][1]];//创建还原数组，标明数组的行和列
        for (int i = 1; i < arrays2.length; i++) {
            arrays3[arrays2[i][0]][arrays2[i][1]] = arrays2[i][2];//将稀疏数组中存的有效数的坐标通过稀疏数组元素给与数组，包括有效数的值
        }
        printArrays(arrays3);
    }

    public static void printArrays(int arrays[][]){
        for (int a[]:arrays) {
            for (int b:a) {
                System.out.print(b+"\t");
            }
            System.out.println();
        }
    }
}

```





# 面向对象编程

> Java的核心思想就是OOP



## 壹 ，初识面向对象

### 1.1, **面向过程思想和面向对象思想**

​	**1.1.1, 面向过程思想**

- 步骤简单,第一步,第二步
- 面向过程适合处理一些简单的问题

 **1.1.2, 面向对象思想**

<!--是一种思想,先从整体把控方向,分类进行具体操作-->

- 物以类聚,分类的思维模式,思考问题首先会解决问题需要那些分类,然后对这些分类单独思考.最后才对某个分类下的细节进行面向过程的探索.
- 面向对象适合处理一些复杂的问题,适合处理多人协作的问题.

**1.1.3, 总结**

**==对于描述复杂的事物,为了从宏观上进行把控,从整体上进行合理分析,我们需要面向对象的思路来分析整个系统.但是具体到微观操作,仍然需要面向过程的思路去处理==**



### 1.2, 什么是面向对象

- 面向对象编程(Object-Oriented Programming,OOP)
- 面向对象编程的本质就是:==以类的方法组织代码,以对象的组织(封装)数据.==

**1.2.2, 抽象**



**1.2.3, 三大特征**

- ==封装==
- ==继承==
- ==多态==



**1.2.4, 小结**

- 从认识论的角度考虑是现有对象后有类。对象，是具体的事物。类，是抽象的，是对对象的抽象。
- 从代码运行的角度来看，先有类后有对象。类是对象的模板



## 贰，方法回顾和加深

### 2.1 方法的定义

- 修饰符：public 公共的

- 返回类型

- break break跳出switch，结束循环 和return 代表方法结束区别

- 方法名：注意规范，见名知意

- 参数列表：（参数类型，参数名）。。。

- 异常抛出：后续讲解，在IO流读文件会有一场

  - ```java
    public void readFile(String file) throws IOException{
        
    }
    //数组下标越界 arrayIndexOutOfBounds
    ```



### 2.2， 方法的调用：递归

- 静态方法：加了修饰符 static；静态方法，在其他类中调用，直接claaName.方法名
- 非静态方法：没有加修饰符 static；非静态方法，调用需要，**实例化这个类 new；Student name = new Student()；再通过 name.方法名**
- 形参和实参
- **值传递和引用传递**

```java
package package_opertor;

//引用传递：对象，本质还是值传递
public class study {
    public static void main(String[] args) {
        Person person = new Person();
        System.out.println(person.name);
        study.change(person);
        System.out.println(person.name);

    }
    public static void change(Person person){
        //person是一个对象，这里赋值指向的是--->Person person = new Person()；是一个具体的对象
        person.name = "cfc";
    }
}
//定义一个类，，有一个属性：name
class Person{
    String name;
}
```



- **thsi关键字**





## 弎，类和对象的创建

### 3.1， 类和对象的关系

- 类是一种抽象的数据类型，它是对某一类事物整体描述/定义，但是并不能代表某一个具体的事物。
- 对象是抽象概念的具体实例

> 理解：类是一个抽象的，像是分类的，在创建一个对象的时候可以将该对象进行分类，创建张三对象分为Person类中



### 3.2， 创建和初始化对象

- ==使用new关键字创建对象==
- 使用new关键字创建的时候，除了分配内存空间之外，还会给创建好的对象进行默认的初始化，以及对类中构造器的调用（构造器下方讲解）
- 类中的构造器也称为构造方法，是在进行创建对象的时候必须调用的。并且构造器有以下两个特点：
  - 必须和类的名字相同
  - 必须没有返回类型，也不能写void
- **==构造器必须掌握==**

<!--一个项目应该只存在一个main方法-->

![](../../tuxiang/创建对象.png)



### 3.3 构造器的讲解

当定义一个class的时候，里面没有代码，其他类使用main方法仍然可以new一个对象，通过查看class的class文件

![](../../tuxiang/构造器1.png)

定义一个显示的构造器

![](../../tuxiang/构造器2.png)

![](../../tuxiang/构造器3.png)

<!--可以理解，构造器可以规定创建对象的默认值-->

**使用deBug可以看到创建对象的时候，需要返回到类中的构造器里，走完后，再去创建对象**



**有参构造**：有参数的构造器

注意，一旦使用有参构造，无参构造必须显示定义

当外部调用该类的时候，会根据new的时候传入的参数，来决定走有参还是无参构造



alt+inset 快捷键可以生成构造器

![](../../tuxiang/构造器构造快捷键1.png)

![](../../tuxiang/构造器构造快捷键2.png)

选择无选择的时候生成，无参构造

![](../../tuxiang/构造器构造快捷键3.png)

结论1：一个类什么都不写，也会存在一个方法

结论2：使用new关键字，本质是在调用构造器，构造器可以控制this类属性的默认值

**总结**

- 构造器：
  - 和类名相同
  - 没有返回值和void
- 作用：
  - new 本质在调用构造器
  - 规定初始化对象的默认值
- 注意点：
  - 定义有参构造之后，如果还想使用无参构造，需要显示定义一个无参构造
- Alt+inset
- this. (代表当前类的)= （一般是参数传入的值）





## 弎，对象的创建分析

> 创建时候内存是怎样的？

![](../../tuxiang/内存简略讲解1.png)



![](../../tuxiang/内存简略讲解2.png)

> Application类调用 Pet类的时候会在，堆中的方法区中产生一个区域，首先是Application类--在其中又main()方法、常量池：旺财，age传的时数值，不在常量池中；其次时Pet类--其中有静态变量name、age还有方法shout()；特殊的是静态方法区：static定义的都会在这里加载，和类一起加载，出现的早，其他后来加载的都可以调用这里面的东西；
>
> 随后，再栈中加载Application类中的main()方法；Application类中定义了Pet模板的对象dog、cat，会在栈中生成dog、cat的引用变量名，实际的对象在堆中；
>
> 随后，堆中会加载一块区域生成dog、cat的实际对象，赋予内存地址，这是new了之后出现的区域；
>
> Application类中赋予dog、cat的name，age值的时候，会在堆中相应的地址中，将值加载到内存里，（在堆中引用的shout方法，没有传入参数，实际引用的就是Pet中的shout方法），这两个堆中的对象都能调用静态方法区中的方法



![](../../tuxiang/内存讲解3.png)



- **小结**

- 类与对象

  - 类是一个模板：抽象，对象是一个具体的实例

- 方法

  - 定义、调用！

- 对象的引用

  - 引用类型：基本类型（8大），除了基本类型之外的都是引用类型

    对象是通过引用来操作的：栈--->堆，栈中存的是堆中对象的地址，实际操作的还是堆

- 属性：别名：字段Field，成员变量

  - 默认初始化：数值 0/0.0；char：u0000；Boolean：false；除了基本类型：null
  - 定义 修饰符 属性类型 属性名 = 属性值；

- 方法：方法的定义和使用

- **对象的创建和使用**

  - 必须使用new关键字创建对象，构造器必须有 Person xiaoming = new Person()；
  - 对象的属性 xiaoming.name
  - 对象的方法 xiaoming.sleep()

- 类

  - 只有两个东西：静态的属性--属性；动态的行为--方法；





## 肆，面向对象的三大特征

**==重点==**

### 4.1， 封装

- 该露的露，该藏的藏
  - 程序设计追求“高内聚，低耦合”。高内聚：类的内部数据操作细节自己完成，不允许外部干涉；低耦合：尽暴露少量的方法给外部使用。
- 封装（数据的隐藏）
  - 通常，应禁止直接访问一个对象中的数据的实际表示，而应通过操作接口访问，这成为信息隐藏。
- 记住：==属性私有，get/set==

<!--方法中很少使用封装-->

private 私有的 --关键字

<!--private 定义的对象，其它类中无法直接调用，与static对比记忆-->

<!--get/set 提供一些可以操作私有属性的方法 get获得这个私有属性数据；set给这个数据设置值-->

**封装的意义**

- 提高程序的安全性，保护数据；
- 隐藏代码的实现细节
- 统一接口
- 系统可维护增加了

![](../../tuxiang/封装1.png)

> 其他：printLn 使用的重载的，可以了解下；
>
> 判断方法相同：名字一致，参数列表一致

### 4.2， 继承

#### 4.2.1， 定义

- **继承本质就是对某一批类的抽象，从而实现对现实世界更好的建模。**
- **`extends` 意思是 扩展， 子类是父类的扩展。**
- **Java中类只有单继承，没有多继承！** 和python不同
- 继承是类和类之间的一种关系。除此之外，类和类之间的关系还有依赖，组合，聚合等
- 继承关系的两个类，一个为子类（派生类），一个为父类（基类）。子类继承父类，使用关键字`extends`表示
- 子类和父类之间，从意义上讲应该具有“ is a”的关系。
- ==**object类**==
- **==super==**
- **==方法重写==**

#### 4.2.2，继承简述

**修饰符**：

- public公共的
- default 默认的
- protected 受保护的
- private 私有的

子类继承父类，继承父类的方法：public、default、protected 修饰的方法属性；private 修饰的不继承；

**ctrl + H 显示继承关系**

Java中所有的类都默认直接间接阶乘Object类

![](../../tuxiang/继承1.png)

#### 4.2.3， super

![](../../tuxiang/继承2super.png)

- this. 调用本类中的属性或者方法
- super. 调用父类中的属性或方法
- 都不写，默认是子类中的，有值传递的时候调用传值的





![](../../tuxiang/super2.png)

同上





![](../../tuxiang/super继承-构造器.png)

- 子类中的无参构造中有隐藏代码，默认先调用父类的无参构造super()，再执行子类的无参构造中语句，父类的必须写在子类构造的第一行，可以不写
- 父类中没有无参构造时，子类也不能调用无参构造，无参构造器中但可以调用父类的有参构造，和自己的有参构造，必须显示调用父类有参构造，才能正常使用

**Super注意点**

- super调用父类构造方法，必须再构造方法的第一个
- super 必须只能出现在子类的方法或者构造方法中
- super和this 不能同事调用构造方法

**this**

- 代表的对象不同
  - this：本身调用者这个对象
  -  super：代表父类对象的引用
- 前提
  - this：没有继承也可以使用
  - super：只能在继承条件下才能使用
- 构造方法区别
  - this：调用本类的构造
  - super：调用的父类的构造

#### 4.2.4， 方法重写

<!--方法重写只在有继承关系中使用，且只有子类可以重写父类的方法，仅限于方法不能重写属性-->

![](../../tuxiang/重写1.png)



![](../../tuxiang/重写2.png)





**override重写父类方法时，重写static方法时不起作用，只针对于非静态方法**

**对于私有方法不起作用**

**总结**

重写：需要有继承关系，子类重写父类的方法；

- 方法名必须相同
- 参数列表必须相同
- 修饰符：范围可以扩大：public > protected >default >private
- 抛出的异常：范围可以缩小（对于异常可以细化，不能扩大）：Exception >Class Not Found Exception

重写，子类的方法必须和父类一致，方法体不同！



**为什么重写**

- 父类的功能子类不一定需要，或者不一定满足。

快捷键：Alt + Insert ： OVerride；



#### 4.2.5， 多态

定义：

- 动态编译：程序中类型的最终状态只有在程序执行中才能决定，写代码时确定不了。通过多态使扩展性增强
- 既同一个方法可以根据发送对象的不同而采用多种不同的行为方式。
- 一个对象的实际类型是确定的，但可以指向对象的引用的类型有很多。



多态存在的条件

- 有继承关系
- 子类重写父类的方法
- 父类引用指向子类对象

注意：多态是方法的多态，属性没有多态性。

- instanceof 引用类型的类型转换





![](../../tuxiang/继承-多态理解1.png)



**多态注意事项**

- 多态是方法的多态，属性没有
- 父类和子类，有联系，才能转换，且父类引用可以指向子类实际对象 异常 ClassCastException---类型转换异常。
- 存在条件：
  - 有继承关系
  - 方法需要重写
  - 父类引用类型指向子类实际对象 Father f1 = new Son（）；

修饰符

1，static 方法，属于类一方面的，不属于实例，与类同时加载，静态方法

2，final 常量；

3，private 方法；

以上都不能重写



#### 4.2.6，instanceof 判断两个类之间是否存在父子关系

通常在强转换引用类型对象的时候，先判断是否存在父子关系，再决定是否转换，转换成什么。



#### 4.2.7， static关键字详解

> 理解：static修饰的变量和方法又名类变量，类方法，在加载类的时候，该变量或者方法就会加载，所以其他方法可以调用；非静态变量和方法，不能够被静态调用，因为静态变量和方法，已经加载完成。



```java
public class Demo{
    {
        //匿名代码块 在构造器之前加载
    }
    static{
        //静态代码块：可以加载些初始化数据
    }
}
```



![](../../tuxiang/static1.png)

static修饰的代码块，与类一起加载，且只加载一次；

匿名代码块和构造器在new 的时候加载，代码块比构造器要早加载。

> 扩展：final修饰的类不能被其他类继承



## 伍，抽象类和接口

#### 5.1， 抽象类

> 抽象是种思维,将相似的抽取出来

定义：

- `abstract`修饰符可以修饰方法也可以修饰类，如果修饰方法，那么该方法就是抽象方法；如果修饰类，该类就是抽象类。

- 抽象类中可以没有抽象方法，但是有抽象方法的类一定要声明为抽象类。

特点：

- 抽象类，不能使用new关键字创建对象，他是用来让子类继承的，
- 抽象方法，只有方法的声明，没有方法的实现，它是用来让子类实现的。
- 子类继承抽象类，那么就必须要实现抽象类中没有实现的抽象方法，否则该子类也要声明为抽象类。

![](../../tuxiang/抽象类和抽象方法.png)

虽然抽象类没办法new但仍存在构造器

#### 5.2， 接口

- 普通类：只有具体实现

- 抽象类：具体实现和规范（抽象方法）都有！
- 接口：只有规范！，自己无法写方法~专业的约束！约束和实现分离：面向接口编程。



- 接口就是规范，定义的是一组规则，体现了现实世界中“如果你是……则必须能……”的思想，
- ==接口的本质就是契约==，就像是法律。
- OO的精髓，是对对象的抽象，最能体现这一点的就是接口，为什么我们讨论设计 模式都是只针对具备了抽象能力的语言（c++，java，c#等），就是因为设计模式所研究的，实际上就是如何合理的去抽象。

**声明类的关键字是class，声明接口的关键字是`interface`**

> 接口都需要实现类，接口中所有的定义都是抽象的



## 陆，内部类和OOP实战























































---

# 玖玖，其他

## 1 数组

**数组概述：**数组(array)是一种用于存储多个相同类型数据的存储类型。一次性声明大量的用于存储数据的变量。要存储的数据通常是同类型的数据，例如：考试成绩。

**定义格式**

- 格式一：数据类型[] 变量名 范例：int[] arr
- 定义了一个int类型的数组，数组名是arr
- 格式二：数据类型 变量名[] 范例：int arr[]
- 定义了一个int类型的变量，变量名是arr数组

**数组初始化概述：**Java中的数组必须先初始化，然后才能使用。初始化就是为数组中的数组元素分配内存空间，并为每个数组元素赋值。

**数组初始化方式：**有动态初始化和静态初始化。

**动态初始化**

动态初始化：初始化时只指定数组长度，由系统为数组分配初始值。

- 格式：数据类型[] 变量名 = new 数据类型[数组长度];
- 范例：int[] arr = new int[3];

**静态初始化**

静态初始化：初始化时由程序员自己为数组对象的每个元素赋值，由系统自动计算出数组的长度。

- 格式：数据类型[] 变量名 = new 数据类型[]{数据1，数据2，数据3...};
- 范例：String[] s = new String[]{"Hello","World","Java"};
- 简化格式：数据类型[] 变量名 = {数据1，数据2，数据3...};
- 范例：String[] s = {"Hello","World","Java"};

### 1.2 数组元素访问

**数组变量访问方式(格式)：**数组名

**数组内部保存的数据的访问方式(格式)：**数组名[索引]

**索引：**索引是数组中数据的编号方式。索引用于访问数组中的数据使用，数组名[索引]等同于变量名，是一种特殊的变量名。

- 索引从0开始
- 索引是连续的
- 索引逐一增加，每次加1

### 1.3 内存分配

Java程序在运行时，需要在内存中分配空间。为了提高运算效率，就对空间进行了不同区域的划分，因为每一片区域都有特定的处理数据方式和内存管理方式。

**Java中内存分配**

- 栈内存：存储局部变量，即定义在方法中的变量，例如：arr。使用完毕，立即消失。
- 堆内存：存储new出来的内容(实体，对象)。每一个new出来的东西都有一个地址值，使用完毕，会在垃圾回收器空闲时被回收。

数组在初始化时，会为存储空间添加默认值

- 整数：默认值0
- 浮点数：默认值0.0
- 布尔值：默认值false
- 字符：默认值是空字符
- 引用数据类型：默认值是null

### 1.4 数组操作的两个常见小问题

索引越界：访问了数组中不存在的索引对应的元素，造成索引越界问题。

空指针异常：访问的数组已经不再指向堆内存的数据，造成空指针异常。

null：空值，引用数据类型的默认值，表示不指向任何有效对象。

### 1.5 数组常见操作

**遍历**

获取数组元素数量(格式)：数组名.length。

范例：arr.length

数组遍历的通用格式

```java
int[] arr = {...};

for(int i=0;i<arr.length;i++){
    System.out.println(arr[i]);
}
```

**获取最值**

```java
public class ArrayDemo {
    public static void main(String[] args) {
        int[] arr = {12,45,98,73,60};

        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if(arr[i] > max){
                max = arr[i];
            }
        }
        System.out.println("max:" + max);
    }
}
```





---

## 