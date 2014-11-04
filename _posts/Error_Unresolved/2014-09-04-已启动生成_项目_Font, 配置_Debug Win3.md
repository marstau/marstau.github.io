---
layout: post
title: 1>------ 已启动生成/项目/Font, 配置/Debug Win3
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

1\>------ 已启动生成: 项目: Font, 配置: Debug Win32 ------

1\>生成启动时间为 2012-04-05 21:15:06。

1\>InitializeBuildStatus:

1\> 正在对“Debug\\Font.unsuccessfulbuild”执行 Touch 任务。

1\>ClCompile:

1\> 所有输出均为最新。

1\>ManifestResourceCompile:

1\> 所有输出均为最新。

1\>Font.obj : error LNK2019: 无法解析的外部符号 "void \_\_cdecl
MarstauLibrarry::CreateCube(struct IDirect3DDevice9 \*,struct
IDirect3DVertexBuffer9 \* &,struct IDirect3DIndexBuffer9 \* &)"
(?CreateCube@MarstauLibrarry@@YAXPAUIDirect3DDevice9@@AAPAUIDirect3DVertexBuffer9@@AAPAUIDirect3DIndexBuffer9@@@Z)，该符号在函数
"void \_\_cdecl Setup(void)" (?Setup@@YAXXZ) 中被引用

1\>E:\\Visual Studio 2010\\Projects\\MarstauLibrary\\Debug\\Font.exe :
fatal error LNK1120: 1 个无法解析的外部命令

1\>

1\>生成失败。

1\>

1\>已用时间 00:00:00.39

========== 生成: 成功 0 个，失败 1 个，最新 0 个，跳过 0 个 ==========

 

**<span style="color:#e53333;">//
因为创建静态链接库的目录包含错误</span>**








