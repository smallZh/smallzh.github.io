## 反射相关题目
---
## 在哪些场合应用到反射？⭐⭐⭐ :id=ref-sence
**1 编译时类型和运行时类型**

在 Java 程序中许多对象在运行是都会出现两种类型：编译时类型和运行时类型。 编译时的类型由
声明对象时实用的类型来决定，运行时的类型由实际赋值给对象的类型决定 。如：
```java
Person p=new Student();
```
其中编译时类型为 Person，运行时类型为 Student。

**2 编译时类型无法获取具体方法**

程序在运行时还可能接收到外部传入的对象，该对象的编译时类型为 Object,但是程序有需要调用
该对象的运行时类型的方法。为了解决这些问题，程序需要在运行时发现对象和类的真实信息。
然而，如果编译时根本无法预知该对象和类属于哪些类，程序只能依靠运行时信息来发现该对象
和类的真实信息，此时就必须使用到反射了。

## Java 反射 API有哪些？⭐⭐ :id=ref-api
反射 API 用来生成 JVM 中的类、接口或则对象的信息。

1. Class 类：反射的核心类，可以获取类的属性，方法等信息。
2. Field 类：Java.lang.reflec 包中的类，表示类的成员变量，可以用来获取和设置类之中的属性
值。
3. Method 类： Java.lang.reflec 包中的类，表示类的方法，它可以用来获取类中的方法信息或
者执行方法。
4. Constructor 类： Java.lang.reflec 包中的类，表示类的构造方法。

## 解释一下Java的反射？⭐ :id=java-ref
> 运行状态中知道类所有的属性和方法

在 Java 中的反射机制是指在运行状态中，对于任意一个类都能够知道这个类所有的属性和方法；
并且对于任意一个对象，都能够调用它的任意一个方法；这种动态获取信息以及动态调用对象方
法的功能成为 Java 语言的反射机制。

![](../imgs/reflection_1.jpg)

## 动态语言vs静态语言的含义？⭐⭐⭐ :id=lang-d-vs-s
**动态语言**

动态语言，是指程序在运行时可以改变其结构：新的函数可以引进，已有的函数可以被删除等结
构上的变化。比如常见的 JavaScript 就是动态语言，除此之外 Ruby,Python 等也属于动态语言，
而 C、C++则不属于动态语言。从反射角度说 JAVA 属于半动态语言。

**静态语言**

先编译成机器语言，再执行，如C、C++

## 怎么使用反射？⭐⭐ :id=use-ref
> 获取 Class 对象、调用对象方法

1. 获取想要操作的类的 Class 对象，他是反射的核心，通过 Class 对象我们可以任意调用类的方
法。
2. 调用 Class 类中的方法，既就是反射的使用阶段。
3. 使用反射 API 来操作这些信息。

## 获取Class对象的方式有哪些？⭐⭐ :id=get-clas
**1 调用某个对象的 getClass()方法**
```java
Person p=new Person();
Class clazz=p.getClass();
```
**2 调用某个类的 class 属性来获取该类对应的 Class 对象**
```java
Class clazz=Person.class;
```
**3 使用 Class 类中的 forName()静态方法**
> 最安全/性能最好/最常用

```java
Class clazz=Class.forName("类的全路径");
```

当我们获得了想要操作的类的 Class 对象后，可以通过 Class 类中的方法获取并查看该类中的方法和属性。如下：
```java
//获取 Person 类的 Class 对象
 Class clazz=Class.forName("reflection.Person");
 //获取 Person 类的所有方法信息
 Method[] method=clazz.getDeclaredMethods();
 for(Method m:method){
 	System.out.println(m.toString());
 }
 //获取 Person 类的所有成员属性信息
 Field[] field=clazz.getDeclaredFields();
 for(Field f:field){
 	System.out.println(f.toString());
 }
 //获取 Person 类的所有构造方法信息
 Constructor[] constructor=clazz.getDeclaredConstructors();
 for(Constructor c:constructor){
 	System.out.println(c.toString());
 }
```

## 通过Class对象创建Object实例的方式有哪些？⭐⭐ :id=cls-obj
**1 Class 对象的 newInstance()**

使用 Class 对象的 newInstance()方法来创建该 Class 对象对应类的实例，但是这种方法要求该 Class 对象对应的类有默认的空构造器。

如下：
```java
//获取 Person 类的 Class 对象
 Class clazz=Class.forName("reflection.Person"); 
 //使用.newInstane 方法创建对象
 Person p=(Person) clazz.newInstance();
```

**2 调用 Constructor 对象的 newInstance()**

先使用 Class 对象获取指定的 Constructor 对象，再调用 Constructor 对象的 newInstance()方法来创建 Class 对象对应类的实例,通过这种方法可以选定构造方法创建实例。

如下：
```java
//获取构造方法并创建对象
 Constructor c=clazz.getDeclaredConstructor(String.class,String.class,int.class);
 //创建对象并设置属性
 Person p1=(Person) c.newInstance("李四","男",20);
```