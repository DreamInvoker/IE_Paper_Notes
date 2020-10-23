**GraphRel: Modeling Text as Relational Graphs for Joint Entity and Relation Extraction.**
_Tsu-Jui Fu, Peng-Hsuan Li, Wei-Yun Ma._
ACL 2019.
[[paper]](https://www.aclweb.org/anthology/P19-1136/)

## Motivation

试图统一将RE中的三个要点融合在一个架构中。1.端到端的命名实体识别和关系抽取的联合建模；2.预测那些共有一个实体的关系；3.考虑关系间的交互，尤其是重叠关系

## Method

使用两阶段进行端到端的联合实体抽取和关系抽取。1.第一阶段使用BiLSTM和BiGCN对原文进行编码，以获得序列信息和依存信息，然后计算分类loss得到边权；（2）第二阶段使用第一阶段得到的全连接边权图，再做BiGCN以使不同关系之间可以交互，并最终得到第二阶段的分类loss

## Problems

工作挺novel的，没有啥问题