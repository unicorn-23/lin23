---
title: 学习《Bioinformatics-Data-Skills》之1
author: Package Build
date: '2021-09-14'
slug: 学习-bioinformatics-data-skills-之一
categories:
  - 学习
tags:
  - 书籍
---

学习第一本全英文书籍Bioinformatics Data Skills。

## 目录

### Part Ⅰ. Ideology: Data Skills for Robust and Reproducible Bioinformatics

### 第1部分 理念：稳健和可重复的生物信息学数据技能

1.  **How to Learn Bioinformatics**

    **如何学习生物信息学**

    Why Bioinformatics? Biology’s Growing Data

    为什么是生物信息学？生物学不断增长的数据

    Learning Data Skills to Learn Bioinformatics

    通过学习数据技能来学习生物信息学

    New Challenges for Reproducible and Robust Research
    
    可重复和稳健的研究所面临的新挑战
    
    Reproducible Research
    
    可重复性研究
    
    Robust Research and the Golden Rule of Bioinformatics
    
    稳健研究和生物信息学的黄金法则
    
    Adopting Robust and Reproducible Practices Will Make Your Life Easier, Too
    
    采用稳健且可重复的做法也会让你的生活更轻松
    
    Recommendations for Robust Research
    
    稳健研究的建议
    
    ```
        Pay Attention to Experimental Design
        注意实验设计为人类编写代码
        Write Code for Humans, Write Data for Computers
        为人类编写代码，为计算机编写数据
        Let Your Computer Do the Work For You
        让你的计算机为你做这项工作
        Make Assertions and Be Loud, in Code and in Your Methods
        在代码和方法中做出断言并大声说话
        Test Code, or Better Yet, Let Code Test Code
        测试代码，或者更好，让代码测试代码
        Use Existing Libraries Whenever Possible
        尽可能使用现有库
        Treat Data as Read-Only
        尽可能使用现有库
        Spend Time Developing Frequently Used Scripts into Tools
        花时间将经常使用的脚本开发成工具
        Let Data Prove That It’s High Quality
        让数据证明它是高质量的
    ```
    
    Recommendations for Reproducible Research
    
    可重复性研究建议
    
    ```
    Release Your Code and Data
    发布您的代码和数据
    Document Everything
    记录所有东西
    Make Figures and Statistics the Results of Scripts
    对脚本的结果进行数字和统计
    Use Code as Documentation
    使用代码作为文档
    ```
    
    Continually Improving Your Bioinformatics Data Skills 
    
    不断提高您的生物信息学数据技能

### Part II. Prerequisites: Essential Skills for Getting Started with a Bioinformatics Project

### 第二部分先决条件：开始生物信息学项目的基本技能

2.   **Setting Up and Managing a Bioinformatics Project**

     **建立和管理生物信息学项目**

Project Directories and Directory Structures

项目目录和目录结构

Project Documentation

项目文件

Use Directories to Divide Up Your Project into Subprojects

使用目录将项目划分为子项目

Organizing Data to Automate File Processing Tasks

组织数据以自动化文件处理任务

Markdown for Project Notebooks

使用Markdown做项目笔记

```
Markdown Formatting Basics
markdown格式化基础
Using Pandoc to Render Markdown to HTML
使用pandoc来使markdown编程html
```

3.   **Remedial Unix Shell**

     **什么Unix Shell**

Why Do We Use Unix in Bioinformatics? Modularity and the Unix

为什么我们在生物信息学中使用Unix？模块化与Unix

```
Philosophy
哲学
```

Working with Streams and Redirection

使用流和重定向

```
Redirecting Standard Out to a File
将标准输出重定向到文件
Redirecting Standard Error
重定向标准错误
Using Standard Input Redirection
使用标准输入重定向
```

The Almighty Unix Pipe: Speed and Beauty in One

全能的Unix管道：速度与美合一

```
Pipes in Action: Creating Simple Programs with Grep and Pipes
正在运行的管道：使用Grep和管道创建简单程序
Combining Pipes and Redirection
结合管道和重定向
Even More Redirection: A tee in Your Pipe
甚至更多重定向：管道中的tee
```

Managing and Interacting with Processes

管理流程并与之交互

```
Background Processes
后台进程
Killing Processes
kill进程
Exit Status: How to Programmatically Tell Whether Your
退出状态：如何以编程方式告诉您的
Command Worked
命令工作？
```

Command Substitution

命令替换

4.   **Working with Remote Machines**

     **使用远程机器**

Connecting to Remote Machines with SSH

使用SSH连接到远程计算机

Quick Authentication with SSH Keys

使用SSH密钥进行快速身份验证

Maintaining Long-Running Jobs with nohup and tmux

使用nohup和tmux维护长时间运行的作业

```
nohup
```

Working with Remote Machines Through Tmux

通过Tmux使用远程机器

```
Installing and Configuring Tmux
安装和配置Tmux
Creating, Detaching, and Attaching Tmux Sessions
创建、分离和附加Tmux会话
Working with Tmux Windows
使用Tmux窗口
```

5.   **Git for Scientists**

     **科学家的Git**

Why Git Is Necessary in Bioinformatics Projects

为什么Git在生物信息学项目中是必要的

```
Git Allows You to Keep Snapshots of Your Project
Git允许您保存项目的快照
Git Helps You Keep Track of Important Changes to Code
Git帮助您跟踪代码的重要更改
Git Helps Keep Software Organized and Available After People Leave
Git帮助人们在离开后保持软件的组织性和可用性
```

Installing Git

安装git

Basic Git: Creating Repositories, Tracking Files, and Staging and Committing

Git基础：创建存储库、跟踪文件以及暂存和提交

```
Changes

Git Setup: Telling Git Who You Are
Git设置：告诉Git你是谁
git init and git clone: Creating Repositories
git init和git clone：创建存储库
Tracking Files in Git: git add and git status Part I
跟踪Git中的文件：Git添加和Git状态第一部分
Staging Files in Git: git add and git status Part II
Git中的暂存文件：Git添加和Git状态第二部分
git commit: Taking a Snapshot of Your Project
git提交：拍摄项目的快照
Seeing File Differences: git diff
查看文件差异：git diff
Seeing Your Commit History: git log
查看提交历史记录：git日志
Moving and Removing Files: git mv and git rm
移动和删除文件：git mv和git rm
Telling Git What to Ignore: .gitignore
告诉Git要忽略的内容：.gitignore
Undoing a Stage: git reset
撤消阶段：git重置
```

Collaborating with Git: Git Remotes, git push, and git pull

与Git协作：Git Remotes、Git push和Git pull

```
Creating a Shared Central Repository with GitHub
使用GitHub创建共享中央存储库
Authenticating with Git Remotes
使用Git远程设备进行身份验证
Connecting with Git Remotes: git remote
与Git Remotes连接：Git remote
Pushing Commits to a Remote Repository with git push
使用git push将提交推送到远程存储库
Pulling Commits from a Remote Repository with git pull
使用git pull从远程存储库提取提交
Working with Your Collaborators: Pushing and Pulling
与合作者合作：pushing
Merge Conflicts
合并冲突
More GitHub Workflows: Forking and Pull Requests
更多GitHub工作流：分叉和拉取请求
```

Using Git to Make Life Easier: Working with Past Commits

使用Git让生活更轻松：处理过去的提交

```
Getting Files from the Past: git checkout
从过去获取文件：git签出
Stashing Your Changes: git stash
隐藏更改：git stash
More git diff: Comparing Commits and Files
更多git差异：比较提交和文件
Undoing and Editing Commits: git commit --amend
撤消和编辑提交：git提交--修改
```

Working with Branches

与分支机构合作

```
Creating and Working with Branches: git branch and git checkout
创建和使用分支：git分支和git签出
Merging Branches: git merge
合并分支：git merge
Branches and Remotes
分支和远程
```

Continuing Your Git Education

6.   **Bioinformatics Data**

     **生物信息学数据**

Retrieving Bioinformatics Data

检索生物信息学数据

```
Downloading Data with wget and curl
使用wget和curl下载数据
Rsync and Secure Copy (scp)
Rsync和安全拷贝（scp）
```

Data Integrity

数据完整性

```
SHA and MD5 Checksums
SHA和MD5校验
```

Looking at Differences Between Data

查看数据之间的差异

Compressing Data and Working with Compressed Data

压缩数据和使用压缩数据

```
gzip
Working with Gzipped Compressed Files
使用gzip压缩文件
```

Case Study: Reproducibly Downloading Data

案例研究：重复下载数据

### Part III. Practice: Bioinformatics Data Skills

### 第三部分：实践：生物信息学数据技能

7.   **Unix Data Tools**

     **Unix数据工具**

Unix Data Tools and the Unix One-Liner Approach: Lessons from Programming Pearls

Unix数据工具和Unix一行程序方法：从Pearls编程中学习

When to Use the Unix Pipeline Approach and How to Use It Safely

何时使用Unix管道方法以及如何安全地使用它

Inspecting and Manipulating Text Data with Unix Tools

使用Unix工具检查和操作文本数据

```
Inspecting Data with Head and Tail
从头到尾检查数据
less

Plain-Text Data Summary Information with wc, ls, and awk
带wc、ls和awk的纯文本数据摘要信息
Working with Column Data with cut and Columns
使用具有“剪切”和“列”的列数据
Formatting Tabular Data with column
使用列设置表格数据格式
The All-Powerful Grep
全能的Grep
Decoding Plain-Text Data: hexdump
解码纯文本数据：hexdump
Sorting Plain-Text Data with Sort
使用Sort对纯文本数据进行排序
Finding Unique Values in Uniq
在Uniq中查找唯一值
Join

Text Processing with Awk
基于Awk的文本处理
Bioawk: An Awk for Biological Formats
Bioawk：生物格式的Awk
Stream Editing with Sed
使用Sed进行流编辑
```

Advanced Shell Tricks

先进的shell技巧

```
Subshells

Named Pipes and Process Substitution
命名管道和进程替换
```

The Unix Philosophy Revisited

重新审视Unix哲学

8.   **A Rapid Introduction to the R Language**

     **快速介绍R语言**

Getting Started with R and RStudio

R和RStudio入门

R Language Basics

R语言基础

```
Simple Calculations in R, Calling Functions, and Getting Help in R
R中的简单计算、调用函数以及在R中获得帮助
Variables and Assignment
变量和赋值
Vectors, Vectorization, and Indexing
向量、向量化和索引
```

Working with and Visualizing Data in R

在R中处理和可视化数据

```
Loading Data into R
将数据加载到R
Exploring and Transforming Dataframes
探索和转换数据帧
Exploring Data Through Slicing and Dicing: Subsetting Dataframes
通过切片和切分探索数据：子集数据帧
Exploring Data Visually with ggplot2 I: Scatterplots and Densities
使用ggplot2 I直观地探索数据：散点图和密度
Exploring Data Visually with ggplot2 II: Smoothing
使用ggplot2 II直观地探索数据：平滑
Binning Data with cut() and Bar Plots with ggplot2
使用cut（）组合数据，使用ggplot2组合条形图
Merging and Combining Data: Matching Vectors and Merging Dataframes
合并和组合数据：匹配向量和合并数据帧
Using ggplot2 Facets
使用ggplot2 facets
More R Data Structures: Lists
更多R数据结构：列表
Writing and Applying Functions to Lists with lapply() and sapply()
使用lapply（）和sapply（）编写函数并将其应用于列表
Working with the Split-Apply-Combine Pattern
使用拆分应用组合模式
Exploring Dataframes with dplyr
使用dplyr探索数据帧
Working with Strings
使用字符串
```

Developing Workflows with R Scripts

使用R脚本开发工作流

```
Control Flow: if, for, and while
控制流：if、for和while
Working with R Scripts
使用R脚本
Workflows for Loading and Combining Multiple Files
加载和组合多个文件的工作流
Exporting Data
导出数据
```

Further R Directions and Resources

进一步研究方向和资源

9.   **Working with Range Data**

     **使用范围数据**

A Crash Course in Genomic Ranges and Coordinate Systems

基因组范围和坐标系速成班

An Interactive Introduction to Range Data with GenomicRanges

基因组范围数据的交互式介绍

```
Installing and Working with Bioconductor Packages
安装和使用Bioconductor封装
Storing Generic Ranges with IRanges
使用IRanges存储通用范围
Basic Range Operations: Arithmetic, Transformations, and Set Operations
基本范围运算：算术、变换和集合运算
Finding Overlapping Ranges
寻找重叠范围
Finding Nearest Ranges and Calculating Distance
寻找最近距离并计算距离
Run Length Encoding and Views
运行长度编码和视图
Storing Genomic Ranges with GenomicRanges
使用基因组范围存储基因组范围
Grouping Data with GRangesList
使用GRangesList对数据进行分组
Working with Annotation Data: GenomicFeatures and rtracklayer
使用注释数据：基因组特征和rtracklayer
Retrieving Promoter Regions: Flank and Promoters
检索启动子区域：侧翼和启动子
Retrieving Promoter Sequence: Connection GenomicRanges with Sequence Data
检索启动子序列：基因组范围与序列数据的联系
Getting Intergenic and Intronic Regions: Gaps, Reduce, and Setdiffs in Practice
获得基因间和内含子区域：实践中的差距、减少和差异
Finding and Working with Overlapping Ranges
查找和处理重叠范围
Calculating Coverage of GRanges Objects
计算GRanges对象的覆盖率
```

Working with Ranges Data on the Command Line with BEDTools

使用BEDTools在命令行上处理范围数据

```
Computing Overlaps with BEDTools Intersect
使用BEDTools相交计算重叠
BEDTools Slop and Flank
倾斜和侧翼
Coverage with BEDTools
BEDTools覆盖率
Other BEDTools Subcommands and pybedtools
其他BEDTools子命令和pybedtools
```

10.   **Working with Sequence Data**

      **处理序列数据**

The FASTA Format

FASTA格式

The FASTQ Format

FASTQ格式

Nucleotide Codes

核苷酸密码

Base Qualities

基本

Example: Inspecting and Trimming Low-Quality Bases

示例：检查和修整低质量底座

A FASTA/FASTQ Parsing Example: Counting Nucleotides

FASTA/FASTQ解析示例：计算核苷酸

Indexed FASTA Files

索引FASTA文件

11.   **Working with Alignment Data**

      **使用路线数据**

Getting to Know Alignment Formats: SAM and BAM

了解对齐格式：SAM和BAM

```
The SAM Header
SAM的Header
The SAM Alignment Section
SAM校准部分
Bitwise Flags
位标志
CIGAR Strings
CIGAR字符串
Mapping Qualities
绘图质量
```

Command-Line Tools for Working with Alignments in the SAM Format

用于以SAM格式处理路线的命令行工具

```
Using samtools view to Convert between SAM and BAM
使用samtools视图在SAM和BAM之间转换
Samtools Sort and Index
Samtools排序和索引
Extracting and Filtering Alignments with samtools view
使用samtools视图来提取和过滤路线
```

Visualizing Alignments with samtools tview and the Integrated Genomics Viewer

使用samtools tview和Integrated Genomics Viewer可视化比对

```
Pileups with samtools pileup, Variant Calling, and Base Alignment Quality
samtools堆积，变体调用和基本对齐质量的堆积
```

Creating Your Own SAM/BAM Processing Tools with Pysam

使用Pysam创建自己的SAM/BAM处理工具

```
Opening BAM Files, Fetching Alignments from a Region, and Iterating Across Reads
打开BAM文件，从区域获取对齐方式，并跨读迭代
Extracting SAM/BAM Header Information from an AlignmentFile Object
从AlignmentFile对象中提取SAM/BAM标题信息
Working with AlignedSegment Objects
使用AlignedSegment对象
Writing a Program to Record Alignment Statistics
编写程序以记录对齐统计信息
Additional Pysam Features and Other SAM/BAM APIs
其他Pysam功能和其他SAM/BAM API
```

12.   **Bioinformatics Shell Scripting, Writing Pipelines, and Parallelizing Tasks**

      **生物信息学Shell脚本，编写管道和并行化任务**

Basic Bash Scripting

基本的Bash脚本

```
Writing and Running Robust Bash Scripts
编写和运行健壮的Bash脚本
Variables and Command Arguments
变量和命令参数
Conditionals in a Bash Script: if Statements
Bash脚本中的条件：if语句
Processing Files with Bash Using for Loops and Globbing
使用Bash处理文件用于循环和文件名代换
```

Automating File-Processing with find and xargs

使用find和xargs自动化文件处理

```
Using find and xargs
使用find和xargs
Finding Files with find
使用find查找文件
find’s Expressions
查找用户的表达式
find’s -exec: Running Commands on find’s Results
find的-exec：对find的结果运行命令
xargs: A Unix Powertool
xargs：一个Unix Powertool
Using xargs with Replacement Strings to Apply Commands to Files
使用带替换字符串的xargs将命令应用于文件
xargs and Parallelization
xargs与并行化
```

Make and Makefiles: Another Option for Pipelines

Make和Makefiles：管道的另一个选项

13.   **Out-of-Memory Approaches: Tabix and SQLite**

      **内存不足方法：Tabix和SQLite**

Fast Access to Indexed Tab-Delimited Files with BGZF and Tabix

使用BGZF和Tabix快速访问索引的制表符分隔文件

```
Compressing Files for Tabix with Bgzip
使用Bgzip压缩Tabix文件
Indexing Files with Tabix
使用Tabix索引文件
Using Tabix
使用Tabix
```

Introducing Relational Databases Through SQLite

通过SQLite引入关系数据库

```
When to Use Relational Databases in Bioinformatics
在生物信息学中何时使用关系数据库
Installing SQLite
安装SQLite
Exploring SQLite Databases with the Command-Line Interface
使用命令行界面探索SQLite数据库
Querying Out Data: The Almighty SELECT Command
查询数据：万能的SELECT命令
SQLite Functions
SQLite函数
SQLite Aggregate Functions
SQLite聚合函数
Subqueries
子查询
Organizing Relational Databases and Joins
组织关系数据库和连接
Writing to Databases
写入数据库
Dropping Tables and Deleting Databases
删除表和删除数据库
Interacting with SQLite from Python
从Python与SQLite交互
Dumping Databases
转储数据库
```

14.   **Conclusion**

Where to Go From Here?

