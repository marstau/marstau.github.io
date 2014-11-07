---
layout: post
title: VS2010 下DirectX 配置问题
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---

<span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">首先DirectX要下载最新版,然后设置好[包含目录]和库文件就OK了</span>

comctl32.lib

version.lib

d3d9.lib

d3dx9.lib

dxerr.lib

winmm.lib

Gdi32.lib

user32.lib

AdvAPI32.lib

dinput8.lib

dxguid.lib

ole32.lib

\
\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">否则可能出现如下问题：</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Mantis.obj
: error LNK2001: unresolved external symbol
\_\_imp\_\_DispatchMessageA@4</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Mantis.obj
: error LNK2001: unresolved external symbol
\_\_imp\_\_TranslateMessage@4</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Mantis.obj
: error LNK2001: unresolved external symbol
\_\_imp\_\_GetMessageA@16</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Mantis.obj
: error LNK2001: unresolved external symbol
\_\_imp\_\_LoadStringA@16</span>\
\
\
\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">error
LNK2019: 无法解析的外部符号<span
class="Apple-converted-space"> </span></span><_Direct3DCreate9@4><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
class="Apple-converted-space"> </span></span>\









