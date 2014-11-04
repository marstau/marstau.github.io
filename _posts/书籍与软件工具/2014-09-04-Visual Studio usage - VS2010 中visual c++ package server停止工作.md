---
layout: post
title: VS2010 中visual c++ package server停止工作
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---

 

    class C;
    class Abstract{
    public:
        virtual C *fun( C *c ) = 0;
    };
    class Derived1 : public Abstract{
    public:
        C *fun( C *c );
    };

    class Derived2 : public Abstract{
    public:
        void fun( C *c ); // error.
    };

将这段代码拷进VS2010中,就会出现这种情况

![](http://files.note.sdo.com/XbPJ4~kcxSs2wE0b000ay0)

 

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

问题事件名称: APPCRASH

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  应用程序名: VCPkgSrv.exe

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  应用程序版本: 10.0.30319.1

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  应用程序时间戳: 4ba1fde1

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  故障模块名称: cpfe.dll

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  故障模块版本: 16.0.30319.1

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  故障模块时间戳: 4ba217f7

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  异常代码: c0000005

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  异常偏移: 000ab7a6

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  OS 版本: 6.1.7601.2.1.0.256.48

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  区域设置 ID: 2052

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  其他信息 1: 0a9e

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  其他信息 2: 0a9e372d3b4ad19135b953a78882e789

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  其他信息 3: 0a9e

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

  其他信息 4: 0a9e372d3b4ad19135b953a78882e789

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

VCPkgSrv 是关于Visual Studio 2010 中IntelliSense。 可以从菜单栏中的<span
style="color:red;">工具 -\>选项-\>文本编辑-\>C/C++-》高级-\>IntelliSense-\>禁用IntelliSense。关闭此程序</span>。此外，也可以把问题提交到以下地址，以获得更多的支持：http://connect.microsoft.com/

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

 

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

这里是connect 上关于这个问题的一些链接：

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

1.
http://connect.microsoft.com/VisualStudio/feedback/details/637217/vcpkgsrv-exe-crashing

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

2.
http://connect.microsoft.com/VisualStudio/feedback/details/636817/vcpkgsrv-exe-crashes-periodically

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

3.
http://connect.microsoft.com/VisualStudio/feedback/details/633235/vcpkgsrv-crashing-all-the-time-intellisense-not-working

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

4.
http://connect.microsoft.com/VisualStudio/feedback/details/635679/vcpkgsrv-exe-constantly-crashing-precompiled-headers-involved。

</div>

<div
style="padding-bottom:0px;widows:2;text-transform:none;text-indent:0px;padding-left:0px;padding-right:0px;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;padding-top:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

5.
http://connect.microsoft.com/VisualStudio/feedback/details/502514/vcpkgsrv-exe-throwing-exceptions-on-browsing-project-files\
\

care:这个问题在VS2010旗舰版上无法根本解决的,也就是说只有MS更新编译器后才能根本解决这个问题,如果禁用了IntelliSense就禁用了那几个诸如错误报告和波形曲线很好用的功能...杯具!
而这个貌似在VS2008上没有的,可能是没找到,反正没看到...\

</div>


