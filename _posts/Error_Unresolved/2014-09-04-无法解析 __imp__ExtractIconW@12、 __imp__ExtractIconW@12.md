---
layout: post
title: 无法解析 __imp__ExtractIconW@12、 __imp__ExtractIconW@12
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

\<1\>DXUT.obj : error LNK2019: 无法解析的外部符号
\_\_imp\_\_CommandLineToArgvW@8，该符号在函数 "void \_\_cdecl
DXUTParseCommandLine(void)" (?DXUTParseCommandLine@@YAXXZ) 中被引用

1\>DXUT.obj : error LNK2019: 无法解析的外部符号
\_\_imp\_\_ExtractIconW@12，该符号在函数 "long \_\_cdecl
DXUTCreateWindow(wchar\_t const \*,struct HINSTANCE\_\_ \*,struct
HICON\_\_ \*,struct HMENU\_\_ \*,int,int)"
(?DXUTCreateWindow@@YAJPB\_WPAUHINSTANCE\_\_@@PAUHICON\_\_@@PAUHMENU\_\_@@HH@Z)
中被引用

1\>DXUTmisc.obj : error LNK2019: 无法解析的外部符号
\_\_imp\_\_ShellExecuteW@24，该符号在函数 "bool \_\_cdecl
DXUTReLaunchMediaCenter(void)" (?DXUTReLaunchMediaCenter@@YA\_NXZ)
中被引用

 

**<span
style="color:#e53333;">在[附加依赖项]中勾选[从父级或项目默认设置继承]选项</span>**








