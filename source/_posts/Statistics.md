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
- $P(H)$ : 先验概率, the probability of observing event H
- $P(D|H)$: 似然度　
- $P(D)$ :   the probability of data D

例：在判断垃圾邮件的算法中:
  $P(H)$ : 所有邮件中，垃圾邮件的概率。
  $P(D)$ : 出现某个单词的概率。
  $P(D|H)$ : 垃圾邮件中，出现某个单词的概率。
  $P(H|D)$ : 出现某个单词的邮件，是垃圾邮件的概率。

### 熵（Entropy）
香农 Shannon 

信息论中，熵是接收每条消息中包含的信息的平均值。

表示样本的不确定性量度。在信息世界，熵越高，则能传输越多的信息，熵越低，则意味着传输的信息越少。

单位：

熵的单位通常为比特, bit 或者sh(annon) (基于2)，但也用nat(基于自然对数)、Hart（基于10）计量，取决于定义用到对数的底。

熵定义为信息的期望值：

$$\begin{align} H(X) & = E[I(X)] \\ & = E[-ln(P(X))]  \\ & = -\sum\limits_{i}^n P(x_i)logP(x_i)\end{align} ​$$

- 离散均匀分布

$H(X)=log_2{m}$

例：抛掷三枚硬币

信息：可以得到$2^3=8$种情况

不确定性：$log_2{8}=2\ bit$

- 离散分布

$H(X)=\sum\limits_{i}^nP(x_i)log\frac{1}{P(x_i)}​$

例：选项ABCD

信息量：$H(X)=\sum\limits_{i}^n\frac{1}{4}log_2(\frac{1}{4})=2 bit$

给定A是错的，信息量变为：$H(X)=\sum\limits_{i}^n\frac{1}{3}log_2(\frac{1}{3})=1.585 bit$

“A是错的”，提供了$2-1.585=0.415bit$的信息



