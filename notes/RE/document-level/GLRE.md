**Global-to-Local Neural Networks for Document-Level Relation Extraction.**
_Difeng Wang, Wei Hu, Ermei Cao, Weijian Sun._
EMNLP 2020.
[[paper]](https://arxiv.org/abs/2009.10359)

## Motivation

（1）一篇文章有很多实体；
（2）一个实体有很多mention。
所以篇章级模型需要建模多实体之间复杂的交互并综合多mention
的上下文信息，以更好地对实体进行表示。

## Method

本文提出Global-to-Local的架构，构建异质图，并在异质图上使用R-GCN获取实体的全局表示，针对每个实体对，使用multi-head attention聚合mention的信息，得到实体的局部表示，最后加入关系的主题信息，做关系预测，

## Problems

模型架构没有可解释性，entity的local表示部分，存在很多直观假设，并没有通过实验结果去验证multi-head attention最终学到的是不是和假设一致。