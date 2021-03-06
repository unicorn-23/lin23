---
title: 技能点-matplotlib基础
author: Lin Gui
date: '2021-09-02'
slug: 技能点-matplotlib基础
categories:
  - 学习
tags:
  - 技能点
---
# matplotlib基础

## 折线图

### 基本运用

```python
from matplotlib import pyplot as plt # 导入pyplot
x=range(2,26,2)
y=[15,13,14.5,17,20,25,26,26,24,22,18,15]
plt.plot(x,y) # 通过plot绘制折线图
plt.show() # 展示图像
```
### 设置图形画布大小

```python
# 实例化一个figure对象，参数figsize设置图片宽高，dpi可以让图片清晰
fig=plt.figure(figsize=(20,8),dpi=80)
```

### 存储图片

```python
plt.savefig("./set_size.png") # 存储图片到路径
```

### 设置图形坐标轴

```python
# 设置x轴的刻度
# xticks(ticks,[labels],**kwargs)
# 参数ticks设置刻度间隔，labels设置刻度信息，其余可传rotation旋转角度，color颜色
plt.xticks(range(2,25),rotation=60,color="blue")
# 设置x轴间隔为0.5
xtick_label=[i/2 for i in range(2,49)]
plt.xticks(xtick_label)
# 设置y轴的刻度
plt.yticks(range(min(y),max(y)+1))
```

### matplotlib显示中文问题

```python
# 需要写在plt.plot(x,y)前
plt.rcParams["font.family"] = 'Arial Unicode MS'
```

### 添加描述信息

```python
plt.xlabel("x轴")
plt.ylabel("y轴")
plt.title("标题")
```

### 设置网格

```python
# alpha设置网格透明度
plt.grid(alpha=0.4)
```

### 添加图例

```python
# label参数用于标记
plt.plot(x,a,label="线a")
plt.plot(x,b,label="线b")
# legend将label添加到图例
# 参数loc由upper/lower 与 left/right/center组合，设置图例位置
plt.legend(loc="upper left")
```

### 设置线条样式

```python
# linestyle -实线 --虚线 -.点划线 :点虚线
plt.plot(x,y,color="orange",linestyle="--",linewidth=5,alpha=0.5)
```

## 散点图

```python
plt.scatter(x,y)
```

## 条形图

```python
plt.bar(x,y)
```

### 多条条形图时

```python
from matplotlib import pyplot as plt
a=["one","two","three"]
b_1=[1,2,3]
b_2=[2,3,4]
b_3=[3,4,5]
# 若要b_1,2,3并排展示，可以在plt.bar中width设置条形宽度，并使b_2,3向后移动相应条形宽度，最后在plt.xticks中设置x轴刻度信息
x_1=list(range(len(a)))
x_2=[i+0.2 for i in x_1]
x_3=[i+0.2 for i in x_2]
plt.bar(x_1,b_1,width=0.2)
plt.bar(x_2,b_2,width=0.2)
plt.bar(x_3,b_3,width=0.2)
plt.xticks(x_2,a)
plt.show()
```



### 横着的条形图

```python
# barh中线条宽度weight变为height
plt.barh(x,y)
```

## 直方图

```python
# hist中参数bins设置组数
# 通过(数据的最大值-最小值)//组距获得组数
# 数据在100以内通常分为5-12组
bin_width=3 # 设置组距
bins=int((max(a)-min(a))//bin_width) # 组数=极差/组距
# density设置显示频数或频率，0为频数，1为频率或用布尔值
plt.hist(x,bins,density=0)

```