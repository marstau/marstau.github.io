---
layout: post
title: VS2010 多项目配置
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---

<span class="Apple-style-span"
style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">项目环境目录：</span>

<span class="Apple-style-span"
style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"></span>

![](http://files.note.sdo.com/XbPJ4~kkHSYG4M0os002Sx)\
 <span class="Apple-style-span"
style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">若出现无法打开自己编译的.lib文件或者.h文件的时候,便可通过增加库目录或包含目录解决</span>\
\
\
 <span class="Apple-style-span"
style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">若只想多项目中某个项目生成.lib文件的时候,得修改</span>

<span class="Apple-style-span"
style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"></span>![](http://files.note.sdo.com/XbPJ4~kkHTpVM70yw002U0)\
 <span class="Apple-style-span"
style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">将其改成静态库(.lib)即可</span>

 

VS2010工程详解：

项目结构(VS2010)

默认为：

OGRE - Debug

     - ipch

     - newProject

              - Debug

                newProject.vcxproj

                main.cpp

                newProject.vcxproj.filters

                newProject.vcxproj.user

       OGRE.sdf

       OGRE.sln

       OGRE.suo

       OGRE.opensdf

 [属性]-\>[配置属性]-\>[常规]-\>[输出目录] :
\$(SolutionDir)\$(Configuration)\\ // OGRE/Debug目录下

 [属性]-\>[配置属性]-\>[常规]-\>[中间目录] ：\$(Configuration)\\ //
OGRE/newProject/Debug目录下

 [属性]-\>[配置属性]-\>[调试]-\>[工作目录] ：\$(ProjectDir) //
OGRE/newProject目录下

 

 

我的工程目录为E:\\Visual Studio 2010\\marstau-ml-library\\MarstauLibrary：

\$(SolutionDir) : MarstauLibrary

\$(PlatformName) : Win32

\$(Configuration) : Debug or Release

 

eg : \$(SolutionDir)\$(PlatformName)\\bin.\$(Configuration)\\ 为MarstauLibrary\\Win32\\bin.Debug\\目录









