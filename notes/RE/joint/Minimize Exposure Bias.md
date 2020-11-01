**Minimize Exposure Bias of Seq2Seq Models in Joint Entity and Relation Extraction** ———— Ranran Haoran Zhang1, Qianying Liu2, Aysa Xuemo Fan1, Heng Ji1, Daojian Zeng4,Fei Cheng2, Daisuke Kawahara3 and Sadao Kurohashi2&nbsp;[[paper]](https://arxiv.org/pdf/2009.07503.pdf)  

### Introduction  
&nbsp;&nbsp;&nbsp;&nbsp;作者首先分析以前的pipeline的方式存在的缺陷：1.忽略了实体与关系存在的内部联系&nbsp;2.会造成错误传递的问题（例如：实体预测出错，那后面的关系分类肯定出错），接着作者指出现有的Seq2Seq models会引入exposure bias problem造成模型的结果不好，所谓exposure bias problem也就是训练集与测试集decode的过程不同所导致（例如：在训练时decoder部分会有gold-standard labels来预测，而测试时模型当前预测是基于模型前一个预测的结果，而一旦前面预测出错也会导致模型接下来预测出错），基于此问题也容易导致训练模型时的过拟合问题，这会导致在预测过程中模型会忽略一些三元组，再者，因为有gold-standard labels的存在，在训练时会有一个固定的顺序（例如：都是h-r-t），但是其他的顺序也是正确的（例如：h-r-t和t-r-h都正确），而此顺序会对模型的表现有害。  

&nbsp;&nbsp;&nbsp;&nbsp;作者在Related Work中也分析了table filling方法的问题，第一是会造成计算复杂度增加，第二会造成样本不均衡问题，因为两个token之间任意判断关系，但事实上很多并不存在关系，这无疑造成了positive样本的稀释  

### Motivation
&nbsp;&nbsp;&nbsp;&nbsp;基于exposure bias problem和gold-standard labels所预先设定的顺序会对模型表现有损害，因此作者提出了Seq2UMTree的模型，也是遵循传统的encoder-decoder架构，只不过在解码部分是使用copy mechanism和无序的多标签分类得到最终输出，此多标签分类器可以使得模型忽略预先定义的元组顺序，以此提高模型表现  

### Method
&nbsp;&nbsp;&nbsp;&nbsp;编码器：先使用word embedding，Bi-LSTM得到句子表示，再通过convolutional layer的到另一个句子表示，作为句子表示的一个辅助  
&nbsp;&nbsp;&nbsp;&nbsp;解码器：使用LSTM进行自回归的方式解码

### Problem
&nbsp;&nbsp;&nbsp;&nbsp;从Training and Testing部分来看，作者仍然使用了teacher forcing的方法，而且在后面组织的实验中，测试了不同顺序对于模型结果的影响，最终作者在（r-t-h）顺序上取得最好结果，并且也以此作为模型的最终结果，所以我自己认为作者所提出的无序性并没有很好的解释清楚在decoder端会无序输出结果，更可能是作者尝试了不同的组合顺序对于模型的影响，并且最终也是在固定顺序下训练模型，得到最终的实验结果。但是作者所作工作也能说明不同的解码顺序对于模型的结果会有影响  
&nbsp;&nbsp;&nbsp;&nbsp;还有一点，作者在论文中指出了NYT数据集分布的不合理，测试集中90%与训练集重叠，因此在此数据集上的结果并不具有代表性，而且作者提出的模型在NYT上表现并不好，在DuIE数据集（30%重叠）上表现优于其他模型
