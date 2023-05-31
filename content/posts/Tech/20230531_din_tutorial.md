---
author: "philharmonic77"
title: "动手实现DIN (一)"
date: "2023-05-30"
description: "用tensorflow 2 由浅入深实现DIN模型"
tags: ["python","深度学习","tensorflow","推荐系统"]
hideMeta: false
searchHidden: false
ShowBreadCrumbs: false
--- 

**导言**：这篇blog介绍如何用tensorflow keras API实现[DIN模型](https://paperswithcode.com/paper/deep-interest-network-for-click-through-rate)。该模型在2019年由阿里推出，是推荐系统常用的深度学习模型。而后又基于此发展出了DIEN、DSIN等模型。作为最基础的一个模型，有必要完全掌握它的细节。

[官方版本](https://github.com/zhougr1993/DeepInterestNetwork)是2020年实现的，基于tensorflow 1.4+，而后tensorflow 2.0+ API 又有了较大改革。我这里的实现分为几步，从最简单搭积木的方式开始，逐步将代码模块化，并结合实战中的经验。 

---

这里的第一部分是用jupyter notebook的形式分步实现该模型，并在测试的demo数据上调试。

|title | content|
| --- | --- | 
|[demo1](https://github.com/philharmonic77/deep_interest_network/blob/main/notebook%20demo/1_simple_din_demo_v1.ipynb)| 顺序实现，有助于理解模型结构 |
|[demo2](https://github.com/philharmonic77/deep_interest_network/blob/main/notebook%20demo/2_simple_din_demo_v2.ipynb)| 模块化，可配置，熟悉tf的API|

最终实现的模型结构：

![img](/static/img/202305/din_structure.png)




