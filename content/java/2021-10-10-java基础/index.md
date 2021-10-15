---
title: Java基础
author: Lin Gui
date: '2021-10-10'
slug: java基础
categories:
  - Java
tags:
  - 技能点
---

# Java概述

## java特点

1.  面向对象oop，封装，继承，多态

2.  健壮性，强类型机制、异常处理、垃圾回收机制

3.  跨平台性，即一个编译好的.class文件可以在多个系统下运行。

4.  解释型语言【js、php、java】，编译后的代码需要解释器来运行。

    编译型语言【c、c++】，编译后代码能直接执行。

## java运行机制及运行过程

### java核心机制-Java虚拟机JVM

1.  JVM是一个虚拟计算机，具有指令集并使用不同的存储区域。负责执行指令，管理数据、内存 、寄存器，包含在JDK中。
2.  对于不同的平台有不同的虚拟机。JVM for Linux/Windows/Mac。
3.  Java虚拟机机制屏蔽了底层运行平台的差别，实现一次编译，到处运行。

### 运行过程

编译指令：javac，将.java文件编译成.class文件。

运行指令：java，运行.class文件。

### 什么是编译

-   通过编译器将java源文件编译成JVM可以识别的字节码文件。
-   在该源文件目录下，通过javac编译工具对.java文件进行编译。
-   如果程序没有错误，没有错误提示信息，则会出现一个.class文件，称为字节码文件，是可以执行的java程序。

### 什么是运行

有了可执行的java程序，通过运行工具java.exe对字节码文件进行执行，本质是将.class文件装载到jvm机执行。

## JDK、JRE

### JDK

-   Java Development Kit，Java开发工具包。

-   JDK=JRE+Java开发工具（java，javac，javadoc，javap等）。

-   开发人员用JDK，安装了JDK就不用装JRE了。


### JRE

-   Java Runtime Environment，Java运行环境。

-   JRE=JVM+Java核心类库。
-   如果只想运行开发好的.class文件，只用安装JRE。

## 开发细节注意事项

1.  java严格区分大小写。
2.  每个语句以；结尾。
3.  大括号成对出现。
4.  一个源文件中只能有一个public类，其余类不限，如果有多个类，每个类编译后都对应一个.class文件。
5.  如果包含public类，则文件名必须按该类名命名。
6.  main方法可以放在非public类中，然后指定运行非public类，这样入口方法就是非public类的main方法。可以通过单独运行那个类

------

## 快速入门，Hello.java

### Hello World

需求说明：开发Hello.java程序，可以输出“hello world”。

开发步骤：

1.  将Java代码编写到名为Hello.java的文件中。
2.  通过javac命令对java文件进行编译，生成.class文件。
3.  通过java命令对.class文件进行运行。

```java
// 1、public class Hello，表示Hello是一个类，是一个公有类
// 2、Hello{}，表示一个类的开始和结束
// 3、public static void main(String[] args)，表示一个主方法
// 4、main(){}，表示方法的开始和结束
// 5、System.out.println("hello world")，表示输出到屏幕
// 6、;表示语句结束
public class Hello {
	// main方法
	public static void main(String[] args) {
		System.out.println("hello world～");
	}
}
```

------

# 变量

## 为什么要变量

变量是程序的基本组成单位，变量的三个基本要素（类型+名称+值）

### 变量

变量相当于内存中的一个数据存储空间的表示，通过变量名可以访问到变量值。

### 变量使用步骤，Var01.java

```java
// 声明变量
int a；
//赋值
a=60;
//使用，System.out.println(a);输出
System.out.println(a);
//也可以使用 int a = 60;
```

## 变量使用注意事项，Var02.java

1.  变量表示内存中的一个存储区域（不同的变量，类型不同，占用空间大小不同）
2.  该区域有自己的名称（变量名）和类型（数据类型）
3.  变量必须先声明，后使用
4.  该区域的数据可以在同一类型范围内不断变化
5.  变量在同一个作用域内不能重名
6.  变量三要素，变量=变量名+值+数据类型

------

## 快速入门，Var03.java

```java
public class Var02{
	public static void main(String[] args) {
		//记录人的信息
		int age = 30;
		double score = 88.9;
		char gender = '男';
		String  name = "king";
		//输出信息
		System.out.println("人的信息如下：");
		System.out.println(name);
		System.out.println(age);
		System.out.println(score);
		System.out.println(gender);
	}
}
```

------

## 程序中+号的使用，Plus.java

1.  当左右两边都是数值型时，则做加法运算
2.  当左右两边有字符串时，则做拼接运算
3.  运算顺序从左到右

```java
System.out.println(100+88);//188
System.out.println("100"+88);//10088
System.out.println(100+3+"hello");//103hello
System.out.println("hello"+100+3);//hello1003
```

# 数据类型

每一种数据都定义了明确的数据类型，在内存中分配不同大小的内存空间。

## Java数据类型

-   基本数据类型
    -   数值型
        -   整数类型(byte[1],short[2],int[4],long[8])
        -   浮点类型(float[4],double[8]）
    -   字符型(char[2])
    -   布尔型(boolean[1])
-   引用数据类型
    -   类(class)
    -   接口(interface)
    -   数组([ ])

## 整数类型

| 类型  | 占用存储空间 | 范围         |
| ----- | ------------ | ------------ |
| byte  | 1字节        | -128~127     |
| short | 2字节        | -2^15~2^15-1 |
| int   | 4字节        | -2^31~2^31-1 |
| Long  | 8字节        | -2^63~2^63-1 |

### 整型使用细节，IntDetail.java

1.  Java各整数类型有固定的范围和字段长度，不受具体操作系统的影响，以保证java程序的可移植性
2.  Java的整型常量默认为int型，声明long型常量需要加‘l’或‘L’
3.  Java程序中变量常声明为int，除非不足以表示大数，才使用long

## 浮点类型

Java的浮点类型可以表示一个小数。

| 类型         | 占用存储空间 | 范围                  |
| ------------ | ------------ | --------------------- |
| float单精度  | 4字节        | -3.403E38～3.403E38   |
| double双精度 | 8字节        | -1.798E308～1.798E308 |

### 说明

1.  浮点数=符号位+指数位+尾数位
2.  尾数部分可能丢失，造成精度损失

### 浮点型使用细节，FloatDetail.java

1.  与整数类型相似，Java浮点类型也有固定的范围和字段长度，不受操作系统影响。
2.  Java浮点型常量默认为double，声明float常量，需要加‘f’或‘F'。
3.  浮点型常量有两种表示形式
    1.  十进制形式：5.12，512.0f，.512
    2.  科学计数法形式：5.12e2（5.12乘10的2次方），5.12E-2
4.  通常情况使用double型，因为比float精度更高
5.  浮点数使用陷阱。2.7和8.1/3，小数运算会有精度问题，可以设置精度误差来判断是否相等。
