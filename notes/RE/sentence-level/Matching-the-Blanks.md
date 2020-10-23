**Matching the Blanks Distributional Similarity for Relation Learning.**
_Livio Baldini Soares, Nicholas FitzGerald, Jeffrey Ling, Tom Kwiatkowski._
ACL 2019.
[[paper]](https://arxiv.org/abs/1906.03158)

## Motivation

从预训练模型的角度来看怎么更好地服务于relation learning，希望通过更好的pre-train的训练目标与方法、更好的fine-tune的方式来达到更好的关系抽取效果。

## Method

paper主要分为两部分：1. 探究怎样使用Transformer效果更好，通过实验得到的结论是，在entity前后都插入相应的标记，并且使用entity前面的这个标记对应的输出作为下游分类器的输入效果最好；2. 设计了一个预训练方法，就是假设句子出现同样实体对的，提取的关系应该越接近。所以两个句子作为输入，然后拉近/扯远他们的相似度。同时为了防止模型忽略了句子上下文，因此随机地对实体进行[mask]。

## Problems

Google paper的风格，但是其实它的这个假设不是特别靠谱，只能说在无监督的预训练过程中还比较可靠。