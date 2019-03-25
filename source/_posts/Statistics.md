---
title: Statistic
date: 2019-01-06 23:18:46
tags:
mathjax: true
---

### Beyes

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)}​$$

H: hyposis 假设事件，D: data 数据

- $P(H|D)$ : 后验概率, the probability of observing event H given that D is true
- $P(H)​$ : 先验概率, the probability of observing event H
- $P(D|H)$: 似然度　
- $P(D)$ :   the probability of data D

例：在判断垃圾邮件的算法中:
  $P(H)​$ : 所有邮件中，垃圾邮件的概率。
  $P(D)​$ : 出现某个单词的概率。
  $P(D|H)​$ : 垃圾邮件中，出现某个单词的概率。
  $P(H|D)​$ : 出现某个单词的邮件，是垃圾邮件的概率。

### 熵（Entropy）
香农 Shannon 

信息论中，熵是接收每条消息中包含的信息量($\log\frac{1}{p}$)的平均值。

表示样本的不确定性量度。在信息世界，熵越高，则能传输越多的信息，熵越低，则意味着传输的信息越少。

单位：

熵的单位通常为比特, bit 或者sh(annon) (基于2)，但也用nat(基于自然对数)、Hart（基于10）计量，取决于定义用到对数的底。

熵定义为信息的期望值：

$$\begin{align} H(X) & = E[I(X)] \\ & = E[-ln(P(X))]  \\ & = -\sum\limits_{i}^n P(x_i)logP(x_i)\end{align} ​$$

- 离散均匀分布

$H(X)=log_2{m}​$

例：抛掷三枚硬币

信息：可以得到$2^3=8$种情况

不确定性：$log_2{8}=2\ bit​$

- 离散分布

$H(X)=\sum\limits_{i}^nP(x_i)log\frac{1}{P(x_i)}​$

例：选项ABCD

信息量：$H(X)=\sum\limits_{i}^n\frac{1}{4}log_2(\frac{1}{4})=2 bit​$

给定A是错的，信息量变为：$H(X)=\sum\limits_{i}^n\frac{1}{3}log_2(\frac{1}{3})=1.585 bit​$

“A是错的”，提供了$2-1.585=0.415bit$的信息

例：编码

分布p=(1/2, 1/2, 0, 0)，即A和B出现的概率均为1/2，C和D出现的概率都为0。计算H(p)为1，即只需要1位编码即可识别A和B

分布q=(1/4, 1/4, 1/4, 1/4)来编码则得到H(q)=2，即需要2位编码来识别A和B，还有C和D

### 交叉熵

使用分布 q 来预测真实分布 p 的平均编码长度

$H(p,q)=\sum\limits_{i}^{} p(i)*log\frac{1}{q(i)} $

参考: https://www.zhihu.com/question/41252833

现有关于样本集的2个概率分布p和q，其中p为真实分布，q预测分布。

按照真实分布p来衡量识别一个样本的所需要的编码长度的期望(即平均编码长度)为：$H(p)=\sum\limits_{i}^{} p(i)*log\frac{1}{p(i)}$

使用预测分布q来表示来自真实分布p的平均编码长度，则应该是：$H(p,q)=\sum\limits_{i}^{} p(i)*log\frac{1}{q(i)} ​$

因为用q来编码的样本来自分布p，所以期望H(p,q)中概率是p(i)。H(p,q)我们称之为“交叉熵”。

比如含有4个字母(A,B,C,D)的数据集中，真实分布p=(1/2, 1/2, 0, 0)，即A和B出现的概率均为1/2，C和D出现的概率都为0。计算H(p)为1，即只需要1位编码即可识别A和B。如果使用分布Q=(1/4, 1/4, 1/4, 1/4)来编码则得到H(p,q)=2，即需要2位编码来识别A和B(当然还有C和D，尽管C和D并不会出现，因为真实分布p中C和D出现的概率为0，这里就钦定概率为0的事件不会发生啦)。

根据非真实分布q得到的平均编码长度H(p,q)大于根据真实分布p得到的平均编码长度H(p)。事实上，根据[Gibbs' inequality](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Gibbs%2527_inequality)可知，H(p,q)>=H(p)恒成立，当q为真实分布p时取等号。

### KL散度（相对熵）

衡量分布 p 和 q 的差异，使用分布 q 来近似分布 p

$D(p||q)=H(p,q)-H(p) = \sum\limits_{i}^{} p(i)*\log\frac{1}{q(i)} - \sum\limits_{i}^{} p(i) *\log\frac{1}{p(i)} = \sum\limits_{i}^{} p(i)*\log\frac{p(i)}{q(i)}​$

我们将由q得到的平均编码长度比由p得到的平均编码长度多出的bit数称为“相对熵”，又被称为KL散度(Kullback–Leibler divergence，KLD) [Kullback–Leibler divergence](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Kullback%25E2%2580%2593Leibler_divergence)。它表示2个函数或概率分布的差异性：差异越大则相对熵越大，差异越小则相对熵越小，特别地，若2者相同则熵为0。注意，KL散度的非对称性。



