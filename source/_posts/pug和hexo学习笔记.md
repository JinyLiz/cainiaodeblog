---
title: pug和hexo学习笔记
date: 2018-03-29 10:31:02
tags:
    - 开发
    - 前端
---

## pug学习
#### pug编译
输入
```
pug filename.pug
```
生成html文件；
若输入
```
pug -P -w filename.pug 
```
可以监听并自动更新。

#### 分支条件
```
- var friends=0
    case friends
        when 10
         p 您没有朋友
        default
         p 您有#{friends}个朋友
```
渲染结果：
您有10个朋友

#### Mixin混入
混入是一种允许在 Pug 中重复使用一整个代码块的方法。
```
mixin list
 ul
   li foo
+list
+list
```
渲染结果：
* foo
* foo

## hexo学习
**hexo官方网址：**[https://hexo.io/docs/](https://hexo.io/docs/)
*****
**hexo本地测试注意点：**
修改hexo根目录下的_config.yml站点配置目录后，要重新启动hexo再刷新，修改theme主题目录下的_config.yml主题配置目录则只需刷新即可。


