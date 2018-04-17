title: 关于Docker镜像的使用
author: Machinezht
date: 2018-04-10 19:16:50
tags:
---
有挺长时间没有更新博客了，下次改改。。
docker核心是容器，它的作用就是虚拟化一个容器，这个容器可能是系统，可能是web服务器等等，通过pull、run之后容器保持运行状态，这样我们就可以在容器跑应用了。

![upload successful](\assets\online_img\docker架构.png)
<!--more-->

### **基本使用**

弄清楚几个概念：
* 镜像：docker images(这里显示的镜像基本只有两个途径，一个是你自己在官方仓库pull的，一个是你修改仓库再commit提交的,相当于ghost镜像）

> fav开头的是自己commit的，docker.io开头的明显是官方镜像

![upload successful](\assets\online_img\image.png)
* 容器：docker ps -a（这里的容器包括运行与未运行的）

![upload successful](\assets\online_img\docker容器.png)
docker有个-d的指令，是在后台以进程形式运行command。但要强调一点，并不是有-d，用docker ps就能显示它是运行状态的了，因为只要后台跑完这个command就不会存在与运行状态

docker logs container-id:显示这个容器中运行的log，相关输出。

```
docker run ubuntu:15.10 /bin/echo "Hello world"
```
这段代码实际上分为三步：
1. docker pull ubuntu:15.10   (这步是下载镜像)
2. docker run -i -t  ubuntu:15.10 /bin/bash  (打开ubuntu镜像，打开内部终端，并与外部输入交互)
3. echo "hello world" 

这个容器不同于服务，如果用docker运行mysql这类的服务的时候，docker容器是属于保持打开状态的，也就是用docker ps命令会显示容器id，而这个helloworld则属于片段性的，跑完就关闭。