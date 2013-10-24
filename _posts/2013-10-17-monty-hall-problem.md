---
layout: post
title: "Monty Hall problem"
description: "The Monty Hall problem is a probability puzzle, loosely based on the American television game show Let's Make a Deal and named after its original host, Monty Hall."
keywords: "math, funny"
category: 数学奥义
tags: [Math, Fun]
---
{% include JB/setup %}

<a name="top" id="top"></a>

这是一个蛮有趣的问题。

你是否在娱乐节目上见过这么一幕？嘉宾有一个抽奖环节，抽奖规则是从眼前的三个盒子中选取一个，当嘉宾选了其中一个以后，主持人会打开嘉宾未选取的两个盒子中的一个，并让展示给嘉宾看，打开的这个盒子没有奖，这时，主持人便会古惑地问嘉宾，“嘿嘿，嘿嘿，你还坚持你的选择吗？现在给你一次机会，你换还是不换？嘿嘿~”。这时如果你是那个纠结的嘉宾，你会选择换还是不换呢？

大家不妨思考一下，说不定什么时候你就成为了那个“纠结的嘉宾”。

<!-- more -->

<br/>

![MHprob](/assets/images/2013/10/MHprob.png "MHprob")

<br/>

其实这是一个概率问题，想先试验一下同学可点击<a href="#bottom">“开始游戏”</a>体验一下。

或许你会想，主持人拿掉了一个没有奖的，接下来的两个中，任选一个中奖的概率不就都是一半一半吗？为什么我要换啊。但是如果我们仔细想想的话就会知道其实换了以后中奖的概率确实会提高，而且比不换高一倍！

这是一个经典问题—— [Monty Hall problem](http://en.wikipedia.org/wiki/Monty_Hall_problem "Monty Hall problem") 

> **蒙提霍尔问题**，亦称为蒙特霍问题或三门问题（英文：Monty Hall problem），是一个源自博弈论的数学游戏问题，大致出自美国的电视游戏节目Let's Make a Deal。问题的名字来自该节目的主持人蒙提·霍尔（Monty Hall）。
> 
这个游戏的玩法是：参赛者会看见三扇关闭了的门，其中一扇的后面有一辆汽车或者是奖品，选中后面有车的那扇门就可以赢得该汽车或奖品，而另外两扇门后面则各藏有一只山羊或者是后面没有任何东西。当参赛者选定了一扇门，但未去开启它的时候，知道门后情形的节目主持人会开启剩下两扇门的其中一扇，露出其中一只山羊。主持人其后会问参赛者要不要换另一扇仍然关上的门。问题是：换另一扇门会否增加参赛者赢得汽车的机会率？如果严格按照上述的条件的话，答案是会—换门的话，赢得汽车的机率是2/3。
这条问题亦被叫做蒙提霍尔悖论：虽然该问题的答案在逻辑上并不自相矛盾，但十分违反直觉。这问题曾引起一阵热烈的讨论。

用一幅图直观排列出所有的情形如下所示：

![MontyCars](/assets/images/2013/10/Monty_Cars.png "Monty_Cars")

如上图所示，不失一般性地我们假设车子（奖品）放在第一个门后，那么参赛者是主持人挑出一只羊后转换失败的情况只有三种情况中的一种，即参赛者若第一次选择的是第一道门，其余两种情况（参赛者第一次选择第二道或第三道门）在转换后都将获胜。即如果参赛者在主持人挑出羊后选择转换获胜的概率为$$\frac{2}{3}$$。

当然，我们也可以用[Bayes定理](http://en.wikipedia.org/wiki/Bayes'_theorem)来进行计算。

假设三道门分别用A, B, C表示，不失一般性地，假设参赛者第一次挑选的是A门，令

事件X：A有车
事件Y：B有车
事件Z：C有车

显然，``$$P(X)=P(Y)=P(Z)=\frac{1}{3}$$``

若A有车，即X事件成立，那么主持人选择打开B门的概率和打开C门的概率为  
``$$P(B|X)=\frac{1}{2}$$``  
``$$P(C|X)=\frac{1}{2}$$``



	


<a name="bottom" id="bottom"></a>

{% include custom/games/monty-hall-problem.html %}

<a href="#top" id="top">点击返回文章</a>