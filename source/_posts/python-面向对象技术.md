---
title: python 面向对象技术
date: 2018-03-29 12:22:14
tags:
    - 开发
    - 后端
    - python
---
python是一门面向对象的语言，在python中一切都是对象。&lt;type'object'&gt;和&lt;type'type'&gt;是python两个最基本的对象，是所有对象的起源。

<!--more--> 

**python对象有三个基本要素：**
* 身份：对象的唯一性身份标志，是该对象的内存地址；
* 类型：对象的类型决定了该对象可以保存什么类型的值，可进行什么样的操作；
* 值：对象代表的数据

**&lt;type'object'&gt;和&lt;type'type'&gt;：**
```
print (object)
print(type(object))
print(object.__class__)
print(object.__bases__)

print()

print(type)
print(type(type))
print(type.__class__)
print(type.__bases__)
```
输出值：
&lt;class 'object'&gt;
&lt;class 'type'&gt;
&lt;class 'type'&gt;
()

&lt;class 'type'&gt;
&lt;class 'type'&gt;
&lt;class 'type'&gt;
(&lt;class 'object'&gt;,)

*****
说明:
* &lt;type'object'&gt;的类型是&lt;type'type'&gt;
* &lt;type'type'&gt;的类型是它本身；
* &lt;type'object'&gt;没有父类；
* &lt;type'type'&gt;的父类是&lt;type'object'&gt;



## 类和实例
类是抽象的模板，实例是根据类创建出来的一个具体的对象。各个实例拥有的数据都互相独立，互不影响。
*****
**举例：**
*****
类Student：
```
class Student（object）：
  pass
```
实例bart：
```
bart=Student（）
```
给实例变量绑定属性：
```
bart.name='Bart Simpson'
```
*****
## 方法
方法是与实例绑定的函数，和普通函数不同，方法可以直接访问实例的数据。


## 类的继承
实现代码重用的方法之一是通过继承机制。
**继承语法：** class 派生类名（基类名）：

在python中继承的特点：
* 在继承中基类的构造（__init__()方法）不会被自动调用，它需要在其派生类的构造中亲自专门调用；
* 在调用基类的方法时，需要加上基类的类名前缀，且需要带上self参数变量。区别在于类中调用普通函数时并不需要带上self参数；
* Python总是首先查找对应类型的方法，如果它不能在派生类中找到对应的方法，它才开始到基类中逐个查找。（先在本类中查找调用的方法，找不到才去基类中找）；
* 如果在继承元组中列了一个以上的类，那么它就被称作"多重继承" 。

#### 多重继承


