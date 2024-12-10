Atitit jdk new feature v3 v66 jdk16 15 14 10 11 12 13
Atitit jdk new feature jdk10 11 12 13

Jdk16
395:Records
简单来说，Records 就是一种新的语法糖，目的还是为了简化代码，在 JDK 14 中首次成为预览特性，在 JDK 16 中正式转正。
Records 可以在一定程度上避免低级冗余的代码，比如：constructors, getters, equals(), hashCode(), toString() 方法等，相当于 Lombok 的 @Data 注解，但又不能完全替代。
下面来看一个示例：
public record Student(String name, int id, int age) {}

J15none
Java版本新发现：JDK15的14个新特性和变化

java14新特性
在JDK14中新增了以下16个新特性：
358: 友好的空指针异常
 368: 文本块 (第二个预览版)
 Java 8 新特性
Java 8 (又称为 jdk 1.8) 是 Java 语言开发的一个主要版本。 Oracle 公司于 2014 年 3 月 18 日发布 Java 8 ，它支持函数式编程，新的 JavaScript 引擎，新的日期 API，新的 Stream API 等。

新特性
Java8 新增了非常多的特性，我们主要讨论以下几个：

Lambda 表达式 
− Lambda 允许把函数作为一个方法的参数（函数作为参数传递到方法中）。


方法引用 −
 方法引用提供了非常有用的语法，可以直接引用已有 Java 类或对象（实例）的方法或构造器。与 lambda 联合使用，方法引用可以使语言的构造更紧凑简洁，减少冗余代码。


默认方法 − 默认方法就是一个在接口里面有了一个实现的方法。


新工具 − 新的编译工具，如：Nashorn 引擎 jjs、 类依赖分析器 jdeps。


Stream API  函数式编程风格引入
−新添加的 Stream API（java.util.stream） 把真正的函数式编程风格引入到 Java 中。


Date Time API − 加强对日期与时间的处理。


Optional 类 − Optional 类已经成为 Java 8 类库的一部分，用来解决空指针异常。


Nashorn, JavaScript 引擎 − Java 8 提供了一个新的 Nashorn javascript 引




JDK10 允许编译器推断局部变量的类型，
但是局部变量类型推断能力仅适用于局部变量。它不能用于定义实例或者类
变量也不能用于方法的参数和返回类型，但是可以在增强型 for 循环或者迭代器中使用它，使用局部变量类型组主要的优点是

Ldk11 大部分是增强
HttpClient

Java11相对Java8，在语法上的新特性并不多。主要有：
本地变量类型推断
HttpClient
Collection增强
Stream增强
Optional增强
String增强
InputStream增强

Jdk12 none


Java 语言特性系列
Java5 的新特性
Java6 的新特性
Java7 的新特性
Java8 的新特性
Java9 的新特性
Java10 的新特性
Java11 的新特性
Java12 的新特性
Java13 的新特性

JDK13 的六大重要新特性
JDK13 的六大重要特性
JDK13 在 9 月 17 号全球首发了，Oracle JDK 13 通过改善 Java SE 平台和 JDK 的性能，稳定性和安全性来提高开发人员的生产力。这次的 JDK13 包含了 5 个 JEP (Java Enhancement Proposals) 和一个 Unicode 12.1 的支持总共 6 大主要新特性。下面我们一一详细说明。
支持 Unicode 12.1
动态 CDS 归档（Dynamic CDS Archiving）
java.net.Socket 和 java.net.ServerSocket API 的重新实现
ZGC 的增强
文本块（预览语言功能）


