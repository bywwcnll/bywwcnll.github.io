---
title: vue-watch
date: 2018-07-17 18:36:35
categories:
tags:
- js
- vue
- watch
---
# VUE中watch的使用注意事项

## 组件嵌套
> 当使用组件嵌套时，子组件中存在对需要发请求获取的父组件属性监视时，需要同时在子组件的created和watch中操作，原因如下：
1. 父子组件的生命周期是：`父组件`在created和mounted完成后，执行`子组件`的created和mounted
2. 父组件的发送请求是异步的，当请求过快的时候，子组件的监视对象的watch就无法执行，当请求慢的时候能执行监视操作，所以需同时在子组件的created和watch中都加入操作代码