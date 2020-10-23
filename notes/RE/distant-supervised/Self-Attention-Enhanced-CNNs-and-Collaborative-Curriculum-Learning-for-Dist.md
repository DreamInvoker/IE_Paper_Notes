**Self-Attention Enhanced CNNs and Collaborative Curriculum Learning for Distantly Supervised Relation Extraction.**
_Yuyun Huang Jinhua Du._
EMNLP 2019.
[[paper]](https://www.aclweb.org/anthology/D19-1037/)

## Motivation

对于DS，不同bag-level的relation prediction模型被提出，这篇paper的目的是用某种机制把他们的优点结合起来，更好地排除DS中false positive数据的干扰。
          
## Method

使用两个不同bag-level relation prediction的模型：一个是从中选出最大概率的；一个是用attention软聚合的。两个模型共同学习，对于某个bag，如果两个模型预测出来其中最大概率的句子相同，就认为是easy的样本，加进去算loss；如果不相同，认为是difficult的样本，不加进去学习。然后还加了一个两个模型预测出来的最大概率句子的交叉熵作为正则项，让两个模型预测倾向更紧密。

## Problems

