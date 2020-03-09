# Relation Extraction Papers Reading Notes
This is a relation extraction reading notes contributed by the [Shuang Zeng](https://github.com/gaotianyu1350) and [Runxin Xu](https://github.com/RunxinXu).

* [Datasets](#datasets)
* [Survey Papers](#survey-papers)
* [Journal and Conference Papers](#journal-and-conference-papers)

## Datasets
### Sentence-Level Relation Extraction

1. **ACE 2005 Dataset**. [[link]](https://catalog.ldc.upenn.edu/LDC2006T06) [[paper]](https://www.semanticscholar.org/paper/The-ACE-2005-(-ACE-05-)-Evaluation-Plan-Evaluation-Ntroduction/3a9b136ca1ab91592df36f148ef16095f74d009e)
2. **SemEval-2010 Task 8 Dataset**. [[link]](http://semeval2.fbk.eu/semeval2.php?location=tasks#T11) [[paper]](https://www.aclweb.org/anthology/W09-2415)
3. **TACRED**. [[link]](https://nlp.stanford.edu/projects/tacred/) [[paper]](https://nlp.stanford.edu/pubs/zhang2017tacred.pdf)

### Distantly Supervised Relation Extraction Datasets

1. **NYT Dataset**. [[link]](http://iesl.cs.umass.edu/riedel/ecml/) [[paper]](https://dl.acm.org/citation.cfm?id=1889799)

### Few-shot Relation Extraction Datasets

1. **FewRel**. [[link]](https://github.com/thunlp/fewrel) [[1.0 paper]](https://www.aclweb.org/anthology/D18-1514/) [[2.0 paper]](https://doi.org/10.18653/v1/D19-1649)

### Document-Level Relation Extraction Datasets

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

### Neural Encoders
1. **CopyMTL: Copy Mechanism for Joint Extraction of Entities and Relations with Multi-Task Learning.**
  _Daojian Zeng, Haoran Zhang, Qianying Liu._
  AAAI 2020.
  [paper](https://arxiv.org/abs/1911.10438)
    ```
    Motivation: 对[CopyRE](https://www.aclweb.org/anthology/P18-1047.pdf)进行改进，针对其不区分头尾实体生成顺序以及实体不能包括多个词的问题提出相应解决方案。
    Method:1.对于CopyRE不区分头尾实体生成顺序，分析其原因是生成头尾实体softmax分布的时候与decoder所在时间步t无关，因此在模型中间加了个非线性层使得其与t相关。2. 对于实体不能包括多个词，加入了一个BiLSTM+CRF的NER任务，然后multi-task训练。
    Problems: 对于CopyRE的改进从模型来看并没有特别大变化，不过还是改得有理有据的。
    Github: https://github.com/WindChimeRan/CopyMTL
    Note Link：[Note](https://github.com/DreamInvoker/RE_papers/blob/master/CopyMTL%20Copy%20Mechanism%20for%20Joint%20Extraction%20of%20Entities%20and%20Relations%20with%20.pdf)
    ```
2.

### 
