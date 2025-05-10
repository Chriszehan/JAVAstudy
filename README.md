# JAVAstudy

## 1、运行一个JAVA 程序 先将.java文件交由编译器编译为.class 再交给JVM执行

一个Java源码只能定义一个public类型的class，并且class名称和文件名要完全一致；

使用javac可以将.java源码编译成.class字节码；

使用java可以运行一个已编译的Java程序，参数是类名。

## 2、程序基本结构
面向对象的程序 基本单位就是class 要求类名--------驼峰

Java入口程序规定的方法必须是静态方法，方法名必须为main，括号内的参数必须是String数组。

## 3、变量
基本类型的变量和引用类型的变量

基本类型变量 在Java中，变量必须先定义后使用 
同一变量无需再次定义变量类型  变量可重新赋值

## 4、基本数据类型 
CPU可直接进行运算的类型
整型：byte（8个bit）、short、int 、long
浮点型：float、double
字符型：char
布尔类型：boolean

计算机内存的最小存储单元是字节（byte），一个字节就是一个8位二进制数，即8个bit。它的二进制表示范围从00000000~11111111，换算成十进制是0~255，换算成十六进制是00~ff。

内存单元从0开始编号，称为内存地址
![image](https://github.com/user-attachments/assets/36c72179-63bc-4bc3-be55-a0a67a1009f1)

### 整型
  int类型可以赋值给long 
  表示为 long n1 = 900;
  但是不能把long型赋值给int


### 浮点型
  float f1 = 3.14f;
  float f2 = 3.14e38f; // 科学计数法表示的3.14x10^38
  float f3 = 1.0; // 错误：不带f结尾的是double类型，不能赋值给float

  double d = 1.79e308;
  double d2 = -1.79e308;
  double d3 = 4.9e-324; // 科学计数法表示的4.9x10^-324


### 布尔类型
  boolean b1 = true;
  boolean b2 = false;
  boolean isGreater = 5 > 3; // 计算结果为true
  int age = 12;
  boolean isAdult = age >= 18; // 计算结果为false

### 字符类型
  char a = 'A'  
  注意char类型使用单引号'，且仅有一个字符，要和双引号"的字符串类型区分开。


### 引用类型
  String s = "hello";
  内部存储一个地址 ，指向某个对象在内存的位置

### 常量
  final修饰符 变量加上此修饰符之后 就变成常量
  初始化定义后 不可再次赋值 会导致编译错误

### var关键字
  有些时候，类型的名字太长，写起来比较麻烦。例如：
  StringBuilder sb = new StringBuilder();
  
  这个时候，如果想省略变量类型，可以使用var关键字：
  var sb = new StringBuilder();
  
  编译器会根据赋值语句自动推断出变量sb的类型是StringBuilder。对编译器来说，语句：
  var sb = new StringBuilder();
  
  实际上会自动变成：
  StringBuilder sb = new StringBuilder();
  因此，使用var定义变量，仅仅是少写了变量类型而已。

变量作用域以{}为准

## 整数运算
  n++ 自增运算
  ++n表示先加1再引用n
  n++表示先引用n再加1 

### 移位运算
  计算机中 整数总是以二进制的形式表示 int类型移位运算

  向左移 实际上是不断地 x2 

  int n = 7;       // 00000000 00000000 00000000 00000111 = 7
  int a = n << 1;  // 00000000 00000000 00000000 00001110 = 14
  int b = n << 2;  // 00000000 00000000 00000000 00011100 = 28
  int c = n << 28; // 01110000 00000000 00000000 00000000 = 1879048192
  int d = n << 29; // 11100000 00000000 00000000 00000000 = -536870912

  向右移 实际上是不断地 /2
  int n = 7;       // 00000000 00000000 00000000 00000111 = 7
  int a = n >> 1;  // 00000000 00000000 00000000 00000011 = 3
  int b = n >> 2;  // 00000000 00000000 00000000 00000001 = 1
  int c = n >> 3;  // 00000000 00000000 00000000 00000000 = 0

  >> 有符号位移运算  >>>无符号位移运算 右移后高位总是补0 因此对一个负数进行>>>右移 会变成正数 最高位有1变成0

### 位运算
  
  与运算的规则是，必须两个数同时为1，结果才为1：
  n = 0 & 0; // 0
  n = 0 & 1; // 0
  n = 1 & 0; // 0
  n = 1 & 1; // 1

  或运算的规则是，只要任意一个为1，结果就为1：
  n = 0 | 0; // 0
  n = 0 | 1; // 1
  n = 1 | 0; // 1
  n = 1 | 1; // 1

  非运算的规则是，0和1互换：
  n = ~0; // 1
  n = ~1; // 0

  异或运算的规则是，如果两个数不同，结果为1，否则为0：

  n = 0 ^ 0; // 0
  n = 0 ^ 1; // 1
  n = 1 ^ 0; // 1
  n = 1 ^ 1; // 0

### 类型自动提升 和 强制转型

如果参与运算的两个数类型不一致 那么计算自动提升类型为较大的类型
// 类型自动提升与强制转型
public class Main {
    public static void main(String[] args) {
        short s = 1234;
        int i = 123456;
        int x = s + i; // s自动转型为int
        short y = s + i; // 编译错误!
    }
}

也可以将结果强制转型，即将大范围的整数转型为小范围的整数。强制转型使用(类型)，例如，将int强制转型为short：
int i = 12345;
short s = (short) i; // 12345

要注意，超出范围的强制转型会得到错误的结果，原因是转型时，int的两个高位字节直接被扔掉，仅保留了低位的两个字节：

// 强制转型
public class Main {
    public static void main(String[] args) {
        int i1 = 1234567;
        short s1 = (short) i1; // -10617
        System.out.println(s1);
        int i2 = 12345678;
        short s2 = (short) i2; // 24910
        System.out.println(s2);
    }
}
因此，强制转型的结果很可能是错的。

## 浮点数运算
  只能加减乘除 无法精确表示 存在运算误差 一般通过判断两个浮点数之差的绝对值是否小于一个很小的数 
  
  类型提升：
    如一个是整型 另一个是浮点型 那么整型自动提升到浮点型


## 布尔运算
  三元运算 b ? x : y
  注意到三元运算b ? x : y会首先计算b，如果b为true，则只计算x，否则，只计算y。此外，x和y的类型必须相同，因为返回值不是boolean，而是x和y之一

## 字符和字符串
  字符类型char是基本数据类型 一个char保存一个Unicode字符
  int n1 = 'A' 
  int n2 = '中'

  字符串类型String是引用类型  一个字符穿可以存储0-任意个字符
  如果用+连接字符串和其他数据类型，会将其他数据类型先自动转型为字符串，再连接
  java 字符串重要特性 字符串不可变
  // 字符串不可变
public class Main {
    public static void main(String[] args) {
        String s = "hello";
        System.out.println(s); // 显示 hello
        s = "world";  这里改变了变量s的指向地址  原来的"hello"无法通过变量s访问
        System.out.println(s); // 显示 world  
    }
}


  java13 可以使用""" xxx """ 表示多行字符串了

public class Main {
    public static void main(String[] args) {
        String s = """
                   SELECT * FROM
                     users
                   WHERE id > 100
                   ORDER BY name DESC
                   """;
        System.out.println(s);
    }
}

引用类型的变量可以指向一个空值null 表示不存在 既该变量不指向任何对象

## 数组类型
    所有元素初始化为默认值 整型都是0，浮点型为0.0 布尔型是false
    一旦创建后 大小不可改变;
    索引从0开始  可以通过复制修改数组中某个元素 n[15] = 79;
    S.length 获取数组大小

    数组是引用类型 
    // 数组
public class Main {
    public static void main(String[] args) {
        // 5位同学的成绩:
        int[] ns;
        ns = new int[] { 68, 79, 91, 85, 62 };
        System.out.println(ns.length); // 5
        ns = new int[] { 1, 2, 3 };                //实则更换了新的地址赋值给到ns
        System.out.println(ns.length); // 3
    }
}

      问？
        String[] names = {"ABC", "XYZ", "zoo"};
        String s = names[1];
        names[1] = "cat";
        System.out.println(s); // s是"XYZ"还是"cat"?

## 输入/输出
  ### 输出
  如果要把数据显示成我们期望的格式，就需要使用格式化输出的功能。格式化输出使用System.out.printf()，通过使用占位符%?，printf()可以把后面的参数格式化成指定格式：
    double d = 3.1415926;
    System.out.printf("%.2f\n", d); // 显示两位小数3.14
    System.out.printf("%.4f\n", d); // 显示4位小数3.1416
格式化 
  占位符	说明
  %d	格式化输出整数
  %x	格式化输出十六进制整数
  %f	格式化输出浮点数
  %e	格式化输出科学计数法表示的浮点数
  %s	格式化字符串

 ### 输入
   使用scanner 创建scanner对象并传入System.in 然后使用scanner.nextline() 读取用户输入字符串
   scanner.nextInt() 读取用户输入整数
   









    











