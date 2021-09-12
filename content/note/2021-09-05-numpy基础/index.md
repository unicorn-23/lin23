---
title: numpy基础
author: Package Build
date: '2021-09-05'
slug: numpy基础
categories:
  - 学习
tags:
  - Python
  - numpy
---
# numpy基础

### 创建数组

```python
#首先import一下numpy包
import numpy as np
#生成数组，numpy.ndarray类型
a1=np.array([0,1,2,3])
a2=np.array(range(10))
a3=np.arange(10)
#生成全0数组
np.zeros((1,2)).astype(int)
#全1数组
np.ones((1,2)).astype(int)
#方阵,对角线为1
np.eye(10)
```

### 数据类型

Int8、uint8 有符号和无符号的8位整型(一个字节)

Int16、uint16 (两个字节)

Int32、uint32 (4个字节)

Int64、uint64 (8个字节)

float16 半精度浮点数

float32 单精度浮点数

float64 双精度浮点数

float128 扩展精度浮点数

Complex64、complex128、complex256 用2个32位浮点数表示复数

bool 布尔值

```python
#使用a.dtype查看
#创建数组时指定数据类型
a1=np.array([1,0,1,0],dtype=np.bool)
#修改数组的数据类型
a1.astype(np.int8)
#修改浮点型的小数位数，用np.round()
a2=np.array([random.random() for i in range(10)]) #生成是个小数
np.round(a2,2) #取两位小数
```

### 数组的形状

```python
#使用a.shape查看数组形状
a1=np.array([0,1,2,3,4,5,6,7,8,9])
print(a1.shape) #返回(10,)
a2=np.array([1,2,3],[4,5,6])
print(a2.shape) #返回(2,3)
#使用a.reshape()修改数组的形状,参数传一个元组
a3=np.array(24).reshape((2,3,4))
#将数组变成一维的 方法一
a4=a3.reshape((a3.shape[0]*a3.shape[1],))
#方法二
a4=a3.flatten()
```

###  数组的计算

```python
a=np.array(range(24)).reshape((4,6))
#可以对a整体进行计算操作
print(a+2)
print(a/0)#会返回 nan not a number 及inf infinity无穷
#数组和数组计算，形状相同，对应位置的数进行计算
#一个数组多行，另一个一行，且列数相同，则每位按列计算
#一个数组多列，另一个一列，且行数相同，则每位按行计算
```

### 轴

在numpy中可以理解为方向，使用0，1，2表示，对于一个一位数组，只有0轴；对于二维数组，有0和1轴；对于三位数组有0，1，2轴。

有了轴的概念后，可以指定数组哪个方向的数字进行计算

在np.arrage(10).reshape((2,5))中reshape中的2表示0轴的长度，5表示1轴的长度

### 读取数据

```python
np.loadtxt(frame,dtype=np.float,delimiter=None,skiprows=0,usecols=None,unpack=False)
#参数 frame 文件路径
#dtype 数据类型
#delimiter 分割字符串
#skiprows 跳过前几行
#usecols 读取指定的列
#umpack True时，读入属性将分别写入不同数组变量，False读入数据只写入一个数组变量，默认false。当umpack为True时，可以起到转置的效果
```

### 数组的转置

```python
#二维数组的转置
a=np.arange(18).reshape(3,6)
#方法一
a.transpose()
#方法二
a.swapaxes(1,0) #交换0，1轴
#方法三
a.T
```

### 数据的索引和切片

```python
a=np.arange(12).reshape(3,4)
a[1]#取指定行
a[1:]#取连续多行
a[[0,2]]#取不连续的多行
#[a:b,c:d]
#a:b为行，c:d为列，逗号前为行，逗号后为列
a[:,1]#取指定列
a[1:2,3:4]#取第2行到第3行的第4列到第5列
a[2,3]#指定数
a[[0,2,0],[1,3,3]]#取不相邻的点
```

### 数值的修改

```python
a[:,2:4]=0#指定位置修改
a<10#返回一个布尔类型的数组，符合条件的为True
a[a<10]=0#a中为True的数据进行修改
#where numpy的三元运算符
np.where(a<10,0,10)
#clip 裁剪
a.clip(3,9)#将数组中小于3的替换为3，将大于9的替换为9
```

### 数组的拼接

```python
np.vstack((t1,t2))#竖直拼接，t1在上t2在下
np.hstack((t1,t2))#水平拼接，t1在左t2在右
```

### 交换数组的行列

```python
a[[1,2],:]=t[[2,1],:]#行交换
a[:[0,2]]=a[:[2,0]]#列交换
```

### 一些方法

```python
np.argmax(a,axis=0)#获取行中最大值的位置
np.argmin(a,axis=0)#获取行中最小值的位置
np.random.rand(2,3)#均匀分布的随机数数组，浮点数，从0-1
np.random.randn(2,3)#标准正态分布的随机数，浮点数，平均数0，标准差1
np.random.randint(low,high,(shape))#给定范围，和形状的随机数
np.random.uniform(low,high,(shape))#均匀分布的数组
np.random.normal(loc,scale,(shape))#指定正态分布中随机抽取样本，分布中心是loc（概率分布的均值），scale是标准差
np.randome.seed(s)#随机数种子，给定随机数种子，可以每次生成相同的随机数
```

### 复制数组

```
a=b
a=b[:]，视图，a的数据由b保管
a=b.copy()，复制，ab不影响
```

### nan和inf

1.  读取的文件为float时，如果有缺失，会出现nan
2.  做了不适合的计算，比如inf减去inf，出现nan
3.  除以零时inf（infinity无穷）

```python
#1.两个nan是不相等的
#2.替换nan为0
#可以用np.isnan()判断
a[np.isnan(a)]=0
#3.获取数组中nan的个数
#利用np.nan!=np.nan返回True
np.count_nonezero(a!=a)
```

### 统计函数	

```python
#求和
a.sum(axis=None)
#均值
a.mean(a,axis=None)
#中值
np.median(a,axis=None)
#最大值
a.max(axis=None)
#最小值
a.min(axis=None)
#极值
np.ptp(a,axis=None)
#标准差
a.std(axis=None)
标准差是一组数据平均值分散程度的度量,标准差较大,代表大部分数值和其平均值差异大,越大代表数据波动情况不稳定
```

