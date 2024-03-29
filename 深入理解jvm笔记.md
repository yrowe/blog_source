---
title: 深入理解jvm笔记
date: 2019-08-03 15:38:26
tags:
---

## JVM学习大纲

- JVM介绍
- HotSpot虚拟机讲解
- 垃圾收集方式详解
- 垃圾收集算法详解
- 垃圾收集器详解
- 分代垃圾收集机制详解
- 新生代讲解
- 老年代讲解
- G1收集器分析与实例
- 常见且重要虚拟机参数示例
- 栈
- 方法区
- 线程共享内存区
- 根搜索算法
- Serial收集器
- ParNew收集器
- 类加载机制详解
- 类加载的双亲委托机制
- 字节码文件生成与分析
- 魔数
- 常量池与方法表
- 各种指令详解
- 锁详解
- 线程安全
- 偏向锁、自旋锁与轻量级锁
- JIT编译器
- GC日志生成与分析
- 虚拟机监控工具详解
- jConsole使用方式详解
- 何为逃逸与逃逸分析
- 方法内联
- 虚拟机内存模型详解



## 类加载器深入解析与阶段分解

### 类加载

- 在java代码中， 类型的加载、连接与初始化过程都是在程序运行期间完成的
- 提供了更大的灵活性， 增加了更多的可能性。

### 类加载器深入剖析

- Java虚拟机与程序的生命周期
- 在如下几种情况下， Java虚拟机将结束生命周期
  - 执行了System.exit()方法
  - 程序正常执行结束
  - 程序在执行过程中遇到了异常或错误而异常终止
  - 由于操作系统出现错误而导致Java虚拟机进程终止

### 类的加载、连接与初始化

- 加载: 查找并加载类的二进制数据
- 连接：
  - 验证： 确保被加载的类的正确性
  - 准备： 为类的<font color=red>静态变量</font>分配内存， 并将其初始化为<font color=red>默认值</font>
  - 解析：<font color=red>把类中的符号引用转换为直接引用</font>
- <font color=red>初始化： 为类的静态变量赋予正确的初始值</font>

### 类的使用与卸载

- 使用
- 卸载





## 类的加载连接与初始化过程详解

