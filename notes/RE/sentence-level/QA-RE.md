**Relation Extraction as Two-way Span-Prediction.**
_Amir DN Cohen, Shachar Rosenman, Yoav Goldberg._
arxiv 2020.
[[paper]](https://arxiv.org/abs/2010.04829)

## Motivation

将传统的relation classification (RC)转变成基于QA的span prediction的任务，在TACRED和SemEval上取得了最新的SOTA。

## Method

(Levy et al., 2017)是第一次将QA任务引入到句子级关系抽取任务中来的，与前人不同的是，本文使用双向的question（1.给定context，head，relation；2.给定context，tail，relation），对于每个实体对，设计2|R|个关系，作者任务通过QA的方式预测span可以引入语义信息。

## Problems

没有给代码，不具有解释性，模型简单粗暴效果还好，对于一个关系不同的实体类别的compatibility问题没有解释清楚。

  