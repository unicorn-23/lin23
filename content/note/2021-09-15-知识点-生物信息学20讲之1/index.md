---
title: 知识点-生物信息学20讲之1
author: Lin Gui
date: '2021-09-15'
categories:
  - 学习
tags:
  - 知识点
slug: 生物信息学20讲之1
---

[资料来源](https://www.bilibili.com/video/BV1of4y1i7uW?from=search&seid=6901614588662867571&spm_id_from=333.337.0.0)，好像学习路径有点歪，暂时不更。

## 环状RNA简介

### 环状RNA，circRNA

环状RNA是mRNA在剪接的过程中，上游exon的5’端与下游exon的3’端剪接到一起，从而形成首尾相连的环状RNA分子。

### circRNA特点

-   大多数定位于细胞质，且序列高度保守。
-   比线性RNA更稳定，不易被降解。
-   许多circRNA表达水平与线性RNA的表达水平相当，一些circRNA的表达水平甚至超过他们的线性异构体10倍。
-   大多数来自蛋白质编码基因的外显子。
-   大部分是非编码RNA（noncoding RNA，ncRNA）。

### circRNA功能

-   与miRNA相互作用。
-   circRNA通过碱基互补配对直接调控其他RNA水平。
-   circRNA能与蛋白质结合，抑制蛋白质活性、募集蛋白质复合体的部分或调控蛋白质的活性。
-   一些circRNA可作为翻译的模板指导蛋白质的合成。

### circRNA的测序

RNA测序（RNA sequencing，RNA-seq）和生物信息学技术快速发展，使大规模分析转录组成为可能。

**三种建库类型**

1.  polyA尾抓取RNA
2.  rRNA delete，去除核糖体RNA
3.  RNase R酶处理，去除线性RNA

**circRNA建库类型选择**

1.  rRNA delete

    优势：同时得到mRNA、ncRNA、circRNA表达量

    劣势：假阳性高，无法获得circRNA序列全长

2.  RNAse R处理

    优势：排除线性RNA干扰，circRNA高度富集，准确性高

    劣势：建库成本高，要做共表达分析需要重新测mRNA、ncRNA表达量

     
