---
layout: post
title: "Android简易对讲机的设计与实现"
description: "Android简易对讲机的设计与实现"
keywords: "android, programing"
category: 程序开发
tags: [Android, Programing]
---
{% include JB/setup %}

近日猎奇于Android，卒造简易对讲机以练手，以此文存载。

这里主要分析一下对讲机的设计思路。读者也可先自行思索一下这个问题，如何设计一个对讲机。

###功能

本简易对讲机的功能简单有两：

- 登录
- 对讲

###交互模型

各个终端通过网络，与服务器通讯：

<!-- more -->

- ![Main](/assets/images/2014/01/speaker1.png)

###前、后端

- 服务器

	1. 登录
	2. 上传音频
	3. 下载音频
	4. 群发音频

<br />

- Android端

	1. 登录
	2. 上传音频
	3. 下载音频
	4. 录音、播放

<br />

- 由上可看出，前后端交互的主要环节在于登录与上传下载。













