title: Spring基础认识
author: Machinezht
tags:
  - spring
  - ioc
  - DI
categories:
  - 计算机
date: 2018-03-31 21:43:00
---
Spring框架是一个开源的轻量级企业应用开发框架。大致可以分为七个模块。

![七大模块](/assets/blog_img/180331-3.gif)
> [七大模块作用及简介](https://blog.csdn.net/xlgen157387/article/details/45290799)

<!-- more -->

### **依赖注入(DI)与控制反转(IOC)**

简明扼要的说的话就是ioc通过DI这种技术来实现。

其中依赖注入有以下实现方式：

* 基于接口。实现特定接口以供外部容器注入所依赖类型的对象。
* 基于 set 方法。实现特定属性的public set方法，来让外部容器调用传入所依赖类型的对象。
* 基于构造函数（构造器）。实现特定参数的构造函数，在新建对象时传入所依赖类型的对象。
* 基于注解（@Autowired）

具体关系也不是很明白，大概也就是这个样子

- 下面先给出不采用依赖注入的
```
public class 大哥{
    pubic void method(){
        小弟 x=....;（一般是用new,可能是new hh，mm，ll，说不好）;
        x.打架();
    }
}
```
首先大哥是要依赖于小弟的，否则什么都不是，要使用小弟，必须要获得小弟的实例引用。这本不是问题，但一旦要修改就需要单位到这个代码，整体的代码完整性就要受到影响，所以就出来了依赖注入。

- 依赖注入的基于set方法和基于构造器的实现

```
public class 大哥{
    private 小弟 x;
    pubic void method(){
        //小弟 x=....;（一般是用new,可能是new hh，mm，ll，说不好，反正创建实例）;
        x.打架();
    }
    //基于set
    public void setx（小弟 x）｛
    this.小弟=小弟;
    }
    //基于构造器
    public 大哥(小弟 x){
    this.小弟=小弟;
    }
}
```
新增setter方法，在spring中，这个方法会被spring框架调用，以注入一个小弟的实例。好处是什么呢？原来要new的，现在呢，可以在xml配置里面添加注入对象，降低耦合性。
所以，讲真，依赖注入真的没什么，就是种简单的设计模式而已。

总结来看

*所谓的依赖注入，则是，甲方开放接口，在它需要的时候，能够讲乙方传递进来(注入)
所谓的控制反转，甲乙双方不相互依赖，交易活动的进行不依赖于甲乙任何一方，整个活动的进行由第三方负责管理（这个第三方在这里就是spring容器）。*

- 上面是便于理解，下面来真实的实现代码

1. 首先spring是通过beans来管理对象的，首先这是个xml文件。看个helloworld的例子

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

    <bean id="helloBean" class="com.shiyanlou.demo.helloworld.HelloWorld">
        <property name="name" value="shiyanlou" />
    </bean>

</beans>
```
这里就创建了一个类的bean对象了（sprin实际上用的是反射实现），下面是property意味着这是个setter注入，如果是constructor-arg就是构造器注入。到这里实际上已经基本实现依赖注入，接着要去用

```
        ApplicationContext context =
                new ClassPathXmlApplicationContext(new String[] {"xx.xml"});
```
这样就实现了调用，还是很简洁美观的。
再次总结，依赖注入是手段，控制反转是思想，把对象创建权交给spring容器管理。
