---
title: Basic Answers
description: Concise answers to common basic questions about floating-point math, like "Why don't my numbers add up?"
标题: 基础答案
描述: 关于浮点数学的基础问题的简明回答，例如“为什么我的数字加起来不对?"
---

### Why don't my numbers, like 0.1 + 0.2 add up to a nice round 0.3, and instead I get a weird result like 0.30000000000000004?

Because internally, computers use a format ([binary](/formats/binary/) [floating-point](/formats/fp/)) that
cannot accurately represent a number like 0.1, 0.2 or 0.3 *at all*.

When the code is compiled or interpreted, your "0.1" is already 
rounded to the nearest number in that format, which results 
in a small [rounding error](/errors/rounding/) even before the calculation happens.

### Why do computers use such a stupid system?

It's not stupid, just different. Decimal numbers cannot accurately 
represent a number like 1/3, so you have to round to something like 
0.33 - and you  don't expect 0.33 + 0.33 + 0.33 to add up to 1, either - do you?

Computers use [binary numbers](/formats/binary/) because they're faster at dealing with 
those, and because for most calculations, a tiny error in the 17th
decimal place doesn't matter at all since the numbers you work with
aren't round (or that precise) anyway.

### What can I do to avoid this problem?

That depends on what kind of calculations you're doing.

* If you really need your results to add up exactly, especially when you work with money: use a special [decimal datatype](/formats/exact/).
* If you just don't want to see all those extra decimal places: simply format your result rounded to a fixed number of decimal places when displaying it.
* If you have no decimal datatype available, an alternative is to work with [integers](/formats/integer/), e.g. do money calculations entirely in cents. But this is more work and has some drawbacks.

### Why do other calculations like 0.1 + 0.4 work correctly?

In that case, the result (0.5) *can* be represented exactly as a floating-point number,
and it's possible for rounding errors in the input numbers to cancel each other out -
But that can't necessarily be relied upon (e.g. when those two numbers
were stored in differently sized floating point representations first, the rounding 
errors might not offset each other).

In other cases like 0.1 + 0.3, the result actually isn't *really* 0.4, but close enough that 0.4 
is the shortest number that is closer to the result than to any other floating-point number. Many languages then display that number instead of converting the actual result back to the closest
decimal fraction.

### 为什么我的数字，比如 0.1 + 0.2 加起来不正好是 0.3，而是奇怪的类似 0.30000000000000004 的结果？

因为计算机内部使用的格式 ([二进制](/formats/binary/) [浮点](/formats/fp/)) 不能
精确地表示像 0.1, 0.2 或者 0.3 这样的数。

当代码编译或解释后，你的 "0.1" 就已经舍入到在这种格式下最接近的数；即使没有进行任何计算，
这已经造成了一个小的[舍入误差](/errors/rounding/) 。

### 为什么计算机用这么傻的（记数）系统？

它不是傻，只是不同而已。小数不能精确地表示像 1/3 这样的数，所以你不得不舍入到类似
0.33 这样的数 - 你也不能期望 0.33 + 0.33 + 0.33 得到 1 - 对吧?

计算机使用[二进制数](/formats/binary/) 因为在处理的时候更快，也因为在大多数计算时，你处
理的数字不需要舍入（或者那么精确），所以,在小数点后第 17 位上的细微误差完全无关紧要。

### 我怎么做能避免这样的问题？

这取决于你做什么类型的计算。

* 如果你确实需要累加的结果完全准确，特别是在你和钱打交道的时候：使用特殊的 [小数数据类型](/formats/exact/)。
* 如果你只是不想看到所有多出来的小数位：简单地格式化你的结果，让它在显示的时候舍入到固定的小数位。
* 如果你没有小数数据类型，替代的方案是用[整数](/formats/integer/)，例如，在进行货币计算时完全以分为单位，但是这需要更多的工作，也存在一些弊端。

### 为什么其它的计算，比如 0.1 + 0.4 结果正确？

在这种情况下，浮点数*可以*精确地表示结果（0.5），也可能是两者输入数字之间的舍入误差相互抵消 - 
但是这不一定可靠（例如，当那两个数字起先使用不同精度的浮点格式存放时，舍入误差不一定相互抵消）。

在另外的情况如 0.1 + 0.3，结果确实不是*真实*的 0.4，但足够接近了，这个 0.4 和其它浮点数比
是最接近结果的。很多语言就显示这个数字，而不是把实际的结果转换回最接近的小数。
