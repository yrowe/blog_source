---
title: java一些基本语法
date: 2019-08-03 13:19:17
tags:
---

# 初始化数组

```java
int[] nums = new int[]{2,7,11,15};
```



# HashMap一些用法

- K,V 需要是包装类， new后面的尖括号里 具体类可以省略。
- put, get分别为向容器中放值和取值.
- containsKeys则判断容器中是否有对应的key



```java
Map<Integer, Integer> map = new HashMap<>();

map.put(1, 2);
map.containsKey(1);
map.get(1);
```

# List一些用法

```java
//声明list
List<Integer> l = new ArrayList();

//两种初始化赋值的方式

ArrayList<String> lists1 = new ArrayList<String>();
lists1.add("test1");
lists1.add("test2");

//Method 2 , (double brace initialization)
ArrayList<String> lists2 = new ArrayList<String>(){{
    add("test1");
    add("test2");


```

# Java 数组Swap和Reverse实现
```java
private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    
private void reverse(int[] nums, int st) {
    int i = st, j = nums.length - 1;
    while (i < j) {
    swap(nums, i, j);
        i++;
        j--;
    }
}
```





# java二维数组初始化及获取长宽



### 初始化

1.在定义时初始化。

```java
double[][] a = new double[][] {{1,2,3},{4,2,7}};
double[][] b = new double[][] {{3,3},{1,1},{2,2}};
```
如图，a 中的 {1,2,3} 即为第一行，{4,2,7}为第二行。

2.先定空间，随后赋值。

```java
double [][] container = new double[3][4];
for(int i = 0; i < 3;i++) {
	for(int j = 0; j < 4;j++) {
		container[i][j] = 4.5;
	}
}
```

### 获取长款

```java
//获取行数---3行
int lenY = a.length;
//获取列数---4列
int lenX = a[0].length;
```

