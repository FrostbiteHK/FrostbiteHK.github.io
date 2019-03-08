---
layout:     post
title:      Java编程技巧
subtitle:   String、StringBuffer与StringBuilder的区别
date:       2019-03-03
author:     HK
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Java
---
# String、StringBuffer与StringBuilder的区别。

java中String、StringBuffer、StringBuilder是编程中经常使用的字符串类，他们之间的区别也是经常在面试中会问到的问题。现在总结一下，看看他们的不同与相同。
#### 可变与不可变
&emsp;String类中使用字符数组保存字符串，因为有“final”修饰符，所以可以知道string对象是不可变的。<br>
```java
private final char value[];
```


　StringBuilder与StringBuffer都继承自AbstractStringBuilder类，在AbstractStringBuilder中也是使用字符数组保存字符串，可知这两种对象都是可变的。<br>
 ```java
 char[] value;
 ```
 
#### 运行速度
  **StringBuilder > StringBuffer > String**<br>
 String最慢的原因;String为字符串常量，而StringBuilder和StringBuffer均为字符串变量，即String对象一旦创建之后该对象是不可更改的，
 但后两者的对象是变量，是可以更改的。例如：
```java
String str="abc";
System.out.println(str);
str=str+"de";
System.out.println(str);
```
　运行这段代码先输出“abc”，然后又输出“abcde”，好像是str这个对象被更改了，但其实JVM对于这几行代码是这样处理的：首先创建一个String对象str，
并把“abc”赋值给str，然后在第三行中，其实JVM又创建了一个新的对象也名为str，然后再把原来的str的值和“de”加起来再赋值给新的str，str实际上并没有被更改，
也就是前面说的String对象一旦创建之后就不可更改了。当 str = str + "xxx"的时候，是在堆内存中重新新建了两份内存，即：xxx和最终的 strxxx，但是这个时候，
原始的 str，以及上一步的 xxx，这两块内存，并不会即时机会被gc（垃圾回收机制），在大量的string拼接操作出现的时候，jvm由于内存紧张，基本实时进行gc，
这样才会引起速度变慢。而StringBuilder和StringBuffer的对象是变量，对变量进行操作就是直接对该对象进行更改，而不进行创建和回收的操作，所以速度要比String快很多。<br>

#### 线程安全
  **StringBuilder是线程不安全的，而StringBuffer是线程安全的**<br>
  　如果一个StringBuffer对象在字符串缓冲区被多个线程使用时，StringBuffer中很多方法可以带有synchronized关键字，所以可以保证线程是安全的，
   但StringBuilder的方法则没有该关键字，所以不能保证线程安全，有可能会出现一些错误的操作。所以如果要进行的操作是多线程的，那么就要使用StringBuffer，
   但是在单线程的情况下，还是建议使用速度比较快的StringBuilder。
   
#### 小结
　　String：适用于少量的字符串操作的情况

　　StringBuilder：适用于单线程下在字符缓冲区进行大量操作的情况

　　StringBuffer：适用多线程下在字符缓冲区进行大量操作的情况
