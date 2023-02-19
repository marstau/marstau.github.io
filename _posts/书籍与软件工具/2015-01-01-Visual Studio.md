---
layout: post
title: Visual Studio
category: 书籍与软件工具
tags: software
keywords: 
description: 
---

## Installation

#### Microsoft Visual Studio Ultimate 2012 旗舰版

密钥:YKCW6-BPFPF-BT8C9-7DCTH-QXGWC或YQ7PR-QTHDM-HCBCV-9GKGG-TB2TM

#### VS2013

密钥:BWG7X-J98B3-W34RT-33B3R-JVYW9

#### VS2012

密钥:YKCW6-BPFPF-BT8C9-7DCTH-QXGWC

## Visual Studio 2010

密钥:YCFHQ-9DWCY-DKV88-T2TMH-G7BHP

#### 项目环境目录：

![](http://files.note.sdo.com/XbPJ4~kkHSYG4M0os002Sx)

若出现无法打开自己编译的.lib文件或者.h文件的时候,便可通过增加库目录或包含目录解决

若只想多项目中某个项目生成.lib文件的时候,得修改

![](http://files.note.sdo.com/XbPJ4~kkHTpVM70yw002U0)

将其改成静态库(.lib)即可


#### VS2010工程详解：

项目结构(VS2010)

默认为：

OGRE - Debug

     - ipch

     - newProject

              - Debug

                newProject.vcxproj

                main.cpp

                newProject.vcxproj.filters

                newProject.vcxproj.user

       OGRE.sdf

       OGRE.sln

       OGRE.suo

       OGRE.opensdf

 [属性]-\>[配置属性]-\>[常规]-\>[输出目录] :
\$(SolutionDir)\$(Configuration)\\ // OGRE/Debug目录下

 [属性]-\>[配置属性]-\>[常规]-\>[中间目录] ：\$(Configuration)\\ //
OGRE/newProject/Debug目录下

 [属性]-\>[配置属性]-\>[调试]-\>[工作目录] ：\$(ProjectDir) //
OGRE/newProject目录下
 

我的工程目录为E:\\Visual Studio 2010\\marstau-ml-library\\MarstauLibrary：

\$(SolutionDir) : MarstauLibrary

\$(PlatformName) : Win32

\$(Configuration) : Debug or Release
eg : \$(SolutionDir)\$(PlatformName)\\bin.\$(Configuration)\\ 为MarstauLibrary\\Win32\\bin.Debug\\目录



#### DirectX 配置问题

首先DirectX要下载最新版,然后设置好[包含目录]和库文件就OK了

```
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
```

否则可能出现如下问题：

```
Mantis.obj : error LNK2001: unresolved external symbol __imp__DispatchMessageA@4
Mantis.obj : error LNK2001: unresolved external symbol __imp__TranslateMessage@4
Mantis.obj : error LNK2001: unresolved external symbol __imp__GetMessageA@16
Mantis.obj : error LNK2001: unresolved external symbol __imp__LoadStringA@16
error LNK2019: 无法解析的外部符号 <_Direct3DCreate9@4> 
```


#### visual c++ package server停止工作


```
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
```

将这段代码拷进VS2010中,就会出现这种情况

![](http://files.note.sdo.com/XbPJ4~kcxSs2wE0b000ay0)

```
问题事件名称: APPCRASH

  应用程序名: VCPkgSrv.exe

  应用程序版本: 10.0.30319.1

  应用程序时间戳: 4ba1fde1

  故障模块名称: cpfe.dll

  故障模块版本: 16.0.30319.1

  故障模块时间戳: 4ba217f7

  异常代码: c0000005

  异常偏移: 000ab7a6

  OS 版本: 6.1.7601.2.1.0.256.48

  区域设置 ID: 2052

  其他信息 1: 0a9e

  其他信息 2: 0a9e372d3b4ad19135b953a78882e789

  其他信息 3: 0a9e

  其他信息 4: 0a9e372d3b4ad19135b953a78882e789
```

VCPkgSrv 是关于Visual Studio 2010 中IntelliSense。 可以从菜单栏中的`工具 ->选项->文本编辑->C/C++-》高级->IntelliSense->禁用IntelliSense。关闭此程序。`此外，也可以把问题提交到以下地址，以获得更多的支持：<http://connect.microsoft.com>



这里是connect 上关于这个问题的一些链接：

<http://connect.microsoft.com/VisualStudio/feedback/details/637217/vcpkgsrv-exe-crashing>

<http://connect.microsoft.com/VisualStudio/feedback/details/636817/vcpkgsrv-exe-crashes-periodically>

<http://connect.microsoft.com/VisualStudio/feedback/details/633235/vcpkgsrv-crashing-all-the-time-intellisense-not-working>

<http://connect.microsoft.com/VisualStudio/feedback/details/635679/vcpkgsrv-exe-constantly-crashing-precompiled-headers-involved。>

<http://connect.microsoft.com/VisualStudio/feedback/details/502514/vcpkgsrv-exe-throwing-exceptions-on-browsing-project-files>

care:这个问题在VS2010旗舰版上无法根本解决的,也就是说只有MS更新编译器后才能根本解决这个问题,如果禁用了IntelliSense就禁用了那几个诸如错误报告和波形曲线很好用的功能...杯具! 而这个貌似在VS2008上没有的,可能是没找到,反正没看到...


#### 生成文件的用途及区别

##### .APS
存放二进制资源的中间文件，VC把当前资源文件转换成二进制格式，并存放在APS文件中，以加快资源装载速度。资源辅助文件。
##### .BMP
位图资源文件。
##### .BSC
浏览信息文件，由浏览信息维护工具（BSCMAKE）从原始浏览信息文件（.SBR）中生成，BSC文件可以用来在源代码编辑窗口中进行快速定位。用于浏览项目信息的，如果用source
brower的话就必须有这个文件。可以在project options里去掉Generate Browse Info File 这样可以加快编译进度。
##### .C
用C语言编写的源代码文件。
##### .CLW
ClassWizard生成的用来存放类信息的文件。classwizard信息文件，ini文件的格式。
##### .CNT
用来定义帮助文件中“Contents”的结构。
##### .CPP或.CXX
用C++语言编写的源代码文件。
##### .CUR
光标资源文件。
##### .DEF
模块定义文件，供生成动态链接库时使用。
##### .DLG
定义对话框资源的独立文件。这种文件对于VC工程来说并非必需，因为VC一般把对话框资源放在.RC资源定义文件中。
##### .DSP
VC开发环境生成的工程文件，VC4及以前版本使用MAK文件来定义工程。项目文件，文本格式。
##### .DSW
VC开发环境生成的WorkSpace文件，用来把多个工程组织到一个WorkSpace中。工作区文件，与.dsp差不多。
##### .EXP
由LIB工具从DEF文件生成的输出文件，其中包含了函数和数据项目的输出信息，LINK工具将使用EXP文件来创建动态链接库。只有在编译DLL时才会生成，记录了DLL文件中的一些信息.
##### .H、.HPP或.HXX
用C/C++语言编写的头文件，通常用来定义数据类型，声明变量、函数、结构和类。
##### .HLP
Windows帮助文件。
##### .HM
在Help工程中，该文件定义了帮助文件与对话框、菜单或其它资源之间ID值的对应关系。
##### .HPJ
由Help Workshop生成的Help工程文件，用来控制Help文件的生成过程。
##### .HPG
生成帮助的文件的工程。
##### .ICO
图标资源文件。
##### .ILK
连接过程中生成的一种中间文件，只供LINK工具使用。
##### .INI
配置文件。
##### .LIB
库文件，LINK工具将使用它来连接各种输入库，以便最终生成EXE文件。
##### .LIC
用户许可证书文件，使用某些ActiveX控件时需要该文件。
##### .MAK
即MAKE文件，VC4及以前版本使用的工程文件，用来指定如何建立一个工程，VC6把MAK文件转换成DSP文件来处理。
##### .MAP
由LINK工具生成的一种文本文件，其中包含有被连接的程序的某些信息，例如程序中的组信息和公共符号信息等。执行文件的映像信息记录文件。
##### .MDP
旧版本的项目文件，相当于.dsp
##### .NCB
NCB是“No Compile
Browser”的缩写，其中存放了供ClassView、WizardBar和Component
Gallery使用的信息，由VC开发环境自动生成。无编译浏览文件。当自动完成功能出问题时可以删除此文件。编译工程后会自动生成。
##### .OBJ
由编译器或汇编工具生成的目标文件，是模块的二进制中间文件。
##### .ODL
用对象描述语言编写的源代码文件，VC用它来生成TLB文件。
##### .OLB
带有类型库资源的一种特殊的动态链接库，也叫对象库文件。
##### .OPT
VC开发环境自动生成的用来存放WorkSpace中各种选项的文件。工程关于开发环境的参数文件。如工具条位置信息等。
##### .PBI、.PBO和.PBT
由VC的性能分析工具PROFILE生成并使用的三种文件。
##### .PCH
预编译头文件，比较大，由编译器在建立工程时自动生成，其中存放有工程中已经编译的部分代码，在以后建立工程时不再重新编译这些代码，以便加快整个编译过程的速度。
##### .PDB
程序数据库文件，在建立工程时自动生成，其中存放程序的各种信息，用来加快调试过程的速度。记录了程序有关的一些数据和调试信息。
##### .PLG
编译信息文件，编译时的error和warning信息文件。
##### .RC
资源定义文件。
##### .RC2
资源定义文件，供一些特殊情况下使用。
##### .REG
注册表信息文件。
##### .RES
二进制资源文件，资源编译器编译资源定义文件后即生成RES文件。
##### .RTF
Rich Text
Format（丰富文本格式）文档，可由Word或写字板来创建，常被用来生成Help文件。
##### .SBR
VC编译器为每个OBJ文件生成的原始浏览信息文件，浏览信息维护工具（BSCMAKE）将利用SBR文件来生成BSC文件。
##### .TLB
OLE库文件，其中存放了OLE自动化对象的数据类型、模块和接口定义，自动化服务器通过TLB文件就能了解自动化对象的使用方法。
##### .WAV
声音资源文件。
