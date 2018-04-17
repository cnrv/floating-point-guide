--- 
title: Exact Types
description: Description of various datatypes that can be more exact that floating-point numbers
---

While [binary](/formats/binary/) [floating-point](/formats/fp/) numbers are better for computers to work with, and usually good enough for humans, sometimes they are just not appropriate. Sometimes, the numbers really must add up to the last bit, and no technical excuses are acceptable - usually when the calculations involve money. 

Unfortunately, there is no dominating standard like IEEE 754 for this (The 2008 version of the standard added decimal types, which is too recent to have seen widespread adoption).
Each language or platform has its own solution, sometimes multiple different ones. For details, look at the language cheat sheets.

There are at least three fundamentally different kinds of such types:

Limited-Precision Decimal
-------------------------
Basically the same as a IEEE 754 binary floating-point, except that the exponent is interpreted as base 10. As a result, there are no unexpected [rounding errors](/errors/rounding/). Also, this kind of format is relatively compact and fast, but usually slower than binary formats.

Arbitrary-Precision Decimal
---------------------------
Sometimes called "bignum", this is similar to a limited-precision type, but has the ability to increase the length of the significand (possibly also the exponent) as required. The downside is that there is some basic overhead (memory and speed) to support this flexibility, and that the longer the significand gets, the more
memory is needed and the slower all calculations become.

It can be very tempting to say "My calculation is important, so I need as much precision as possible", but in practice the actual importance of precision at the 10,000th decimal digit quickly pales in comparison with the
performance penalty required to support it.

Symbolic calculations
---------------------
The "holy grail" of exact calculations. Achieved by writing a program that actually knows all the rules of math and represents data as *symbols* rather than imprecise, rounded numbers. For example:

* 1/3 is actually a fraction "one divided by three"
* The square root of 2 is really the number that, multiplied by itself, is *exactly* 2
* Even [transcendental numbers](http://en.wikipedia.org/wiki/Transcendental_numbers) like **e** and **&pi;** are known, together with their properties, so that e<sup>i&pi;</sup> is *exactly* equal to -1.

However, these symbolic math systems are complex, slow and require significant mathematical knowledge to use. 
They are invaluable tools for mathematicians, but not appropriate for most everyday programming tasks. And 
even many mathematicians work on problems where imprecise, numerical solutions are better because no 
symbolic solution is known. 

--- 
- 题目: 精确类型
- 描述: 比浮点数更精确的数据类型的介绍
---

二进制浮点数很适合计算机，对于人类来说通常也足够好，不过，它们也不总是适用。有时候，就是需要把数字的每一个比特都加起来，而不允许任何误差——通常是在算钱的时候。

然而，目前没有针对这种场景的类似 IEEE 754 那样权威的标准 （IEEE 754-2008 版本加入了十进制小数类型，不过这是新近加入的，还没有广泛使用）。
每一种语言或者平台有它自己的(一个或多个)解决方案。详见语言速查表。

它们至少可以分成三种本质上不同的类型：

## 有限精度十进制小数

这种类型基本上和 IEEE 754 的二进制浮点是相同的，只是解码采用 10 进制表示。因此不存在未知的[舍入误差](/errors/rounding/)。此外，这种类型的格式相对而言更紧凑也更快，不过通常比二进制格式还是慢一些。

## 任意精度十进制小数

用时候也称之为“大数”，它和有限精度类型相似，不过可以根据需要增加尾数（可能也有指数）的长度。缺点是为了支持灵活性的必要开销（存储空间和速度），尾数的长度越长，那么就需要更多的存储空间，所有计算的速度也就更慢。

“我的计算很重要，所以我需要尽可能精确”，这样说也许很诱人，但是和性能损失比起来，在十进制数字第 10,000 位的精度的重要性不值一提。

## 符号计算

精确计算的“银弹”（译者注：原文 holy grail，圣杯，意为稀世珍宝）。通过编写一个程序来实现这个目标，这样的程序应该包括所有数学规则，并且使用 *符号* 来表示数据，而不是使用非精确的舍入过的数字。例如：

- “一除以三” 的尾数就用 1/3 表示
- 2 的平方根就是那个乘上自身结果是*精确*的 2 的数字
- 即使对于[超越数](http://en.wikipedia.org/wiki/Transcendental_numbers)，比如已知 **e** 和 **&pi;**，再加上它们的属性，那么 e<sup>i&pi;</sup> 的结果就是*精确*地等于 -1。

然而，这样的符号数学系统是复杂、缓慢的，还需要很多的数学知识才能使用它。它们是数学家的无价之宝，但是对于大多数普通编程任务来说并不适用。甚至许多的数学家研究的问题就是非精确的，数值方案是更好的选择，因为对于这些问题，没有已知的符号方案。
