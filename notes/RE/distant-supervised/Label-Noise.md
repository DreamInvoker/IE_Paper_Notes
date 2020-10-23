**Looking Beyond Label Noise: Shifted Label Distribution Matters in Distantly Supervised Relation Extraction.**
_Qinyuan Ye, Liyuan Liu, Maosen Zhang, Xiang Ren._
EMNLP 2019.
[[paper]](https://arxiv.org/abs/1904.09331)

## Motivation

利用神经网络进行关系抽取的方法，在人工标注数据集上比传统基于特征的方法提升较大，但是在远程监督的数据集上却提升不是特别大。因此通过一系列的实验来探究内在原因。
          
## Method

先是提出了两种阈值过滤的方法，通过实验反映出问题可能是远程监督数据集在训练集与测试集的标签分布不太一致（训练集是远程监督自动标注，测试集用于测试是人工标注），之后通过数学推导提出了基于偏差补偿的方法。

## Problems

挺好的一篇paper，通过实验一步一步递进地探究，感觉不出什么太大的问题！