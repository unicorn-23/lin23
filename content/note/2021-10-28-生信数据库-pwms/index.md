---
title: 生信数据库-PWMs
author: Lin Gui
date: '2021-10-28'
slug: 生信数据库-pwms
categories:
  - 学习
tags:
  - 生信数据库
---

学习资料：汪国华老师生物信息第二次课。

------

Databases of PWM。

-   [Transfac](https://genexplain.com/transfac/)：商业。
-   [Jaspar](https://jaspar.genereg.net)
-   [CisGenome](https://www.biostat.jhsph.edu/~hji/cisgenome/)：开源的。

------

Transfac中包含了几个不同的表

| Table     | Description                                                  | Entries |
| --------- | ------------------------------------------------------------ | ------- |
| Factor    | 记录转录因子的一些信息，比如序列信息、对应的基因、不同物种中基因名。 |         |
| Gene      | 转录因子对应基因的注释信息                                   |         |
| Site      | 转录因子结合的序列                                           |         |
| ChIP-chip |                                                              |         |
| matrix    | 每个转录因子的矩阵                                           |         |
| class     | 将转录因子分类                                               |         |
| cell      | 不同组织转录因子结合的位置不同                               |         |
| reference |                                                              |         |



老师以AP1为例，可以看到，有矩阵代码和转录因子名，可以通过这些来搜索相应的位置频率矩阵。

![image-20211027211022535](../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027211022535.png)

1、进入官网。点击Search for TF来搜索。

![image-20211027210635715](../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027210635715.png)

2、可以通过输入转录因子名，来搜索。

![image-20211027210746511](../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027210746511.png)

或者用Matrix输入矩阵代码也可以搜到。

<img src="../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027210829103.png" alt="image-20211027210829103" style="zoom:50%;" />

输入M00925，选择Matrix来搜索。

![image-20211027211419209](../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027211419209.png)

点击T0029，可以看到。

![image-20211027211508213](../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027211508213.png)

但这个网站是商业的，要注册码？打不开Matix，只能看到这个页面。

需要购买。

**一个转录因子有可能是一个蛋白，也有可能是几个蛋白聚集在一起，构成蛋白质复合物，然后去调控基因表达。**

比如AP1这个转录因子，是两个蛋白质的复合物，JUN和FOS两个基因组合构成AP1转录因子？？？？这两个蛋白构成这个转录因子。

<img src="../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027212114477.png" alt="image-20211027212114477" style="zoom:50%;" />

将位置频率矩阵转换为位置权重矩阵，

<img src="../2021-10-27-生信数据库-pwms-transfac/index.assets/image-20211027212415337.png" alt="image-20211027212415337" style="zoom:50%;" />

老师将，所有2w+序列的起始位点上游前1000bp用位置权重矩阵进行计算，

1000bp，转录因子长度为8，共993个得分，反链也有998个，共998\*2\*2w个得分，成正态分布。

得分越高，AP1越有可能结合在这个位置。
