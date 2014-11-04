---
layout: post
title:  无法解析的外部符号 __imp__ExtractIconW@12
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1\>dxut.obj
: error LNK2019: 无法解析的外部符号<span
class="Apple-converted-space"> </span></span><__imp__ExtractIconW@12><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，该符号在函数
"long \_\_cdecl DXUTCreateWindow(wchar\_t const \*,struct
HINSTANCE\_\_ \*,struct HICON\_\_ \*,struct HMENU\_\_ \*,int,int)"
(</span><?DXUTCreateWindow@@YAJPB_WPAUHINSTANCE__@@PAUHICON__@@PAUHMENU__@@HH@Z><span
class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">)
中被引用</span>\
\
\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">solution:</span>\
 <span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">add</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:red;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
class="Apple-converted-space"> </span>shell32.lib</span>







