---
title: 每个程序员应该知道关于浮点的代数
description: Aims to provide both short and simple answers to the common recurring questions of novice programmers about floating-point numbers not 'adding up' correctly, and more in-depth information about how IEEE 754 floats work, when and how to use them correctly, and what to use instead when they are not appropriate.
verification: SoYmbsJEmSz2s1LmZk_cku4pKwhRsU6m0ZOTgGdnTL0
---

或者
--

为什么我的数字加起来不对？
============================

比如你写了一些非常简单的代码，例如：

		0.1 + 0.2

得到了完全意外的结果：

		0.30000000000000004

你有可能在某个论坛寻求帮助，然后得到一个指向 [有很多公式的长文章](http://download.oracle.com/docs/cd/E19957-01/806-3568/ncg_goldberg.html) ，但这个结果好像并不能帮你解决问题。

好吧，本网站就是：

* 简明解释为什么你得到了意外的结果
* 告诉你怎么处理这个问题
* 如果你感兴趣，本站也提供了深入的解释来说明为什么浮点数要这样工作，还有其他一些可能出现的问题

你应该首先看 [基础答案](/basic/) - 但你不应该在那里停下来！
