**Relation Extraction with Temporal Reasoning Based on Memory Augmented Distant Supervision.**
_Jianhao Yan, Lin He, Ruqin Huang, Jian Li, Ying Liu._
NAACL 2019.
[[paper]](https://www.aclweb.org/anthology/N19-1107/)

## Motivation

前人DS RE的工作忽略了关系实例中的时间信息，比如实体对在今天和明天可能是不同的关系，所以本文提出了一个新的任务，即从时序的角度推理实体对之间的关系，并提出专门针对时序RE的新数据集[WIKITIME](https://github.com/ElliottYan/DS_Temporal)
          
## Method

基于前人encoding + fusion的架构, 将时序RE看做是在memory上的序列标注任务。1.在encoding阶段引入时间编码来建模bag中instance之间的时序信息；2.在fusion阶段，使用Memory Network对经过时间信息增强后的句子编码进行迭代地推理。

## Problems

对于给定时间点两个实体对之间的关系，有这样的数据集来做固然是很好的，但是没法从根本上解决公开数据集关于时间序列RE的问题。
