**Graph Neural Networks with Generated Parameters for Relation Extraction.**
_Hao Zhu, Yankai Lin, Zhiyuan Liu, Jie Fu, Tat-seng Chua, Maosong Sun._
ACL 2019.
[[paper]](https://www.aclweb.org/anthology/P19-1128/)


## Motivation

现有的关系抽取模型不能很好的解决多跳推理问题，而GNN做多跳推理已经有很多研究，但都是在预先定义好的图上，因此，本工作探索如何在在富文本信息上做信息传递（GCN message-passing)
          
## Method

首先构造一个全连接的实体图（实体的初始表示为0或者one-hot向量），然后分为三个组件。1.编码组件，负责将原文信息编码，生成图上边的表示；2.信息传递组件，使用第1步得到的边的信息，对图做GCN；3.使用得到的节点表示做实体对的关系预测。

## Problems

1.每层GCN都生成边的参数，不同层（hop）之间的推理没有交互；2.刚开始是全链接的图，实体表示为0，可能不是一个很好的选择；3.分类端只使用了节点的信息，没有加入边（关系）的信息。
