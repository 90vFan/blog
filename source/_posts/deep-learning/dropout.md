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
Dropout
-------------

## Dropout

![img](nn_cs231n_note/63fcf4cc655cb04f21a37e86aca333cf_hd.png)

1.  Bagging 集成模型，随机抽样神经网络的子集。很多个共享参数的子网络组成。
2.  增强单个神经元独立学习特征的能力，减少神经元之间的依赖（避免学习某些固定组合才产生的特征，有意识的让神经网络去学习一些普遍的共性）
3.  加性噪声

```python
"""
反向随机失活: 推荐实现方式.
在训练的时候drop和调整数值范围，测试时不做任何事.
"""

p = 0.5 	# 激活神经元的概率. p值更高 = 随机失活更弱

def train_step(X):
  # 3层neural network的前向传播
  H1 = np.maximum(0, np.dot(W1, X) + b1)
  # 神经元以p的概率失活 [0, 1]随机分布 P(rand(x)) < p = p
  # 第一个随机失活掩码. 注意/p! inverted dropout, 保持当前层输出期望一致
  mask1 = (np.random.rand(*H1.shape) < p) / p
  H1 *= mask1                                  # dropout!
  H2 = np.maximum(0, np.dot(W2, H1) + b2)
  mask2 = (np.random.rand(*H2.shape) < p) / p  # 第二个随机失活掩码. 注意/p!
  H2 *= mask2 # drop!
  out = np.dot(W3, H2) + b3

  # 反向传播:计算梯度... (略)
  # 进行参数更新... (略)

def predict(X):
  # 前向传播时模型集成
  H1 = np.maximum(0, np.dot(W1, X) + b1)       # 不用数值范围调整了
  H2 = np.maximum(0, np.dot(W2, H1) + b2)
  out = np.dot(W3, H2) + b3
```

