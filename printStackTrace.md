---
title: printStackTrace
date: 2019-08-05 11:07:04
tags:java
---

```java
catch(Exception e){
    e.printStackTrace() ;
}

```


当try语句中出现异常是时，会执行catch中的语句，java运行时系统会自动将catch括号中的Exception e 初始化，也就是实例化Exception类型的对象。e是此对象引用名称。然后e（引用）会自动调用Exception类中指定的方法，也就出现了e.printStackTrace() ;

printStackTrace()方法的意思是：在命令行打印异常信息在程序中出错的位置及原因。