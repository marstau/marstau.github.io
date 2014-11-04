---
layout: post
title: \@synthesize和\@dynamic
category: 游戏技术
tags: Objective　C
keywords: 
description: 
---

@synthesize:

除非开发人员已经做了，否则由编译器生成相应的代码，以满足属性声明。

 

@dynamic:

由开发人员提供相应的代码：对于只读属性需要提供
setter，对于读写属性需要提供setter 和
getter，若不提供，则无法调用getter和setter。






