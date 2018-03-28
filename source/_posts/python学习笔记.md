---
title: python学习笔记
date: 2018-03-20 11:48:34
tags: 
  - 开发
categories:
  - cate开发
---

相关链接：
python3中文手册：[http://docs.pythontab.com/python/python3.4/](http://docs.pythontab.com/python/python3.4/)

## 面向对象编程
#### 类和实例
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
#### 方法
方法是与实例绑定的函数，和普通函数不同，方法可以直接访问实例的数据。


#### 类的继承
实现代码重用的方法之一是通过继承机制。
**继承语法：** class 派生类名（基类名）：

在python中继承的特点：
* 在继承中基类的构造（__init__()方法）不会被自动调用，它需要在其派生类的构造中亲自专门调用；
* 在调用基类的方法时，需要加上基类的类名前缀，且需要带上self参数变量。区别在于类中调用普通函数时并不需要带上self参数；
* Python总是首先查找对应类型的方法，如果它不能在派生类中找到对应的方法，它才开始到基类中逐个查找。（先在本类中查找调用的方法，找不到才去基类中找）；
* 如果在继承元组中列了一个以上的类，那么它就被称作"多重继承" 。




## 函数
#### 缺省参数
调用函数时，缺省参数的值如果没有传入，则被认为是默认值。
举例：
```
def printme(a="aa"):
    print (a);
    return;

printme();

```
输出值为：
aa

#### 不定长参数
你可能需要一个函数能处理比当初声明时更多的参数。这些参数叫做不定长参数，不定长参数声明时不会命名。
*args 可变的positional arguments列表；**kwargs可变的keyword arguments列表。
举例：
```
def printme(*args, **kwargs):
    for var in args:
        print (var)
    for k,v in kwargs.items():
        print(kwargs)
    return
    
printme(1,2,3,a1=4)
```
输出值为：
1
2
3
{'a1': 4}

#### 参数self
self代表类的实例。
```
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
t=Test()
t.prt()
```
输出值：
<__main__.Test object at 0x1814cec9b0>
&lt; class '__main__.Test'>

#### 构造函数
\__init\__()为类的构造函数或初始化方法。

#### 装饰器@
一个装饰器就是一个语法糖。

```
def dec(f):
    print("call for "+f.__name__+"()...")
    return f

@dec
def factorial():
    return ("aa")


print (factorial())
```
输出值：
call for factorial()...
aa

## python内置函数
#### classmethod修饰符
classmethod修饰符可以来调用类的属性，类的方法，实例化对象等，对应的函数不需要实例化，不需要self参数，但第一个参数需要是表示自身类的 cls 参数。
self一般是在实例方法中使用，而cls则一般在类方法中使用，在静态方法中则不需要使用一个默认参数。
```
class A():
    bar=1
    def func1():
        print("foo")
    @classmethod
    def func2(cls):
        print("funct2")
        print(cls.bar)
        
A.func2()
```
输出值：
funct2
1


