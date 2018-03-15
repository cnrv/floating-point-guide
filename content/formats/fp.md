--- 
title: Floating Point Numbers
description: Explanation of how floating-points numbers work and what they are good for
---

Why floating-point numbers are needed
-------------------------------------

Since computer memory is limited, you cannot store numbers with infinite precision, no matter whether you use [binary fractions](/formats/binary/) or decimal ones: at some point you have to cut off. But how much accuracy is needed? And *where* is it needed? How many integer digits and how many fraction digits? 

* To an engineer building a highway, it does not matter whether it's 10 meters or 10.0001 meters wide - his measurements are probably not that accurate in the first place.
* To someone designing a microchip, 0.0001 meters (a tenth of a millimeter) is a *huge* difference - But he'll never have to deal with a distance larger than 0.1 meters.
* A physicist needs to use the [speed of light](http://en.wikipedia.org/wiki/Speed_of_light) (about 300000000) and [Newton's gravitational constant](http://en.wikipedia.org/wiki/Gravitational_constant) (about 0.0000000000667) together in the same calculation.
 
To satisfy the engineer and the chip designer, a number format has to provide accuracy for numbers at very different magnitudes. However, only *relative* accuracy is needed. To satisfy the physicist, it must be possible to do calculations that involve numbers with different magnitudes.

Basically, having a fixed number of integer and fractional digits is not useful - and the solution is a format with a *floating point*.

How floating-point numbers work
-------------------------------
The idea is to compose a number of two main parts:

* A **significand** that contains the number's digits. Negative significands represent negative numbers.
* An **exponent** that says where the decimal (or binary) point is placed relative to the beginning of the significand. Negative exponents represent numbers that are very small (i.e. close to zero).

Such a format satisfies all the requirements:

* It can represent numbers at wildly different magnitudes (limited by the length of the exponent)
* It provides the same relative accuracy at all magnitudes (limited by the length of the significand)
* It allows calculations across magnitudes: multiplying a very large and a very small number preserves the accuracy of both in the result.

Decimal floating-point numbers usually take the form of [scientific notation](http://en.wikipedia.org/wiki/Scientific_notation) with an
explicit point always between the 1st and 2nd digits. The exponent is
either written explicitly including the base, or an **e** is used to
separate it from the significand.

| Significand | Exponent | Scientific notation | Fixed-point value |
|-------------|----------|---------------------|-------------------|
| 1.5 | 4 | 1.5 &sdot; 10<sup>4</sup> | 15000 |
| -2.001 | 2 | -2.001 &sdot; 10<sup>2</sup> | -200.1 |
| 5 | -3 |  5 &sdot; 10<sup>-3</sup> | 0.005 | 
| 6.667 | -11 | 6.667e-11 | 0.00000000006667 |

The standard
------------
Nearly all hardware and programming languages use floating-point numbers in the same binary formats, which are defined in the [IEEE 754](http://en.wikipedia.org/wiki/IEEE_754-2008) standard. The usual formats are 32 or 64 bits in total length:

| Format | Total bits | Significand bits | Exponent bits | Smallest number | Largest number |
|--------|------------|------------------|---------------|-----------------|----------------|
| Single precision | 32 | 23 + 1 sign | 8  | ca. 1.2 &sdot; 10<sup>-38</sup> | ca. 3.4 &sdot; 10<sup>38</sup>|
| Double precision | 64 | 52 + 1 sign | 11 | ca. 5.0 &sdot; 10<sup>-324</sup> | ca. 1.8 &sdot; 10<sup>308</sup> |

Note that there are some peculiarities:

* The **actual bit sequence** is the sign bit first, followed by the exponent and finally the significand bits.
* The exponent does not have a sign; instead an **exponent bias** is subtracted from it (127 for single and 1023 for double precision). This, and the bit sequence, allows floating-point numbers to be compared and sorted correctly even when interpreting them as integers.
* The significand's most significant digit is omitted and assumed to be 1, except for **subnormal numbers** which are marked by an all-0 exponent and allow a number range beyond the smallest and largest numbers given in the table above, at the cost of precision.
* There are separate **positive and a negative zero** values, differing in the sign bit, where all other bits are 0. These must be considered equal even though their bit patterns are different.
* There are special **positive and negative infinity** values, where the exponent is all 1-bits and the significand is all 0-bits. These are the results of calculations where the positive range of the exponent is exceeded, or division  of a regular number by zero.
* There are special **not a number** (or NaN) values where the exponent is all 1-bits and the significand is *not* all 0-bits. These represent the result of various undefined calculations (like multiplying 0 and infinity, any calculation involving a NaN value, or application-specific cases). Even bit-identical NaN values must *not* be considered equal.

--- 
标题 : 浮点数
描述 : 解释浮点数的原理和适用场景
---

为什么需要浮点数
----------------

受限于计算机的存储器容量，无论使用[二进制小数](/formats/binary/)还是十进制小数，你都不能保存无限精度的数字 —— 有时候，你不得不截断它。不过，到底需要多么精确？究竟哪里需要截断？整数和小数的位数又应该是多少呢？

* 对于建造公路的工程师，宽度是 10 米还是 10.0001 米无关紧要 —— 很可能在最初测量数据时就没那么精确。
* 对于微芯片的设计者，0.0001 米 （十分之一毫米，100 微米）的距离非常*巨大* —— 但是，他从不涉及到大于 0.1 米的距离。
* 对于物理学家，则需要在计算中同时使用[光速](http://en.wikipedia.org/wiki/Speed_of_light)（大约 3_0000_0000）和（牛顿）[重力常数](http://en.wikipedia.org/wiki/Gravitational_constant)（大约 0.0000_0000_0066_7）。

为了满足工程师和芯片设计者，数字的格式应该能在跨度很大的数量级上都足够精确。不过，只是需要*相对*精确。为了满足物理学家，则必须能对不同数量级的数字进行计算。

事实上，由整数加上小数位组成的定点数并不实用 —— 我们需要的答案是一种 *浮点* 格式。

浮点数怎么算？
-------------

主要思路是用两大部分来构成一个数：

* 尾数：用来包含一个数的具体数字。尾数的正负代表了数字的正负。
* 指数：指出十进制或者二进制小数点相对于尾数首位的位置。如果指数是负的，那么这个数非常小（即接近于 0）。

这个数字格式满足了上述所有的需求：

* 它可以表示的数字数量级很广（由指数部分的长度决定）
* 它在所有的数量级上都能提供一致的相对精度（由尾数部分的长度决定）
* 它允许任意数量级之间的计算：不论是成一个很大的数，还是一个很小的数，结果的精度总是一致的。

十进制浮点数通常采用[科学计数法](http://en.wikipedia.org/wiki/Scientific_notation)表示，其尾数的第一位和第二位（从高到低）之间，总是有一个显式的（小数）点。其指数可能和基一起显式的写出，也可能使用 **e** 与尾数分离开来。

| 尾数   | 指数 | 科学计数法                   | 定点值           |
|--------|------|------------------------------|------------------|
| 1.5    | 4    | 1.5 &sdot; 10<sup>4</sup>    | 15000            |
| -2.001 | 2    | -2.001 &sdot; 10<sup>2</sup> | -200.1           |
| 5      | -3   |  5 &sdot; 10<sup>-3</sup>    | 0.005            |
| 6.667  | -11  | 6.667e-11                    | 0.00000000006667 |

浮点数标准
----------

几乎所有的硬件和编程语言都使用一个相同的二进制格式——即 [IEEE 754](http://en.wikipedia.org/wiki/IEEE_754-2008) 标准定义的格式。常用格式的总长为 32 或者 64 比特：

| 格式   | 总位数 | 尾数位数      | 指数位数 | 最小数                           | 最大数                          |
|--------|--------|---------------|----------|----------------------------------|---------------------------------|
| 单精度 | 32     | 23 + 1 符号位 | 8        | ca. 1.2 &sdot; 10<sup>-38</sup>  | ca. 3.4 &sdot; 10<sup>38</sup>  |
| 双精度 | 64     | 52 + 1 符号位 | 11       | ca. 5.0 &sdot; 10<sup>-324</sup> | ca. 1.8 &sdot; 10<sup>308</sup> |

有几个特殊情况需要注意：

* 在**实际的比特顺序**中，符号位是第一位（最高位），然后是指数，最后是尾数。
* 指数并没有符号位，而是从中减去指数偏移量（对于单精度，这个偏移值是 127，对于双精度是 1023）。依靠指数偏移和浮点数的比特序列，即使把浮点数当做整数理解，也可以正确的比较和排序它们。
* 尾数的最高有效位默认省略，并且假设是 1（译者注：上表中的 23 位尾数，是指省略后为 23 位，加上省略的最高位，是 24 位，再加上符号位，是 25 位）。例外情况是**非规格化数**，它的指数为全 0，并且可以表示超出上表给出的最小数和最大数范围的数字，不过这会牺牲数字的精度。
* 有独立的**正 0 和负 0** 值，二者只有符号位不同，其他所有比特位都是 0。虽然它们的比特值是不同的，但是必须认为是相等的。
* 有特殊的**正无穷大和负无穷大**，它们的指数为全 1 并且尾数是全 0。在计算中，超出指数的上界，或者用一个普通数字（译者注：原文 “regular number”，据 IEEE 754-2008，准确地说应该是“有穷非零数”）除以 0，就会得到无穷大的结果。
* 有特殊的**非数值**（或者简写为 NaN，译者注：原文 “not a number”），其指数为全 1，尾数*不是*全 0。各种未定义的计算的结果使用 NaN 来表示（比如：0 乘以无穷大，任何包括 NaN 值的计算，或者应用程序定义的情况）。即使 NaN 的比特值是一致的，也不能认为二者相等。
