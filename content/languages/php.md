--- 
title: Floating-point cheat sheet for PHP
description: Tips for using floating-point and decimal numbers in PHP
--- 

Floating-Point Types
--------
PHP is dynamically typed and will often convert implicitly between strings and floating-point numbers (which are platform-dependant, but typically IEEE 64 bit values). To force a value to floating-point, evaluate it in a numerical context:

		$foo = 0 + "10.5"; 


Decimal Types
-------------
The BC Math extension implements [arbitrary-precision](/formats/exact/) decimal math:

		$a = '0.1';
		$b = '0.2';
		echo bcadd($a, $b);     // prints 0.3

How to Round
------------
Rounding can be done with the `number_format()` function:

		$number = 4.123;
		echo number_format($number, 2); // prints 4.12


Resources 
---------
* [PHP manual](http://www.php.net/manual/en/index.php)
   * [Floating point types](http://www.php.net/manual/en/language.types.float.php)
   * [BC Math extension](http://php.net/manual/en/ref.bc.php)
   * [number_format()](http://php.net/manual/en/function.number-format.php)




--- 
title: 为 PHP 准备的浮点小抄
description: Tips for using floating-point and decimal numbers in PHP
--- 

Floating-Point Types
--------
PHP 是动态类型的，它经常暗地里在字符串和浮点数（它们是平台相关的，但典型的是 IEEE 64 位值）之间转换。为了强制一个值为浮点类型，可以在数字上下文中使用：

		$foo = 0 + "10.5"; 


小数类型
-------------
BC Math 扩展实现了[arbitrary-precision](/formats/exact/) 小数数学：

		$a = '0.1';
		$b = '0.2';
		echo bcadd($a, $b);     // 打印 0.3

如何取整
------------
取整可以用 `number_format()` 函数完成：

		$number = 4.123;
		echo number_format($number, 2); // 打印 4.12


资源
---------
* [PHP 手册](http://www.php.net/manual/en/index.php)
   * [浮点类型](http://www.php.net/manual/en/language.types.float.php)
   * [BC Math 扩展](http://php.net/manual/en/ref.bc.php)
   * [number_format()](http://php.net/manual/en/function.number-format.php)

