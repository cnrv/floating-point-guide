--- 
title: Floating-point cheat sheet for SQL
description: Tips for using floating-point and decimal numbers in SQL
--- 

Floating-Point Types
--------
The SQL standard defines three binary floating-point types:

* `REAL` has implementation-dependant precision (usually maps to a hardware-supported type like IEEE 754 single or double precision)
* `DOUBLE PRECISION` has implementation-dependant precision which is greater than `REAL` (usually maps to IEEE 754 double precision)
* `FLOAT(N)` has at least `N` binary digits of precision, with an implementation-dependant maximum for `N`

The exponent range for all three types is implementation-dependant as well.

Decimal Types
-------------
The standard defines two fixed-point decimal types:

* `NUMERIC(M,N)` has exactly `M` total digits, `N` of them after the decimal point
* `DECIMAL(M,N)` is the same as `NUMERIC(M,N)`, except that it is allowed to have more than `M` total digits

The maximum values of `M` and `M` are implementation-dependant. Vendors often implement the two types identically.

How to Round
------------

The SQL standard defines no explicit rounding, but most vendors provide a `ROUND()` or `TRUNC()` function.

However, it usually makes little sense to round within the database, since its job is *storing* data, while rounding is an aspect of *displaying* data, and should therefore be done by the code in the presentation layer.


Resources 
---------
* [Official ISO SQL 2008 standard (non-free)](http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=38640)  
* [SQL 92 draft (free)](http://www.contrib.andrew.cmu.edu/~shadow/sql/sql1992.txt)
* [MySQL numeric types](http://dev.mysql.com/doc/refman/5.0/en/numeric-types.html)
* [PostgreSQL Numeric Types](https://www.postgresql.org/docs/current/static/datatype-numeric.html)
* [MS SQL Server data types](http://msdn.microsoft.com/en-US/library/ms187752%28v=SQL.90%29.aspx)


--- 
title: 为 SQL 准备的浮点小抄
description: Tips for using floating-point and decimal numbers in SQL
--- 

浮点类型
--------
SQL 标准定义了三个二进制浮点类型：

* `REAL` 是和实现相关的精度 (通常映射到硬件支持的类型，比如 IEEE 754 单精度或双精度)
* `DOUBLE PRECISION` 是和实现相关的精度，它比 `REAL` 更大(通常映射到 IEEE 754 双精度)
* `FLOAT(N)` 至少有 `N` 位二进制数的精度，它和实现相关最大化 `N`

The exponent range for all three types is implementation-dependant as well.

小数类型
-------------
标准定义了两个定点小数类型：

* `NUMERIC(M,N)` 的总数字数正好有 `M` 个， 其中 `N` 个是小数点以后的数字个数
* `DECIMAL(M,N)` 和 `NUMERIC(M,N)` 几乎一样，除了它允许总数字数多于 `M`

`M` 和 `M` 的最大值和实现相关。SQL 供应商经常是把二者实现相同。

如何取整
------------

SQL 标准没有取整，但大多数供应商会提供 `ROUND()` 或者 `TRUNC()` 函数。

但在数据库中取整意义不大，因为数据库的工作是 *保存* 数据，但取整是 *显示* 数据，因此这类代码应该在表示层实现。


资源
---------
* [官方 ISO SQL 2008 标准 (不免费)](http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=38640)
* [SQL 92 草案 (免费)](http://www.contrib.andrew.cmu.edu/~shadow/sql/sql1992.txt)
* [MySQL 数字类型](http://dev.mysql.com/doc/refman/5.0/en/numeric-types.html)
* [PostgreSQL 数字类型](https://www.postgresql.org/docs/current/static/datatype-numeric.html)
* [MS SQL Server 数据类型](http://msdn.microsoft.com/en-US/library/ms187752%28v=SQL.90%29.aspx)
