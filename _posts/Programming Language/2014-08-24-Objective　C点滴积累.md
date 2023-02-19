---
layout: post
title: Objective-C点滴积累
category: 编程开发
tags: objective-c
keywords: 
description: 
---

## 基础

#### NSString赋值

```
 NSString *name;
 name = @"abc";
 [name release];
 name = [str copy];
```

#### obj中创建新对象有两种方式：[classname new]和[[classname alloc] init]。两种方法等价，Cocoa惯例是使用alloc和init。


#### `@property`

atomic,assign和readwrited都是默认行为。


#### `@interface` and `@implementation`[More](http://blog.csdn.net/l271640625/article/details/8393531),[<\<Programming in objective-c 4th>>]

interface和implementation共同代表一个类，两者的组合相当于java中的class，即oc中的类必须包括两部分，interface部分和implementation部分，这才是oc中的一个类的完整声明；然后OC中将成员变量和成员方法的声明部分放置在interface部分中，包括继承关系，protocal实现关系，都在interface里面的头部进行声明，然后将实现部分放置在implementation部分中，相当于是将类拆分成声明和实现两部分，这两部分缺一不可，所以在OC中，不妨不要将interface叫做接口，直接叫做类声明部分来得容易理解多了，简而言之，oc中interface是类的一个部分，和implementation共同组成一个完整的类。

#### `实例方法` and `类方法`

实例方法指成员函数,类方法指静态成员函数


#### 实现Controller类的初始化的地方有两处：

application:didFinishLaunchingWithOptions:
applicationDidFinishLaunching:
这两个方法，后者是前期版本下的。在iOS3.0以及之后，应该使用前者来完成开始这个过程。XCode4运行的是application:didFinishLaunchingWithOptions:
当然，你也可以删除application:didFinishLaunchingWithOptions:，自己添加applicationDidFinishLaunching方法来实现。不推荐此操作。

#### C++、objective-c 混合编程[More](http://blog.csdn.net/jiarusun000/article/details/6996984)[More2](http://beanchen.iteye.com/blog/522028)


在XCODE中想使用C++代码，你需要把文件的扩展名从.m改成.mm，这样才会启动g++编译器。

我们来看个测试代码：

``` {.java name="code"}
class TestC {
private:
    NSString *str_;//C++类可以使用OC对象作为成员变量
    
public:
    TestC() {
        str_ = @"hi mc0066.";//构造函数内可以使用OC对象来赋值
    }
    TestC(NSString *str) {//函数可以接收OC对象（通过函数参数）
        str_ = str;
    }
    TestC(NSInteger num) {
        str_ = [NSString stringWithFormat:@"%d",num];//C++函数可以调用OC方法
    }
    void show() {
        printf("%s\n",[str_ UTF8String]);
        NSLog(@"str_ is:%@\n",str_);
    }
};
```

这是我写的C++类，类内部使用了OC的代码。根据测试可以确定以下几点：

1\. C++函数内可以调用OC方法、可以创建OC对象、函数参数可以为OC对象。

2\. C++类的成员变量可以是OC对象。

其实，在混编时，OC和C++的对象都是单纯的指针，所以可以任意的彼此调用对方的方法、使用对方的内部数据。

再来看看OC中是如何使用C++代码的：

``` {.java name="code"}
@interface TestOC : NSObject
{
    TestC *c;//可以使用C++对象作为参数
}

- (id)initTestOC;
- (void)testC;

@end

@implementation TestOC

- (id)initTestOC{
    if ((self = [super init])) {
        c = new TestC();//以C++语法调用构造函数
    }
    return self;
}

- (void)testC{
    c->show();//调用C++类的内部函数
}

- (void)dealloc{
    delete c;//用完 记得删除C++对象，避免内存泄露
    [super dealloc];
}

@end
```

和之前分析c++类没啥区别，毅然是可以使用c++的语法
可以使用c++的方法和成员。

还有一点要注意，OC类无法继承C++类，C++也一样。因为oc类的结构和c++类结构不同，所以才导致该问题。


## FAQ

#### `.h、.m、.mm的区别`

`.h` ：头文件。头文件包含类，类型，函数和常数的声明。 
`.m` ：源代码文件。这是典型的源代码文件扩展名，可以包含Objective-C和C代码。 
`.mm` ：源代码文件。带有这种扩展名的源代码文件，除了可以包含Objective-C和C代码以外还可以包含C++代码。仅在你的Objective-C代码中确实需要使用C++类或者特性的时候才用这种扩展名

当你需要在源代码中包含头文件的时候，你可以使用标准的#include编译选项，但是Objective-C提供了更好的方法。#import选项和#include选项完全相同，只是它可以确保相同的文件只会被包含一次。Objective-C的例子和文档都倾向于使用#import。

#### `@synthesize和@dynamic`

`@synthesize:`

除非开发人员已经做了，否则由编译器生成相应的代码，以满足属性声明。

`@dynamic:`

由开发人员提供相应的代码：对于只读属性需要提供
setter，对于读写属性需要提供setter 和 getter，若不提供，则无法调用getter和setter。

#### UIView, UIViewController and GLKViewController[More](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIViewController_Class/Reference/Reference.html#//apple_ref/occ/cl/UIViewController)[More2](https://developer.apple.com/Library/ios/documentation/GLkit/Reference/GLKViewController_ClassRef/Reference/Reference.html)


* UIViewController
UIViewController is the controller of UIView, does following jobs:

```
View Management
Memory Management
Handling View Rotations
View Event Notification
```

UIViewController is a classic MVC pattern.

* GLKViewController

The GLKViewController class provides all of the standard view controller functionality, but additionally implements an OpenGL ES rendering loop. A GLKViewController object works in conjunction with a GLKView object to display frames of animation in the view.

#### 获取设备当前使用语言device language

```
NSString * language = [[NSLocale preferredLanguages] firstObject];
```

## ERROR

#### `Terminating app due to uncaught exception 'NSInvalidArgumentException'`

```
*** Terminating app due to uncaught exception 'NSInvalidArgumentException', reason: '-[AppController window]: unrecognized selector sent to instance 0x283fddc00'
*** First throw call stack:
(0x19e90c794 0x19e62ebcc 0x19e810f18 0x19e91061c 0x19e9127cc 0x1034dbdb8 0x1034eaf18 0x10355c870 0x103511574 0x10355cc04 0x1a236b750 0x1a23701e0 0x1a23705e8 0x1a2385c64 0x1a237ea54 0x1a2380450 0x1a2382a64 0x1a2e5a1cc 0x1a23829c4 0x1a2382e64 0x1a23828ac 0x1a2382b18 0x103534b58 0x10350c608 0x1035495d4 0x10705a338 0x10705b730 0x107069710 0x19e88a7fc 0x19e8856d0 0x19e884ce8 0x1a89cf38c 0x1a29b3444 0x102536290 0x19e70c8f0)
libc++abi.dylib: terminating with uncaught exception of type NSException
```

Solution:
```
在Appcontroller.mm文件中，在@implementation Appcontroller下增加代码@synthesize window = window；即可，
或者在appcontroller.h文件添加：
@property(nonatomic,retain)UIWindow * window;
```

#### 

## Reference