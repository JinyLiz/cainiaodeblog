---
title: Tornadoweb学习笔记
date: 2018-03-20 10:46:26
tags:
---

相关链接：
官方文档：[http://www.tornadoweb.cn/](http://www.tornadoweb.cn/)

*****
## Tornado框架设计模型
![Tornado框架设计模型](../img/Tornadokuangjia.png)
Tornado框架分为四层：
* 最底层的EVENT层：处理IO事件；
* TCP层实现TCP服务器，负责数据传输；
* HTTP/HTTPS层基于HTTP协议实现HTTP服务器和客户端；
* 最上层为WEB框架。

*****
## Tornado模块分类
#### 主要模块
* **tornado.web** - FriendFeed 使用的基础 Web 框架，包含了 Tornado 的大多数重要的功能；
* **tornado.escape** -XHTML, JSON, URL 的编码/解码方法；
* **tornado.options** -命令行和配置文件解析工具，针对服务器环境做了优化
*****
#### 底层模块
* **tornado.httpserver** -服务于web模块的一个非常简单的HTTP服务器的实现；
* **tornado.ioloop** - 核心的I/O循环

*****
## tornado.web
#### Application()



*****
## tornado.options
#### parse_comand_line()
解析命令行函数。
#### define()

*****
## tornado.ioloop

#### epoll
**设备驱动：**操作系统和输入输出设备间的粘合剂。驱动负责将操作系统的请求传输，转化为特定物理设备控制器能够理解的命令。
**I/O多路复用：**监视多个描述符，一旦某个描述符就绪（一般是读就绪或者写就绪），能够通知程序进行相应的读写操作。
##### poll机制
为了减少CPU资源的占用率，在编写驱动函数中添加poll机制。poll（）是linux中的字符设备驱动中的一个函数，作用是把当前的文件指针挂到等待队列。

**poll执行过程：**
1、将用户传入的pollfd数组拷贝到内核空间；
2、查询每个文件描述符对应设备的状态，如果该设备尚未就绪，则在该设备的等待队列中加入一项并继续查询下一设备的状态。查询完所有设备后如果没有一个设备就绪，这时则需要挂起当前进程等待，直到设备就绪或者超时，挂起操作是通过调用schedule_timeout执行的。设备就绪后进程被通知继续运行，这时再次遍历所有设备，以查找就绪设备；
3、将获得的数据传送到用户空间并执行释放内存和剥离等待队列等善后工作。

**epoll：**
是linux内核为处理大批量文件描述符而改进的poll，能显著提高程序在大量并发连接中只有少量活跃的情况下的系统CPU利用率。





