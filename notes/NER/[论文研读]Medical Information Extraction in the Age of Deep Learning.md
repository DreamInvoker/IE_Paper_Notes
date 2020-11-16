# [论文研读]Medical Information Extraction in the Age of Deep Learning

## 一、导读

这篇文章是一篇深度学习在医疗信息抽取中发展的综述文章，文章研究了过去三年文献中报道的医学信息提取的最新进展。文章重点是从标准机器学习技术到深度神经网络的基本方法论范式转变。描述了这种新范式的应用，集中在两个基本的信息抽取（IE）任务上，主要是有命名实体识别（NER）和关系抽取（RE），用于两个选定的语义类别疾病（diseases ）和药物（drugs、medications）——以及它们之间的关系。因为个人原因，本文主要关注这篇文章中的命名实体识别的相关内容。



## 二、方法

### 2.1 Diseases

NER在医学领域的主要目标是在科学文章和临床报告中自动识别疾病。例如，疾病提及的文本事件。

常见的数据集：

- NCBI：由793篇PubMed的摘要组成，注释有6892个疾病提及，映射到790个独特的疾病概念。

- BC5CDR：是一个由1500篇PubMed文章组成的语料库，其中有4409种注释化学物质、5818种疾病和3116种化学物质-疾病相互作用。

  

以下是出现的SOTA方法：

<img src="C:\Users\sishu\AppData\Roaming\Typora\typora-user-images\image-20201115205119465.png" alt="image-20201115205119465" style="zoom: 67%;" />

目前疾病识别的最高性能接近90%的$F_1$，由bidirectional Transformer+BioBERT取得，同时(attention-based) BiLSTMs等方法也有着不错的表现。面对这些实验，有以下结论是：

- 对于所使用的embedding的选择，self-trained的可能是比pre-trained的更好的选择。
- 大型的词典没有提供一个显著的提升。
- 多任务学习和迁移学习似乎是应对数据集稀疏性的合理选择，但它们通常不会将效果提升到top级别。
- 同一种方法在不同的评估数据集（NCBI,BC5CDR）上存在差异，这种差异也许是很大的。



### 2.2 Medication

在此任务下，NER的困难程度是增加的，因为该该任务被分成几个子任务，例如识别以下内容：

- 药物名称（Drug）

- 用药频率（Dr-Freq）

  <img src="C:\Users\sishu\AppData\Roaming\Typora\typora-user-images\image-20201116145958080.png" alt="image-20201116145958080" style="zoom:80%;" />

- 用药途径（Dr-Route）

  <img src="C:\Users\sishu\AppData\Roaming\Typora\typora-user-images\image-20201116150010852.png" alt="image-20201116150010852" style="zoom:80%;" />

- 剂量（Dr-Dose）

  <img src="C:\Users\sishu\AppData\Roaming\Typora\typora-user-images\image-20201116150141413.png" alt="image-20201116150141413" style="zoom:80%;" />

- 药物持续时间（Dr-Dur）

  <img src="C:\Users\sishu\AppData\Roaming\Typora\typora-user-images\image-20201116150050080.png" alt="image-20201116150050080" style="zoom:80%;" />

- 药物不良事件（Dr-ADE）

  <img src="C:\Users\sishu\AppData\Roaming\Typora\typora-user-images\image-20201116150112474.png" alt="image-20201116150112474" style="zoom:80%;" />

- ...



常见的数据集：

-  n2c2
-  i2b2 
- MADE

面对这些实验，有以下结论是：

- 除了ADE和Route问题，NER的所有最高分都是在n2c2语料库上获得的。
- Freq、Route和Dose识别在95%至97%的范围内达到显著的$F_1$分数，而在Dur方面，最高$F_1$分数显著下降至少10至20个百分点。而ADE任务的表现更差，同样表明ADE似乎是最困难的任务。

-  从pre-trained Word2vec embeddings and self-trained on MIMIC-III 到GloVe embeddings pre-trained on CommonCrawl, 
  Wikipedia, EHR notes, and PubMed.鉴于目前的评估状况，两种嵌入方式似乎都没有普遍的赢家，但在医学原始数据上的self-training ，如MIMIC-III或更具挑战性的数据集，或者更可取的是，使用现在可用的BioSentVec 和BlueBERT在MIMIC-III上 pre-trained的嵌入方式，可能是有利的。



## 三、实验

综述文章，无实验。



## 四、小结

在文章最后，除在第二部分给出的结论外，作者列出了一些从其他文献中得到的简单的结论：

- Word2vec嵌入在私人临床笔记、PMC、维基百科和谷歌新闻语料库上进行了定性和定量培训，并显示在大多数测试场景中，接受电子健康记录数据培训的嵌入表现更好。
- 然而，在生物医学领域语料库上训练的单词嵌入并不一定比在普通领域语料库上训练的embedding在任何下游生物医学NLP任务中具有更好的性能

本文主要介绍了医学NER中主要的数据集和一些SOTA结果，可以作为后续实验和项目的标准。