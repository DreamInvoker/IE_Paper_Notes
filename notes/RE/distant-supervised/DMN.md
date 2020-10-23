**Effective Deep Memory Networks for Distant Supervised Relation Extraction.**
_Xiaocheng Feng, Jiang Guo, Bing Qin, Ting Liu, Yongjie Liu SCIR._
IJCAI 2017.
[[paper]](https://www.ijcai.org/Proceedings/2017/559)

## Motivation

DS RE通常用多实例多标签学习的方法来解决，本文针对多实例的attention机制，提出两个基于attention机制的memory组件来同时显式地捕捉context word的信息（比如instance中的每个词对分类的关系贡献程度不一样）和关系类别之间的内在依存信息（比如两个关系类别可能有对称关系或者蕴含关系）
          
## Method

使用两个基于attention机制的memory network。1.词级别的memory，用于学习每个context word对实体对关系的贡献程度；2.两层关系级别的memory, 用于得到关系的表示并进行最终bag级别的所有关系类别的二分类

## Problems

用到的memory只有query功能，没有update和forget功能。
