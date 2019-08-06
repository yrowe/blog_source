---
title: super关键字
date: 2019-08-05 17:11:37
tags:java
---

# super关键词

- 访问父类的构造函数： 可以使用super()函数访问父亲的构造函数， 从而委托父类完成一些初始化的工作
- 访问父类的成员： 如果子类重写了父类的某个方法， 可以通过使用super关键字来引用父类的方法实现

```java
public class SuperExample {
    protected int x;
    protected int y;

    public SuperExample(int x, int y){
        this.x = x;
        this.y = y;
    }

    public void func(){
        System.out.println(this.x);
        System.out.println(y);
        System.out.println("SuperExample.func()");

    }
}


public class SuperExtendExample extends SuperExample {
    private int z;

    public SuperExtendExample(int x, int y, int z){
        super(x, y);
        this.z = z;
    }

    @Override
    public void func(){
        super.func();
        System.out.println(z);
        System.out.println("SuperExtendExample.func()");
    }
}


public class SuperTest {
    public static void main(String[] args) {
        SuperExtendExample s = new SuperExtendExample(1,2,3);
        s.func();
    }
}
```



```
1
2
SuperExample.func()
3
SuperExtendExample.func()
```

