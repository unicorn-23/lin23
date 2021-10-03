---
title: 技能点-R语言基础
author: Lin Gui
date: '2021-09-11'
slug: 技能点-r语言基础
categories:
  - 学习
tags:
  - 技能点
---
找到了大佬的[r语言文档](https://www.math.pku.edu.cn/teachers/lidf/docs/Rbook/html/_Rbook/index.html)，直接看文档吧

## 逻辑操作

### 判断语句
```R
#1. if语句
#2. if..else
#3. switch
#switch分整数和字符串
switch(3,case1,case2,case3)#整数直接返回3号位的case
switch("s2",s1="str1",s2="str2")#字符串返回字符串对应的值
```
### 循环
```R
#1. repeat{},需要使用break退出
#2. while(){}
#3. for(value in vector){}
#退出当前循环break，跳过当前循环next
```

## 数据相关
### 数据类型
1. 向量vector
2. 列表list
3. 矩阵matrix
4. 数组array
5. 因子factor
6. 数据框data.frame

1.向量
```R
#创建向量
#使用c()函数创建向量
v=c(3,4)#获得二维向量(3,4)
v=c(1:4)#生成1-4的连续序列
#使用seq()函数创建等差数列
v=seq(1,9,2)#生成等差数列
v=seq(1,10,length.out=4)#生成1-10中等差的4个数
#使用rep()函数创建重复序列
rep(0,5)#0 0 0 0 0

#NA和NULL
#NA表示缺失，没有值但占位，NULL表示不存在

#向量中元素的操作
v[1:3]#取出v中1-3位的元素，R中的下标没有偏移量
v[c(1,2,4)]#取出v中在位置1，2，4上的元素
v[c(-1,-4)]#删除v中在位置1，4上的元素

#向量逻辑操作
v[v<3]#返回小于3的元素
which(v==3)#返回v中等于3的元素
all()#检查是否全为True
any()#检查是否含有True

#向量的运算
#标量运算
#+ - * / ...
#相同维度的向量之间可以运算

#向量排序
sort(v)#排序
rev(v)#反转
v[order(v)]#排
order(v)#返回排序后元素的下标

#统计函数
sum(v)#和
mean(v)#平均值
var(v)#方差
sd(v)#标准差
min(v)#最小值
max(v)#最大值
range(v)#返回a的取值范围

#字符串的操作
toupper("ABcd")#转换为大写
tolower("ABcd“)#转换为小写
substr("abcdef",1,4)#截取1-4的字符串
substring("abcdef",5)#截取从5开始的字符串
as.numeric("123")#字符串转化为数字
as.character(12.34)#数字转为字符串
strsplit("2021-9-11","-")#分隔符拆分字符串
gsub("/","-","2021-9-11")#替换字符串
```
2.矩阵
```R
vector=c(1,2,3,4,5,6)
matrix(vector,2,3)#传入一个向量，按列填充
matrix(vector,2,3,byrow=TRUE)#按行填充
#设置矩阵行列的名称
colnames(m)=c("x","y","z")#列名
rownames(m)=c("a","b")#行名
#矩阵运算
m1 %*% m2 #矩阵乘法
solve(m1) #逆矩阵
apply(m1,1,sum) #apply函数，第一个参数传入矩阵，第二个参数为1时按行操作，2时按列操作，第三个参数为需要进行的操作
```
## 文件相关
### 输出函数
```R
#1.print() print支持数值和字符串的输出
#2.cat() cat可以将数值字符串拼接，两个拼接的元素之间有空格
#cat可以直接写入进文件，为覆盖写入，如果添加属性append=True，则变为追加写入
cat("content",file="path",append=True)
```
### 输入函数
```R
readLines("path")#读取文件中的内容为字符串

```
###工作路径
```R
getwd()#获取当前工作目录
setwd()#设置当前工作路径
```
