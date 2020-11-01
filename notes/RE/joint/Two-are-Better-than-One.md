**Two are Better than One: Joint Entity and Relation Extraction with Table-Sequence Encoders** ———— 
Jue Wang1 and Wei Lu2&nbsp;[[paper]](https://arxiv.org/pdf/2010.03851)  

### Introduction  
&nbsp;&nbsp;&nbsp;&nbsp;本文提出的table filling模型是基于句子级别的实体识别和关系分类联合抽取任务，1、首先作者分析了传统的联合抽取模型存在的
feature confusion问题，也就是使用一个特征来编码关系和实体，以此解决NER与RE问题会导致模型无法很好区分实体和关系2、传统的table filling并未充分利用
table的特征，而只是将其作为一个序列标注任务，将table中的格子标上特定的标识符  

### Motivation  
&nbsp;&nbsp;&nbsp;&nbsp;由于上述所说的传统的table filling模型具有的局限性，因此作者认为只有一个encoder对句子进行编码得到token的特征是不够的，
将table也要进行编码，使用两个编码器得到两个embedding，一个进行关系分类，一个进行实体识别  

### Method  
&nbsp;&nbsp;&nbsp;&nbsp;作者提出两个encoder架构，一个encoder编码句子，一个encoder编码table，并且两个encoder之间会进行信息的交互，也就是table的
特征会被句子encoder使用，句子的特征会被table的encoder使用，如此往复迭代多层，最终得到较好的embedding，同时进行关系分类和实体识别。并且作者还会
将BERT的attention权重加入到模型中以提高表现  

### Problem  
&nbsp;&nbsp;&nbsp;&nbsp;作者提出的双encoder结构比较充分的利用了table和句子的信息，并且也利用了BERT的attention权重提升模型的表现，但是table filling
的方法仍然存在局限性，很多的实体之间并不存在相应关系，会造成样本不均衡的问题，positive的样本会被稀释，并且table的encoder仍然可以进行改进  
