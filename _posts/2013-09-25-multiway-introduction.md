---
layout: post
title: "完全立方体计算之多路数组聚集"
description: "数据立方体计算是数据仓库实现的一项基本任务..."
keywords: "DM, Algorithm"
category: 数据挖掘
tags: [DM, Algorithm]
---
{% include JB/setup %}

上一篇提到方体计算的有效方法主要有：

- 基于ROLAP的方体算法
- 基于MOLAP的方体算法（数组）

这两种。其中基于ROLAP的方体算法相对比较简单，如DMQL中的方体定义和计算

	define cube sales[item, city, year]: sum(sales_in_dollars)
	compute cube sales

通过ROLAP，上述的compute cube子句可以转化为一个类似于SQL的语句
	
	SELECT item, city, year, SUM(amount)
	FROM SALES
	CUBE BY item, city, year 

<!-- more -->

需要计算以下的group by子句

	(item, city, year)
	(item, city), (item, year), (city, year)
	(item), (city), (year)
	()

今天主要是介绍一下MOLAP的多路数组聚集方法。

**多路数组聚集（简称MultiWay）**方法使用多维数组作为基本数据结构，计算完全数据立方体。它是一种使用数组直接寻址的典型MOLAP方法，其中维值通过位置或对应数组位置的下标访问。因此，MultiWay不能使用任何基于值的重新排序作为优化技术，

一种不同的方法是为基于数组的立方体结构开发的，如下所述：

1. 将数组分成块。**块**是一个子立方体，其大小能够放入立方体计算时可用的内存。分块（chunking）是一种将n维数组划分成小的n维块的方法，其中每块作为一个对象存放在磁盘中。块被压缩以避免空数组单元（即不含任何有效数据的单元，其单元计数为零）所导致的空间浪费。**划分的块数要综合考虑2个因素：一个是I/O的开销，另一个是内存实际的负载量。**

2. 通过访问立方体单元（即存取立方体单元的值）计算聚集。可以优化访问单元的次序，使每一个单元必须重复访问的次数最小化，从而减少内存和存储开销。技巧是使用这样的一次次序，使得部分聚集可以同时计算，并避免不必要的单元再次访问。

由于分块技术涉及“重叠”某些聚集计算，称该技术为多路数组聚集（multiway array aggregation）。它进行同时聚集————即同时对多个维计算聚集。




