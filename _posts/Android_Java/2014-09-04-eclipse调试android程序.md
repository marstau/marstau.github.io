---
layout: post
title: eclipse调试android程序
category: 游戏技术
tags: android／java
keywords: 
description: 
---

用eclipse开发android程序的时,跟VS一样是可以断点单步调试的.\
 步骤如下.\
 1 设置断点:在编码窗体的左边框上用鼠标双击,或者右键点击菜单,选择 Toggle
Breakpoint菜单项即可.

![](http://pic002.cnblogs.com/images/2012/381354/2012072714164135.gif)

\
\
 2
在debug模式下运行程序进入调试状态:通过点击工具栏上的小虫按钮或者是在项目右键点击然后选择Debug
As，Android Application菜单,启动程序的调试模式.\
 第一次运行调试模式eclipse会弹出如下确认窗口

![](http://pic002.cnblogs.com/images/2012/381354/2012072714165855.gif)

\
\
\

当程序运行到你的断点地方时就会停下,这时可以按照下面的功能键按需求进行调试:\
 <span
style="font-size:small;">[1]快捷键（F8）直接执行程序,直到下一个断点处停止。\
 [2]快捷键（F5）单步执行程序，遇到方法时进入。\
 [3]快捷键（F6）单步执行程序，遇到方法时跳过。\
 [4]快捷键（F7）单步执行程序，从当前方法跳出。</span>

 

3.停止调试

右上角有两个按钮(Java和Debug)，选择Java按钮即可![](http://files.note.sdo.com/XbPJ4~keoW9OwE04400feD)

 

**caution:有一个选项是 跳过所有断点，必须得去掉才能正常调试**








