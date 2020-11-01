**Document-Level Relation Extraction with Adaptive Thresholding and Localized Context Pooling.**
_Wenxuan Zhou, Kevin Huang, Tengyu Ma, Jing Huan._
ArXiv 2020.
[[paper]](https://arxiv.org/abs/2010.11304)

## Motivation

（1）之前的论文大多采用graph-based method进行推理，忽略了BERT中的transformer信息也可以实现类似的功能；

（2）之前的论文在对实体对的关系作出预测时，使用的是Global Thresholding，这种方法过于机械

## Method

本文提出Localized Context Pooling方法充分利用BERT中的transformer信息达到推理的效果，在预测实体关系时，采用Adaptive Thresholding方法（即添加一个AT class）使预测的准确度更高。

## Problems

