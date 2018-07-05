---
title: docker_attention
date: 2018-03-08 19:02:52
categories: docker
tags:
- windows
---
# windows下使用docker的注意事项

- win路径的挂载问题
```bash
# 示例代码
> docker run -it --name ng --rm -p 80:80 -v /c/Users/xxx/Desktop/nginx/config:/etc/nginx nginx
```

- A required privilege is not held by this client
> 使用带管理员权限的命令行工具
```bash
> docker cp -a ng:/etc/nginx ./config
```
