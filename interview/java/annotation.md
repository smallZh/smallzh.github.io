## 注解相关题目
---
## 1 解释一下Java中的注解？⭐ :id=java-annotation
Annotation（注解）是 Java 提供的一种对元程序中元素关联信息和元数据（metadata）的途径和方法。Annatation(注解)是一个接口，程序可以通过反射来获取指定程序中元素的 Annotation
对象，然后通过该 Annotation 对象来获取注解中的元数据信息。

![](../imgs/annotation_1.jpg)

## 2 Java提供了哪些标准元注解？⭐⭐⭐ :id=anno-meta
元注解的作用是负责注解其他注解。 Java5.0 定义了 4 个标准的 meta-annotation 类型，它们被用来提供对其它 annotation 类型作说明。

**1 @Target 修饰的对象范围**

@Target说明了Annotation所修饰的对象范围： Annotation可被用于 packages、types（类、
接口、枚举、Annotation 类型）、类型成员（方法、构造方法、成员变量、枚举值）、方法参数
和本地变量（如循环变量、catch 参数）。在 Annotation 类型的声明中使用了 target 可更加明晰
其修饰的目标

**2 @Retention 定义 被保留的时间长短**

Retention 定义了该 Annotation 被保留的时间长短：表示需要在什么级别保存注解信息，用于描
述注解的生命周期（即：被描述的注解在什么范围内有效），取值（RetentionPoicy）由：
1. SOURCE:在源文件中有效（即源文件保留）
1. CLASS:在 class 文件中有效（即 class 保留）
1. RUNTIME:在运行时有效（即运行时保留）

**3 @Documented 描述-javadoc**

@ Documented 用于描述其它类型的 annotation 应该被作为被标注的程序成员的公共 API，因
此可以被例如 javadoc 此类的工具文档化。

**4 @Inherited 阐述了某个被标注的类型是被继承的**

@Inherited 元注解是一个标记注解，@Inherited 阐述了某个被标注的类型是被继承的。如果一个使用了@Inherited 修饰的 annotation 类型被用于一个 class，则这个 annotation 将被用于该class 的子类。

## 3 Java中怎么处理注解？⭐⭐ :id=anno-handle
如果没有用来读取注解的方法和工作，那么注解也就不会比注释更有用处了。使用注解的过程中，
很重要的一部分就是创建于使用注解处理器。Java SE5 扩展了反射机制的 API，以帮助程序员快速
的构造自定义注解处理器。下面实现一个注解处理器。

代码：
```java
/1：*** 定义注解*/
@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
@Documented
public @interface FruitProvider {
 /**供应商编号*/
public int id() default -1;
/*** 供应商名称*/
 public String name() default ""；13/04/2018 Page 108 of 283
 /** * 供应商地址*/
 public String address() default "";
}
//2：注解使用
public class Apple {
 @FruitProvider(id = 1, name = "陕西红富士集团", address = "陕西省西安市延路")
 private String appleProvider;
 public void setAppleProvider(String appleProvider) {
 this.appleProvider = appleProvider;
 }
 public String getAppleProvider() {
 return appleProvider;
 }
}
/3：*********** 注解处理器 ***************/
public class FruitInfoUtil {
 public static void getFruitInfo(Class<?> clazz) {
 String strFruitProvicer = "供应商信息：";
 Field[] fields = clazz.getDeclaredFields();//通过反射获取处理注解
 for (Field field : fields) {
 if (field.isAnnotationPresent(FruitProvider.class)) {
 FruitProvider fruitProvider = (FruitProvider) field.getAnnotation(FruitProvider.class);
//注解信息的处理地方 
strFruitProvicer = " 供应商编号：" + fruitProvider.id() + " 供应商名称："
 + fruitProvider.name() + " 供应商地址："+ fruitProvider.address();
 System.out.println(strFruitProvicer);
 }
 }
 }
public class FruitRun {
 public static void main(String[] args) {
 FruitInfoUtil.getFruitInfo(Apple.class);
/***********输出结果***************/
// 供应商编号：1 供应商名称：陕西红富士集团 供应商地址：陕西省西安市延
 }
}

```