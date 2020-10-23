**Span-based Joint Entity and Relation Extraction with Transformer Pre-training.**
_Markus Eberts and Adrian Ulges._
arxiv 2019.
[[paper]](https://arxiv.org/abs/1909.07755)

## Motivation

与上一篇相同，也是为了解决NER中实体重叠问题。

## Method

与上一篇不同的是，这里把LSTM换成了BERT，然后编码span的时候用到了BERT [cls]对应位置的输出作为全局context信息。而在预测两个entity的关系的时候，利用两个entity中间的文字context信息，做了实验验证了这样做比用全局context更好。

## Problems 

和上一篇的问题一样，遍历所有的Span总感觉不是特别优雅。