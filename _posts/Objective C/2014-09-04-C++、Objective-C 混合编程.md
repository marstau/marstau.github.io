---
layout: post
title: C++、Objective-C 混合编程
category: 游戏技术
tags: Objective　C
keywords: 
description: 
---

<div id="article_content" class="article_content"
xmlns="http://www.w3.org/1999/xhtml">

FROM:<http://blog.csdn.net/jiarusun000/article/details/6996984>

REFERENCE:<http://beanchen.iteye.com/blog/522028>

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

</div>





