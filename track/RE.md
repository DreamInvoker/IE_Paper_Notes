
# Relation Extraction
* [Datasets](#datasets)
* [Survey Papers](#survey-papers)
* [Journal and Conference Papers](#journal-and-conference-papers)
   * [Sentence-Level RE Methods](#sentence-level-re-methods)
   * [Document-level RE Methods](#document-level-re-methods)
   * [Joint Extraction of Entities and Relations Methods](#joint-extraction-of-entities-and-relations-methods)
   * [Distant Supervised Methods](#distant-supervised-methods)
   * [Few Shot RE Methods](#few-shot-re-methods)

## Datasets
### Sentence-Level Datasets

1. **ACE 2005 Dataset**. [[link]](https://catalog.ldc.upenn.edu/LDC2006T06) [[paper]](https://www.semanticscholar.org/paper/The-ACE-2005-(-ACE-05-)-Evaluation-Plan-Evaluation-Ntroduction/3a9b136ca1ab91592df36f148ef16095f74d009e)
2. **SemEval-2010 Task 8 Dataset**. [[link]](http://semeval2.fbk.eu/semeval2.php?location=tasks#T11) [[paper]](https://www.aclweb.org/anthology/W09-2415)
3. **TACRED**. [[link]](https://nlp.stanford.edu/projects/tacred/) [[paper]](https://nlp.stanford.edu/pubs/zhang2017tacred.pdf)

### Document-Level Datasets

1. **SciREX**. ACL 2020. [[link]](https://github.com/allenai/SciREX) [[paper]](https://www.aclweb.org/anthology/2020.acl-main.670/)
2. **DocRED**. ACL 2019. [[link]](https://github.com/thunlp/DocRED) [[paper]](https://www.aclweb.org/anthology/P19-1074/)
3. **GDA**. RECOM 2019. [[link]](https://bitbucket.org/alexwuhkucs/gda-extraction/get/fd4a7409365e.zip) [[paper]](https://link.springer.com/chapter/10.1007/978-3-030-17083-7_17) [[preprocess]](https://github.com/fenchri/edge-oriented-graph)
4. **SciERC**. EMNLP 2018. [[link]](https://bitbucket.org/luanyi/scierc/src/master/) [[paper]](https://www.aclweb.org/anthology/D18-1360/)
5. **CDR**. Database 2016. [[link1]](https://biocreative.bioinformatics.udel.edu/tasks/biocreative-v/track-3-cdr/) [[link2]](https://figshare.com/articles/GLRE_data/12385979) [[paper]](https://doi.org/10.1093/database/baw068) [[preprocess]](https://github.com/fenchri/edge-oriented-graph)

### Distantly Supervised Datasets

1. **NYT Dataset**. [[link]](http://iesl.cs.umass.edu/riedel/ecml/) [[paper]](https://dl.acm.org/citation.cfm?id=1889799)

### Few-shot Datasets

1. **FewRel**. [[link]](https://github.com/thunlp/fewrel) [[1.0 paper]](https://www.aclweb.org/anthology/D18-1514/) [[2.0 paper]](https://doi.org/10.18653/v1/D19-1649)

## Survey papers

1. **[Relation Extraction Using Distant Supervision: A Survey](https://exascale.info/assets/pdf/smirnova2019acmcsur.pdf).**
   _ALISA SMIRNOVA and PHILIPPE CUDRÉ-MAUROUX._ ACM Computing Surveys 2018.

2. **[A Survey of Deep Learning Methods for Relation Extraction](https://arxiv.org/pdf/1705.03645.pdf).**
   _Shantanu Kumar._ Arxiv Preprint 2017.
   
3. **[Relation Extraction : A Survey](https://arxiv.org/pdf/1712.05191.pdf).**
   _Sachin Pawara,b, Girish K. Palshikara, Pushpak Bhattacharyyab._ Arxiv Preprint 2017.

4. **[A Review of Relation Extraction](https://www.cs.cmu.edu/~nbach/papers/A-survey-on-Relation-Extraction.pdf).**
   _Nguyen Bach, Sameer Badaskar._ 2017.
   
5. **[More Data, More Relations, More Context and More Openness: A Review and Outlook for Relation Extraction](https://arxiv.org/pdf/2004.03186.pdf).**
   _Xu Han, Tianyu Gao, Yankai Lin, Hao Peng, Yaoliang Yang, Chaojun Xiao, Zhiyuan Liu, Peng Li, Maosong Sun, Jie Zhou._ Arxiv Preprint 2020.
   
6. **[Neural relation extraction: a survey](https://arxiv.org/pdf/2007.04247.pdf).**
   _Mehmet Aydar, Ozge Bozal, Furkan Ozbay._ Arxiv Preprint 2020.

## Journal and Conference Papers

### Sentence-Level RE Methods

1. **Beyond Word Attention: Using Segment Attention in Neural Relation Extraction.**
_Bowen Yu, Zhenyu Zhang, Tingwen Liu, Bin Wang, Sujian Li, Quangang Li._
IJCAI 2019.
[[paper]](https://www.ijcai.org/Proceedings/2019/750)
[[code]](https://github.com/yubowen-ph/segment)
[[note]](../notes/RE/sentence-level/SA-LSTM.md)
[[file]](../files/RE/sentence-level/SA-LSTM.pdf)
 
2. **Matching the Blanks Distributional Similarity for Relation Learning.**
_Livio Baldini Soares, Nicholas FitzGerald, Jeffrey Ling, Tom Kwiatkowski._
ACL 2019.
[[paper]](https://arxiv.org/abs/1906.03158)
[[code]](https://github.com/zhpmatrix/BERTem)
[[note]](../notes/RE/sentence-level/Matching-the-Blanks.md)
[[file]](../files/RE/sentence-level/Matching-the-Blanks.pdf)

3. **Attention Guided Graph Convolutional Networks for Relation Extraction.**
_Yan Zhang, Zhijiang Guo, Wei Lu._
ACL 2019.
[[paper]](https://arxiv.org/abs/1906.07510)
[[code]](https://github.com/Cartus/AGGCN)
[[note]](../notes/RE/sentence-level/AGGCN.md)
[[file]](../files/RE/sentence-level/AGGCN.pdf)

4. **Relation Extraction as Two-way Span-Prediction.**
_Amir DN Cohen, Shachar Rosenman, Yoav Goldberg._
arxiv 2020.
[[paper]](https://arxiv.org/abs/2010.04829)
[[code]]()
[[note]](../notes/RE/sentence-level/QA-RE.md)
[[file]](../files/RE/sentence-level/QA-RE.pdf)
  
### Document-level RE Methods

1. **Global-to-Local Neural Networks for Document-Level Relation Extraction.**
_Difeng Wang, Wei Hu, Ermei Cao, Weijian Sun._
EMNLP 2020.
[[paper]](https://arxiv.org/abs/2009.10359)
[[code]](https://github.com/nju-websoft/GLRE)
[[note]](../notes/RE/document-level/GLRE.md)
[[file]](../files/RE/document-level/GLRE.pdf)

2. **Document-Level Relation Extraction with Adaptive Thresholding and Localized Context Pooling.**
_Wenxuan Zhou, Kevin Huang, Tengyu Ma, Jing Huang._
ArXiv 2020.
[[paper]](https://arxiv.org/abs/2010.11304)
[[code]](https://github.com/wzhouad/ATLOP)
[[note]](../notes/RE/document-level/ATLOP.md)
[[file]](../files/RE/document-level/ATLOP.pdf)

### Joint Extraction of Entities and Relations Methods
1. **CopyMTL: Copy Mechanism for Joint Extraction of Entities and Relations with Multi-Task Learning.**
_Daojian Zeng, Haoran Zhang, Qianying Liu._
AAAI 2020.
[[paper]](https://arxiv.org/abs/1911.10438)
[[code]](https://github.com/WindChimeRan/CopyMTL)
[[note]](../notes/RE/joint/CopyMTL.md)
[[file]](../files/RE/joint/CopyMTL.pdf)

2. **A Novel Hierarchical Binary Tagging Framework for Joint Extraction of Entities and Relations.**
_Zhepei Wei, Jianlin Su, Yue Wang, Yuan Tian, Yi Chang._
AAAI 2020.
[[paper]](https://arxiv.org/abs/1909.03227)
[[code]]()
[[note]](../notes/RE/joint/HBT.md)
[[file]](../files/RE/joint/HBT.pdf)
    
3. **GraphRel: Modeling Text as Relational Graphs for Joint Entity and Relation Extraction.**
_Tsu-Jui Fu, Peng-Hsuan Li, Wei-Yun Ma._
ACL 2019.
[[paper]](https://www.aclweb.org/anthology/P19-1136/)
[[code]]()
[[note]](../notes/RE/joint/GraphRel.md)
[[file]](../files/RE/joint/GraphRel.pdf)
 
4. **Span-Level Model for Relation Extraction.**
_Kalpit Dixit, Yaser Al-Onaizan._
ACL 2019.
[[paper]](https://www.aclweb.org/anthology/P19-1525/)
[[code]]()
[[note]](../notes/RE/joint/Span-model.md)
[[file]](../files/RE/joint/Span-model.pdf)
    
5. **Span-based Joint Entity and Relation Extraction with Transformer Pre-training.**
_Markus Eberts and Adrian Ulges._
arxiv 2019.
[[paper]](https://arxiv.org/abs/1909.07755)
[[code]](https://github.com/markus-eberts/spert)
[[note]](../notes/RE/joint/SpERT.md)
[[file]](../files/RE/joint/SpERT.pdf)

6. **Minimize Exposure Bias of Seq2Seq Models in Joint Entity and Relation Extraction.**
Ranran Haoran Zhang, Qianying Liu, Aysa Xuemo Fan, Heng Ji, Daojian Zeng,Fei Cheng, Daisuke Kawahara and Sadao Kurohashi
EMNLP 2020.(finding)
[[paper]](https://arxiv.org/pdf/2009.07503.pdf)
[[code]](https://github.com/WindChimeRan/OpenJERE)
[[note]](../notes/RE/joint/Seq2UMTree.md)
[[file]](../files/RE/joint/Seq2UMTree.pdf)

7. **Recurrent Interaction Network for Jointly Extracting Entities and Classifying Relations.**
Kai Sun, Richong Zhang, Samuel Mensah, Yongyi Mao, Xudong Liu
EMNLP2020.
[[paper]](https://arxiv.org/abs/2005.00162)
[[file]](../files/RE/joint/Recurrent-Interaction-Network.pdf)

8. **Two are Better than One:Joint Entity and Relation Extraction with Table-Sequence Encoders.**
Jue Wang and Wei Lu
EMNLP2020.
[[paper]](https://arxiv.org/pdf/2010.03851)
[[code]](https://github.com/LorrinWWW/two-are-better-than-one)
[[note]](../notes/RE/joint/Two-are-Better-than-One.md)
[[file]](../files/RE/joint/Two-are-Better-than-One.pdf)

### Distant Supervised Methods
1. **Relation Extraction with Temporal Reasoning Based on Memory Augmented Distant Supervision.**
_Jianhao Yan, Lin He, Ruqin Huang, Jian Li, Ying Liu._
NAACL 2019.
[[paper]](https://www.aclweb.org/anthology/N19-1107/)
[[code]](https://github.com/ElliottYan/DS_Temporal)
[[note]](../notes/RE/distant-supervised/TempMEM.md)
[[file]](../files/RE/distant-supervised/TempMEM.pdf)

2. **Effective Deep Memory Networks for Distant Supervised Relation Extraction.**
_Xiaocheng Feng, Jiang Guo, Bing Qin, Ting Liu, Yongjie Liu SCIR._
IJCAI 2017.
[[paper]](https://www.ijcai.org/Proceedings/2017/559)
[[code]]()
[[note]](../notes/RE/distant-supervised/DMN.md)
[[file]](../files/RE/distant-supervised/DMN.pdf)
    
3. **Self-Attention Enhanced CNNs and Collaborative Curriculum Learning for Distantly Supervised Relation Extraction.**
_Yuyun Huang Jinhua Du._
EMNLP 2019.
[[paper]](https://www.aclweb.org/anthology/D19-1037/)
[[code]]()
[[note]](../notes/RE/distant-supervised/Self-Attention-Enhanced-CNNs-and-Collaborative-Curriculum-Learning-for-Dist.md)
[[file]](../files/RE/joint/Self-Attention-Enhanced-CNNs-and-Collaborative-Curriculum-Learning-for-Dist.pdf)

4. **Graph Neural Networks with Generated Parameters for Relation Extraction.**
_Hao Zhu, Yankai Lin, Zhiyuan Liu, Jie Fu, Tat-seng Chua, Maosong Sun._
ACL 2019.
[[paper]](https://www.aclweb.org/anthology/P19-1128/)
[[code]](https://github.com/thunlp/gp-gnn)
[[note]](../notes/RE/distant-supervised/GP-GNN.md)
[[file]](../files/RE/joint/GP-GNN.pdf)

5. **Looking Beyond Label Noise: Shifted Label Distribution Matters in Distantly Supervised Relation Extraction.**
_Qinyuan Ye, Liyuan Liu, Maosen Zhang, Xiang Ren._
EMNLP 2019.
[[paper]](https://arxiv.org/abs/1904.09331)
[[code]](https://github.com/INK-USC/shifted-label-distribution)
[[note]](../notes/RE/distant-supervised/Label-Noise.md)
[[file]](../files/RE/distant-supervised/Label-Noise.pdf)

### Few Shot RE methods
1. **FewRel: A Large-Scale Supervised Few-Shot Relation Classification Dataset with State-of-the-Art Evaluation**
_Han, X., Zhu, H., Yu, P., Wang, Z., Yao, Y., Liu, Z., & Sun, M._
EMNLP2018
[[paper]](https://www.aclweb.org/anthology/D18-1514.pdf)
[[code]](https://github.com/thunlp/FewRel)
[[note]](../notes/RE/few-shot/few1.0.md)
[[file]](../files/RE/few-shot/few1.0.pdf)
