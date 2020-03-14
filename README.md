# Relation Extraction Papers Reading Notes
This is a relation extraction reading notes contributed by the [Shuang Zeng](https://github.com/gaotianyu1350) and [Runxin Xu](https://github.com/RunxinXu).

* [Datasets](#datasets)
* [Survey Papers](#survey-papers)
* [Journal and Conference Papers](#journal-and-conference-papers)
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

### Joint Extraction of Entities and Relations Methods
1. **CopyMTL: Copy Mechanism for Joint Extraction of Entities and Relations with Multi-Task Learning.**
  _Daojian Zeng, Haoran Zhang, Qianying Liu._
  AAAI 2020.
  [paper](https://arxiv.org/abs/1911.10438)
  
    Motivation: 对[CopyRE](https://www.aclweb.org/anthology/P18-1047.pdf)进行改进，针对其不区分头尾实体生成顺序以及实体不能包括多个词的问题提出相应解决方案。
    
    Method: 1.对于CopyRE不区分头尾实体生成顺序，分析其原因是生成头尾实体softmax分布的时候与decoder所在时间步t无关，因此在模型中间加了个非线性层使得其与t相关。2. 对于实体不能包括多个词，加入了一个BiLSTM+CRF的NER任务，然后multi-task训练。

    Problems: 对于CopyRE的改进从模型来看并没有特别大变化，不过还是改得有理有据的。
    
    Github: [https://github.com/WindChimeRan/CopyMTL](https://github.com/WindChimeRan/CopyMTL)
    
    Note Link：[Note](notes/CopyMTL.pdf)
    
2. **A Novel Hierarchical Binary Tagging Framework for Joint Extraction of Entities and Relations.**
  _Zhepei Wei, Jianlin Su, Yue Wang, Yuan Tian, Yi Chang._
  AAAI 2020.
  [paper](https://arxiv.org/abs/1909.03227)
  
    Motivation: 之前RE的方法无法解决同个实体属于多个关系的情况，也就是一个实体最多指定到一个关系中。CopyRE是最近第一个显式解决这个问题的，但是效果还不够好。这篇paper主要就是为了解决这个问题，提出了一个层次标注的方法同时做实体抽取和关系抽取。
    
    Method: 用BERT编码输入句子，之后decoder端有两层tagger。第一层tagger先做序列标注标出可能的头实体，之后每个relation有自己一套参数，给定头实体和某个relation，可以在第二层tagger上继续做序列标注标注出可能的尾实体，这样就得到了一个(h,r,t)三元组。方法简单粗暴，效果很好。

    Problems: 想法不复杂，但是参数量会随关系种类线性增长，在relation种类多的情况下可能对硬件要求较高。
    
    Github: [https://github.com/WindChimeRan/NREPapers2019](https://github.com/WindChimeRan/NREPapers2019)
    
    Note Link：[Note](notes/HBT.pdf)

### Distant Supervised Methods
1.**Relation Extraction with Temporal Reasoning Based on Memory Augmented Distant Supervision.**
  _Jianhao Yan, Lin He, Ruqin Huang, Jian Li, Ying Liu._
  NAACL 2019.
  [paper](https://www.aclweb.org/anthology/N19-1107/)
  
  Motivation: 前人DS RE的工作忽略了关系实例中的时间信息，比如实体对在今天和明天可能是不同的关系，所以本文提出了一个新的任务，即从时序的角度推理实体对之间的关系，并提出专门针对时序RE的新数据集[WIKITIME](https://github.com/ElliottYan/DS_Temporal)
              
  Method: 基于前人encoding + fusion的架构, 将时序RE看做是在memory上的序列标注任务。1.在encoding阶段引入时间编码来建模bag中instance之间的时序信息；2.在fusion阶段，使用Memory Network对经过时间信息增强后的句子编码进行迭代地推理。
  
  Github: [https://github.com/ElliottYan/DS_Temporal](https://github.com/ElliottYan/DS_Temporal)
  
  Note Link: [Note](notes/TempMEM.pdf)

2.**Effective Deep Memory Networks for Distant Supervised Relation Extraction.**
  _Xiaocheng Feng, Jiang Guo, Bing Qin, Ting Liu, Yongjie Liu SCIR._
  IJCAI 2017.
  [paper](https://www.ijcai.org/Proceedings/2017/559)
  
  Motivation: DS RE通常用多实例多标签学习的方法来解决，本文针对多实例的attention机制，提出两个基于attention机制的memory组件来同时显式地捕捉context word的信息（比如instance中的每个词对分类的关系贡献程度不一样）和关系类别之间的内在依存信息（比如两个关系类别可能有对称关系或者蕴含关系）
              
  Method: 使用两个基于attention机制的memory network。1.词级别的memory，用于学习每个context word对实体对关系的贡献程度；2.两层关系级别的memory, 用于得到关系的表示并进行最终bag级别的所有关系类别的二分类
  
  Github: unreleased
  
  Note Link: [Note](notes/DMN.pdf)