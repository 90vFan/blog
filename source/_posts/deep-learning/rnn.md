---
title: Dropout
date: 2019-06-17
mathjax: true
categories:
  - dl
tag:
  - dl
  - hexo-asset-image
---

Recurrent Neuro Network
------------------------------------

**循环神经网络**可以更好地处理序列信息（如一句话），允许记忆信息（在时序上传递输入的有效信息），可以解决长期依赖的问题（Long-term Dependencies）

## RNN结构

![img](rnn/v2-71652d6a1eee9def631c18ea5e3c7605_hd.jpg)

![img](rnn/v2-b0175ebd3419f9a11a3d0d8b00e28675_hd.jpg)

$$O_t = g(VS_t)$$                     # 在时间点 t 的输出

$$S_t = f(UX_t + WS_{t-1})$$     # 在时间点 t 的状态

W,V,U: 权重

g,f: 激活函数

#### 循环

![1562068950392](rnn/1562068950392.png)

输出值 $O_t$ 受前面历次输入值 $x_t, x_{t-1}, x_{t-2}...$ 的影响，相当于一定程度上记忆之前任意时间段的有效信息，从而在时序上累积输入 $X_t$，解决长期依赖问题。

*疑问： S作为一个固定大小的矩阵如何记忆有效信息？*



![点击查看大图](rnn/2256672-3b20294694c3904b.png)

## BPTT

损失函数对权重 $W$ 的梯度是各个时刻梯度之和：

$$\nabla_W L = \sum_{i=1}^{t} \nabla_{W_i} L$$



## LSTM

![lstm](rnn/lstm.png)





## GRU













References:

1. [Understanding-LSTMs colah](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
2. [理解LSTM（1的翻译）](https://www.jianshu.com/p/9dc9f41f0b29)
3. [零基础入门深度学习(5) - 循环神经网络](https://zybuluo.com/hanbingtao/note/541458)
4. 