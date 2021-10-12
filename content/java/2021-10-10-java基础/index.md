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

## 快速入门

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
