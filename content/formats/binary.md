--- 
title: Binary Fractions
description: In-depth explanation of how binary fractions work, what problems the cause and why they are used anyway
---

How they work
-------------
As a programmer, you should be familiar with the concept of binary integers, i.e.
the representation of integer numbers as a series of bits:

<table>
<tr><th colspan="9">Decimal (<span class="num_base">base 10</span>)</th><th> </th><th colspan="17">Binary (<span class="num_base">base 2</span>)</th></tr>
<tr class="base_example">
<td class="digit">1</td><td>&sdot;</td><td class="num_base">10<sup>1</sup></td><td>+</td>
<td class="digit">3</td><td>&sdot;</td><td class="num_base">10<sup>0</sup></td><td>=</td>
<td class="digit">13<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">1101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>3</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>2</sup></td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td class="num_base">2<sup>1</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>0</sup></td>
</tr><tr class="base_example">
<td class="digit">1</td><td>&sdot;</td><td>10</td><td>+</td>
<td class="digit">3</td><td>&sdot;</td><td>1 </td><td>=</td>
<td class="digit">13<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">1101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td>8</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>4</td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td>2</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>1</td>
</tr></table>

This is how computers store integer numbers internally. And for fractional numbers in [positional notation](http://en.wikipedia.org/wiki/Positional_notation), they do the same thing:

<table>
<tr><th colspan="13">Decimal (<span class="num_base">base 10</span>)</th><th> </th><th colspan="13">Binary (<span class="num_base">base 2</span>)</th></tr>
<tr class="base_example">
<td class="digit">6</td><td>&sdot;</td><td class="num_base">10<sup>-1</sup></td><td>+</td>
<td class="digit">2</td><td>&sdot;</td><td class="num_base">10<sup>-2</sup></td><td>+</td>
<td class="digit">5</td><td>&sdot;</td><td class="num_base">10<sup>-3</sup></td><td>=</td>
<td class="digit">0.625<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">0.101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>-1</sup></td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td class="num_base">2<sup>-2</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>-3</sup></td>
</tr><tr class="base_example">
<td class="digit">6</td><td>&sdot;</td><td>1/10</td><td>+</td>
<td class="digit">2</td><td>&sdot;</td><td>1/100</td><td>+</td>
<td class="digit">5</td><td>&sdot;</td><td>1/1000</td><td>=</td>
<td class="digit">0.625<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">0.101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td>1/2</td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td>1/4</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>1/8</td>
</tr></table>

Problems
--------
While they work the same in principle, binary fractions are different from decimal fractions in what
numbers they can accurately represent with a given number of digits, and thus also in what numbers result in [rounding errors](/errors/rounding/):

Specifically, binary can only represent those numbers as a finite fraction where the denominator
is a power of 2. Unfortunately, this does not include most of the numbers that can be 
represented as finite fraction in base 10, like 0.1.

| Fraction | Base | Positional Notation | Rounded to 4 digits| Rounded value as fraction | Rounding error |
|-|-|-|-|
| 1/10 | 10 | 0.1 | 0.1 | 1/10 | 0 |
| 1/3  | 10 | 0.<span class="over">3</span> | 0.3333 | 3333/10000 | 1/30000 |
| 1/2  | 2  | 0.1 | 0.1 | 1/2 | 0 |
| 1/10 | 2  | 0.0<span class="over">0011</span> | 0.0001 | 1/16 | 3/80 |

And this is how you already get a rounding error when you just *write down* a number like 0.1 and
run it through your interpreter or compiler. It's not as big as 3/80 and may be invisible because
computers cut off after 23 or 52 binary digits rather than 4. But the error is there and *will* cause
problems eventually if you just ignore it.


Why use Binary?
---------------
At the lowest level, computers are based on billions of electrical elements that have only two states, (usually low and high voltage). By interpreting these as 0 and 1, it's very easy to build circuits for storing binary numbers and doing calculations with them.

While it's possible to simulate the behaviour of decimal numbers with binary circuits as well, it's less efficient. If computers used decimal numbers internally, they'd have less memory and be slower at the same level of technology. 

Since the difference in behaviour between binary and decimal numbers is not important for most applications, the logical choice is to build computers based on binary numbers and live with the fact
that some extra care and effort are necessary for applications that require [decimal-like behaviour](/formats/exact/).

二进制小数
----------

他们是如何工作的
----------------

作为程序员的你，应该熟悉二进制整数这个概念，或者说，使用一串比特来表示的整形数字：

<table>
<tr><th colspan="9">Decimal (<span class="num_base">base 10</span>)</th><th> </th><th colspan="17">Binary (<span class="num_base">base 2</span>)</th></tr>
<tr class="base_example">
<td class="digit">1</td><td>&sdot;</td><td class="num_base">10<sup>1</sup></td><td>+</td>
<td class="digit">3</td><td>&sdot;</td><td class="num_base">10<sup>0</sup></td><td>=</td>
<td class="digit">13<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">1101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>3</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>2</sup></td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td class="num_base">2<sup>1</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>0</sup></td>
</tr><tr class="base_example">
<td class="digit">1</td><td>&sdot;</td><td>10</td><td>+</td>
<td class="digit">3</td><td>&sdot;</td><td>1 </td><td>=</td>
<td class="digit">13<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">1101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td>8</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>4</td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td>2</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>1</td>
</tr></table>

在计算机内部，整数就是这样存储的。同样，对于按位计数的小数，也如此表示：

<table>
<tr><th colspan="13">Decimal (<span class="num_base">base 10</span>)</th><th> </th><th colspan="13">Binary (<span class="num_base">base 2</span>)</th></tr>
<tr class="base_example">
<td class="digit">6</td><td>&sdot;</td><td class="num_base">10<sup>-1</sup></td><td>+</td>
<td class="digit">2</td><td>&sdot;</td><td class="num_base">10<sup>-2</sup></td><td>+</td>
<td class="digit">5</td><td>&sdot;</td><td class="num_base">10<sup>-3</sup></td><td>=</td>
<td class="digit">0.625<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">0.101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>-1</sup></td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td class="num_base">2<sup>-2</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>-3</sup></td>
</tr><tr class="base_example">
<td class="digit">6</td><td>&sdot;</td><td>1/10</td><td>+</td>
<td class="digit">2</td><td>&sdot;</td><td>1/100</td><td>+</td>
<td class="digit">5</td><td>&sdot;</td><td>1/1000</td><td>=</td>
<td class="digit">0.625<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">0.101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td>1/2</td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td>1/4</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>1/8</td>
</tr></table>

问题
----

尽管它们遵循相同的运算法则，不过，在给定的位数中，二者能够精确表示的数字是不同的，因此，它们误差舍入的结果也不同：

特别是，只有分母是 2 的幂的小数才能用二进制表示。很不幸，这样的小数只占十进制能够表示的小数的很小一部分，比如，不能表示 0.1 。

| Fraction | Base | Positional Notation | Rounded to 4 digits| Rounded value as fraction | Rounding error |
|-|-|-|-|
| 1/10 | 10 | 0.1 | 0.1 | 1/10 | 0 |
| 1/3  | 10 | 0.<span class="over">3</span> | 0.3333 | 3333/10000 | 1/30000 |
| 1/2  | 2  | 0.1 | 0.1 | 1/2 | 0 |
| 1/10 | 2  | 0.0<span class="over">0011</span> | 0.0001 | 1/16 | 3/80 |

这样，当你写下一个数字，比方说 0.1，然后通过解释器或者编译器运行它，就会产生舍入误差。误差不会有 3/80 那么大，甚至是不可见的，这是因为计算机并不是从第 4 比特位之后截断数字，而是从 23 或者 52 位之后。但是，如果你视之不见，那么误差会始终存在并最终导致问题。

为何使用二进制？
----------------

在最底层，计算机构建于数十亿的电子元件之上，这些元件只有两种状态（通常是低电平和高电平）。把这两种状态解释为 0 和 1，构建电路来存储和计算二进制数就变得很容易。

虽然也可以用二进制电路模拟十进制数，不过这很低效。如果在计算机内部使用十进制数，那么在相同的技术水平下，计算机的存储器会更小，并且速度更慢。

对于多数应用程序，二进制数和十进制数的行为区别并不重要，所以，基于二进制数构建计算机，对于要求保持十进制行为的应用程序给予额外的关注和处理，是合理的选择。
