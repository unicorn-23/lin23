---
title: 技能点-Linux基础
author: Lin Gui
date: '2021-09-12'
slug: 技能点-linux基础
categories:
  - 学习
tags:
  - 技能点
---

[学习连接](https://www.bilibili.com/video/BV1mW411i7Qf?from=search&seid=16340694041606946979&spm_id_from=333.337.0.0)

## 快捷键

| 快捷键 | 作用 | 命令  |
| ------ | ---- | ----- |
| ctrl+l | 清屏 | clear |
|        |      |       |

**Linux**

【终端登录服务器】：ssh [root@xx.xx.xx.xx](mailto:root@121.5.230.159)

【文本搜索】：grep

【传递数据】：管道符｜

​	history | grep addu :在history命令得到的结果中检索addu

【显示目前登录系统的用户信息】：w

【系统整体运行情况】：top

【睡眠】：sleep

【任务在后台运行】：&

【查看进程】：ps -ef

【查看当前文件夹】：ls [-a(全部) d(目录本身) l(包含属性权限)]

【ip地址】：ifconfig

【显示当前目录】：pwd（print work directory）

【创建文件夹】：mkdir

【删除文件夹】：mrdir

【复制】：cp

【删除文件或目录】：rm

【移动文件与目录】：mv

## 服务器管理和维护建议

### linux各目录作用

| 目录名     | 目录作用                                                     |
| :--------- | :----------------------------------------------------------- |
| /bin/      | 存放系统命令的目录。普通用户和超级用户都能执行。             |
| /sbin/     | 保存系统环境设置相关命令。只有超级用户可以进行设置，有些命令允许普通用户进行查看。 |
| /usr/bin/  | 存放系统命令的目录。普通用户和超级用户可以执行。             |
| /usr/sbin/ | 存放根文件系统不必要的系统管理命令。只有超级用户可以使用。   |
| /boot/     | 系统启动目录，保存系统启动相关的文件。                       |
| /dev/      | 设备文件保存位置。                                           |
| /etc/      | 配置文件保存位置。                                           |
| /home/     | 普通用户的家目录。所有普通用户的家目录就是在/home下建立一个和用户名相同的目录。 |
| /lib/      | 系统调用的函数库的位置。                                     |
| /media/    | 挂载目录。系统建议用来挂载媒体设备，如光盘。                 |
| /mnt/      | 挂载目录。建议挂载额外设备，如U盘。                          |
| /misc/     | 挂载目录。系统建议用来挂载NFS服务的共享目录。                |
| /opt/      | 第三方安装的软件保存位置。                                   |
| /proc/     | 虚拟文件系统，该目录数据不保存到硬盘中，而是保存到内存中。主要保存系统的内核、进程。 |
| /sys/      | 虚拟文件系统。和proc蕾丝保存内核相关信息                     |
| /root/     | 超级用户的家目录。                                           |
| /srv/      | 服务数据目录。一些系统服务启动之后，可以在这个目录中保存所需要的数据。 |
| /tmp/      | 临时目录。系统存放临时文件的目录。                           |
| /usr/      | 系统软件资源目录。是Unix Software Resource的缩写，不是存放用户数据，而是存放系统软件资源的目录。 |
| /var/      | 动态数据保存位置。主要保存缓存、日志以及软件运行产生的文件。 |

## linux常用命令

### 命令格式

格式：命令 [-选项] [参数]

例：ls -la /etc

说明：

1.个别命令使用不遵循此格式

2.当有多个选项时，可以写一起

3.简化选项与完整选项 -a等于--all

### 目录处理命令

-   目录处理命令：**ls**，显示目录文件

英文原意：**l**i**s**t

语法：ls [-alhdi] [文件或目录]

选项：

```
-a 显示所有文件，包括隐藏文件 all

-l 详细信息显示 long

-h 人性化显示 human

-d 查看当前目录属性 directory

-i 查看任何文件的i节点 id

```

其中ls -l显示的第一列为：-rw-r--r--，分为两部分

```
1.文件类型：
	-：二进制文件
	d：目录
	l：软连接文件
2.权限：
	rw- ：u：所有者
	r--：g：所属组
	r--：o：其他人
	r：读read
	w：写write
	x：执行execute
```

-   目录处理命令：**mkdir**，创建目录

英文原意：**m**a**k**e **dir**ectories

语法：mkdir -p [目录名]

选项：

```
-p：递归创建
```

例：

```
mkdir /tmp/a/b #若a未创建，则会报错
mkdir -p /tmp/a/b #使用-p递归创建
mkdir /tmp/a/c /tmp/a/d #同时创建
```

-   目录处理命令：**cd**，切换目录

英文原意：**c**hange **d**irectory

语法：cd [目录]

例：

```
cd /tmp/a/b #切换到指定目录
cd .. #返回上级目录
```

-   目录处理命令：**pwd**，显示当前目录

英文原意：**p**rint **w**orking **d**irectory

语法：pwd

-   目录处理命令：**rmdir**，删除空目录

英文原意：**r**e**m**ove empty **dir**ectories

语法：rmdir [目录名]

-   目录处理命令：**cp**，复制目录

英文原意：**c**o**p**y

语法：cp -rp [原文件或目录] [目标目录]

选项：

```
-r：复制目录
-p：保留文件属性，如文件修改时间
```

例：

```
cp -r /tmp/a/b /root #将/tmp/a/b复制到/root下
cp -rp /tmp/a/b /tmp/a/c /root #将b和c复制到/root下，保持目录属性
cp -r /tmp/a/b /root/d #可以复制的同时重命名目录
```

-   目录处理命令：**mv**，剪切目录、改名

英文原意：**m**o**v**e

语法：mv [原文件或目录] [目标目录]

例：

```
mv /tmp/a/b /root #剪切b到root
mv /tmp/a/b /root/c #剪切并改名
mv /tmp/a/b /tmp/a/c #改名
```

-   目录处理命令：**rm**，删除文件

英文原意：**r**e**m**ove

语法：rm -rf [文件或目录]

选项：

```
-r：删除目录
-f：强制执行
```

### 文件处理命令

-   文件处理命令：**touch**，创建空文件

语法：touch [文件名]

例：

```
touch /root/a/b.list
```

-   文件处理命令：**cat**，显示文件内容

语法：cat -n [文件名]

选项：

```
-n：显示行号
```

-   文件处理命令：**tac**，反向显示文件内容

语法：tac -n [文件名]

-   文件处理命令：**more**，分页显示文件内容

语法：more [文件名]

操作：

```
空格 或 f：翻页
enter：换行
q 或 Q：退出
```

-   文件处理命令：**less**，分页显示文件内容，可向上翻页

语法：less [文件名]

操作：

```
空格 或 f：翻页
enter：换行
pageup：按页向上翻
上键：向上一行
/+关键词：搜索关键词，按n显示下一个
q 或 Q：退出
```

-   文件处理命令：**head**，显示文件前几行

语法：head -n [文件名]

例：

```
head -n 10 /etc/services #显示前十行
```

-   文件处理命令：**tail**，显示文件末尾几行

语法：tail [-nf] [文件名]

选项：

```
n：显示几行
f：动态显示
```

-   文件处理命令：**ln**，生成链接文件

语法：ln -s [源文件] [目标文件]

选项：

```
-s 创建软链接
```

例：

```
ln -s /etc/issue /tmp/issue.soft #创建issue的软链接
ln /etc/issue /tmp/issue.hard #创建issue的硬链接
```



### 文本编辑器vim

常用操作

| 命令            | 作用                                   |
| --------------- | -------------------------------------- |
| :w              | 保存修改                               |
| :w new_filename | 另存为                                 |
| :wq             | 保存修改并退出                         |
| ZZ              | 快捷键，保存修改并退出                 |
| :q!             | 不保存修改退出                         |
| :wq!            | 保存修改并退出，文件所有者及root可使用 |
| a               | 在光标所在字符后插入                   |
| A               | 在光标所在行尾插入                     |
| i               | 在光标所在字符前插入                   |
| I               | 在光标所在行行首插入                   |
| o               | 在光标下插入新行                       |
| O               | 在光标上插入新行                       |
| :set nu         | 设置行号                               |
| :set nonu       | 取消行号                               |
| gg              | 到第一行                               |
| G               | 到最后一行                             |
| nG              | 到第n行                                |
| :n              | 到第n行                                |
| $               | 移到行尾                               |
| 0               | 移到行首                               |
| x               | 删除光标所在处的字符                   |
| nx              | 删除光标所在处后n个字符                |
| dd              | 删除光标所在行，ndd删除n行             |
| dG              | 删除光标所在行到文件末尾内容           |
| D               | 删除光标所在处到行尾内容               |
| :n1,n2d         | 删除指定范围的行                       |
