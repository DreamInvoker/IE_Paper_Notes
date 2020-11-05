**A Frustratingly Easy Approach for Joint Entity and Relation Extraction.**
Zexuan Zhong, Danqi Chen
EMNLP2020.
[[paper]](https://arxiv.org/abs/2010.12812)

## Motivation

现有的端到端的RE模型（即同时抽取实体和关系），通常使用joint的模型，要么将他们使用统一的预测架构进行预测（比如基于标注的模型、Table Filling、Seq2Seq模型等），要么使用共享的表示进行多任务学习（比如SciIE、DyIE、DyIE++）。这篇文章提出一种pipeline的形式，相比前人更加简单，效果更好。

## Method

这篇文章的方法特别简单，模型基于span级别的表示，也就是说数据输入是枚举所有span，定义两个独立的预训练好的编码器（参数不共享，不一起训练，span表示不共享），即entity model和relation model，entity model对每个span进行实体分类和实体类别分类，relation model对每个span pair进行关系分类。在inference的时候将entity model的输出作为relation model的输入特征。

## Problems 

没有公布源码和超参，时间复杂度尽管batch化计算过程，但是因为需要遍历所有的span还是有点大。