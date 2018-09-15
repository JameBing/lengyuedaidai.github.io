
---
layout: post
title: java回调函数
date: 2018-02-26 00:00:00 +0800
description: java回调函数 # Add post description (optional)
img:  # Add image post (optional)
tags: [java] # add tag
---

理解一个东西，必须从它的本源入手，再实例化到生活事例中，加深理解，毕竟程序是对现实生活的一种抽象。而Android中的回调，遵循的基本思想是Java中的回调函数。

回调函数就是一个通过函数指针调用的函数。如果你把函数的指针(地址)作为参数传递给另一个函数，当这个指针被用为调用它所指向的函数时，我们就说这是回调函数。回调函数不是由该函数的实现方直接调用，而是在特定的事件或条件发生时由另外的一方调用的，用于对该事件或条件进行响应。

Java 中没有指针的概念，通过接口和内部类的方式实现回调的功能: 
1. 定义接口 Callback ,包含回调方法 callback() 
2. 在一个类Caller 中声明一个Callback接口对象 mCallback 
3. 在程序中赋予 Caller对象的接口成员(mCallback) 一个内部类对象如 
new Callback（）{ 
callback（）{ 
//函数的具体实现 
} 
这样,在需要的时候,可用Caller对象的mCallback接口成员 调用callback()方法,完成回调


```java
public class Test{
         // 方法是fun
        public static void fun(Callbackinterface ci){
                ci.callbackfun();
        }

        //这就是接口
        public interface Callbackinterface{
                public void callbackfun();
        }
}

public static void main(){
        // 调用fun,传入接口对象并构造内部类
        Test.fun(new Callbackinterface(
                public void callbackfun(){
                        //你的实现
                }        
        )
        );
}
```

看完这个，大家可能还会比较模糊，没关系。我再讲一个实例： 
一项工程由程序员A和B共同完成，分别负责不同的模块，模块之间有交叉，A和B可能用到对方的方法，这时需要进行回调。

###### 假设我是程序员A，写了一个程序a：


```java
public class Caller {

    private MyCallInterface mc;

    //构造函数
    public Caller() {
    }

    public setI(MyCallInterface mc) {
        this.mc = mc;
    }

    //Caller的调用方法
    public call() {
        mc.fuc();
    }
}

```
###### 这里需要定义一个接口，以便程序员B根据我的定义编写程序实现接口。

```java
public interface MyCallInterface {
    public void fuc();
}

```
###### 于是，程序员B只需要实现这个接口就能达到回调的目的了：

```java
public class callee implements MyCallInterface {
    public void fuc() {
        //do something
    }
}

```
###### 下面是调用过程：
```java
public class callbacks {
    public static void main(String args[]) {
        Callee c1 = new Callee();
        Caller caller = new Caller();
        caller.setI(c1);
        caller.call();
    }
}

```

在以上代码中，caller是调用者，callee是被调用者，callbacks表示调用过程。

先产生了Callee对象（已经实现Caller提供的接口），利用这个callee对象产生的Caller对象则携带了一些信息（即与Callee对象的关联，因为Callee对象已经作为参数传入），所以Caller对象可以利用自己的call方法调用Callee的方法。——这就是整个回调过程。

看了这个例子，想必大家已经清楚了Java回调函数的机制了吧。

现在来总结一下，一般来说分为以下几步： 
1. 　声明回调函数的统一接口interface A，包含方法fuc(); 
2. 在调用类caller内将该接口设置为私有成员private A XXX; 
3. 在caller内提供一个public方法，可以将外部“该接口A的实现类的引用”通过形参传给XXX； 
4. caller的某个方法call()中会用到XXX.fuc()方法; 
5. 在caller的实例中，将实现了A接口的对象的引用传给caller，后调用call()方法