# Relation Extraction Papers Reading Notes
This is a relation extraction reading notes repo contributed by the [Shuang Zeng](https://github.com/gaotianyu1350) and [Runxin Xu](https://github.com/RunxinXu).

* [Datasets](#datasets)
* [Survey Papers](#survey-papers)
* [Journal and Conference Papers](#journal-and-conference-papers)
    * [Sentence-Level RE Methods](#sentence-level-re-methods)
    * [Joint Extraction of Entities and Relations Methods](#joint-extraction-of-entities-and-relations-methods)
    * [Distant Supervised Methods](#distant-supervised-methods)

## Datasets
### Sentence-Level Datasets

1. **ACE 2005 Dataset**. [[link]](https://catalog.ldc.upenn.edu/LDC2006T06) [[paper]](https://www.semanticscholar.org/paper/The-ACE-2005-(-ACE-05-)-Evaluation-Plan-Evaluation-Ntroduction/3a9b136ca1ab91592df36f148ef16095f74d009e)
2. **SemEval-2010 Task 8 Dataset**. [[link]](http://semeval2.fbk.eu/semeval2.php?location=tasks#T11) [[paper]](https://www.aclweb.org/anthology/W09-2415)
3. **TACRED**. [[link]](https://nlp.stanford.edu/projects/tacred/) [[paper]](https://nlp.stanford.edu/pubs/zhang2017tacred.pdf)

### Distantly Supervised Datasets

1. **NYT Dataset**. [[link]](http://iesl.cs.umass.edu/riedel/ecml/) [[paper]](https://dl.acm.org/citation.cfm?id=1889799)

### Few-shot Datasets

1. **FewRel**. [[link]](https://github.com/thunlp/fewrel) [[1.0 paper]](https://www.aclweb.org/anthology/D18-1514/) [[2.0 paper]](https://doi.org/10.18653/v1/D19-1649)

### Document-Level Datasets

1. **DocRED**. [[link]](https://github.com/thunlp/DocRED) [[paper]](https://www.aclweb.org/anthology/P19-1074/)

## Survey papers

1. **Relation Extraction Using Distant Supervision: A Survey.**
   _ALISA SMIRNOVA and PHILIPPE CUDRÉ-MAUROUX._ ACM Computing Surveys 2018.
   [paper](https://exascale.info/assets/pdf/smirnova2019acmcsur.pdf)

2. **A Survey of Deep Learning Methods for Relation Extraction.**
   _Shantanu Kumar._ Arxiv Preprint 2017.
   [paper](https://arxiv.org/pdf/1705.03645.pdf)

3. **Relation Extraction : A Survey.**
   _Sachin Pawara,b, Girish K. Palshikara, Pushpak Bhattacharyyab._ Arxiv Preprint 2017.
   [paper](https://arxiv.org/pdf/1712.05191.pdf)

4. **A Review of Relation Extraction.**
   _Nguyen Bach, Sameer Badaskar._ 2017.
   [paper](https://www.cs.cmu.edu/~nbach/papers/A-survey-on-Relation-Extraction.pdf)                                                                                                                                                                                                              

## Journal and Conference Papers

### Sentence-Level RE Methods

1. **Beyond Word Attention: Using Segment Attention in Neural Relation Extraction.**
  _Bowen Yu, Zhenyu Zhang, Tingwen Liu, Bin Wang, Sujian Li, Quangang Li._
  IJCAI 2019.
  [paper](https://www.ijcai.org/Proceedings/2019/750)
  
    Motivation: 1.基于采样调查发现，一般的关系表达(relation expression)是连续的词片段，提出Segment Attention. 2.前人方法使用attention机制进行降噪, 但对于每个词仅仅是soft selection，没有明确目标.
    
    Method: 1.输入为词向量 + Positional Feature, 过了BiLSTM得到每个词的上下文表示，然后使用CRF为每个词生成一个二项分布隐变量，并得到所有隐状态的概率分布然后加权组合表达整个关系实例。2.loss加入transition正则器（用于将约束转移特征值）和sparse正则器（得到稀疏的权重分布以focus更少的词）.

    Problems: 模型比较简单，就是将传统的attention变成了分段attention，这样的改进仅仅是让分类层的输入有更好的表达，并且segment attention可能会学不到一些模式，比如paper提出的实体重叠问题。
    
    Github: [https://github.com/yubowen-ph/segment](https://github.com/yubowen-ph/segment) 
    
    Note Link：[Note](notes/SA-LSTM.pdf)
 
 2. **Matching the Blanks Distributional Similarity for Relation Learning.**
  _Livio Baldini Soares, Nicholas FitzGerald, Jeffrey Ling, Tom Kwiatkowski._
  ACL 2019.
  [paper](https://arxiv.org/abs/1906.03158)
  
    Motivation: 从预训练模型的角度来看怎么更好地服务于relation learning，希望通过更好的pre-train的训练目标与方法、更好的fine-tune的方式来达到更好的关系抽取效果。
    
    Method: paper主要分为两部分：1. 探究怎样使用Transformer效果更好，通过实验得到的结论是，在entity前后都插入相应的标记，并且使用entity前面的这个标记对应的输出作为下游分类器的输入效果最好；2. 设计了一个预训练方法，就是假设句子出现同样实体对的，提取的关系应该越接近。所以两个句子作为输入，然后拉近/扯远他们的相似度。同时为了防止模型忽略了句子上下文，因此随机地对实体进行[mask]。

    Problems: Google paper的风格，但是其实它的这个假设不是特别靠谱，只能说在无监督的预训练过程中还比较可靠。
    
    Github: https://github.com/zhpmatrix/BERTem
    
    Note Link：[Note](notes/Matching-the-Blanks.pdf)

 3. **Attention Guided Graph Convolutional Networks for Relation Extraction.**
  _Yan Zhang, Zhijiang Guo, Wei Lu._
  ACL 2019.
  [paper](https://arxiv.org/abs/1906.07510)
  
    Motivation: 前人使用剪枝后的依存树来做关系抽取，但是容易将一些重要的信息给剪掉，因此本文提出一种软剪枝的策略，来让模型学习怎么去给依存树上的边给定权重
    
    Method: 首先将句子变成依存树（数据集给定），然后将依存树加上自环和反向连接变成依存图，然后通过Attention Guided Layer，将原始的依存图变成N个不同的全连接的图，每个图过DCGCN，来得到最终图的表示进行合并。

    Problems: Attention Guided Layer使用Self-Attention，其实类似于用了GAT，只不过这个attention系数不是根据GAT的公式计算出来，而是单独拿出来进行学习，所以感觉可以用DCGAT(Densely)来对比一下
    
    Github: [https://github.com/Cartus/AGGCN](https://github.com/Cartus/AGGCN)
    
    Note Link：[Note](notes/AGGCN.pdf)
 
    
### Joint Extraction of Entities and Relations Methods
1. **CopyMTL: Copy Mechanism for Joint Extraction of Entities and Relations with Multi-Task Learning.**
  _Daojian Zeng, Haoran Zhang, Qianying Liu._
  AAAI 2020.
  [paper](https://arxiv.org/abs/1911.10438)
  
    Motivation: 对[CopyRE](https://www.aclweb.org/anthology/P18-1047.pdf)进行改进，针对其不区分头尾实体生成顺序以及实体不能包括多个词的问题提出相应解决方案。
    
    Method: 1.对于CopyRE不区分头尾实体生成顺序，分析其原因是生成头尾实体softmax分布的时候与decoder所在时间步t无关，因此在模型中间加了个非线性层使得其与t相关。2. 对于实体不能包括多个词，加入了一个BiLSTM+CRF的NER任务，然后multi-task训练。

    Problems:对于CopyRE的改进从模型来看并没有特别大变化，不过还是改得有理有据的。
    
    Github: [https://github.com/WindChimeRan/CopyMTL](https://github.com/WindChimeRan/CopyMTL)
    
    Note Link：[Note](notes/CopyMTL.pdf)
    
2. **A Novel Hierarchical Binary Tagging Framework for Joint Extraction of Entities and Relations.**
  _Zhepei Wei, Jianlin Su, Yue Wang, Yuan Tian, Yi Chang._
  AAAI 2020.
  [paper](https://arxiv.org/abs/1909.03227)
  
    Motivation: 之前RE的方法无法解决同个实体属于多个关系的情况，也就是一个实体最多指定到一个关系中。CopyRE是最近第一个显式解决这个问题的，但是效果还不够好。这篇paper主要就是为了解决这个问题，提出了一个层次标注的方法同时做实体抽取和关系抽取。
    
    Method: 用BERT编码输入句子，之后decoder端有两层tagger。第一层tagger先做序列标注标出可能的头实体，之后每个relation有自己一套参数，给定头实体和某个relation，可以在第二层tagger上继续做序列标注标注出可能的尾实体，这样就得到了一个(h,r,t)三元组。方法简单粗暴，效果很好。

    Problems: 想法不复杂，但是参数量会随关系种类线性增长，在relation种类多的情况下可能对硬件要求较高。
    
    Github: unrelease
    
    Note Link：[Note](notes/HBT.pdf)

 3. **GraphRel: Modeling Text as Relational Graphs for Joint Entity and Relation Extraction.**
  _Tsu-Jui Fu, Peng-Hsuan Li, Wei-Yun Ma._
  ACL 2019.
  [paper](https://www.aclweb.org/anthology/P19-1136/)
  
    Motivation: 试图统一将RE中的三个要点融合在一个架构中。1.端到端的命名实体识别和关系抽取的联合建模；2.预测那些共有一个实体的关系；3.考虑关系间的交互，尤其是重叠关系
    
    Method: 使用两阶段进行端到端的联合实体抽取和关系抽取。1.第一阶段使用BiLSTM和BiGCN对原文进行编码，以获得序列信息和依存信息，然后计算分类loss得到边权；（2）第二阶段使用第一阶段得到的全连接边权图，再做BiGCN以使不同关系之间可以交互，并最终得到第二阶段的分类loss

    Problems: 工作挺novel的，没有啥问题
    
    Github: unreleased
    
    Note Link：[Note](notes/GraphRel.pdf)
    
4. **Span-Level Model for Relation Extraction.**
  _Kalpit Dixit, Yaser Al-Onaizan._
  ACL 2019.
  [paper](https://www.aclweb.org/anthology/P19-1525/)
  
    Motivation: 之前有工作针对实体可能作为多个关系的head/tail来进行改进，但是其实还有一种情况是在进行NER的时候，其实也有可能产生实体重叠，这里的实体重叠指的是同一个word属于不同的entity，比如“常宝宝老师”，“常宝宝”，可以是两个实体。
    
    Method: paper提出的方法就是遍历所有的span，把他们独立进行joint learning，判断这个span是否是实体，同时判断与其他实体的关系。为了减少复杂度，实验的时候限定了span的最长长度。

    Problems: 遍历所有可能的span听起来还是太暴力的，尽管它是一种解决方法。
    
    Github: unreleased
    
    Note Link：[Note](notes/Span-model.pdf)
    
5. **Span-based Joint Entity and Relation Extraction with Transformer Pre-training.**
  _Markus Eberts and Adrian Ulges._
   arxiv.
  [paper](https://arxiv.org/abs/1909.07755)
  
    Motivation: 与上一篇相同，也是为了解决NER中实体重叠问题。
    
    Method: 与上一篇不同的是，这里把LSTM换成了BERT，然后编码span的时候用到了BERT [cls]对应位置的输出作为全局context信息。而在预测两个entity的关系的时候，利用两个entity中间的文字context信息，做了实验验证了这样做比用全局context更好。

    Problems: 和上一篇的问题一样，遍历所有的Span总感觉不是特别优雅。
    
    Github: https://github.com/markus-eberts/spert
    
    Note Link：[Note](notes/SpERT.pdf)
    

### Distant Supervised Methods
1. **Relation Extraction with Temporal Reasoning Based on Memory Augmented Distant Supervision.**
  _Jianhao Yan, Lin He, Ruqin Huang, Jian Li, Ying Liu._
  NAACL 2019.
  [paper](https://www.aclweb.org/anthology/N19-1107/)
  
    Motivation: 前人DS RE的工作忽略了关系实例中的时间信息，比如实体对在今天和明天可能是不同的关系，所以本文提出了一个新的任务，即从时序的角度推理实体对之间的关系，并提出专门针对时序RE的新数据集[WIKITIME](https://github.com/ElliottYan/DS_Temporal)
              
    Method: 基于前人encoding + fusion的架构, 将时序RE看做是在memory上的序列标注任务。1.在encoding阶段引入时间编码来建模bag中instance之间的时序信息；2.在fusion阶段，使用Memory Network对经过时间信息增强后的句子编码进行迭代地推理。
    
    Problems: 对于给定时间点两个实体对之间的关系，有这样的数据集来做固然是很好的，但是没法从根本上解决公开数据集关于时间序列RE的问题。
    
    Github: [https://github.com/ElliottYan/DS_Temporal](https://github.com/ElliottYan/DS_Temporal)
  
    Note Link: [Note](notes/TempMEM.pdf)

2. **Effective Deep Memory Networks for Distant Supervised Relation Extraction.**
  _Xiaocheng Feng, Jiang Guo, Bing Qin, Ting Liu, Yongjie Liu SCIR._
  IJCAI 2017.
  [paper](https://www.ijcai.org/Proceedings/2017/559)
  
    Motivation: DS RE通常用多实例多标签学习的方法来解决，本文针对多实例的attention机制，提出两个基于attention机制的memory组件来同时显式地捕捉context word的信息（比如instance中的每个词对分类的关系贡献程度不一样）和关系类别之间的内在依存信息（比如两个关系类别可能有对称关系或者蕴含关系）
              
    Method: 使用两个基于attention机制的memory network。1.词级别的memory，用于学习每个context word对实体对关系的贡献程度；2.两层关系级别的memory, 用于得到关系的表示并进行最终bag级别的所有关系类别的二分类
  
    Problems: 用到的memory只有query功能，没有update和forget功能。
    
    Github: unreleased
  
    Note Link: [Note](notes/DMN.pdf)
    
3. **Self-Attention Enhanced CNNs and Collaborative Curriculum Learning for Distantly Supervised Relation Extraction.**
  _Yuyun Huang Jinhua Du._
  EMNLP 2019.
  [paper](https://www.aclweb.org/anthology/D19-1037/)
  
    Motivation: 对于DS，不同bag-level的relation prediction模型被提出，这篇paper的目的是用某种机制把他们的优点结合起来，更好地排除DS中false positive数据的干扰。
              
    Method: 使用两个不同bag-level relation prediction的模型：一个是从中选出最大概率的；一个是用attention软聚合的。两个模型共同学习，对于某个bag，如果两个模型预测出来其中最大概率的句子相同，就认为是easy的样本，加进去算loss；如果不相同，认为是difficult的样本，不加进去学习。然后还加了一个两个模型预测出来的最大概率句子的交叉熵作为正则项，让两个模型预测倾向更紧密。
  
    Problems: 
    
    Github: unreleased
  
    Note Link: [Note](notes/Self-Attention-Enhanced-CNNs-and-Collaborative-Curriculum-Learning-for-Dist.pdf)

4. **Graph Neural Networks with Generated Parameters for Relation Extraction.**
  _Hao Zhu, Yankai Lin, Zhiyuan Liu, Jie Fu, Tat-seng Chua, Maosong Sun._
  ACL 2019.
  [paper](https://www.aclweb.org/anthology/P19-1128/)
  
    Motivation: 现有的关系抽取模型不能很好的解决多跳推理问题，而GNN做多跳推理已经有很多研究，但都是在预先定义好的图上，因此，本工作探索如何在在富文本信息上做信息传递（GCN message-passing)
              
    Method: 首先构造一个全连接的实体图（实体的初始表示为0或者one-hot向量），然后分为三个组件。1.编码组件，负责将原文信息编码，生成图上边的表示；2.信息传递组件，使用第1步得到的边的信息，对图做GCN；3.使用得到的节点表示做实体对的关系预测。
  
    Problems: 1.每层GCN都生成边的参数，不同层（hop）之间的推理没有交互；2.刚开始是全链接的图，实体表示为0，可能不是一个很好的选择；3.分类端只使用了节点的信息，没有加入边（关系）的信息。
    
    Github: [https://github.com/thunlp/gp-gnn](https://github.com/thunlp/gp-gnn)
  
    Note Link: [Note](notes/GP-GNN.pdf)
    
5. **Looking Beyond Label Noise: Shifted Label Distribution Matters in Distantly Supervised Relation Extraction.**
  _Qinyuan Ye, Liyuan Liu, Maosen Zhang, Xiang Ren._
  EMNLP 2019.
  [paper](https://arxiv.org/abs/1904.09331)
  
    Motivation: 利用神经网络进行关系抽取的方法，在人工标注数据集上比传统基于特征的方法提升较大，但是在远程监督的数据集上却提升不是特别大。因此通过一系列的实验来探究内在原因。
              
    Method: 先是提出了两种阈值过滤的方法，通过实验反映出问题可能是远程监督数据集在训练集与测试集的标签分布不太一致（训练集是远程监督自动标注，测试集用于测试是人工标注），之后通过数学推导提出了基于偏差补偿的方法。
  
    Problems: 挺好的一篇paper，通过实验一步一步递进地探究，感觉不出什么太大的问题！
    
    Github: https://github.com/INK-USC/shifted-label-distribution
  
    Note Link: [Note](notes/Label-Noise.pdf)
