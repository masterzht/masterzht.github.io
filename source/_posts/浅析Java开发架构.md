title: 浅析Java开发架构
author: Machinezht
tags:
  - java
  - 架构模式
  - MVC
categories:
  - 计算机
date: 2018-04-26 10:29:00
---
目前了解的有三层架构模式，MVC模式，这里会详解这两种开发模式。

比较古老的是三层架构模式，这属于抽象宏观层面的，给了我们一个开发的思路。

三层架构模式把整个业务应用划分为：界面层（User Interface layer）、业务逻辑层（Business Logic Layer）、数据访问层（Data access layer）。

![upload successful](\assets\online_img\架构.png)
对应的包名分别为ui、service、dao。

三次架构模式对应到生活当中就是服务员、厨师、采购员。
![upload successful](\assets\online_img\三层架构模式.png)

这属于宏观的解决方案，而MVC模式属于微观解决方案，现实中程序员接触到的还是MVC模式。
<!-- more -->

MVC模式的model层实际上包括三次架构模式的业务逻辑与数据访问层，而controller则是管理分配model层。这样说可能不怎么好理解，继续对应到生活当中就是服务员，总店派送员，总店的厨师加上采购员。

包名示范（注：其中package ui是强行加入的，现实中交由前端html解决）

![upload successful](\assets\online_img\image1.png)

养成自己的一套编程规范也是格外重要的，我把所有的接口前面加个I，接口实现去掉I加上Impl，符合一下驼峰原则。

最后就是阿里有自己的编码规范，可以下载一下这个插件，idea搜索ali。。。