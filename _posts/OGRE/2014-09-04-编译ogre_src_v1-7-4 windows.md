---
layout: post
title: 编译ogre_src_v1-7-4 windows
category: 游戏技术
tags: OGRE
keywords: 
description: 
---

 

 

用CMake编译OGRE的时候出现这种情况，原因是从官网下过来的Dependencies文件没有编译，编译Dependencies\\src目录下的.sln文件即可

\
   

<span style="color:#ff0000;">CMake Error at
CMake/Utils/MacroLogFeature.cmake:100 (MESSAGE):</span>

<span style="color:#ff0000;"></span>

\

<span style="color:#ff0000;"></span>

<span
style="color:#ff0000;">-----------------------------------------------------------------------------</span>

\

\

<span style="color:#ff0000;">-- The following REQUIRED packages could
NOT be located on your system.</span>

\

<span style="color:#ff0000;">-- Please install them before continuing
this software installation.</span>

\

<span style="color:#ff0000;">-- If you are in Windows, try
passing -DOGRE\_DEPENDENCIES\_DIR=\<path to</span>

<span style="color:#ff0000;">dependencies\></span>

\

<span style="color:#ff0000;"></span>

<span
style="color:#ff0000;">-----------------------------------------------------------------------------</span>

\

\

<span style="color:#ff0000;">+ freetype: Portable font engine
\<http://www.freetype.org\></span>

\

<span style="color:#ff0000;"></span>

<span
style="color:#ff0000;">-----------------------------------------------------------------------------</span>

<span style="color:#ff0000;">Call Stack (most recent call first):</span>

<span style="color:#ff0000;">CMake/Dependencies.cmake:208
(MACRO\_DISPLAY\_FEATURE\_LOG)</span>

<span style="color:#ff0000;">CMakeLists.txt:175 (include)</span>

 

记住要debug版本和release版本都生成,如果只生成debug版本,会报如下错误。

<span
style="color:#e53333;">send\_errorE:/Source Code/OGRE/OGRE/Dependencies/bin/release/OIS.dll did not exist, can't install!</span>

<span
style="color:#e53333;">send\_errorE:/Source Code/OGRE/OGRE/Dependencies/bin/release/cg.dll did not exist, can't install!</span>

<span
style="color:#e53333;">send\_errorE:/Source Code/OGRE/OGRE/Dependencies/bin/debug/libgles\_cm.dll did not exist, can't install!</span>

<span
style="color:#e53333;">send\_errorE:/Source Code/OGRE/OGRE/Dependencies/bin/release/libgles\_cm.dll did not exist, can't install!</span>

 

 然后再次configure。

![](http://files.note.sdo.com/XbPJ4~kfgoSOwE02I000aM)

红色表示第一次生成，为了确认不会出错，再次点击configure。

 

确认无误后，点击generate即可。

 





