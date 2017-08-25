---
title: Basic Answers
description: Concise answers to common basic questions about floating-point math, like "Why don't my numbers add up?"
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


---
title: 基础答案
description: Concise answers to common basic questions about floating-point math, like "Why don't my numbers add up?"
---

### 为什么我的数字，比如 0.1 + 0.2 加起来不正好是 0.3，而是奇怪的类似 0.30000000000000004 的结果？

因为在计算机内部使用的格式 ([二进制](/formats/binary/) [浮点](/formats/fp/)) *完全*不能
精确地表示像 0.1, 0.2 或者 0.3 这样的数。

当代码编译或解释后，你的 "0.1" 就已经在这种格式下取整到最接近的数；甚至在你计算前，
[取整错误](/errors/rounding/) 已经在取整的结果中产生了。

### 为什么计算机用这么傻的系统？

它不是傻，只是不同而已。小数也不能精确地表示像 1/3 这样的数，所以你不得不取整到
0.33 - 你也不能期望 0.33 + 0.33 + 0.33 得到 1 - 对吧。

计算机使用[二进制数](/formats/binary/) 因为在处理的时候更快，也因为在大多数计算时，你处
理的数字不需要取整（或者那么精确），这样在小数的第十七位上发生细微的误差完全无关紧要。

### 我怎么做能避免这样的问题？

这取决于你做什么类型的计算。

* 如果你确实需要累加的结果完全准确，特别是在你和钱打交道的时候：使用特殊的 [小数数据类型](/formats/exact/)。
* 如果你只是不想看到所有多出来的二进制位数：简单地格式化你的结果，让它在显示的时候取整到固定的小数位。
* 如果你没有小数数据类型，替代的方案是用[整数](/formats/integer/)，例如，在做钱的计算时完全以分为单位。但是这需要更多的工作和缺点。

### 为什么其它的计算，比如 0.1 + 0.4 结果正确？

在那个情况下，结果(0.5)是*可以*精确地表示为浮点数，也可能两者之间的取整错误相互抵消 - 
但这不是必然相关的 （例如，当那两个数字首先存放在不同精度的浮点类型时，两数之间的取整错误也许不一定相互对齐）。

在另外的情况如 0.1 + 0.3，结果确实不是*真实*的0.4，但足够接近了，这个0.4和其它浮点数比
是最接近结果的。很多语言就显示这个数字，而不是把实际的结果转换回最接近的小数。
