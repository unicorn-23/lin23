---
title: 文献-深度监督卷积生成随机网络预测蛋白质二级结构
author: Lin Gui
date: '2021-09-25'
categories:
  - 学习
tags:
  - 文献
slug: 文献-蛋白质二级结构预测的深度监督卷积生成随机网络
---
# 没看完
[文献来源](https://arxiv.org/pdf/1403.1347v1.pdf)

Abstract

Predicting protein secondary structure is a fun- damental problem in protein structure predic- tion. Here we present a new supervised gen- erative stochastic network (GSN) based method to predict local secondary structure with deep hierarchical representations. GSN is a recently proposed deep learning technique (Bengio & Thibodeau-Laufer, 2013) to globally train deep generative model. We present the supervised ex- tension of GSN, which learns a Markov chain to sample from a conditional distribution, and ap- plied it to protein structure prediction. To scale the model to full-sized, high-dimensional data, like protein sequences with hundreds of amino- acids, we introduce a convolutional architecture, which allows efficient learning across multiple layers of hierarchical representations. Our archi- tecture uniquely focuses on predicting structured low-level labels informed with both low and high-level representations learned by the model. In our application this corresponds to labeling the secondary structure state of each amino-acid residue. We trained and tested the model on sepa- rate sets of non-homologous proteins sharing less than 30% sequence identity. Our model achieves 66.4% Q8 accuracy on the CB513 dataset, bet- ter than the previously reported best performance 64.9% (Wang et al., 2011) for this challenging secondary structure prediction problem.

蛋白质二级结构预测是蛋白质结构预测中的一个重要问题。本文提出了一种新的基于监督生成随机网络（GSN）的方法来预测具有深层层次表示的局部二级结构。GSN是最近提出的一种深度学习技术（Bengio&Thibodeau-Laufer，2013），用于在全球范围内训练深度生成模型。我们提出了GSN的监督扩展，它从条件分布中学习马尔可夫链进行采样，并将其应用于蛋白质结构预测。为了将模型扩展到全尺寸、高维数据，如含有数百个氨基酸的蛋白质序列，我们引入了卷积结构，它允许跨多层次表示的有效学习。我们的体系结构特别注重预测结构化的低级标签，这些标签由模型学习到的低级和高级表示形式通知。在我们的应用中，这对应于标记每个氨基酸残基的二级结构状态。我们在共享少于30%序列同一性的非同源蛋白质的分离集上训练和测试该模型。我们的模型在CB513数据集上实现了66.4%的Q8精度，比之前报道的针对这一具有挑战性的二级结构预测问题的最佳性能64.9%（Wang et al.，2011）要好。

\1. Introduction

Understanding complex dependency between protein se- quence and structure is one of the greatest challenges in computational biology (Cheng et al., 2008). Although it

*Proceedings of the* 31st *International Conference on Machine Learning*, Beijing, China, 2014. JMLR: W&CP volume 32. Copy- right 2014 by the author(s).

JZTHREE@PRINCETON.EDU OGT@CS.PRINCETON.EDU

is widely accepted that the amino-acid sequence contains sufficient information to determine the three dimensional structure of a protein, it is extremely difficult to predict protein structure based on sequence. Understanding pro- tein structure is critical for analyzing protein function and applications like drug design. Protein secondary structure prediction determines structural states of local segments of amino-acid residues, such as α-helix and β-strand, and it provides important information for further elucidating the three-dimensional structure of protein. Thus it is also being used as input by many other protein sequence and structure analysis algorithms.

Protein secondary structure prediction has been exten- sively studied with machine learning approaches (Singh, 2005).The key challenge in this field is predicting for pro- tein sequences with no close homologs that have known 3D structures. Since the early work by (Qian & Sejnowski, 1988), neural networks have been widely applied and are core components of many most successful approaches (Rost & Sander, 1993; Jones, 1999; Baldi et al., 1999). Most significant improvement to secondary structure pre- diction has been achieved by leveraging evolutionary infor- mation by using sequence profiles from multiple-sequence alignment (Rost & Sander, 1993) or position-specific scor- ing matrices from PSI-BLAST (Jones, 1999). Other devel- opments include better capturing spatial dependencies us- ing bidirectional recurrent neural networks (BRNN) (Baldi et al., 1999; Pollastri et al., 2002), probabilistic graphical models (Schmidler et al., 2000; Chu et al., 2004; van der Maaten et al., 2011), or combination of neural network and graphical models, like conditional neural fields (CNF) which integrate a windows-based neural network with con- ditional random field (CRF) (Peng et al., 2009; Wang et al., 2011). Secondary structures are commonly classified to 8 states (Kabsch & Sander, 1983) or be further combined into 3 states (Singh, 2005). Most secondary structure predic- tion studies have been focusing on coarse-grained 3-state secondary structure prediction. Achieving fine-grained 8- state secondary secondary prediction, while it reveals more structural details than 3-state predicitons, is a more chal-lenging and less-addressed problem (Pollastri et al., 2002; Wang et al., 2011). Here we address the 8-state classifi- cation problem for proteins with no close homologs with known structure.

It is widely believed that introducing global information from the whole protein sequence is crucial for further im- proving prediction performance of local secondary struc- ture labels, since secondary structure formation depends on both local and long-range interactions. For example, a secondary structure state β-strand is stabilized by hydro- gen bonds formed with other β-strands that can be far apart from each other in the protein sequence. Many contempo- rary methods such as BRNN can capture some form of spa- tial dependency, but they are still limited in capturing com- plex spatial dependency. To our knowledge none of these methods learns and leverages deep hierarchical represen- tation, which has enabled construction of better intelligent systems interpreting various types of other complex struc- tured natural data, like images, speech, and text. Models with deep representation have been exceptionally success- ful in capturing complex dependency in these data (Bengio et al., 2013a; Salakhutdinov & Hinton, 2009). Learning features automatically can be especially helpful for pro- teins, as we lack the necessary intuition or knowledge for hand-crafting mid- and high- level features involving mul- tiple amino acids.

In this work, we introduce a series of techniques to tackle challenges of protein secondary structure prediction with deep learning, and we demonstrate their superior accuracy on 8-state protein secondary structure prediction over pre- vious methods. Although we focus on the secondary struc- ture prediction application here, our methods are general and can be applied to a broad range of problem within and outside of computational biology. First, we extended the recently developed generative stochastic network (GSN) technique to supervised structured output prediction as pro- posed in (Bengio et al., 2013a). Supervised GSN learns a Markov chain to sample from the distribution of output conditioned on input data, and like GSN it avoided in- tractable explicit marginalization over hidden variables in learning deep models with hidden layers. The advantage of the supervised GSN over GSN is analogous to the advan- tage of conditional random field (CRF) over Markov ran- dom field (MRF), or discriminative versus generative clas- sifiers, that is, we focus the resources on dependencies that are important for our desired prediction, or the distribution of labels conditional on data. The supervised GSN can be applied to generate structured output of secondary structure states for all amino-acid residues of each protein.

Another important element of our approach that enables learning hierarchical representation of full-size data, like protein sequences with hundreds of amino-acids, is intro-

ducing a convolutional architecture for GSN that allows for learning multiple layers of hierarchical representations. The convolutional architecture also allows efficient com- munication between high- and low- level features and fea- tures at different spatial locations. Convolutional GSN is well suited for making predictions sensitive to low-level or local information, while informed with high-level or global information.

\2. Preliminaries

2.1. Generative Stochastic Networks

The generative stochastic network (GSN) is a recently pro- posed model that utilizes a new unconventional approach to learn a generative model of data distribution without ex- plicitly specifying a probabilistic graphical model, and al- lows learning deep generative model through global train- ing via back-propagation. Generative stochastic network learns a Markov chain to sample from data distribution P (X ). During training, GSN trains a stochastic compu- tational graph to reconstruct the input X, which general- izes the generalized denoising auto-encoder (Bengio et al., 2013b). The difference of GSN is that it allows the com- putational graph to have a latent state, and noise is injected to not just the input, but also to the intermediate computa- tions.

Compared to other deep generative models like deep Boltz- mann machine, a major advantage of GSN is that it avoided intractable inference and explicit marginalization over la- tent variables, as it does not explicitly learn parameters of a probabilistic graphical model but rather learns to directly sample from the data distribution. GSN also enjoys feasi- ble global training by back-propagating the reconstruction cost.

The following are proven in (Bengio et al., 2013b) and (Bengio et al., 2013a) as theoretical basis for generalized denoising autoencoder and generative stochastic network:

