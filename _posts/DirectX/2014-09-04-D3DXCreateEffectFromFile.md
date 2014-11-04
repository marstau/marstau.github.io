---
layout: post
title: D3DXCreateEffectFromFile
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

<span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">效果文件建失败，直接返回 E\_fail,路径尝试改成绝对的，还是一样。</span>\
 <span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"> 不但pEffect是0x0000,即获取不到值，</span>\
 <span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"> 连errors也为0x0000,也获取不到错误消息，而且输出框也不显示编译 错误，</span>\
 <span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"> 更何况，fx文件是肯定是没有问题的，因它在其它程序里都可以正确使用。</span>\
 <span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"> fx 里compile 也本来就vs\_2.0</span>

<span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span> 

<span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span> 

<span
style="widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;display:inline !important;font:14px/24px Helvetica, Tahoma, Arial, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#333333;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">
</span>

可能是因为新版本的SDK默认使用DX10的HLSL编辑器引擎的问题，如果是这种情况，只要在调用D3DXCreateEffectFromFile时的flag

 

参数里面加上D3DXSHADER\_USE\_LEGACY\_D3DX9\_31\_DLL这个值就可以了。

 

DX SDK的文档里面有说的，在D3DXSHADER Flags这个主题里面。

不过说的很隐晦，要两个地方结合起来看：

1）D3DXCreateEffectFromFile函数对Flags参数的描述里面说了这么一句：

The Direct3D 10 HLSL compiler is now the default

也就是说默认使用D3D10的HLSL编译器

2）D3DXSHADER Flags对D3DXSHADER\_USE\_LEGACY\_D3DX9\_31\_DLL的描述里面有这么一句：

Enable the use of the original Direct3D 9 HLSL compiler.

也就是说加入这个值以后就使用D3D9的HLSL编译器了。

 

然后errorBuffer就可以报错了.







