---
title: 技能点-R语言绘图基础
author: Lin Gui
date: '2021-09-11'
slug: 技能点-r语言绘图基础
categories:
  - 学习
tags:
  - 技能点
---
## day1

#安装包
install.packages('ggplot2')
#查看包版本
library(ggplot2)
#升级包
update.packages()

#可以用?c来查看c的文档
#创建一个数组v
v=c(1,4,4,3,2,2,3)
#返回v的第2，3，4位上的元素
v[c(2,3,4)]
#返回v的第2到4位的元素
v[2:4]
#返回v的第2，4，3位上的元素
v[c(2,4,3)]
#删除v的第2位元素
v[-2]
#删除v的第2到第4位元素
v[-2:-4]
#返回小于4的元素
v[v<4]
#返回v等于3的位置
which(v==3)
#返回数组的最大值
which.max(v)

#产生随机数
set.seed(250)
a=runif(3,min=0,max=100)
#rnorm()正态分布随机数,默认mean=0，sd=1
a=rnorm(3)
#向下取整
floor(a)
#进一
ceiling(a)
#四舍五入到几位小数，
round(a,3)

#读文件
data1=read.csv(file='./test.txt')
data2=read.table
data3=read.csv("http://www.macalester.edu/~kaplan/ISM/datasets/swim100m.csv")
#将列名当作变量名使用
attach(data3)
sex

#作图
set.seed(123)
x=rnorm(100,100,10)
set.seed(234)
y=rnorm(100,100,10)
#柱状图,breaks是柱子个数
hist(x,breaks=20,col='#aaccff')
#密度图，先用density求出x的密度
plot(density(x))
#散点图
plot(x,type = 'p')
plot(x,type = 'l')
#箱线图
boxplot(x,y)
boxplot(time~sex)
#Quantile-Quantile plot
qqnorm(x)
qqline(x)
qqplot(x,y)

## day2
# 数据集结构包括 vector，matrix,array,data frame,list
### vector,向量，一维的数组，可以放数字，字符串，布尔值
a=c(1,2,4,5,2,-2,-3)
b=c("one","two","three")
c=c(TRUE,FALSE,TRUE)

### matrix,矩阵,是个二维数组
x= matrix(1:20,nrow=5,ncol=4,byrow=TRUE)
x
y= matrix(1:20,nrow=5,ncol=4,byrow=FALSE)
y
#第1行
x[1,]
#第1列
x[,1]
#第2行第4列的元素
x[2,4]
#第2行的第2，4个元素
x[2,c(2,4)]
#第3到5行的第2个元素
x[3:5,2]
rnames=c("apple","banana","orange","melon","corn")
cnames=c("cat","dog","bird","pig")
x=matrix(1:20,nrow = 5,ncol=4,byrow=TRUE)
rownames(x)=rnames
colnames(x)=cnames
x

### array，多维矩阵
arr1=c("A1","A2")
arr2=c("B1","B2","B3")
arr3=c("C1","C2","C3","C4")
arr4=c("D1","D2","D3")
z=array(1:72,c(2,3,4,3),dimnames = list(arr1,arr2,arr3,arr4))
z
z[1,2,3,]

### data frame
patientID =c(1,2,3,4)
age=c(25,34,28,52)
diabetes=c("Type1","Type2","Type1","Type1")
status=c("Poor","Improved","Excellent","Poor")
patientdata=data.frame(patientID,age,diabetes,status)
patientdata
# 前2列的内容
patientdata[1:2]
patientdata[1:3]
patientdata[1,1:3]
patientdata[c(1,3),1:3]
#swim也是data frame格式
swim=read.csv("http://www.macalester.edu/~kaplan/ISM/datasets/swim100m.csv")

### attach,将列名转为变量名，detach，将表中变量名删除
attach(mtcars)

### list
mylist=list(patientdata,swim,x)
mylist

#graph, 作图
### par,用c的参数设定网格,可以放几个图
par(mfrow=c(2,2))
### plot
#pch设定点的形状
plot(rnorm(50),pch=17)
#lty设定线的类型
plot(rnorm(20),type="l",lty=4)
#cex设定点大小
plot(rnorm(100),cex=0.5)
#lwd设置线宽度
plot(rnorm(200),lwd=2)

par(mfrow=c(1,1))
plot(rnorm(20),pch=11)
#title设置标题
title(main="normal list")
#axis设置轴的什么东西没懂，轴的名字要在plot中设定
?axis
axis(2, at = 5*(0:20), las = 1, gap.axis = 1/4)
#legend,说明点的作用
?legend
legend("bottom","(x,y)", pch=2, title= "bottom")

#layout,和par类似，第一个matrix划分图占的位置
?layout
attach(mtcars)
#1，1第一个图占第一行的两个，第二行的两个位置给2，3，相当于合并单元格
layout(matrix(c(1,1,2,3),2,2,TRUE))
hist(wt)
hist(mpg)
hist(disp)
detach(mtcars)

## day3
x=matrix(1:20,nrow = 5,ncol = 4,byrow = TRUE)
swim=read.csv("http://www.macalester.edu/~kaplan/ISM/datasets/swim100m.csv")
mylist=list(swim,x)
mylist[[2]][2]
mylist[[2]][1:2]
mylist[[2]][1:2,3]
mylist[[2]][1:2,]

# 操作符
# > >= < <= == != | &
for(i in 1:10){
    print(i)
}

while(i<=10){
    print(i)
    i=i+1
}


i=1
if(i==1){
    print("hello world")
}

feelings=c("sad","afraid")
for(i in feelings){
    print(
        switch(i,
        happy="i am glad you are happy",
        afraid="there is nothing to fear",
        sad="cheer up",
        angry="calm down now"
    )
    )
}

myfunction=function(x,a,b,c){
    return(a*sin(x)^2-b*x+c)
}
curve(myfunction(x,20,3,4),xlim=c(1,20))

## day4
install.packages("vcd")
library(vcd)
counts=table(Arthritis$Improved)
counts
par(mfrow=c(2,2))
barplot(counts,main="Simple Bar Plot",xlab="Improvement",ylab="Frequency")
barplot(counts,main="Horizontal Bar Plot",xlab="Frequency",ylab="Improvement",horiz=TRUE)

counts <- table(Arthritis$Improved,Arthritis$Treatment)
counts
# 柱状图
barplot(counts,main="Stacked Bar Plot",xlab="Treatment",ylab="Frequency",col=c("red","yellow","green"),legend=rownames(counts))
barplot(counts,main="Grouped Bar Plot",xlab="Treatment",ylab="Frequency",col=c("red","yellow","green"),legend=rownames(counts),beside=TRUE)

#饼图
install.packages("plotrix")
library(plotrix)
par(mfrow=c(2,2))
slices <- c(10,12,4,16,8)
lbls  <- c("US","UK","Australia","Germany","France")
#edges 方格大小，radius 图片半径
pie(slices,labels = lbls,main="Simple Pie Chart",edges=300,radius=1)
#用饼图观察比例
pct <- round(slices/sum(slices)*100)
lbls2 <- paste(lbls," ",pct,"%",sep="")#paste可以将字母连接起来
pie(pct,labels = lbls2,col=rainbow(length(lbls2)),main="Pie Chart with Percentages",edges=300,radius=1)
#3D的饼图，explode让饼分开
pie3D(slices,labels = lbls,explode=0.5,main="3D Pie Chart",edges = 300,radius=1)
mytable <- table(state.region)
lbls3 <- paste(names(mytable),"\n",mytable,esp="")
pie(mytable,labels=lbls3,main="Pie Chart from a Table\n(with sample size)",edges = 300,radius = 1)

#扇形图
slices <- c(10,12,4,16,8)
lbls  <- c("US","UK","Australia","Germany","France")
fan.plot(slices,labels = lbls,main="Fan Plot")

#散点图
dotchart(mtcars$mpg,labels=row.names(mtcars),cex=0.7,main="Gas Mileage for Car Models",xlab="Miles Per Gallon")

#摘要
mtcars
head(mtcars)#打印前6个
summary(mtcars)

#表格
attach(mtcars)
table(cyl)
summary(mpg)
#cut 区间的频率
table(mpg)
table(cut(mpg,seq(10,34,by=2)))

#correlation
states=state.x77[,1:6]
cov(states)
var(states)
cor(states)

#T检验
x=rnorm(100,mean=10,sd=1)
y=rnorm(100,mean=30,sd=10)
t.test(x,y,alt="two.sided",paired=TRUE)

#wilcoxon test
wilcox.test(x,y,alt="less")

## day 5
#矩阵匀运算
set.seed(123)
A=matrix(sample(100,15),nrow=5,ncol=3)
set.seed(234)
B=matrix(sample(100,15),nrow=5,ncol=3)
set.seed(321)
X=matrix(sample(100,25),nrow=5,ncol=5)
set.seed(213)
b=matrix(sample(100,5),nrow=5,ncol=1)
A
B
X
b
#矩阵加减乘除
A+2
A*2
A^2 #平方

#矩阵的乘法 %*%
#t()转置
t(A) %*% B

#平均数
colMeans(A)
rowMeans(A)
#和
colSums(A)
rowSums(A)

#叉乘 相当于t(x) %*% y
crossprod(A)
crossprod(A,B)
#相当于x %*% t(y)
tcrossprod(A)
A %*% t(A)

# 求矩阵的逆
solve(X)
#用solve解 b=Ax 的x
v=solve(X,b)
v

#返回矩阵的对角线
diag(X)
#创建一个对角线上是1，2，3，4的矩阵
diag(c(1,2,3,4))
#创建一个对角线为1的5维矩阵
diag(5)

#返回特征值和特征向量
eigen(X)

## day6
#factor 标记
factor= factor(rep(c(1:3),times=5))
factor

X=sample(100,15)
?tapply
tapply(X,factor,mean)
rbind(X,factor)

boo=rbind(X,factor)[2,]==2
which(boo)
rbind(X,factor)[1,which(boo)]
sum(rbind(X,factor)[1,which(boo)])/length(which(boo))
