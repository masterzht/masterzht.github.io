title: web开发中的mode1和mode2
author: Machinezht
tags:
  - Java web
  - mode1与mode2
categories:
  - 计算机
date: 2018-04-02 09:20:00
---
### **Mode1**
mode1指的是将显示层，数据层，控制层交给jsp+javabean处理。jsp负责显示（v层）与逻辑处理（c层），javabean负责业务层(讲真，这种模式在项目中是禁止使用的，个人觉得就是是小型项目也别用了吧)
![](\assets\blog_img\180402-1.png)
[给一个jsp+javabean登陆的案例: ](https://github.com/masterzht/Study-Notes/tree/master/Java/web%E5%BC%80%E5%8F%91%E4%B8%AD%E7%9A%84mode1%E4%B8%8Emode2/mode1/%E7%99%BB%E9%99%86-jsp%2Bjdbc)

### **Mode2**

mode2
mode2指的是给予MVC模型的，jsp专注显示层，servlet专注控制层，javabean专注模型层（往三次架构模式上面看，模型层其实是业务逻辑层的一部分，javabean还不够强大，可能要在他的基础上嵌套一点业务逻辑）。在这种模式中，最关键的部分就是使用RequestDispatcher接口，servlet就是通过这个接口把也业务层内容保存到jsp上面显示的。
![](\assets\blog_img\180402-2.png)
这种图应该算是mode2的雏形，不过有个缺陷，就是model层的数据都是封装进jsp模型页面的，而目前主流的技术应该是前端完成渲染工作，就是请求html页面，html页面里面用jsp脚本再次请求服务器的零碎数据，具体有什么优势，我也不怎么清楚，不过耦合度应该会有所降低吧。

在github上传了mode2的两个案例，第一个是采用典型的mode2模式，不过mvc的c层和业务逻辑层在一起了，项目复杂增加时候会导致不少问题，所以第二个对其进行了改进，用来一个DispatcherServlet专门来做控制层，管理请求，建立了一个controller包，专门作为业务逻辑层，实现解耦。（参考了Servlet、Jsp和Spring MVC初学指南）

源码地址： [mode2](https://github.com/masterzht/Study-Notes/tree/master/Java/web%E5%BC%80%E5%8F%91%E4%B8%AD%E7%9A%84mode1%E4%B8%8Emode2/mode2)

注：写的有点乱，继续学习，以后再看看