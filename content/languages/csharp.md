--- 
title: Floating-point cheat sheet for C#
description: Tips for using floating-point and decimal numbers in C#
--- 

Floating-Point Types
--------
C# has [IEEE 754](/formats/fp/) single and double precision types supported by keywords:

		float f = 0.1f; // 32 bit float, note f suffix
		double d = 0.1d; // 64 bit float, suffix optional


Decimal Types
-------------
C# has a 128 bit [limited-precision](/formats/exact/) decimal type denoted by the keyword
<code>decimal</code>:

		decimal myMoney = 300.1m; // note m suffix on the literal


How to Round
------------
The <code>Math.Round()</code> method works with the double and decimal types, and allows you to specify a [rounding mode](/errors/rounding/):

		Math.Round(1.25m, 1, MidpointRounding.AwayFromZero); // returns 1.3



Resources 
---------
* [C# Reference](http://msdn.microsoft.com/en-us/library/618ayhy6%28v=VS.80%29.aspx)
   * [float type](http://msdn.microsoft.com/en-us/library/b1e65aza%28v=VS.80%29.aspx)  
   * [double type](http://msdn.microsoft.com/en-us/library/678hzkk9%28v=VS.80%29.aspx)  
   * [decimal type](http://msdn.microsoft.com/en-us/library/364x0z75%28v=VS.80%29.aspx)  
   * [Math.Round()](http://msdn.microsoft.com/en-US/library/system.math.round%28v=VS.80%29.aspx)



--- 
title: 为 C# 准备的浮点小抄
description: Tips for using floating-point and decimal numbers in C#
--- 

Floating-Point Types
--------
C# 用关键字来支持 [IEEE 754](/formats/fp/) 的单精度和双精度类型：

		float f = 0.1f; // 32 bit float, note f suffix
		double d = 0.1d; // 64 bit float, suffix optional


小数类型
-------------
C# 用关键字 <code>decimal</code> 来支持 128 位 [limited-precision](/formats/exact/) 小数类型：

		decimal myMoney = 300.1m; // note m suffix on the literal


如何取整
------------
<code>Math.Round()</code> 方法与双精度和小数类型一直工作，现时也允许使用特定的 [取整模式](/errors/rounding/)：

		Math.Round(1.25m, 1, MidpointRounding.AwayFromZero); // returns 1.3


资源
---------
* [C# 参考](http://msdn.microsoft.com/en-us/library/618ayhy6%28v=VS.80%29.aspx)
   * [浮点类型](http://msdn.microsoft.com/en-us/library/b1e65aza%28v=VS.80%29.aspx)
   * [双精度类型](http://msdn.microsoft.com/en-us/library/678hzkk9%28v=VS.80%29.aspx)
   * [小数类型](http://msdn.microsoft.com/en-us/library/364x0z75%28v=VS.80%29.aspx)
   * [Math.Round()](http://msdn.microsoft.com/en-US/library/system.math.round%28v=VS.80%29.aspx)


