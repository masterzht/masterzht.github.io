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

本身代码没有任何问题，相当完美，但程序员哪就是懒，讨厌输这么多
```
// JDK8 Lambda表达式写法
new Thread(
        () -> System.out.println("666")// 省略接口名和方法名
).start();
```
其实只是简单介绍一下，在java的lambda表达式中，主要可以靠IDEA的缩进选项自动选择，没必要额外记录。
<!-- more -->
**Android**

最常用的click语句
```
textView.setOnClickListener(new View.OnClickListener(){
    @Override
    public void onClick(View v) {
        Toast.makeText(getApplicationContext(), "hello Lambda", Toast.LENGTH_LONG).show();
    }
});
```
采用lambda表达式

```
textView.setOnClickListener( v -> Toast.makeText(getApplicationContext(), "hello Lambda", Toast.LENGTH_LONG).show());
```
一个字，强，然而。。。
kotlin貌似崛起了，还成为了google指定的Android开发语言，比lambda强，那么要弃lambda转kotlin吗？

虽说kotlin真的有替代Java的势头，这确实是大势所趋。但目前的编程语言应该也过于饱化了，更多语言的诞生目的多是为了简化程序员的工作，使编程变得更加简单方便。然而过于先进的语法会使人减少对语句的思考，使程序员流于表面而不能透其内核。




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