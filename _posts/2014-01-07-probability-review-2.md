---
layout: post
title: "迷のProbability Review·续"
description: "Review the Probability class."
keywords: "math, probability"
category: 数学奥义
tags: [Math, Probability]
---
{% include JB/setup %}

由于篇幅关系，此Review拆分为两部分，第一部分：<a href="http://yabuhoo.com/%E6%95%B0%E5%AD%A6%E5%A5%A5%E4%B9%89/2014-01/probability-review.html" target="_blank">迷のProbability Review</a>。

###随机变量X的函数分布

- 随机变量$$X$$的任意函数$$g(X)$$也是一个随机变量，通常称之为Derived Random Variable。

- 若$$X$$为离散：直接推$$Y=g(X)$$的PMF

$$p_{g(X)}(y)=\sum_{x,g(x)=y}p_X(x)$$

- 若$$X$$为连续：先推$$Y=g(X)$$的CDF，再微分得PDF

$$F_{g(x)}(y)=P[g(X)\leqslant y]$$

$$f_{g(X)}(y)=\frac{d}{dy}F_{g(X)}(y)$$

<!-- more -->

###条件概率

- 若$$X$$是一离散随机变量，其PMF为$$p_X(x)$$。若已知某事件B已发生，则在此情况下的条件概率分布为：

$$
PMF:p_{X\mid B}(x)=\begin{cases}
x\in B:&\frac{p_X(x)}{P(B)} ,\\ 
x\notin B:&0. 
\end{cases}
$$

- 若$$X$$是一连续随机变量，其PDF为$$f_X(x)$$。若已知某事件B已发生，则在此情况下的条件概率分布为：

$$
PDF:f_{X\mid B}(x)=\begin{cases}
x\in B:&\frac{f_X(x)}{P(B)} \\ 
x\notin B: & 0
\end{cases}
$$

$$
CDF:F_{X\mid B}(x)=\int_{-\infty}^xf_{X\mid B}(u)du=\int_{-\infty \leqslant u \leqslant x,u\in B} \frac{f_X(x)}{P(B)}du
$$

- 关于条件概率的期望、方差都可在此基础上推出。

###联合概率分布

- 同时考虑多个随机变量的概率分布称之为联合概率分布(joint probability distribution)

$$PMF:p_{X,Y}(x,y)=P(X=x,Y=y)$$

$$CDF:F_{X,Y}(x,y)=P(X\leqslant x,Y\leqslant y)$$

$$
f_{X,Y}(x,y)=\frac{\partial ^2F_{X,Y}(x,y)}{\partial x\partial y} \\
\Rightarrow F_{X,Y}(x,y)=\int_{-\infty}^x\int_{-\infty}^yf_{X,Y}(u,v)dvdu
$$

