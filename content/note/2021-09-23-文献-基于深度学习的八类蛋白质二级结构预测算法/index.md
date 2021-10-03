---
title: 文献-基于深度学习的八类蛋白质二级结构预测算法
author: Lin Gui
date: '2021-09-23'
categories:
  - 学习
tags:
  - 文献
slug: 文献-基于深度学习的八类蛋白质二级结构预测算法
---
[文献来源](http://www.hzlib.net:7080/rwt/CNKI/https/NNYHGLUDN3WXTLUPMW4A/kcms/detail/detail.aspx?dbcode=CJFD&dbname=CJFDLAST2017&filename=JSJY201705054&uniplatform=NZKPT&v=E%25mmd2BFQSieGrOE8HzaH7AzUb0wjW5I5%25mmd2BBaY8VLBOrcngd15PP%25mmd2F%25mmd2Fe%25mmd2Fk4R7dvbX3KPssF)

### 数据

[uniref50](https://www.uniprot.org/downloads)

PSSM:可以反映出每个位置上不同碱基出现的频率，矩阵每一列表示相应位置上碱基出现的频率。

步骤：

1.  下载[ncbi-blast](https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/)

2.  下载[NCBI nr数据库](ftp://ftp.ncbi.nlm.nih.gov/blast/db/)

3.  格式化数据库

    ```
    makeblastdb -in /Users/lin/Desktop/dataset/uniref50.fasta -dbtype prot -title uniref50 -parse_seqids -out uniref50
    ```

4.  输出单条PSSM

    ```
    psiblast -db /Users/lin/Desktop/dataset/uniref50 -query /Users/lin/Desktop/dataset/sequences/4Y3F.fasta -evalue 0.001 -num_iterations 3 -out_ascii_pssm 1.pssm
    ```

5.  批量输出

pfilt:可通过Google查询并下载，这个东西好像是psipred2、3的一个库？psipred4中并不包含这个“从PSIPRED V4.0开始，我们不再认为没有必要过滤与PSI-BLAST一起使用的序列数据库，以删除低复杂度区域、跨膜区域和线圈段。因此，搜索数据库可以是任何大型非冗余蛋白质序列数据库”

[makeblastdb](https://blog.csdn.net/likelet/article/details/7567426)：格式：

```
makeblastdb -in input_file -dbtype molecule_type -title database_title -parse_seqids -out database_name -logfile File_Name
```

