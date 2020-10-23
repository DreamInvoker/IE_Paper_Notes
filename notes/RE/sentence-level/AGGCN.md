**Attention Guided Graph Convolutional Networks for Relation Extraction.**
_Yan Zhang, Zhijiang Guo, Wei Lu._
ACL 2019.
[[paper]](https://arxiv.org/abs/1906.07510)


## Motivation

前人使用剪枝后的依存树来做关系抽取，但是容易将一些重要的信息给剪掉，因此本文提出一种软剪枝的策略，来让模型学习怎么去给依存树上的边给定权重

## Method

首先将句子变成依存树（数据集给定），然后将依存树加上自环和反向连接变成依存图，然后通过Attention Guided Layer，将原始的依存图变成N个不同的全连接的图，每个图过DCGCN，来得到最终图的表示进行合并。

## Problems

Attention Guided Layer使用Self-Attention，其实类似于用了GAT，只不过这个attention系数不是根据GAT的公式计算出来，而是单独拿出来进行学习，所以感觉可以用DCGAT(Densely)来对比一下
