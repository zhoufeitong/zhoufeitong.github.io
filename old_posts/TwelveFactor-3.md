---
title: Twelve Factor Part III
date: "2019-04-23"
summary: "Port binding; Concurrency; Disposability" 
---
Twelve Factor Part Three  
Port binding  
Concurrency  
Disposability  

## 七、端口号绑定  
通过绑定端口号导出服务  

应用程序应当是自包含(self-contained)的，并且它不应当依赖运行时服务器的注入。web app通过将HTTP绑定到一个端口号上来将其导出作为服务。  

在本地的开发环境，开发者通过像`http://localhost:5000/`这样的URL访问自己开发的服务。在部署环境中，则通过公共域名和端口访问。  

通常这通过使用依赖声明将一个web服务器库添加到app中完成，例如Python的Tornado，Java的Jetty。  

注意绑定端口的服务意味着它也可以成为其他app的`backing service`。  

## 八、并发  
通过进程模型达成横向扩展  

任何计算机程序都表示为一个或多个计算机程序。Web应用使用了许多不同类型的进程执行形式，例如PHP进程作为Apache的子进程存在，Java由JVM提供一个维护大块系统资源的进程，而并发就由线程内在的管理。不管哪种形式，运行着的进程对于app的开发者来说都只具有最小的可见性。  

在twelve-factor app中，进程是一等公民。twelve-factor中的进程从运行守护服务的UNIX进程模型获得强烈的启发。在这种模型下，开发者可通过将每种类型的工作分发一个进程类型来架构自己的app以使它们能处理形色各异的工作负载。  

twelve-factor app无共享、水平可分的特性意味着增强并发是一个简单可信任的操作。进程类型和每种类型的进程数量组成的矩阵则是进程信息。  

twelve-factor app不能被配置为守护进程也不能写PID文件，而应当依赖操作系统的进程管理器来管理输出流，对崩溃进程作出反应或是处理用户的重启和关闭  

## 九、可弃性(Disposability)
通过快速启动和优雅的关闭来最大化鲁棒性  

`disposability`意味着app可以被一瞬间开启或关闭。这对于伸缩性、代码或配置改变时的快速部署以及生产环境部署的鲁棒性都很重要。  

进程应当尽量最小化启动时间，最好只需几秒钟。短暂的启动时间意味着更灵活，更鲁棒(进程管理器可以更快的把进程移动到新的物理机上)  

当进程从进程管理器处收到`SIGTERM`信号时应当优雅的关闭。对于web进程来说，这意味着停止监听端口，让当前的请求结束然后退出。  

对于工作进程来说，这意味着把当前的工作返回到工作队列中。  

进程应当对由底层硬件导致的突然死亡也鲁棒。一个建议的方法是使用鲁棒的后端队列，例如Beanstalked  
