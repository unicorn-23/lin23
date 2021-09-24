---
title: 基于生成对抗和卷积神经网络的蛋白质二级结构预测之笔记
author: Package Build
date: '2021-09-16'
slug: 基于生成对抗和卷积神经网络的蛋白质二级结构预测之笔记
categories:
  - 学习
tags:
  - 生物信息
  - 神经网络
  - 文献
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

