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
\begin{aligned}
&f_{X,Y}(x,y)=\frac{\partial ^2F_{X,Y}(x,y)}{\partial x\partial y} \\
\Rightarrow &F_{X,Y}(x,y)=\int_{-\infty}^x\int_{-\infty}^yf_{X,Y}(u,v)dvdu
 \end{aligned}
$$

- 联合PDF的性质

$$f_{x,y}(x,y)\geqslant 0$$

$$\int_{-\infty}^\infty f_{X,Y}(x,y)dxdy=1$$

$$if\ x,y\ independent\Rightarrow f_{X,Y}(x,y)=f_X(x)\cdot f_Y(y)$$

$$
\begin{aligned} 
for\ event\ B,&\\
&P(B)=\iint_{(x,y)\in B}f_{X,Y}(x,y)dxdy
\end{aligned}
$$

###边际概率分布

- 对于离散情形，$$X$$和$$Y$$的边际分布分别为：

$$p_X(x)=\sum_yp_{X,Y}(x,y)$$

$$p_Y(y)=\sum_xp_{X,Y}(x,y)$$

- 对于连续情形，$$X$$和$$Y$$的边际分布分别为：

$$f_X(x)=\int_{-\infty}^\infty f_{X,Y}(x,y)dy$$

$$f_X(y)=\int_{-\infty}^\infty f_{X,Y}(x,y)dx$$

- 期望值

$$PMF:E[h(X,Y)]=\sum_{x=-\infty}^{\infty}\sum_{y=-\infty}^{\infty}h(x,y)\cdot p_{X,Y} (x,y)$$

$$PDF:E[h(X,Y)]=\int_{-\infty}^\infty \int_{-\infty}^\infty h(x,y)\cdot f_{X,Y}(x,y)dxdy$$

$$if\ x,y\ independent\Rightarrow E[g(X)h(Y)]=E[g(X)]\cdot E[h(Y)]$$

- 方差

$$
\begin{aligned}
Var(X+Y)&=E[(X+Y-E[X+Y])^2] \\
&=E[(X-\mu _X)^2]+Var((Y-\mu _Y)^2)+2E[(X-\mu _X)(Y-\mu _Y)] \\
&=Var(x)+Var(y)+2Cov(X,Y) \\
\end{aligned}
$$

$$
if\ X,Y\ independent\Rightarrow Var(X+Y)=Var(X) + Var(Y)
$$

###随机变量之和

- 若$$X,Y$$独立

![Z](/assets/images/2014/01/z.png)

- 考虑不只两个随机变量的情形，求和的分布的需要多次卷积（摺积）(convolution),很复杂。用MGF转换问题。

###MGF(Moment Generation Function)

- MGF$$\phi _X(s)$$定义：

$$\phi _X(s)=E[e^{sX}]=\begin{cases}
\sum_{x=-\infty}^\infty e^{sx}\cdot p_X(x) &(discreted)\\ 
\int_{-\infty}^\infty e^{sx}\cdot f_X(x)dx & (continue)
\end{cases}$$

- 逆转换通常靠查表

- Why named "Moment Generation Funtion"
	- Discreted case:  
![whymgf](/assets/images/2014/01/whymgf.png)
	- Continue case:  
![whymgf](/assets/images/2014/01/whymgf2.png)

- 性质

$$
\begin{aligned}
Y=aX+b \\
&\phi_Y(s)=E[e^{sY}]=E[e^{s(aX+b)}]=e^{sb}\cdot \phi_X(as)
\end{aligned}
$$

- 常见概率分布MGF及特征方程

![mgf](/assets/images/2014/01/mgf.png)

###独立随机变量之和

- $$X_1,X_2,...$$独立且各自都有一模一样的概率分布，表示为

$$\left\{X_i\right\} \ I.I.D.\\
Independently\ and\ Identically\ Distributed$$

- $$X=X_1+X_2+\cdots +X_n$$,$$n$$为常数，求$$X$$的概率分布

$$\Phi_X(s)=[\phi_X_1(s)]^n$$

- $$X_1,X_2,...I.I.D.$$，$$X=X_1+X_2+\cdots +X_N$$，若$$N$$本身也为随机变量

$$
N:p_N(n)\ given\\
\Rightarrow \phi _N(\widetilde{s})=\sum _{n=0}^\infty e^{\widehat{s}n}\cdot p_N(n)
$$

$$\Phi_X(s)=\phi_N(\ln(\phi _x_1(s))))$$







