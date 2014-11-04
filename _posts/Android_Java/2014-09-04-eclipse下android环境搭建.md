---
layout: post
title: eclipse下android环境搭建
category: 游戏技术
tags: android／java
keywords: 
description: 
---

1.  安装jdk，我安装的是jdk-6u25-ea-bin-b03-windows-i586-27\_feb\_2011。然后配置java环境，环境变量中新建系统变量,变量名为JAVA\_HOME,变量值为安装路径D:\\Program Files\\Java\\jdk1.6.0\_25,然后在Path变量中编辑变量值，添加%JAVA\_HOME%\\bin;%JAVA\_HOME%\\jre\\bin;这个即可。
2.  在<http://developer.android.com/sdk/index.html>中下载SDK,打开SDK Manager，按照如下图所示的安装各个组件：\
     ![](http://files.note.sdo.com/XbPJ4~kr6rv9M70JY0070s)\
     Tools两个组件(R21即可，R22在Unity 4.1.2f1下无法正常编译)
3.  用户变量中新建 变量名为PATH,变量值为android
    sdk的tools目录（eg,我的为D:\\android-sdk-windows\\tools）的用户变量,然后在cmd中输入android -h检测是否设置成功。
4.  在eclipse中安装ADT








