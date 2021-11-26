---
title: 笔记-基因芯片数据处理
author: Lin Gui
date: '2021-11-10'
slug: 笔记-基因芯片数据处理
categories:
  - 学习
tags:
  - 笔记
---

## 基因芯片数据处理

### 实验目的

1：掌握Affy表达谱芯片基本知识;

2: 掌握从cel文件中读取基因表达量及present/absent量； 

3：掌握芯片数据标准化方法；

4：掌握差异表达基因计算方法。

### 实验原理及步骤

1、给定两组3*3芯片数据AD01.CEL，AD02.CEL，AD03.CEL与AI01.CEL，AI02.CEL，AI03.CEL，利用R语言环境中affy和simpleaffy软件包中的ReadAffy，call.exprs，mas5calls函数读取芯片数据。

2、分别利用Quantile和Scale标准化方法对数据标准化。

3、利用t检验找出差异表达基因。

```R
#调用库
library(affy);
library(simpleaffy);
#把cel文件读入affybatch--Data
Data <- ReadAffy(filenames=c('AD01.CEL','AD02.CEL','AD03.CEL','AI01.CEL','AI02.CEL'));
#生成Data的表达总结并标准化Affymetrix
eset <- call.exprs(Data,'mas5',FALSE);
#进行高通量表达水平分析，将结果写进expressionlevels.txt
write.exprs(eset,file='expressionlevels.txt');
#通过mas5来检测Data基因表达的A/P
data.mas5calls <- mas5calls(Data);
#将结果写进call.txt
write.exprs(data.mas5calls,file='call.txt');

#调用库
library('preprocessCore');
#将表达水平数据读入expression
expression <- read.table(file='expressionlevels.txt');
#将expression转换为矩阵形式
expression <- as.matrix(expression);
#画出箱线图
boxplot(log(expression));


####组内标准化
#对进行重复实验对芯片进行分位数标准化----组内标准化
new.expression <- cbind(normalize.quantiles(expression[,1:3]),normalize.quantiles(expression[,4:5]));
#画出进行分位数标准化后的箱线图
boxplot(log(new.expression));


####组间标准化
#apply函数计算矩阵每一列的中位数，x为中位数的均值
x <- mean(apply(new.expression,2,median));
#对每个芯片每一列的数据进行处理----组间标准化
for (i in 1:5) {
  new.expression[,i] <- new.expression[,i]*x/median(new.expression[,i]);
}
#画出组间标准化后的箱线图
boxplot(log(new.expression));
#将标准化后的基因表达量数据写入文件normalized.expressionlevels.csv
write.csv(new.expression,file='normalized.expressionlevels.csv');


####计算pvalue foldchange
#初始化
pvalue <- array(0,dim=nrow(new.expression));
foldchange <- array(0,dim=nrow(new.expression));
for (i in 1:nrow(new.expression)) {
  #对实验组和对照组数据进行t检验 返回值为t，自由度，pvalue
  tmp <- t.test(log10(new.expression[i,1:3]),log10(new.expression[1,4:5]));
  #取pvalue
  pvalue[i] <- tmp[[3]];
  #计算foldchange;
  tmp_f <- (mean(new.expression[i,1:3])/mean(new.expression[i,4:5]));
  foldchange[i] <- tmp_f[[1]];
}
#print(pvalue);
#print(foldchange);


####筛选差异表达基因 foldchange>2或foldchange<0.5 且 p<0.05
count <- 0;
#用来记录差异表达基因行号
countnum <- array(0);
#用来记录差异表达基因foldchange
differ_foldchange <- array(0);
#用来记录差异表达基因pvalue
differ_pvalue <- array(0);
#满足foldchange>2或者foldchange<0.5 且 pvalue<0.05
for (i in 1:nrow(new.expression)){
  if ((foldchange[i]>2||foldchange[i]<0.5)&&pvalue[i]<0.05){
    count <- count+1;
    countnum[count] <- i;
    differ_foldchange[count] <- foldchange[i];
    differ_pvalue[count] <- pvalue[i];
  }
}

#输出差异基因总数
print(count);
print(countnum);
#在difference.expression中添加differ_pvalue和differ_foldchange列
difference.expression <- new.expression[countnum,];
difference.expression <- data.frame(difference.expression,differ_pvalue);
difference.expression <- data.frame(difference.expression,differ_foldchange);
write.csv(difference.expression,file='difference.expression.csv');

```

