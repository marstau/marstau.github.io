---
layout: post
title: error LNK2019  __imp__InitCommonControls@0
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

 

1\>------ 已启动生成: 项目: Billboard, 配置: Debug Win32 ------

1\>生成启动时间为 2012/12/11 12:14:45。

1\>InitializeBuildStatus:

1\>  正在对“Debug\\Billboard.unsuccessfulbuild”执行 Touch 任务。

1\>ClCompile:

1\>  Billboard.cpp

1\>ManifestResourceCompile:

1\>  所有输出均为最新。

1\>DXUT.lib(DXUT.obj) : error LNK2019: 无法解析的外部符号 \_\_imp\_\_InitCommonControls@0，该符号在函数 "long \_\_stdcall 

 

DXUTInit(bool,bool,wchar\_t \*,bool)" (?DXUTInit@@YGJ\_N0PA\_W0@Z) 中被引用

1\>DXUT.lib(DXUTmisc.obj) : error LNK2019: 无法解析的外部符号 \_DXTraceW@20，该符号在函数 "long \_\_stdcall DXUTTrace

 

(char const \*,unsigned long,long,wchar\_t const \*,bool)" (?DXUTTrace@@YGJPBDKJPB\_W\_N@Z) 中被引用

1\>E:\\Visual Studio 2010\\Projects\\DXUT\\Debug\\Billboard.exe : fatal error LNK1120: 2 个无法解析的外部命令

1\>

1\>生成失败。

1\>

1\>已用时间 00:00:04.01

========== 生成: 成功 0 个，失败 1 个，最新 0 个，跳过 0 个 ==========

 

**<span style="color:#e53333;">解决:</span>**\
 **<span style="color:#e53333;">添加lib库</span>**

**<span style="color:#e53333;">comctl32.lib</span>**

**<span style="color:#e53333;">version.lib</span>**

**<span style="color:#e53333;">d3d9.lib</span>**

**<span style="color:#e53333;">d3dx9.lib</span>**

**<span style="color:#e53333;">dxerr.lib</span>**

**<span style="color:#e53333;">winmm.lib</span>**

**<span style="color:#e53333;">Gdi32.lib</span>**

**<span style="color:#e53333;">user32.lib</span>**

**<span style="color:#e53333;">AdvAPI32.lib</span>**

**<span style="color:#e53333;">dinput8.lib</span>**

**<span style="color:#e53333;">dxguid.lib</span>**

**<span style="color:#e53333;">ole32.lib</span>**








