---
title: java反射与泛型
date: 2019-08-04 15:10:12
tags:
---

# 反射1-Class类

- JVM为每个加载的class创建对应的Class实例来保存class的所有信息
- 获取一个class对应的Class实例后， 就可以获取该class的所有信息
- 通过Class实例获取class信息的方法称为反射（Reflection）
- JVM总是动态加载class， 可以在运行期根据条件控制加载class



# 反射2-访问字段

- Field对象封装了字段的所有信息

- 通过Class实例的方法可以获取Field实例:

    getField/getFields/getDeclaredField/getDeclaredFields

- 通过Field实例可以获取字段信息：

  getName/getType/getModifiers

- 通过Field实例可以读取或设置某个对象的字段：

  get(Object instance)/set(Object instance, Object fieldValue)

- 通过设置setAccessible(true)来访问非public字段

# 反射3-调用方法

- Method对象封装了方法的所有信息

- 通过Class实例的方法可以获取Method实例:

  getMethod/getMethods/getDeclaredMethod/getDeclaredMethods

- 通过Method实例可以获取方法信息：

  getName/getReturnType/getParameterTypes/getModifiers

- 通过Method实例可以调用某个对象的方法：

  Object invoke(Object instance, Object .. parameters)

- 通过设置setAccessible(true)来访问非public方法

# 反射4-调用构造方法

- Constructor对象封装了构造方法的所有信息

- 通过Class实例的方法可以获取Constructor实例：

  getConstructor/getConstructors/getDeclaredConstructor/getDeclaredConstructors

- 通过Constructor实例可以创建一个实例对象:

  newInstance(Object... parameters)

- 通过设置setAccessible(true)来访问非public构造方法

# 反射5-获取继承关系

- 通过Class对象可以获取继承关系：
  - getSuperclass()
  - getInterfaces()
- 通过Class对象的isAssignableFrom()方法可以判断一个向上转型是否正确



# 注解1- 使用注解

- 注解(Annotation)是Java语言用于工具处理的标注
- 注解可以配置参数， 没有指定配置的参数使用默认值
- 如果参数名称是value， 可以省略名称

# 注解2- 定义注解

- 使用@interface定义注解
- 可定义多个参数和默认值， 核心参数使用value名称
- 必须设置@Target来指定Annotation可以应用的范围
- 应当设置@Retention为RUNTIME便于运行期读取该Annotation

# 注解3 - 处理注解

- 可以在运行期通过反射读取RUMTIME类型的注解

  <font color=red>不要漏写@Retention(RetentionPolicy.RUNTIME)</font>

- 可以通过工具处理注解来实现相应的功能：

  - 对JavaBean的属性值按规则进行检查
  - JUnit会自动运行@Test注解的测试方法



# 泛型1 - 什么是泛型

- 泛型就是编写模板代码来适应任意类型
- 不必对类型进行强制转换
- 编译器将对类型进行检查
- 注意泛型的继承关系:
  - 可以把ArrayList<Integer>向上转型为List<Integer>(<font color=red>T不能变!</font>)
  - <font color=red>不能</font>把ArrayList<Integer>向上转型为ArrayList<Number>

# 泛型2-使用泛型

- 使用泛型时， 把泛型类型<T>替换为需要的class类型：

  List<String> list = new ArrayList<String>();

- 可以省略编译器能自动推断出的类型：

  List<String> list = new ArrayList<>();

- 不指定泛型参数类型时， 编译器会给出警告， 且只能将<T>视为Object类型

# 泛型3 - 编写泛型

- 编写泛型时， 需要定义泛型类型<T>

  public class Pair<T>{...}

- 静态方法不能引用泛型类型<T>， 必须定义其他类型<K>来实现“泛型”

  ```java
  public static <K> Pair create(K first, K last){...}
  ```

- 泛型可以同时定义多种类型<T, K>

  ```java
  public class Pair<T, K>{...}
  ```

  

# 泛型4 - 擦拭法

- Java的泛型采用擦拭法实现
- 擦拭法决定了泛型<T>:
  - 不能是基本类型， 例如：int
  - 不能获取带泛型类型的Class， 例如： Pair<String>.class
  - 不能判断带泛型类型的类型， 例如： x instanceof Pair<String>
  - 不能实例化T类型， 例如：new T();
  - 泛型方法要防止重复定义方法， 例如: public boolean equals(T obj)
- 子类可以获取父类的泛型类型<T>



# 泛型5 - extends通配符

- 使用类型<? extends Number>通配符作为方法参数表示：

  - 方法内部可以调用Number引用的方法

    Number n = obj.getXxx();

  - 方法内部无法调用传入Number引用的方法（null除外）

    <font color=red>obj.setXxx(Number n)</font>

- 使用类型<T extends Number>定义泛型类时表示：

  - 泛型类型限定为Number或Number的子类



# 泛型6 - super通配符

- 使用类型<? super Integer>通配符作为方法参数时表示:

  - 方法内部可以调用传入Integer引用的方法

    obj.setXxx(Integer n)

  - 方法内部无法调用获取Integer引用的方法(Object除外)

    <font color=red>Integer n = obj.getXxx()</font>

- 使用类似<T super Integer>定义泛型类时表示：

  - 泛型类型限定为Integer或Integer的超类

- 无限定通配符<?>很少使用， 可以用<T>替换



# 泛型7 - 泛型与反射

- 部分反射API是泛型：
  - Class<T>
  - Constructor<T>
- 可以声明带泛型的数组， 但不能直接创建带泛型的数组， 必须强制转型
- 可以通过Array.newInstance(Class<T>, int)创建T[]数组， 需要强制转型