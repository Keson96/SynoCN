# A "soft" Chinese Synonyms Collection
中文近义词表，主要爬取自[百度汉语](http://hanyu.baidu.com/)、[CWN](http://lope.linguistics.ntu.edu.tw/cwn/)，内含80966个词，335061条近义关系。

## Why call it "soft"
实习的过程中想用近义词来辅助同义句子的匹配，找了一圈却找不到一个很好的数据库
* [Open Multilingual Wordnet](http://compling.hss.ntu.edu.sg/omw/) 内含大量短语而不是词，这可能是为了对应到英文wordnet的单词，翻译时无法避免的问题。例如："删除背景的照片"，"利物浦市民的"等。
* 直接使用词向量。有两个问题，一是阈值不好确定，二是距离近的词不一定是近义词，距离远的词也不一定不是近义词(词向量只是描述了共现度)。例如，在我们训练的词向量中，离"男"最近的词却是"女"。有[文章](https://arxiv.org/abs/1603.00892)也讨论了这个问题。
* [CWN](http://lope.linguistics.ntu.edu.tw/cwn/) 词数不多，且涉及简繁转换的问题，对近义词的选择上有点过于偏学术

我想找一个对近义关系要求不严格，适合判断口语语句中词语的近义关系，即相对 **"soft"** 的库。后来发现百度汉语上提供了近义词，正好符合我的要求。

## 数据来源
爬取的数据总共有三个来源，下面是总库的链接和各个数据源数据的链接。
总数据：[百度网盘](https://pan.baidu.com/s/1nxsscMd)

### 百度汉语（直接爬取）
使用[汉典网](http://www.zdic.net/)上(几乎)所有词构成的词表，去百度汉语上爬取了这些词的近义词

链接：[百度网盘](https://pan.baidu.com/s/1c37nqIs)，共计35395个词，62002条近义关系

### [CWN](http://lope.linguistics.ntu.edu.tw/cwn/)
爬取了[CWN](http://lope.linguistics.ntu.edu.tw/cwn/)上（几乎）所有词的近义词，将一个词下不同义项的近义词整合到一起

链接：[百度网盘](https://pan.baidu.com/s/1pMRPAzh)，共计6188个词，12541条近义关系

### 百度汉语（利用每个词的翻译）
第一种方法爬取时，不能解决单字成词的问题，即单字的页面是没有近义词的，例如："吃" 和 "吃饭"。所以我爬取了每个词的英文解释，然后将相同英文解释的词视为近义词。这种方法只做了一些简单的处理，可能会有一些问题存在，会使整个库更加 "soft"。

链接：[百度网盘](https://pan.baidu.com/s/1mj7CUww)，共计59074个词，271577条近义关系

## 数据格式
txt文件，每行两个词，以空格分隔，表示一组近义关系
