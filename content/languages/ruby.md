--- 
title: Floating-point cheat sheet for Ruby
description: Tips for using floating-point and decimal numbers in Ruby
--- 

Floating-Point Types
--------
Ruby floats are mapped to double-precision [IEEE 754](/formats/fp/).

		f = 0.1 

Decimal Types
-------------
Ruby has an [arbitrary-precision](/formats/exact/) decimal type named <code>BigDecimal</code> in the <code>bigdecimal</code> module, which also allows to choose the [rounding mode](/errors/rounding/).

		require 'bigdecimal'

		a = BigDecimal('0.1')
		b = BigDecimal('0.2')
		c = a + b # returns a BigDecimal representing exactly 0.3

How to Round
------------
To get a string:

		"%.2f" % 1.2399 # returns "1.24"
		"%.3f" % 1.2399 # returns "1.240"
		"%.2f" % 1.2 # returns "1.20"
		
To print to standard output:

		puts "%.2f" % 1.2399
		
Resources 
---------
* [Floating Point Arithmetic](http://www.ruby-doc.org/core-2.1.2/Float.html)
* [The bigdecimal module](http://www.ruby-doc.org/stdlib-2.1.2/libdoc/bigdecimal/rdoc/index.html)
* [String formatting in Ruby](http://www.ruby-doc.org/core-2.1.2/String.html)


--- 
title: 为 Ruby 准备的浮点小抄
description: Tips for using floating-point and decimal numbers in Ruby
--- 

浮点类型
--------
Ruby 浮点映射 [IEEE 754](/formats/fp/) 双精度浮点.

		f = 0.1 

小数类型
-------------
在 Ruby 的 <code>bigdecimal</code> 模块中有一个称为 <code>BigDecimal</code> 的 [arbitrary-precision](/formats/exact/) 小数类型，它同时允许选择 [取整模式](/errors/rounding/)。

		require 'bigdecimal'

		a = BigDecimal('0.1')
		b = BigDecimal('0.2')
		c = a + b # 返回 BigDecimal 表示的精确的 0.3

如何取整
------------
得到字符串：

		"%.2f" % 1.2399 # 返回 "1.24"
		"%.3f" % 1.2399 # 返回 "1.240"
		"%.2f" % 1.2 # 返回 "1.20"

打印到标准输出：

		puts "%.2f" % 1.2399

资源
---------
* [浮点代数](http://www.ruby-doc.org/core-2.1.2/Float.html)
* [bigdecimal 模块](http://www.ruby-doc.org/stdlib-2.1.2/libdoc/bigdecimal/rdoc/index.html)
* [在 Ruby 里进行字符串格式化](http://www.ruby-doc.org/core-2.1.2/String.html)
