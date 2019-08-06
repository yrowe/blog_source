---
title: jvm server client模式
date: 2019-08-04 13:28:20
tags:
---

### 概述

JVM有两种运行模式Server与Client。两种模式的区别在于，Client模式启动速度较快，Server模式启动较慢；但是启动进入稳定期长期运行之后Server模式的程序运行速度比Client要快很多。这是因为Server模式启动的JVM采用的是重量级的虚拟机，对程序采用了更多的优化；而Client模式启动的JVM采用的是轻量级的虚拟机。所以Server启动慢，但稳定后速度比Client远远要快。

### 1. 当前是Client or Server？

使用[Java](http://lib.csdn.net/base/java) -version命令就能显示出当前虚拟机处于哪种模式。 
**Client：** 
如下图所示，可以看到HotSpot虚拟机采用Client模式启动的。 

**Server：** 
如下图所示，可以看到HotSpot虚拟机采用Server模式启动的。另外我们也能看到该虚拟机是64位的。如果像上面的Client图中那样不显示位数，则是32位虚拟机。所以使用java -version也能查看虚拟机是32位还是64位。 

**在部分JDK1.6版本和后续的JDK版本(64位系统)中，-client参数已经不起作用了，Server模式成为唯一**
![images](https://static.oschina.net/uploads/space/2018/0124/150223_Ga9j_2621611.png)