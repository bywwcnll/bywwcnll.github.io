---
title: js基本概念
date: 2017-06-01 10:12:17
categories:
tags:
- js学习笔记
---

## 数据类型
### 基本数据类型

Undefined、Null、Boolean、Number、String
### 复杂数据类型
Object


---
## typeof操作符
对一个值使用 typeof 操作符可能返回下列某个字符串:
- "undefined"——如果这个值未定义;
- "boolean"——如果这个值是布尔值;
- "string"——如果这个值是字符串;
- "number"——如果这个值是数值;
- "object"——如果这个值是对象或 **null** ;
- "function"——如果这个值是函数;
``` js
typeof null;            //'object'
typeof undefined;       //'undefined'
//typeof function;      //SyntaxError
typeof function(){};    //'function'
typeof (function(){});  //'function'
//typeof ()=>{};        //SyntaxError
typeof (()=>{});        //'function'
```
typeof 操作符的操作数可以是变量(message),也可以是数值字面量。
typeof 是一个操作符而不是函数,因此例子中的圆括号尽管可以使用,但不是必需的。
> *Safari 5 及之前版本、Chrome 7 及之 前版本在对正则表达式调用 typeof 操作符时会返回"function",而其他浏览器在这种情况下会返回 "object"。*


---
## Undefined类型
```js
var a = undefined;
console.log(a);         //'undefined'
```
未经初始 化的值默认就会取得 undefined 值。
```js
var a;
console.log(a);         //'undefined'
console.log(b);         //ReferenceError: b is not defined
console.log(null==c);   //ReferenceError: c is not defined
console.log(typeof a);  //'undefined'
console.log(typeof b);  //'undefined'
```
> *对于尚未声明过的变量,只能执行一项操作,即使用 typeof 操作符检测其数据类型(对未经声明的变量调用 delete 不会导致错 误,但这样做没什么实际意义,而且在严格模式下确实会导致错误)。*


---
## Null类型
```js
var a = null;
console.log(a);         //'object'
```
Null 类型是第二个只有一个值的数据类型,这个特殊的值是 null。从逻辑角度来看,null 值表 示一个空对象指针,而这也正是使用 typeof 操作符检测 null 值时会返回"object"的原因。
```js
console.log(null==undefined);       //true
console.log(null===undefined);      //false
```
undefined 值是派生自 null 值的,因此 ECMA-262 规定对它们的相等性测试要返回 true。


---
## Boolean类型
Boolean 类型的字面值 true 和 false 是区分大小写的。也就是说,`True` 和 `False` (以及其他的混合大小写形式)都不是 Boolean 值,只是标识符。
-- 对任何数据类型的值调用 Boolean()函数,而且总会返回一个 Boolean 值。至于返回的 这个值是 true 还是 false,取决于要转换值的数据类型及其实际值。

数据类型 | 转换为true的值 | 转换为false的值
--- | --- | ---
Boolean | true | false
String | 任何非空字符串 |  ""(空字符串)
Number | 任何非零数字值(包括无穷大) | 0和NaN(参见本章后面有关NaN的内容)
Object | 任何对象 | null
Undefined | N/A(不适用) | undefined


---
## Number类型
Number 类型应该是 ECMAScript 中最令人关注的数据类型了,这种类型使用 IEEE754 格式来表示 整数和浮点数值(浮点数值在某些语言中也被称为双精度数值)。
为支持各种数值类型,ECMA-262 定 义了不同的数值字面量格式。
```js
var intNum = 55;        // 十进制整数

var octalNum1 = 070;    // 八进制的 56
var octalNum2 = 079;    // 无效的八进制数值——解析为 79
var octalNum3 = 08;     // 无效的八进制数值——解析为 8

var hexNum1 = 0xA;      // 十六进制的 10
var hexNum2 = 0x1f;     // 十六进制的 31

```
*八进制字面量在严格模式下是无效的,会导致支持的 JavaScript 引擎抛出错误。*
> 在进行算术计算时,所有以八进制和十六进制表示的数值最终都将被转换成十进制数值。

- 浮点数值
由于保存浮点数值需要的内存空间是保存整数值的两倍,因此 ECMAScript 会不失时机地将浮点数值 转换为整数值。
显然,如果小数点后面没有跟任何数字,那么这个数值就可以作为整数值来保存。同样 地,如果浮点数值本身表示的就是一个整数(如 1.0),那么该值也会被转换为整数。
在默认情况下,ECMASctipt 会将那些小数点后面带有 6 个零以上的浮点数值转换为以 e 表示法 表示的数值(例如,0.0000003 会被转换成 3e-7)。
```js
var a = 0.1+0.2;        // 0.30000000000000004 IEEE754 数值的浮点计算的通病

```
浮点数值的最高精度是 17 位小数,但在进行算术计算时其精确度远远不如整数。

- 数值范围
```js
Number.MIN_VALUE        //5e-324
Number.MAX_VALUE        //1.7976931348623157e+308
```
如果某次计算的 结果得到了一个超出 JavaScript 数值范围的值,那么这个数值将被自动转换成特殊的 Infinity 值。
具体来说,如果这个数值是负数,则会被转换成-Infinity(负无穷),如果这个数值是正数,则会被转换成 Infinity(正无穷)。
要想确定一个数值是不是有穷的(换句话说,是不是位于最 小和最大的数值之间),可以使用`isFinite()`函数。


---
## 小结
- ECMAScript 中的基本数据类型包括 Undefined、Null、Boolean、Number 和 String。
- 与其他语言不同,ECMScript 没有为整数和浮点数值分别定义不同的数据类型,Number 类型可用于表示所有数值。
- ECMAScript 中也有一种复杂的数据类型,即 Object 类型,该类型是这门语言中所有对象的基础类型。
- 严格模式为这门语言中容易出错的地方施加了限制。
- ECMAScript 提供了很多与 C 及其他类 C 语言中相同的基本操作符,包括算术操作符、布尔操作符、关系操作符、相等操作符及赋值操作符等。
- ECMAScript 从其他语言中借鉴了很多流控制语句,例如 if 语句、for 语句和 switch 语句等。 ECMAScript 中的函数与其他语言中的函数有诸多不同之处。
- 无须指定函数的返回值,因为任何 ECMAScript 函数都可以在任何时候返回任何值。
- 未指定返回值的函数返回的是一个特殊的 undefined 值。
- ECMAScript 中也没有函数签名的概念,因为其函数参数是以一个包含零或多个值的数组的形式传递的。
- 可以向 ECMAScript 函数传递任意数量的参数,并且可以通过 arguments 对象来访问这些参数。
- 由于不存在函数签名的特性,ECMAScript 函数不能重载。


















