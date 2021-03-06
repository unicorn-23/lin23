---
title: 笔记-用于预测药物药物相互作用的机器学习框架
author: Lin Gui
date: '2021-10-06'
slug: 笔记-用于预测药物药物相互作用的机器学习框架
categories:
  - 学习
tags:
  - 笔记
---



[预测药物相互作用的机器学习框架原文](https://www.nature.com/articles/s41598-021-97193-8.pdf)

关于药物-药物相互作用，现有的计算方法可大致分为三类，即基于**相似性**的方法，基于**神经网络**的方法和**机器学习**的方法。基于相似性的方法根据药物组间的相似性得分直接推断药物之间的相互作用。Vilar等人8回顾了几种药物成分，如药物成分、基因表达成分和酚类成分，它们被用于推断药物的再利用、药物不良反应和药物-药物相互作用。其中，基于这一假设可以很好地解释药物结构，结构相似的药物往往以相同或功能相关的基因为靶点，产生相似的药物效应。基于相似性的方法的另一个主要关注点是开发有效的指标来衡量药物成分之间的相似性。Ferdousi等人10从药物靶点之间的十几个相似性度量中选择最佳度量（例如，内积、Jaccard相似性、Russell Rao相似性和Tanimoto coef  fcient）来推断DDI。尽管解释简单直观，但基于相似性的方法很容易受到噪声的影响，例如，相似性分数的阈值设置受到虚假DDI的严重影响。

第二类方法，即基于网络的方法，可进一步分为基于药物相似性网络的方法和基于蛋白质-蛋白质相互作用（PPI）网络的方法。基于药物相似性网络的方法通过对药物-药物相似性网络的网络推理来预测新的链接/DDI，该网络通过各种药物相似性度量构建，例如矩阵分解12,13、块坐标下降优化。与基于相似性的方法类似，这些方法也利用药物结构形式之间的相似性来推断DDI。

相比之下，基于网络的方法比基于直接相似性的方法对噪声更具鲁棒性。然而，药物-药物相互作用并不意味着两个结构相似的药物分子之间的直接反应，而是相互作用的协同增强或拮抗减弱。当两种药物作用于同一基因、相关代谢物或串扰信号通路时，两种联合处方药物相互影响或改变治疗效果的生物事件很可能发生10。从这个意义上说，关于两种药物靶点的知识比药物结构相似性更有用，更易于解释，从而推断药物-药物相互作用，特别是对于结构不相似的两种药物之间的潜在相互作用。

基于PPI网络的方法假设，如果两种药物同时作用于相同或相关基因，则会对彼此的治疗效果产生意想不到的干扰，因此，这些方法具有捕获药物相互作用的潜在机制的优点。Park等人15假设，如果两种药物在同一通路内引起近摄动或在两条串扰通路内引起远距离摄动，则它们相互作用，其中远距离摄动通过PPI网络上的随机游走算法捕获。黄et al.16还考虑了在PPI网络的背景下的药物作用。在他们的方法中，将PPI网络中的目标基因及其相邻基因定义为药物的以目标为中心的系统，然后提出了一种称为S评分的指标来衡量两种药物的以目标为中心的系统之间的相似性，以推断药物-药物相互作用。迄今为止，PPI网络还很不完整，并且包含一定程度的噪声，因此在推断药物-药物相互作用的应用中受到限制。

第三类方法，即机器学习方法，已广泛用于推断药物-药物相互作用。这些方法大多侧重于通过数据集成提高药物相互作用预测的性能。在这些方法中，数据集成试图捕获单个数据源或组合多个异构数据源的信息的多个方面。Dhami等人17试图从药物微笑表征的唯一数据中结合多种相似性度量（例如，分子特征相似性、字符串相似性、分子指纹相似性、分子访问系统）。其他方法18–25都结合了多个数据源。EN的数据集成结合了多种特征信息，如药物不良反应（ADR）18–20,23,24、目标相似性18–20,22–24、PPI网络23,24、信号通路19等。在这些特征中，以微笑描述符形式出现的药物化学结构信息是最常用的17–24。用于集成异构数据的机器学习框架包括集成学习18,19、核心方法17,20和深度学习21,22。

实证研究表明，数据整合确实从多个方面丰富了药物的描述，从而提高了药物-药物相互作用预测的性能。然而，数据集成有两个主要缺点。一个缺点是数据集成增加了数据复杂性。在大多数情况下，我们不知道哪些信息是预测药物相互作用最重要、最不可分割的信息。一些信息可能对预测任务的贡献较小。更重要的是，数据集成使得数据约束要求更高。一旦特征信息的任何方面不可用，例如药物分子结构，经过训练的模型可能无法工作。实际上，没有数据集成的单任务学习也可以实现

已知的药物-药物相互作用和药物-基因相互作用摘自药物库27。由于我们使用药物靶点谱来表示药物和药物对，因此本研究仅对已发现的至少针对一个人类基因的药物进行研究。结果，我们从药物库27中共提取了6066种药物和2940个靶向人类基因。Tere是与这些药物相关的915413种药物-药物相互作用和23169种药物-基因相互作用。由于药物-药物相互作用预测本质上是一个二元监督学习问题，我们使用915413药物对作为正训练数据，并从6066种药物中随机抽取另915413药物对作为负训练数据。Te确保两类数据没有重叠。Te综合数据库28为实验和文本挖掘中的药物-药物相互作用提供了一个大型存储库，其中一些来自分散的数据库，如DrugBank27、KEGG29、OSCAR30(https://oscar-emr.com/)，VA NDF-RT31等。除去DrugBank27中已经存在的药物-药物相互作用后，我们总共获得了13个外部数据集作为阳性独立测试数据，例如，KEGG29中最大的8188个药物-药物相互作用。为了估计模型偏差的风险，我们随机抽取8188对药物作为阴性独立试验数据。这些药物对与训练数据和阳性独立测试数据不重叠。为了定量估计两种药物相互干扰的强度，我们从现有数据库中建立了综合物理蛋白质-蛋白质相互作用（PPI）网络（HPRD32，BioGRID33，IntAct34，HitPredict35。我们总共获得了171249个物理PPI。从NetPath36中，我们获得了27个免疫信号通路，其中IL1–IL11合并为一个通路以简化操作。从Reactome37中，我们获得了1846个人类信号通路。
