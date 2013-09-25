---
layout: post
title: "完全立方体计算之多路数组聚焦"
description: "数据立方体计算是数据仓库实现的一项基本任务..."
keywords: "DM, Algorithm"
category: 数据挖掘
tags: [DM]
---
{% include JB/setup %}

上一篇提到方体计算的有效方法主要有：

- 基于ROLAP的方体算法
- 基于MOLAP的方体算法（数组）

这两种。其中基于ROLAP的方体算法相对比较简单，如DMQL中的方体定义和计算

	**define cube** sales[item, city, year]: sum(sales_in_dollars)
	**compute cube** sales

通过ROLAP，上述的compute cube子句可以转化为一个类似于SQL的语句
	
	SELECT item, city, year, SUM(amount)
	FROM SALES
	**CUBE BY** item, city, year 

<!-- more -->