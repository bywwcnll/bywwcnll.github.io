---
title: instanceof
date: 2018-07-05 11:40:12
categories: javascript
tags: 
- js
- prototype
- instanceof
---
# javascript instanceof 详解

## instanceof运算符逻辑示例

```js
function instance_of(L, R) {//L 表示左表达式，R 表示右表达式
 var O = R.prototype;// 取 R 的显示原型
 L = L.__proto__;// 取 L 的隐式原型
 while (true) {
   if (L === null)
     return false;
   if (O === L)// 这里重点：当 O 严格等于 L 时，返回 true
     return true;
   L = L.__proto__;
 }
}
```

---

## Function与Object的关系

```js
console.log(Function instanceof Object) //true
console.log(Object instanceof Function) //true
```

> 先了解js中以下几点定义

1. 所有 JavaScript 对象都有`__proto__`属性
2. 只有 `Object.prototype.__proto__` 为`null`

### Function-Object验证流程

Function的`__proto__`指向Function的Function.prototype，然后Function.prototype的`__proto__`指向Object.prototype，最后Object.prototype的`__proto__` 为`null`

### Object-Function验证流程

Object的`__proto__`指向Function的Function.prototype