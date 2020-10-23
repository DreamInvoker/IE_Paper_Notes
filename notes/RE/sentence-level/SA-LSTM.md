**Beyond Word Attention: Using Segment Attention in Neural Relation Extraction.**
_Bowen Yu, Zhenyu Zhang, Tingwen Liu, Bin Wang, Sujian Li, Quangang Li._
IJCAI 2019.
[[paper]](https://www.ijcai.org/Proceedings/2019/750)


## Motivation

1.基于采样调查发现，一般的关系表达(relation expression)是连续的词片段，提出Segment Attention. 2.前人方法使用attention机制进行降噪, 但对于每个词仅仅是soft selection，没有明确目标.

## Method

1.输入为词向量 + Positional Feature, 过了BiLSTM得到每个词的上下文表示，然后使用CRF为每个词生成一个二项分布隐变量，并得到所有隐状态的概率分布然后加权组合表达整个关系实例。2.loss加入transition正则器（用于将约束转移特征值）和sparse正则器（得到稀疏的权重分布以focus更少的词）.

## Problems

模型比较简单，就是将传统的attention变成了分段attention，这样的改进仅仅是让分类层的输入有更好的表达，并且segment attention可能会学不到一些模式，比如paper提出的实体重叠问题。
