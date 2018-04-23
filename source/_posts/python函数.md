---
title: python函数
date: 2018-03-20 11:48:34
tags: 
  - 开发
  - 后端
  - python
---

相关链接：
python3中文手册：[http://docs.pythontab.com/python/python3.4/](http://docs.pythontab.com/python/python3.4/)


## 缺省参数
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

## 不定长参数
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

## 参数self
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

## 构造函数
\__init\__()为类的构造函数或初始化方法。

## 装饰器@
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
*****
#### open()
open()函数用于打开一个文件，创建一个file对象。
函数语法：
```
open(name[,mode[,buffering]])
```
参数说明：
* name : 包含了你要访问的文件名称的字符串值。
* mode : mode 决定了打开文件的模式：只读，写入，追加等。这个参数是非强制的，默认文件访问模式为只读(r)。
* buffering : 如果 buffering 的值被设为 0，就不会有寄存。如果 buffering 的值取 1，访问文件时会寄存行。如果将 buffering 的值设为大于 1 的整数，表明了这就是的寄存区的缓冲大小。如果取负值，寄存区的缓冲大小则为系统默认。




