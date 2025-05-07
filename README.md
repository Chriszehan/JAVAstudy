# JAVAstudy

1、运行一个JAVA 程序 先将.java文件交由编译器编译为.class 再交给JVM执行

一个Java源码只能定义一个public类型的class，并且class名称和文件名要完全一致；

使用javac可以将.java源码编译成.class字节码；

使用java可以运行一个已编译的Java程序，参数是类名。

2、程序基本结构
面向对象的程序 基本单位就是class 要求类名--------驼峰

Java入口程序规定的方法必须是静态方法，方法名必须为main，括号内的参数必须是String数组。

3、变量
基本类型的变量和引用类型的变量

基本类型变量 在Java中，变量必须先定义后使用 
同一变量无需再次定义变量类型  变量可重新赋值

4、基本数据类型 是CPU可直接进行运算的类型
整型：byte（8个bit）、short、int 、long
浮点型：float、double
字符型：char
布尔类型：boolean

计算机内存的最小存储单元是字节（byte），一个字节就是一个8位二进制数，即8个bit。它的二进制表示范围从00000000~11111111，换算成十进制是0~255，换算成十六进制是00~ff。

内存单元从0开始编号，称为内存地址
![image](https://github.com/user-attachments/assets/36c72179-63bc-4bc3-be55-a0a67a1009f1)
