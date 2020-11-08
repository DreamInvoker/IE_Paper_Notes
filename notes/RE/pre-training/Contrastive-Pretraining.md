**Learning from Context or Names? An Empirical Study on Neural Relation Extraction.**
Hao Peng, Tianyu Gao, Xu Han, Yankai Lin, Peng Li, Zhiyuan Liu, Maosong Sun, Jie Zhou
EMNLP 2020.
[[paper]](https://arxiv.org/abs/2010.01923)

## Motivation

目前RE领域对下面两个问题都没有清晰的理解：
（1）哪一类信息影响着现有的RE模型去做决策？
（2）如何让现有模型的效果得到更进一步的提升？

本文就是为了回答以上两个问题，从经验上去研究了文本中两个可能影响RE模型做决策的信息源头：文本上下文（textual context）和实体mention（名字）
通过经验性的研究发现

（1）尽管上下文是支持RE模型预测结果的主要源头，RE模型也严重地依赖实体mention的信息，其中主要是实体的类别信息；
（2）现有的数据可能通过实体mention得到了浅层的启发，因此导致了RE基准的高性能


## Method

（1）本文采用对比学习的思想(contrastive learning)，这个思想主要是让”neighbor”之间的表示相近，而”non-neighbor”之间的表示更远。这里的”neighbor”就是相近的样本或者实例，对于RE任务来说，就是句子表达了相同的关系。

（2）为了让模型不过拟合实体的特有模式（shallow heuristic），随机使用特殊的token [BLANK]来对实体mention进行mask，随机mask的概率为0.7，


## Problems

（1）	一个context可能不止表达一种关系，也可能不表达关系，这篇文章在这方面的说法可能局限在某个数据集

（2）	效果其实一般般，设计的模型解释性比较差，对比学习让模型去学习context信息的方式比较隐式，是不是用attention的方式对每个实体聚合context中的信息会更好呢？
