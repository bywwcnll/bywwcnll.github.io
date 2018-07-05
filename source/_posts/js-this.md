---
title: js-this
date: 2018-03-07 16:47:49
categories:
tags:
- js
---

# this关键字作用域详解

> this是一个总指向调用者的指针。以下是this指向的不同情况：

- 作为对象方法调用，this是对象-
- 作为函数调用(包括立即执行函数)，this是window
- 作为内部函数，即声明在函数中的函数，this是window
- 作为构造函数调用，即用new，this指向新生成的对象

`node.js中没有window对象，这种情况都指向null。`