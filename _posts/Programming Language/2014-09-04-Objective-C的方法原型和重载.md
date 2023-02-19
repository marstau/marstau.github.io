---
layout: post
title: Objective-C的方法原型和重载
category: 编程开发
tags: objective-c
keywords: 
description: 
---
毫无疑问，objective-c 也是一种面向对象语言，那么面向对象有三个基本特征(封装、继承、多态)。重载似乎与这三大特征没多大关系，方法覆盖才预示着多态。但重载还是与覆盖有一定的关联，它们都要求你能识别出方法的原型，这就引出方法原型与重载的关系。
objective-c 与最常见的语言如，C++、C#、Java 在这方面是不同的，我们知道，Java、C++ 和 C# 识别方法原型是依据于方法名、参数个数、与参数类型这三要素决定，比如下面出自于一个类中的四个计算面积的方法，对于 Java、C++ 或 C#，它们是合法的：

    float calculateArea()
    float calculateArea(int width)
    float calculateArea(float width)
    float calculateArea(int width, int height)
因为它们的方法原型是不同的，分别是：

    calculateArea()
    calculateArea(int)
    calculateArea(float)
    calculateArea(int, int)
然而这应用到 objective-c 中就不同的，因为 objective-c 还为方法的引入了一个参数描述的概念。如果你在 objective-c 的某个类中相应的写下四个类似的方法：

    -(float) calculateArea
    -(float) calculateArea: (int) width
    -(float) calculateArea: (float) width
    -(float) calculateArea: (int) width andHeight: (int) height
那是不行的，这时候第二个和第三个方法会有冲突，会得到错误：
error: duplicate declaration of method '-calculateArea:'
它们被认为是一样的方法，因为它们的方法原型是与参数描述有关，在 objective-c 中方法的定义格式是：

      -/+ (返回类型) 方法名: (参数1类型) 形参1  参数2描述: (参数2类型) 形参2 参数3描述: (参数3类型) 形参3 .......**

objective-c 对于每一个参数都要有一个参数描述，而第一个参数的描述由方法名本身来承载，所以有许多像
initWithFrame:    stringWithString:  这样的方法，在方法名的后部分 frame 或 string 描述了第一个参数
基于上，objective-c 的方法原型是：
方法名: 参数2描述:参数3描述: .......
应用于上面四个方法时，它们的原型分别是，(注意参数描述后的冒号，一个参数对应有一个冒号)：
calculateArea
calculateArea:
calculateArea:
calculateArea:andHeight:
所以第二、三个方法就冲突了，这里还得讲一点，无参数的方法原型就是方法名，有一个参数的原型是方法名后带个冒号(:)，所以执行事件时用 SEL(onclick:) 定位IBAction 时方法名后要加个冒号，因为它后面有一个参数是 (id) sender。
另一方面，采用 objective-c 的方法命名方式，即方法名须描述第一个参数的办法，上面的方法应重新声明如下，并纠正一个方法声明：
-(float) calculateArea
-(float) calculateByWidth: (int) width
-(float) calculateByFloatWidth: (float) width
-(float) calculateByWidth: (int) width andHeight: (int) height
从 objective-c 对方法原型的认定，也告诉我们对方法的命名，还有每一个参数的描述更要讲究。而且它的方法调用方式(确切说是消息发送机制) 中使用到了参数描述，也类似于有些语言(如 VB、Groovy) 中的命名参数，使得代码更人性化，更易于理解。
再进一步演义，在 objective-c 中如果两个方法，方法名相同、参数个数一个，并且每一个参数类型也相同，它们也是可以同时存在于一个类中，如：

    -(float) calculateByWidth: (int) width andXxxHeight: (int) xxxHeight
    -(float) calculateByWidth: (int) width andYyyHeight: (int) yyyHeight
它们也是互为重载的关系，因为它们的原型分别为：

    calculateByWidth:andXxxHeight:
    calculateByWidth:andYyyHeight:
这在 Java、C++、C# 等面向对象的语方中是不允许的。因此，对于 objective-c 来说重载的几要素就变成了 方法名、参数个数 和参数描述，与类型无关。最后着重强调一个，objective-c 的方法原型或重载是与参数类型无关的。
另外，也可以不给方法指定参数描述，或者个别指定个别不指定，这时候调用方式和方法原型也有所不同了，例如：

    -(void) set: (int) x :  (int) d
    
调用方式是： [cat set: 1 : 2]
原型是： set::。

    -(void) set: (int) x : (int) y param3: (int) z
调用方式是：[cat set : 1 : 2 param3:100], 不能用[cat set : 1 : 2 : 100] 来调用
原型是：set::param3:。

参考官方的文档，之前说的参数描述称作 内部参数名(internal argument name)，即给方法调用时用; 而形参被叫做外部参数名(external argument name)。当指定了内部参数名时，调用时一定要用内部参数名来指定参数。
不带参数描述的方式不推荐，会让程序不好理解，还有就是区别方法只能依据方法名与参数的个数了，方法重复定义的可能性就大了。像前面只要方法名是 set 的任何两个参数的方法都是相同的。


## Reference
* <http://blog.csdn.net/lonelyroamer/article/details/7661745>
* <https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/ProgrammingWithObjective-C/DefiningClasses/DefiningClasses.html>
