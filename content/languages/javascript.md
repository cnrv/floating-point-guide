--- 
title: Floating-point cheat sheet for JavaScript
description: Tips for using floating-point and decimal numbers in JavaScript
--- 

Floating-Point Types
--------
JavaScript is dynamically typed and will often convert implicitly between strings and floating-point numbers (which are IEEE 64 bit values). To force a variable to floating-point, use the global <code>parseFloat()</code> function.

		var num = parseFloat("3.5");

Decimal Types
-------------

The oldest decimal type for JavaScript seems to be a port of [Java's](/languages/java/) <code>BigDecimal</code> class, which also supports [rounding modes](/errors/rounding/):

		var a = new BigDecimal("0.01");
		var b = new BigDecimal("0.02");
		var c = a.add(b); // 0.03
		var d = c.setScale(1, BigDecimal.prototype.ROUND_HALF_UP);

There is also <code>bignumber.js</code>, which is smaller and [faster](http://jsperf.com/bignumber-js-vs-big-js-vs-decimal-js/8):

		BigNumber.config({ROUNDING_MODE: BigNumber.ROUND_HALF_UP})
		var a = new BigNumber("0.01");
		var b = new BigNumber("0.02");
		var c = a.plus(b); // BigNumber(0.03)
		var d = c.toFixed(1); // "0.0"


How to Round
------------

		var num = 5.123456;
		num.toPrecision(1) //returns 5 as string
		num.toPrecision(2) //returns 5.1 as string
		num.toPrecision(4) //returns 5.123 as string
		
Using a specific rounding mode:

		new BigDecimal("1.25").setScale(1, BigDecimal.prototype.ROUND_HALF_UP);


Resources 
---------
* [BigDecimal for JavaScript](https://github.com/dtrebbien/BigDecimal.js)
* [bignumber.js](https://github.com/MikeMcl/bignumber.js)
* [Core JavaScript Reference](https://developer.mozilla.org/en/JavaScript/Reference)  
  * [parseFloat()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/parseFloat)
  * [toPrecision()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number/toPrecision)



--- 
title: 为 JavaScript 准备的浮点小抄
description: Tips for using floating-point and decimal numbers in JavaScript
--- 

浮点类型
--------
JavaScript 是动态类型的，它经常暗地里在字符串和浮点数（IEEE 64 位值）之间转换。为了强制一个变量为浮点类型，可以使用全局函数 <code>parseFloat()</code>。

		var num = parseFloat("3.5");

小数类型
-------------

最古老的 JavaScript 小数类型是从 [Java的](/languages/java/) <code>BigDecimal</code> 类中移植的，它也支持 [取整模式](/errors/rounding/)：

		var a = new BigDecimal("0.01");
		var b = new BigDecimal("0.02");
		var c = a.add(b); // 0.03
		var d = c.setScale(1, BigDecimal.prototype.ROUND_HALF_UP);

也有 <code>bignumber.js</code>，它更小[更快](http://jsperf.com/bignumber-js-vs-big-js-vs-decimal-js/8)：

		BigNumber.config({ROUNDING_MODE: BigNumber.ROUND_HALF_UP})
		var a = new BigNumber("0.01");
		var b = new BigNumber("0.02");
		var c = a.plus(b); // BigNumber(0.03)
		var d = c.toFixed(1); // "0.0"


如何取整
------------

		var num = 5.123456;
		num.toPrecision(1) //以字符串形式返回 5 as string
		num.toPrecision(2) //以字符串形式返回 5.1 as string
		num.toPrecision(4) //以字符串形式返回 5.123 as string

使用特殊的取整模式：

		new BigDecimal("1.25").setScale(1, BigDecimal.prototype.ROUND_HALF_UP);


资源
---------
* [Javascript 里的 BigDecimal](https://github.com/dtrebbien/BigDecimal.js)
* [bignumber.js](https://github.com/MikeMcl/bignumber.js)
* [JavaScript 核心参考](https://developer.mozilla.org/en/JavaScript/Reference)
  * [parseFloat()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/parseFloat)
  * [toPrecision()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number/toPrecision)

