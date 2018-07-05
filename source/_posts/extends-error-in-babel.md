---
title: extends-error-in-babel
date: 2018-07-04 19:00:39
categories:
tags: babel
---

## 创建RequestError
```js
class RequestError extends Error {
  constructor (message) {
    super()
    Object.defineProperty(this, 'message', {
      configurable: true,
      enumerable: false,
      value: message !== undefined ? String(message) : ''
    })
    Object.defineProperty(this, 'name', {
      configurable: true,
      enumerable: false,
      value: this.constructor.name
    })
    if (typeof Error.captureStackTrace === 'function') {
      Error.captureStackTrace(this, this.constructor)
    }
  }
}
module.exports = RequestError

```

##webpack配置
```js
//webpackConfig.module.rules
var test = {
  test: /\.js$/,
  loader: 'babel-loader',
  include: [resolve('src'), resolve('test'), resolve('node_modules/webpack-dev-server/client')],
  exclude: [resolve('src/utils/RequestError')]
}
```