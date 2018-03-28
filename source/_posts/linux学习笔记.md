---
title: linux学习笔记
date: 2018-03-21 12:16:39
tags:
---
## linux文件
linux中所有一切都是文件。
linux文件类型：
* 普通文件
* 目录
* 设备文件
* 套接口文件
* 符号链接文件

## 设备
linux设备分类：
* 字符设备
* 块设备
* 网络设备

#### 字符设备：
指只能一个字节一个字节读写的设备，不能随机读取设备内存中的某一数据，读取数据需要按照先后数据。字符设备是面向流的设备。
常见的字符设备：鼠标、键盘、串口、控制台和LED设备等。

#### 块设备：
指可以从设备的任意位置读取一定长度数据的设备。
块设备包括：硬盘、磁盘、U盘和SD卡等。

#### 网络接口：
任何网络事务都通过一个接口来进行, 就是说, 一个能够与其他主机交换数据的设备。

## 进程
一个具有一定独立功能的程序关于某个数据集合的一次运行活动，是系统进行资源分配和调度运行的基本单位。

#### 进程VS程序：
* 进程是程序的一次执行过程，是动态概念；程序是一组有序的指令集和，是静态概念；
* 不同的进程可以执行同一个程序；

#### 进程的声明周期：
当操作系统要完成某个任务时，它会创建一个进程。当进程完成任务之后，系统就会撤销这个进程，收回它所占用的资源。从创建到撤销的时间段就是进程的生命期。

#### 进程的组成：
从结构上讲，每个进程都由程序、数据和一个进程控制块组成。

#### 进程控制块：
Process Control Block，PCB。在linux中task_struct结构体即是PCB。PCB是进程的唯一标识。
PCB包含信息：
* 进程状态（state）
* 进程标识信息（uid、gid）
* 定时器（time）
* 用户可见寄存器、控制状态寄存器、栈指针等

#### 线程：
有时被称为轻量级进程，是程序执行流的最小单元。一个标准的线程由线程ID，当前指令指针(PC），寄存器集合和堆栈组成。

*****
## 进程通信


*****
## 存储结构
数据的存储结构是指数据的逻辑结构在计算机中的表示。数据元素之间的关系有两种不同的表示方法：顺序映象和非顺序映象，并由此得到两种不同的存储结构：顺序存储结构和链式存储结构。
* 顺序存储结构：逻辑上相邻的结点存储在物理位置相邻的存储单元里；通常借助数组来实现；
* 链式存储结构：不要求逻辑上相邻的结点存储在物理位置相邻的存储单元里；通常借助指针来实现。

#### 链表
是一种物理存储单元上非连续、非顺序的存储结构。

****
## socket
#### 地址族
address family，地址划分的标准集合，表示底层是使用哪种通信协议来递交数据的。如AF——INET使用TCP/IPv4；AF——INET6使用TCP/IPv6；AF——LOCAL或者AF——UNIX值本地通信。
#### sin_family
协议族

*****
#### 一些系统调用
##### socket（）函数
用户根据指定的地址族、数据类型和协议来分配一个套接口的 描述字 及其 所用的资源。
```
int socket（int af，int type，int protocol）
```
**af：**目前仅支持AF——INET格式；
**type：**常用的有SOCK_STREAM(TCP)、SOCK_DGRAM(UDP)、SOCK_RAW、SOCK_PACKET、SOCK_SEQPACKET；
**protocol：**指定的协议,如调用者不想指定，可用0；

##### bind（）函数
bind()函数可以帮助你指定一个套接字使用的端口。
```
int bind(int socked, struct sockaddr *my_addr, int addrlen);
```
* **sockfd：**由socket（）函数返回的套接字描述符；
* **my_addr：**指向struct sockaddr的指针；
* **addrlen：**可以设置为sizeof（struct sockaddr）
*****
**sockaddr:**
sockaddr在头文件#include<sys/socket.h>中定义，sa_data把目标地址和端口信息混在一起了。
```
struct sockaddr {
    sa_family_t sin_family;
    char sa_data[14];
    };
```
sockaddr常用于bind、connect、recvfrom、sendto等函数的参数，指明地址信息，是一种通用的套接字地址。
*****
**sockaddr_in:**
sockaddr_in在头文件#include <neine/in.h>或#include<arpa/inet.h>中定义，该结构体解决了sockaddr的缺陷，把port和addr 分开储存在两个变量中。

```
struct sockaddr_in{
    sa_family_t     sin_family;
    uint16_t        sin_port;
    struct in_addr  sin_addr;
    char            sin_zero[8];
    }
```
sockaddr_in 是internet环境下套接字的地址形式。所以在网络编程中我们会对sockaddr_in结构体进行操作，使用sockaddr_in来建立所需的信息，最后使用类型转化就可以了。一般先把sockaddr_in变量赋值后，强制类型转换后传入用sockaddr做参数的函数：sockaddr_in用于socket定义和赋值；sockaddr用于函数参数。



