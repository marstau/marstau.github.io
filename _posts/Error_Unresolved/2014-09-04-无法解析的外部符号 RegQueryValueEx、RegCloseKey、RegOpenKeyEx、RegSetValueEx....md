---
layout: post
title: 无法解析的外部符号 RegQueryValueEx、RegCloseKey、RegOpenKeyEx、RegSetValueEx...
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

<span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>------
已启动生成: 项目: WinTest, 配置: Debug Win32 ------</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>生成启动时间为
2011/10/5 12:35:59。</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>InitializeBuildStatus:</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\> 
正在对“Debug\\WinTest.unsuccessfulbuild”执行 Touch 任务。</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>ClCompile:</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\> 
所有输出均为最新。</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>ResourceCompile:</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\> 
所有输出均为最新。</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>ManifestResourceCompile:</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\> 
所有输出均为最新。</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>d3dUtility.obj
: error LNK2005: "long \_\_stdcall d3d::WndProc(struct
HWND\_\_ \*,unsigned int,unsigned int,long)"
(</span><?WndProc@d3d@@YGJPAUHWND__@@IIJ@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)
已经在 cfont.obj 中定义</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>cfont.obj
: error LNK2019: 无法解析的外部符号 "bool \_\_cdecl d3d::InitD3D(struct
HINSTANCE\_\_ \*,int,int,bool,enum \_D3DDEVTYPE,struct
IDirect3DDevice9 \* \*)"
(</span><?InitD3D@d3d@@YA_NPAUHINSTANCE__@@HH_NW4_D3DDEVTYPE@@PAPAUIDirect3DDevice9@@@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)，该符号在函数</span><_WinMain@16><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
class="Apple-converted-space"> </span>中被引用</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>dxutil.obj
: error LNK2019: 无法解析的外部符号<span
class="Apple-converted-space"> </span></span><__imp__RegCloseKey@4><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，该符号在函数
"long \_\_cdecl DXUtil\_GetDXSDKMediaPathCch(wchar\_t \*,int)"
(</span><?DXUtil_GetDXSDKMediaPathCch@@YAJPA_WH@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)
中被引用</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>dxutil.obj
: error LNK2019: 无法解析的外部符号<span
class="Apple-converted-space"> </span></span><__imp__RegQueryValueExW@24><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，该符号在函数
"long \_\_cdecl DXUtil\_GetDXSDKMediaPathCch(wchar\_t \*,int)"
(</span><?DXUtil_GetDXSDKMediaPathCch@@YAJPA_WH@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)
中被引用</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>dxutil.obj
: error LNK2019: 无法解析的外部符号<span
class="Apple-converted-space"> </span></span><__imp__RegOpenKeyExW@20><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，该符号在函数
"long \_\_cdecl DXUtil\_GetDXSDKMediaPathCch(wchar\_t \*,int)"
(</span><?DXUtil_GetDXSDKMediaPathCch@@YAJPA_WH@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)
中被引用</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>dxutil.obj
: error LNK2019: 无法解析的外部符号<span
class="Apple-converted-space"> </span></span><__imp__RegSetValueExW@24><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，该符号在函数
"long \_\_cdecl DXUtil\_WriteStringRegKey(struct
HKEY\_\_ \*,wchar\_t \*,wchar\_t \*)"
(</span><?DXUtil_WriteStringRegKey@@YAJPAUHKEY__@@PA_W1@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)
中被引用</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>E:\\Visual
Studio 2010\\Projects\\WinTest\\Debug\\WinTest.exe : fatal error
LNK1120: 5 个无法解析的外部命令</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\></span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>生成失败。</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\></span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>已用时间
00:00:01.19</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">==========
生成: 成功 0 个，失败 1 个，最新 0 个，跳过 0 个 ==========</span>\
\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:red;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">solution：未包含AdvAPI32.lib\
 </span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>d3dUtility.obj
: error LNK2005: "long \_\_stdcall d3d::WndProc(struct
HWND\_\_ \*,unsigned int,unsigned int,long)"
(</span><?WndProc@d3d@@YGJPAUHWND__@@IIJ@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)
已经在 cfont.obj 中定义</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>cfont.obj
: error LNK2019: 无法解析的外部符号 "bool \_\_cdecl d3d::InitD3D(struct
HINSTANCE\_\_ \*,int,int,bool,enum \_D3DDEVTYPE,struct
IDirect3DDevice9 \* \*)"
(</span><?InitD3D@d3d@@YA_NPAUHINSTANCE__@@HH_NW4_D3DDEVTYPE@@PAPAUIDirect3DDevice9@@@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)，该符号在函数</span><_WinMain@16><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
class="Apple-converted-space"> </span>中被引用</span>

<span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span> 

<span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">
</span>

1\>------ 已启动生成: 项目: GameProject, 配置: Debug Win32 ------

1\>生成启动时间为 2012-03-25 16:06:49。

1\>InitializeBuildStatus:

1\> 正在对“Debug\\GameProject.unsuccessfulbuild”执行 Touch 任务。

1\>ClCompile:

1\> 所有输出均为最新。

1\>ManifestResourceCompile:

1\> 所有输出均为最新。

1\>main.obj : error LNK2019: 无法解析的外部符号 "bool \_\_cdecl
CreateDMSound(class CSoundSystemInterface \* \*)"
(?CreateDMSound@@YA\_NPAPAVCSoundSystemInterface@@@Z)，该符号在函数
"bool \_\_cdecl InitializeEngine(void)" (?InitializeEngine@@YA\_NXZ)
中被引用

1\>E:\\Visual Studio 2010\\Projects\\GameProject\\Debug\\GameProject.exe
: fatal error LNK1120: 1 个无法解析的外部命令

1\>

1\>生成失败。

1\>

1\>已用时间 00:00:00.98

========== 生成: 成功 0 个，失败 1 个，最新 1 个，跳过 0 个 ==========

 

<span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:red;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">这几个错误有点莫名其妙：将问题函数声明重新敲一遍...不能复制的</span>








