---
layout: post
title: linux usage - common
category: 书籍与软件工具
tags: software／tool
keywords: linux,mac
description: 
---

##**登录直接进入命令界面**

如果当时在安装时设置为一启动就进入图形界面的话，那系统启动后，用户登录界面将是图形化的，有点像Windows，而且当你输入正确的 用户名与密码，就会直接进入X Window。这个设置是可以修改的：

在/etc目录下有一个inittab文件，其中有一行配置：

 <span style="color:#ff0000;">id:3:default</span>


##**编译C++文件**

    $ g++ -o hello hello.C
    
    $ ./hello

    Hello, world!


#Reference
* <http://msdn.microsoft.com/zh-cn/library/ff636699.aspx>

