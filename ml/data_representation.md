# 如何在机器中表示数据

**数据**这个词，包含的范围很广，我们通常接触到的有
1. 文本
2. 语音
3. 图片
4. 视频

那么，这些数据，在机器学习中，如何表示？

或者说：

如果我们假定**机器具有智能**，那么在**机器**眼中，它们看到的文本、语音、图片是什么样子？

当然，我这里所说的**机器**，指的是**计算机**，它的本质，依然是**计算**，因此，在它的眼中，这些数据都是**张量（Tensor）**，只是这些张量的形状不一样而已。

## 1 '文本'的表示

我们从小学开始，语文中，就有作文，对于一篇文章，我们都知道，它包含多个“段”，每个“段”又包含很多“句子”，而“句子”又包含多个“词”，比如，“我要搞懂机器学习”，这就是一个句子，如果拆成词的话，就是 “我 - 要 - 搞懂 - 机器学习”。

在表示成张量（Tensor）时，也遵循由词到句，由句到段的规则。其中，一个词，对应一个向量，也就是一阶张量；一个句子，则对应一个矩阵，也就是二阶张量；一个段则对应了三阶张量。

比如，还是上面这句“我要搞懂机器学习”，表示成张量的话，如下：

```python
[
    [1,2,3],
    [4,5,6],
    [7,8,9],
    [10,11,12]
]
```

“我要搞懂机器学习”这句话，经过`Word2Vec`进行嵌入后，则表示成了上面这个矩阵。

可以理解为，当我们和计算机说：“我要搞懂机器学习”时，它接收到的这句话，就是上面这个矩阵。

从这个矩阵中，也能看出，一个词对应了一个向量，在NLP中，我们把每个词称作Token。

## 2 '语音'的表示
语音是一个序列。

## 3 '图片'的表示

我们知道，视频由语音和一系列连续的图片构成，所以，理解了语音和图片的张量表示，也就理解了视频的张量表示。前面已经理解了语音的张量表示，这里只要在理解了图片的表示，视频的也就理解了。

图片分为黑白图片和彩色图片。

对于一张黑白图片，比如手写数字识别，表示成张量，就是一个矩阵。

对于一张彩色图片，表示成张量，就是一个三阶张量。

## 修改记录
|版次|时间|修改|
|---|---|---|
|v1|2023.04.16|初步整理数据的张量表示|