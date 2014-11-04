---
layout: post
title: ListView无法在onCreate的时候getChildCount()
category: 游戏技术
tags: android／java
keywords: 
description: 
---

在onCreate的时候,View并未被绑定,所以getChildCount()获得的还是0，要正确获得,就要通过handler机制,post到队列尾部即可,用\_handler.post(runnableInstance)。

 

What i feel is, till the execution of onCreate() completes, the views wont be bound. so you will not be able to access the TextView within onCreate(). If you still want to access those variables outside the listeners, then try using Handler and post in in the queue for the thread so that onCreate() method execution is completed.  

handlerInstance.post(runnableInstance); 

(Reference:<http://www.coderanch.com/t/442573/Android/Mobile/View-customised-ListView>)

 








