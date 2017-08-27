--- 
title: Floating-point cheat sheet for Python
description: Tips for using floating-point and decimal numbers in Python
--- 

Floating-Point Types
--------
Almost all platforms map Python floats to [IEEE 754](/formats/fp/)
double precision.

		f = 0.1 

Decimal Types
-------------
Python has an [arbitrary-precision](/formats/exact/) decimal type named <code>Decimal</code> in the <code>decimal</code> module, which also allows to choose the [rounding mode](/errors/rounding/).

		a = Decimal('0.1')
		b = Decimal('0.2')
		c = a + b # returns a Decimal representing exactly 0.3

How to Round
------------
To get a string:

		"%.2f" % 1.2399 # returns "1.24"
		"%.3f" % 1.2399 # returns "1.240"
		"%.2f" % 1.2 # returns "1.20"
		
To print to standard output:

		print "%.2f" % 1.2399 # just use print and string formatting
		
Specific [rounding modes](/errors/rounding/) and other parameters can be defined in a Context object:

		getcontext().prec = 7

Resources 
---------
* [Floating Point Arithmetic: Issues and Limitations](http://docs.python.org/tutorial/floatingpoint.html)
* [The decimal module](http://docs.python.org/library/decimal.html)
    * [Context objects](http://docs.python.org/library/decimal.html#context-objects)
* [String formatting in Python](http://docs.python.org/library/stdtypes.html#string-formatting-operations)



---
title: 为 Python 准备的浮点小抄
description: Tips for using floating-point and decimal numbers in Python
---

浮点类型
--------
几乎所有平台把 Python 的浮点映射成 [IEEE 754](/formats/fp/) 双精度。

		f = 0.1

小数类型
-------------
Python 有 [arbitrary-precision](/formats/exact/) 小数类型，称为 <code>Decimal</code>，这个类型在  <code>decimal</code> 模块中，它同样允许选择 [取整模式](/errors/rounding/). 

		a = Decimal('0.1')
		b = Decimal('0.2')
		c = a + b # 返回 Decimal 表示的精确的 0.3

如何取整
------------
得到字符串：

		"%.2f" % 1.2399 # 返回 "1.24"
		"%.3f" % 1.2399 # 返回 "1.240"
		"%.2f" % 1.2 # 返回 "1.20"

打印到标准输出：

		print "%.2f" % 1.2399 # 只是使用打印和字符串格式化

特殊的 [取整模式](/errors/rounding/) 和其它参数可以在一个 Context 对象中定义：

		getcontext().prec = 7

资源
---------
* [浮点代数：问题和限制](http://docs.python.org/tutorial/floatingpoint.html)
* [小数模块](http://docs.python.org/library/decimal.html)
    * [Context 对象](http://docs.python.org/library/decimal.html#context-objects)
* [Python 中字符串的定义](http://docs.python.org/library/stdtypes.html#string-formatting-operations)
