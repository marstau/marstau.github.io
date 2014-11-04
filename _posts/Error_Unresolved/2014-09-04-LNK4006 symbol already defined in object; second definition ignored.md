---
layout: post
title: LNK4006 symbol already defined in object; second definition ignored
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

<div
style="padding-bottom:0px;padding-left:0px;padding-right:0px;padding-top:0px;">

1\>LINK : warning LNK4075: 忽略“/INCREMENTAL”(由于“/FORCE”规范)

</div>

<div
style="padding-bottom:0px;padding-left:0px;padding-right:0px;padding-top:0px;">

1\>GRMA.obj :<span class="Apple-converted-space"> </span><span
style="color:red;">warning LNK4006</span>: "struct HWND\_\_ \* GhDlg"
(?GhDlg@@3PAUHWND\_\_@@A) 已在 ConnectDatabase.obj
中定义；已忽略第二个定义

</div>

<div
style="padding-bottom:0px;padding-left:0px;padding-right:0px;padding-top:0px;">

1\>GRMA.obj : warning LNK4006: "char \* szAppName" (?szAppName@@3PADA)
已在 ConnectDatabase.obj 中定义；已忽略第二个定义

</div>

<div
style="padding-bottom:0px;padding-left:0px;padding-right:0px;padding-top:0px;">

1\>GRMA.obj : warning LNK4006: "char \* szHeadName" (?szHeadName@@3PADA)
已在 ConnectDatabase.obj 中定义；已忽略第二个定义

</div>

<div
style="padding-bottom:0px;padding-left:0px;padding-right:0px;padding-top:0px;">

1\>E:\\Visual Studio 2010\\Projects\\Guest Room Management
App\\Debug\\Guest Room Management App.exe : warning LNK4088: 因 /FORCE
选项生成了映像；映像可能不能运行

</div>

<div
style="padding-bottom:0px;padding-left:0px;padding-right:0px;padding-top:0px;">

1\>Manifest:

</div>

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

\
 解决方案:\
<div
style="padding-bottom:0px;padding-left:0px;padding-right:0px;padding-top:0px;">

<span
style="line-height:23px;background-color:#ffffff;font-family:simsun;color:red;">如果用头文件定义全局变量的话，就只能在一个cpp里面包含该头文件，其他地方用extern引用 </span>\
 <span
style="text-align:left;line-height:23px;background-color:#ffffff;font-family:simsun;color:red;">否则每个包含该头文件的cpp生成的obj都会有一个定义</span>

</div>

</div>







