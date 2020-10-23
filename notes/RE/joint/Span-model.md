**Span-Level Model for Relation Extraction.**
_Kalpit Dixit, Yaser Al-Onaizan._
ACL 2019.
[[paper]](https://www.aclweb.org/anthology/P19-1525/)

## Motivation

之前有工作针对实体可能作为多个关系的head/tail来进行改进，但是其实还有一种情况是在进行NER的时候，其实也有可能产生实体重叠，这里的实体重叠指的是同一个word属于不同的entity，比如“常宝宝老师”，“常宝宝”，可以是两个实体。

## Method

paper提出的方法就是遍历所有的span，把他们独立进行joint learning，判断这个span是否是实体，同时判断与其他实体的关系。为了减少复杂度，实验的时候限定了span的最长长度。

## Problems

遍历所有可能的span听起来还是太暴力的，尽管它是一种解决方法。
