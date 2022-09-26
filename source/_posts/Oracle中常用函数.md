title: Oracle中常用函数
author: LZH
tags:
  - Oracle
  - 函数
categories: []
date: 2019-04-20 19:18:00
---
[https://www.cnblogs.com/lxl57610/p/7442130.html](https://www.cnblogs.com/lxl57610/p/7442130.html)
# 一、字符函数
 字符函数接受字符参数，这些参数可以是表中的列，也可以是一个字符串表达式。
![upload successful](/images/pasted-1.png)
函数	说明
ASCII(X)	返回字符X的ASCII码
CONCAT(X,Y)	连接字符串X和Y
INSTR(X,STR[,START][,N)	从X中查找str，可以指定从start开始，也可以指定从n开始
LENGTH(X)	返回X的长度
LOWER(X)	X转换成小写
UPPER(X)	X转换成大写
LTRIM(X[,TRIM_STR])	把X的左边截去trim_str字符串，缺省截去空格
RTRIM(X[,TRIM_STR])	把X的右边截去trim_str字符串，缺省截去空格
TRIM([TRIM_STR  FROM]X)	把X的两边截去trim_str字符串，缺省截去空格
REPLACE(X,old,new)	在X中查找old，并替换成new
SUBSTR(X,start[,length])	返回X的字串，从start处开始，截取length个字符，缺省length，默认到结尾



![upload successful](/images/20190506Oracle常用函数演示.png)
示例	示例结果
SELECT ASCII('a') FROM dual;	97
SELECT CONCAT('Hello','world') FROM dual;	Helloworld
SELECT INSTR('Hello world','or') FROM dual;	8
SELECT LENGTH('Hello') FROM dual;	5
SELECT LOWER('Hello') FROM dual;	hello
SELECT UPPER('hello') FROM dual;	HELLO
SELECT LTRIM('=Hello=','=') FROM dual;	Hello=
SELECT RTRIM('=Hello=','=') FROM dual;	=Hello
SELECT TRIM('='FROM'=Hello=') FROM dual;	Hello
SELECT REPLACE('ABCDE','CD','AAA')FROM dual;	ABAAAE
SELECT SUBSTR('ABCDE',2,3) FROM dual;	BCD

# 二、数字函数
数字函数接受数字参数，参数可以来自表中的一列，也可以是一个数字表达式。
函数	说明	示例
ABS(X)	X的绝对值	ABS(-3)=3
ACOS(X)	X的反余弦	ACOS(1)=0
COS(X)	余弦	COS(1)=0.54030230586814
CEIL(X)	大于或等于X的最小值	CEIL(5.4)=6
FLOOR(X)	小于或等于X的最大值	FLOOR(5.8)=5
LOG(X,Y)	X为底Y的对数	LOG(2，4)=2
MOD(X,Y)	X除以Y的余数	MOD(8，3)=2
POWER(X,Y)	X的Y次幂	POWER(2，3)=8
ROUND(X[,Y])	X在第Y位四舍五入	ROUND(3.456，2)=3.46
SQRT(X)	X的平方根	SQRT(4)=2
TRUNC(X[,Y])	X在第Y位截断	TRUNC(3.456，2)=3.45

![upload successful](/images/20190506数字函数演示.png)

# 三、日期函数

