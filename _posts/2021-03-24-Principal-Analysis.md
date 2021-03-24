---
layout:     post
title:      "Principal Analysis"
subtitle:   " \"Thank god, my genome just compiled.\""
date:       2021-03-24
author:     "Ruby"
header-img: "/img/in-post/post-bioinformatics-materials/bioinformatics.jpg"
catalog: true
tags:
    - 生信
---

**问题**：样本$X_1,\cdots,X_n$在$R^d$上。如何将数据投射到维度$d^{\prime}<d$的线性空间并保留尽可能多的信息？

**PCA的解决方案**：找到向该方向投射数据后最大化协方差的正交方向。

**线代前提**：

1. $u^{T}Su$是$u^{T}X_1,\cdots,u^{T}X_n$的样本方差。
2. 特征向量与特征值

**方案的数学表述**：

$$v_1\in argmax\limits_{||u||=1} u^{T}Su$$

...

