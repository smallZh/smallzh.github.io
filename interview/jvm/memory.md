## 内存模型
---
## 1 Java 出现多线程安全问题的原因？⭐ :id=safe-thread
1. 多线程执行乱序，
1. 内存的可见性。

## 2 Java Memory Model? ⭐⭐⭐⭐ :id=model
定义： happens-after关系
1. 如果操作执行顺序具有先后性。
1. 那么后执行的操作能够看到先执行的操作的结果。
1. 规定以下操作必须保证happens-after 关系
1. Unlock 发生在lock之前。
1. 写volatile发生在读volatite 之前
1. 线程start() 发生在线程所有动作之前。
1. 线程中所有操作发生在线程join之前。
1. 构造函数发生在finalizer 开始之前。
1. 传递性：happens-after关系满足传递性 A>B B>C =>A

## 3 JVM 执行new语句创建一个对象时，内部的运行过程是怎样的 ？⭐⭐⭐⭐ :id=new-process
1. 所有的类都是在第一次被使用时，动态加载到JVM中。当首次创建类型为Dog的对象时，或者Dog类的静态方法首次被调用时，或者静态属性域首次被访问时，java解释器查找classPath，定位到Dog.class文件。 
2. 载入Dog.class文件，生成一个Class类型对象，所有有关的静态初始化动作都会执行：如静态代码块，静态成员属性。 并且这种初始化动作只在Class对象首次加载时候进行一次。 
3. 当用new Dog()创建对象时，首先JVM在堆heap上为Dog对象分配足够的存储空间。 
4. 存储空间清空，自动将Dog对象中的所有基本类型数据都设置成了默认值，对象引用被设置为null。 
5. 执行所有在字段定义处的一些初始化操作。 
6. 调用构造器方法。（没有继承）

## 4 Jvm内存区域怎么划分？⭐⭐⭐⭐⭐ :id=area
![](../imgs/jvm_3.jpg)

JVM 内存区域主要分为
1. 线程私有区域：程序计数器、虚拟机栈、本地方法栈
2. 线程共享区域：JAVA 堆、方法区
3. 直接内存：不受Jvm GC管理

线程私有数据区域生命周期与线程相同, 依赖用户线程的启动/结束 而 创建/销毁(在 Hotspot VM 内, 每个线程都与操作系统的本地线程直接映射, 因此这部分内存区域的存/否跟随本地线程的生/死对应)。

线程共享区域随虚拟机的启动/关闭而创建/销毁。

直接内存并不是 JVM 运行时数据区的一部分, 但也会被频繁的使用: 在 JDK 1.4 引入的 NIO 提供了基于 Channel 与 Buffer 的 IO 方式, 它可以使用 Native 函数库直接分配堆外内存, 然后使用DirectByteBuffer 对象作为这块内存的引用进行操作(详见: Java I/O 扩展), 这样就避免了在 Java堆和 Native 堆中来回复制数据, 因此在一些场景中可以显著提高性能。

**也可以按如下进行划分：**

![](../imgs/jvm_4.jpg)

**1 程序计数器(线程私有)**

一块较小的内存空间, 是当前线程所执行的字节码的行号指示器，每条线程都要有一个独立的程序计数器，这类内存也称为“线程私有”的内存。

正在执行 java 方法的话，计数器记录的是虚拟机字节码指令的地址（当前指令的地址）。如果还是 Native 方法，则为空。

这个内存区域是唯一一个在虚拟机中没有规定任何 OutOfMemoryError 情况的区域。

**2 虚拟机栈(线程私有)**

是描述java方法执行的内存模型，每个方法在执行的同时都会创建一个栈帧（Stack Frame）用于存储局部变量表、操作数栈、动态链接、方法出口等信息。

每一个方法从调用直至执行完成的过程，就对应着一个栈帧在虚拟机栈中入栈到出栈的过程。

栈帧（ Frame）是用来存储数据和部分过程结果的数据结构，同时也被用来处理动态链接(Dynamic Linking)、 方法返回值和异常分派（ Dispatch Exception）。

栈帧随着方法调用而创建，随着方法结束而销毁——无论方法是正常完成还是异常完成（抛出了在方法内未被捕获的异常）都算作方法结束。

**3 本地方法区(线程私有)**

本地方法区和 Java Stack 作用类似, 区别是虚拟机栈为执行 Java 方法服务, 而本地方法栈则为Native 方法服务, 如果一个 VM 实现使用 C-linkage 模型来支持 Native 调用, 那么该栈将会是一个C 栈，但 HotSpot VM 直接就把本地方法栈和虚拟机栈合二为一。

**4 堆（Heap-线程共享）-运行时数据区**

是被线程共享的一块内存区域，创建的对象和数组都保存在 Java 堆内存中，也是垃圾收集器进行垃圾收集的最重要的内存区域。由于现代 VM 采用分代收集算法, 因此 Java 堆从 GC 的角度还可以细分为: 新生代(Eden 区、From Survivor 区和 To Survivor 区)和老年代。

**5 方法区/永久代（线程共享）**

即我们常说的永久代(Permanent Generation), 用于存储被 JVM 加载的类信息、常量、静态变量、即时编译器编译后的代码等数据. HotSpot VM把GC分代收集扩展至方法区, 即使用Java堆的永久代来实现方法区, 这样 HotSpot 的垃圾收集器就可以像管理 Java 堆一样管理这部分内存, 而不必为方法区开发专门的内存管理器(永久带的内存回收的主要目标是针对常量池的回收和类型的卸载, 因此收益一般很小)。

运行时常量池（Runtime Constant Pool）是方法区的一部分。Class 文件中除了有类的版本、字段、方法、接口等描述等信息外，还有一项信息是常量池（Constant Pool Table），用于存放编译期生成的各种字面量和符号引用，这部分内容将在类加载后存放到方法区的运行时常量池中。 

Java 虚拟机对 Class 文件的每一部分（自然也包括常量池）的格式都有严格的规定，每一个字节用于存储哪种数据都必须符合规范上的要求，这样才会被虚拟机认可、装载和执行。

## JVM 运行时内存?
Java 堆从 GC 的角度还可以细分为: 新生代(Eden 区、From Survivor 区和 To Survivor 区)和老年
代。

![](../imgs/jvm_5.jpg)

**新生代**

是用来存放新生的对象。一般占据堆的 1/3 空间。由于频繁创建对象，所以新生代会频繁触发
MinorGC 进行垃圾回收。新生代又分为 Eden 区、ServivorFrom、ServivorTo 三个区。

**Eden 区**

Java 新对象的出生地（如果新创建的对象占用内存很大，则直接分配到老年代）。当 Eden 区内存不够的时候就会触发 MinorGC，对新生代区进行一次垃圾回收。

**ServivorFrom**

上一次 GC 的幸存者，作为这一次 GC 的被扫描者。

**ServivorTo**

保留了一次 MinorGC 过程中的幸存者。

**老年代**

主要存放应用程序中生命周期长的内存对象。老年代的对象比较稳定，所以 MajorGC 不会频繁执行。在进行 MajorGC 前一般都先进行
了一次 MinorGC，使得有新生代的对象晋身入老年代，导致空间不够用时才触发。当无法找到足
够大的连续空间分配给新创建的较大对象时也会提前触发一次 MajorGC 进行垃圾回收腾出空间。
 MajorGC 采用标记清除算法：首先扫描一次所有老年代，标记出存活的对象，然后回收没
有标记的对象。MajorGC 的耗时比较长，因为要扫描再回收。MajorGC 会产生内存碎片，为了减
少内存损耗，我们一般需要进行合并或者标记出来方便下次直接分配。当老年代也满了装不下的
时候，就会抛出 OOM（Out of Memory）异常。

**永久代**

指内存的永久保存区域，主要存放 Class 和 Meta（元数据）的信息,Class 在被加载的时候被
放入永久区域，它和和存放实例的区域不同,GC 不会在主程序运行期对永久区域进行清理。所以这
也导致了永久代的区域会随着加载的 Class 的增多而胀满，最终抛出 OOM 异常。

**JAVA8 与元数据**

在 Java8 中，永久代已经被移除，被一个称为“元数据区”（元空间）的区域所取代。元空间
的本质和永久代类似，元空间与永久代之间最大的区别在于：元空间并不在虚拟机中，而是使用
本地内存。因此，默认情况下，元空间的大小仅受本地内存限制。类的元数据放入 native 
memory, 字符串池和类的静态变量放入 java 堆中，这样可以加载多少类的元数据就不再由
MaxPermSize 控制, 而由系统的实际可用空间来控制。