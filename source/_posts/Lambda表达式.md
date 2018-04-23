title: Lambda表达式简介-基于Java与Python平台
author: Machinezht
date: 2018-04-18 14:08:57
tags:
---
Lambda表达式的主要用途就是创建匿名函数,主要是针对只使用一次的函数创建。

**JAVA**

举个栗子：打印"6666“
```
 匿名内部类写法
new Thread(new Runnable(){// 接口名
    @Override
    public void run(){// 方法名
        System.out.println("666");
    }
}).start();
```
<!-- more -->
本身代码没有任何问题，相当完美，但程序员哪就是懒，讨厌输这么多
```
// JDK8 Lambda表达式写法
new Thread(
        () -> System.out.println("666")// 省略接口名和方法名
).start();
```
其实只是简单介绍一下，在java的lambda表达式中，主要可以靠IDEA的缩进选项自动选择，没必要额外记录。

**PYTHON**

输出0,1,4,9。。。。
```
def sq(x):
    return x * x
hh=map(sq, [y for y in range(10)])
print(list(hh))
```
采用lambda表达式

```
a=map( lambda x: x*x, [y for y in range(10)] )
print(list(a))
```
在python中lambda表达式其实才算正统，java语言本身就够复杂了，简洁一点反而不利于阅读维护，采用lambda表达式反而缺失了部分规范性，而python这种胶水语言，小巧简便适合去解决某些微型应用，采用lambda表达式相信体验会不错。