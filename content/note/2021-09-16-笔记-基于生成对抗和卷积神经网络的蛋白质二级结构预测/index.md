---
title: 笔记-基于生成对抗和卷积神经网络的蛋白质二级结构预测
author: Lin Gui
date: '2021-09-16'
categories:
  - 学习
tags:
  - 笔记
slug: 笔记-基于生成对抗和卷积神经网络的蛋白质二级结构预测
---

## 需学习

-   [ ] [生成对抗](https://www.bilibili.com/video/BV1Wv411h7kN?spm_id_from=333.788.b_636f6d6d656e74.6)，李宏毅的课


-   [x] [神经网络](https://www.bilibili.com/video/av66314465?spm_id_from=333.788.b_636f6d6d656e74.4)
-   [x] [卷积神经网络](https://www.bilibili.com/video/av66646276?spm_id_from=333.788.b_636f6d6d656e74.7)
-   [ ] [BLAST使用](https://www.bilibili.com/video/BV16t4y1v7ZN?from=search&seid=17654661102206372449&spm_id_from=333.337.0.0)
-   [ ] [pytorch](https://tangshusen.me/Dive-into-DL-PyTorch/)

## 知识点

### BLAST搜索——生物信息学——双序列比对，详见思维导图

Basic Local Alignment Search Tool 基本局部比对搜索工具

原理：两个给定序列中的一对子序列，他们的长度相等，且可形成无空位的完全匹配

1.  首先找出探测序列和目标序列间所有的匹配程度超过一定阈值的序列片段对

2.  然后对片段对根据给定的相似性阈值进行延伸，得到一定长度的相似性片段最后给出高分值片段对（high-scoring pairs，HSPs）


BLAST是综合在一起的一组工具的统称

-   Blastp 用蛋白质序列搜索蛋白质序列数据库，用于确定查询的氨基酸序列在蛋白数据库中找到相似的序列。

-   Blastn 用核酸序列搜索核酸序列数据库

-   Blastxt 将核酸序列按6条链翻译成蛋白质序列后搜索蛋白质序列数据库

-   blastnt 用蛋白质序列搜索核酸序列数据库，数据库中的核酸序列要按6条链翻译成蛋白质序列 后再搜索

-   blastx 将核酸序列按6条链翻译成蛋白质序列后搜索核酸序列数据库，数据库中的核酸序列要 按6条链翻译成的蛋白质序列后再搜索

按搜索算法分

-   标准BLAST

-   PSI-BLAST：

    位点特异性迭代BLAST，是一种更加高灵敏的Blastp程序，对于发现远亲物种的相似蛋白或某个蛋白家族的新成员非常有效。

    每次使用位置特异权重矩阵（Position-Specific Scoring Matrix，PSSM）搜索数据库后，再利用搜索的结果重新构建PSSM，然后用新的PSSM再次搜索数据库，知道没有新的结果产生为止。

-   PHI-BLAST


# 复现

## abstract

首先，看一下**Abstract**，获取到的信息是：本文主要讲使用生成对抗网络和卷积神经网络模型，对蛋白质二级结构进行预测。流程主要是：首先生成对抗网络提取蛋白质特征，然后将提取的特征与原始PSSM（打分矩阵）数据相结合，作为卷积神经网络的输入，得到预测结果。测试集为CASP9、CASP10、CASP11、CASP12、CB513和PDB25。

## introduction

**Introduction**介绍了一下为什么研究蛋白质二级结构，简述机器学习不足之处（特征提取依赖于经验），引出深度学习，介绍了其他人的研究情况，告诉我们本文将用生成对抗网络来提取氨基酸残基的特征（创新点？），并将提取的特征与原始蛋白质特征进行融合，然后发送到卷积神经网络进行蛋白质二级结构预测。

## model and data

好的！看一下第三部分**Model and Data**。

-   [ ] 第一个问题是：

```
问题1:
The PSI-BLAST parameter is set to a threshold of 0.001 and 3 iterations to obtain a 20*M PSSM matrix, where M is the length of the amino acid sequence and 20 represents the number of amino acid types.

将PSI-BLAST参数设置为阈值0.001，并进行3次迭代，以获得20*M PSSM矩阵，其中M是氨基酸序列的长度，20代表氨基酸类型的数量。
```

获取PSSM矩阵（相关BLAST概念放在[笔记](/note/2021/09/16/基于生成对抗和卷积神经网络的蛋白质二级结构预测之笔记/)中），首先要获取相关fasta序列，看一下问题2:

-   [x] 第二个问题是：

```
问题2:
In this paper, the ASTRAL and CullPDB datasets were used as the training set of the model. 
本文使用ASTRAL和CullPDB数据集作为模型的训练集。

The test set used CASP data set, including CASP9, CASP10, CASP11 and CASP12. In addition, the CB513 and PDB25 data sets are also used as the test set of the model
测试集使用CASP数据集，包括CASP9、CASP10、CASP11和CASP12。此外，CB513和PDB25数据集也用作模型的测试集
```

现在的任务是获取这几个训练集和测试集，首先尝试在[uniprot](https://www.uniprot.org)来获取蛋白质序列，似乎没有这么简单。尝试百度获得cullpdb相关，发现可以点开文章的引用链接到相关文章，在相关文章中寻找。

-   [x] 1、[CullPDB相关文章](https://blog.csdn.net/qq_34218255/article/details/83114285) [cullPDB datasets](https://www.princeton.edu/~jzthree/datasets/ICML2014/)

-   [x] 2、[ASTRAL](http://scop.berkeley.edu/astral/ver=2.07)，该数据集需要使用魔法下载，[ASTRAL datasets](http://scop.berkeley.edu/astral/ver=2.07)

-   [x] 3、[CASP](https://predictioncenter.org/download_area)，[CASP datasets](https://predictioncenter.org/download_area/)

-   [x] 4、[PDB25相关文章](https://onlinelibrary.wiley.com/doi/epdf/10.1002/pro.5560030317)需要通过学校VPN进入文章，并找不到数据集。[最新](http://biomine.cs.vcu.edu/datasets/SCPRED/SCPRED.html)，还是google好用。[PDB25 dataset](http://biomine.cs.vcu.edu/datasets/SCPRED/25PDB.csv)

-   [x] 5、[CB513相关文章](https://onlinelibrary.wiley.com/doi/10.1002/(SICI)1097-0134(19990301)34:4%3C508::AID-PROT10%3E3.0.CO;2-4)，无，找不到，[终于在github中找到](https://github.com/songlab-cal/tape/blob/master/README.md#lmdb-data)。

小结搜索方法：

1.  通过文献引用的文章找到相关数据集
2.  百度
3.  在web of science上搜索关键字
4.  google

当前任务是：学习卷积神经网络、处理数据、生成对抗网络

-   [x] 学习卷积神经网络

-   [x] 处理数据

-   [ ] 生成对抗网络
-   [x] 构建模型