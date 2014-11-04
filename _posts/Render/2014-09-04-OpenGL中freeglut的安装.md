---
layout: post
title: OpenGL中freeglut的安装
category: 游戏技术
tags: Game　Engine
keywords: 
description: 
---

 

GLUT 代表OpenGL Utility Tookit。Mark J.Kilgard 为了使OpenGL应用程序结构能够真正独立于窗口系统构思了GLUT库。

 

Freeglut是一个GLUT的开源实现。

 

本文介绍VS2008环境下的Freeglut 2.6.0配置：

 

1. 下载Freeglut：http://freeglut.sourceforge.net/，http://prdownloads.sourceforge.net/freeglut/freeglut-2.6.0.tar.gz?download

 

2. 下载到的文件为freeglut-2.6.0.tar.gz，解压到任意目录，使用Visual Studio 2008打开freeglut-2.6.0\\VisualStudio2008\\freeglut.vcproj，使用Release执行编译。这时会生成Release目录。

 

3. 将Release目录中的freeglut.dll复制到system32下。

 

4. 查找gl.h位置（默认在C:\\Program Files\\Microsoft SDKs\\Windows\\v6.0A\\Include\\gl），将freeglut-2.6.0\\include\\GL中的.h文件复制进去。

 

5.查找GlU32.Lib位置（默认在C:\\Program Files\\Microsoft SDKs\\Windows\\v6.0A\\Lib），将Release目录下的freeglut.lib文件复制进去。

 

完成配置。






