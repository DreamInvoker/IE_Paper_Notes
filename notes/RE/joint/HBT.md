**A Novel Hierarchical Binary Tagging Framework for Joint Extraction of Entities and Relations.**
_Zhepei Wei, Jianlin Su, Yue Wang, Yuan Tian, Yi Chang._
AAAI 2020.
[[paper]](https://arxiv.org/abs/1909.03227)

## Motivation

之前RE的方法无法解决同个实体属于多个关系的情况，也就是一个实体最多指定到一个关系中。CopyRE是最近第一个显式解决这个问题的，但是效果还不够好。这篇paper主要就是为了解决这个问题，提出了一个层次标注的方法同时做实体抽取和关系抽取。

## Method

用BERT编码输入句子，之后decoder端有两层tagger。第一层tagger先做序列标注标出可能的头实体，之后每个relation有自己一套参数，给定头实体和某个relation，可以在第二层tagger上继续做序列标注标注出可能的尾实体，这样就得到了一个(h,r,t)三元组。方法简单粗暴，效果很好。

## Problems

想法不复杂，但是参数量会随关系种类线性增长，在relation种类多的情况下可能对硬件要求较高。
