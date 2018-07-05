---
title: webpack代码分割注意事项
date: 2018-06-21 10:26:42
categories:
tags:
- webpack
---
# 打包时使用chunkhash进行代码分割
这会导致在修改部分代码后，上一层的文件引用没有使用较新的文件，只能强行清空缓存，但是这在企业微信PC端上就不好操作了。为此，将webpack配置文件webpack.prod.conf.js中的out对象配置成以下形式：
```js
output: {
    path: config.build.assetsRoot,
    filename: utils.assetsPath('js/[name].[hash].js'),
    chunkFilename: utils.assetsPath('js/[id].[hash].js')
}
```