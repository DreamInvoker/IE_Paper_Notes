**CopyMTL: Copy Mechanism for Joint Extraction of Entities and Relations with Multi-Task Learning.**
_Daojian Zeng, Haoran Zhang, Qianying Liu._
AAAI 2020.
[[paper]](https://arxiv.org/abs/1911.10438)

## Motivation

对[CopyRE](https://www.aclweb.org/anthology/P18-1047.pdf)进行改进，针对其不区分头尾实体生成顺序以及实体不能包括多个词的问题提出相应解决方案。

## Method

1.对于CopyRE不区分头尾实体生成顺序，分析其原因是生成头尾实体softmax分布的时候与decoder所在时间步t无关，因此在模型中间加了个非线性层使得其与t相关。2. 对于实体不能包括多个词，加入了一个BiLSTM+CRF的NER任务，然后multi-task训练。

## Problems

对于CopyRE的改进从模型来看并没有特别大变化，不过还是改得有理有据的。
