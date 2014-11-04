---
layout: post
title: Effect Framework
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

Come From : <http://blog.sina.com.cn/s/blog_5349a6e70100i14y.html>

**<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"></span>** 

**<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">摘要</span>**

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">本文简要介绍了在DirectX
9 SDK中提供的Effect Framework支持，以及DirectX FX文件结构和Microsoft
Hight Level Shading Language的基本知识。本文假定读者对DirectX
Graphics有一定了解，并正在学习DirectX Effect
Framework。希望能够与各位读者共同探讨、切磋。</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">**简介**</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">Effect的起源</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">在计算机3维场景中，物体表面的材质代表了其光学特性。最简单的材质可以表现为Diffuse颜色，Specular颜色，Emissive颜色等信息的集合；而为了表现物体表面的细节，可以在材质中加入一张纹理——这些就构成了最基本的材质信息。在以前的Direct3D程序中，这些信息可以直接传送给设备，由设备自动根据它们来计算物体表面的光学效果。但是，仅仅有这些基本的材质信息，已经不足以满足游戏制作者的要求和游戏玩家的要求了——他们希望场景中的材质更加复杂，具有更多的细节，更加逼真。</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">在Direct3D中，除了材质的概念，还存在一个渲染状态（Render
State）的概念。在Direct3D
Device中存在很多的渲染状态，它们可以在Direct3D进行渲染时控制渲染的流程和效果，从而实现某些带有特效的材质。程序员可以通过IDirect3DDevice\*::SetRenderState()方法来设置这些状态。所有的渲染状态都是一些特定的数值。对状态的设置可以通过硬编码完成，即在程序中调用SetRenderState()方法，将设置什么样的状态“写死”在程序里，但是这样做的缺点就是太不灵活了——如果想要实现一种新的渲染状态，就需要修改程序代码。所以更好的一种方法是将为了实现某一种特效材质的一些渲染状态值记录到一个“效果文件”中，通过在程序运行时读取该文件，从中分析出这些值，并将它们作为参数调用SetRenderState()。这样，要想实现一种新的特效，只需修改“效果文件”而不用更改代码。</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">Direct3D
SDK是通过Effect
Framework来支持这种机制的。而前面所述的“效果文件”在Direct3D中是以\*.fx文件存在的。在fx文件中保存了为实现某一特效的渲染状态，包括状态名称和它们的对应值。所以在9.0以前版本的DirectX中就已经有Effect
Framework和FX文件了，早期的Effect
Framework仅仅是为了实现对渲染状态进行控制。但是随着计算机显示硬件技术的发展，图形处理单元（GPU）正在重复CPU所走过的路——新一代的GPU已经具有了可编程特性，程序员可以通过对GPU编写一段程序来控制其渲染的输出效果。这种程序一般称为Shader程序。目前的Shader程序分成两种，Vertex
Shader和Pixel Shader。Vertex
Shader主要用于对3维网格模型的每一个顶点进行处理，而Pixel
Shader主要用于对要绘制到屏幕上的每一个象素进行处理。通过Shader，程序员可以制作出相当丰富的实时渲染效果。</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">同CPU一样，对GPU编程也是借助一定的编程语言来进行的。</span><span
class="Apple-converted-space"> </span><span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">在DirectX
8中，对GPU的编程是通过一种类似于汇编的语言进行的。而在DirectX
9中，使用了一种类似于C语言的高级语言——Microsoft High Level Shading
Language (HLSL) 。</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">无论使用什么语言对GPU编程，都需要把编译好的Shader程序输送到显卡去。Direct3D
Device可以通过SetVertexShader()和SetPixelShader()来向显卡输送Shader程序。然而，由于Shader和材质具有十分紧密的关系——一般来说，一个Shader就是为了实现一种特殊的材质——最好是能够将Shader程序与材质进行整合。所以，在DirectX
8和DirectX 9中，原来的Effect
Framework发生了扩充——在原来的基础上加入了对Shader程序的支持。程序员可以把Vertex
Shader和Pixel Shader程序以函数 的方式直接书写在FX文件中。</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> .FX文件</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">FX文件中的内容大致可以分成几部分：</span>

-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">预编译标志</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">变量表</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">结构定义</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">函数</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">Technique</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">预编译标志：预编译标志包括</span>

-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#define</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#elif</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#else</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#endif</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#error</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#if</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#ifdef</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#ifndef</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#include</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#line</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#pragma</span>
-   <span
    style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#undef</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">其中最常用到的是\#include和\#define，同C语言中的意义很相似：用\#include可以在一个FX文件中引入另外一个或多个文件。\#define可以定义FX文件中的宏替换。例如：</span>

+--------------------------------------------------------------------------+
| <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">\#include                                                            |
| "helper\_Funcs.fx"</span></span><span                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">    <span                                                            |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//引入一个名为hel |
| per\_funcs.fx的fx文件</span>\                                            |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">\#include   |
| "public\_variables.fh</span>"<span                                       |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//引入一个名为pub |
| lic\_variables.fh的文件</span>\                                          |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">\#define    |
| MATRICES\_COUNT 25</span>     <span                                      |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//定义宏MATRIC |
| ES\_COUNT为25</span>\                                                    |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">\#define    |
| VSHADER VShader\_2\_0</span>   <span                                     |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//定义宏VSHADE |
| R为VShader\_2\_0</span></span>                                           |
+--------------------------------------------------------------------------+

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">\#include带来的好处和C中也是一样的－您可以在一个头文件中定义一些公有变量、函数等，在其他文件中引用它们－就不用写很多遍了。例如：</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">文件public.fh:</span>

+--------------------------------------------------------------------------+
| <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">mat4x4</span></span><span                                            |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">matWorldViewProj;<span                                               |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//          |
| 4x4世界－视－投影变换矩阵</span>\                                        |
|  </span><span                                                            |
| style="line-height:18px;word-wrap:normal;word-break:normal;"><span       |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">float3</span></span><span                                            |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">lightPosisiton;  <span                                               |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//          |
| 三维光源位置向量</span>\                                                 |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">float4</spa |
| n><span                                                                  |
| class="Apple-converted-space"> </span>lightColor;     <span              |
| style="line-height:18px;word-wrap:normal;word-break:normal;"> <span      |
| class="Apple-converted-space"> </span>// 光源的颜色</span>\              |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">float</span |
| ><span                                                                   |
| class="Apple-converted-space"> </span>time;             <span            |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//          |
| 当前时间</span></span>                                                   |
+--------------------------------------------------------------------------+

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">//定义一个名为VS\_OUTPUT的结构。关于结构体定义，下文中会有介绍\
 </span>

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">struct</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">VS\_INPUT\
   {\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float4</span><span class="Apple-converted-space"> </span>LocalPos : POSITION;\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float3</span><span class="Apple-converted-space"> </span>Normal : NORMAL;\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float4</span><span class="Apple-converted-space"> </span>Color : COLOR; \
       <span style="line-height:18px;word-wrap:normal;word-break:normal;">float2</span><span class="Apple-converted-space"> </span>Texcoord : TEXCOORD0;\
   };</span>
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">struct VS\_OUTPUT</span></span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">\
   {\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float4</span><span class="Apple-converted-space"> </span>WorldPos : POSITION;\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float4</span><span class="Apple-converted-space"> </span>Color : COLOR;\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float2</span><span class="Apple-converted-space"> </span>Texcoord : TEXCOORD0;\
   };</span>
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">//定义一个名为CaculateWorldPosition的函数。关于函数定义，下文中会有介绍\
 </span>

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">float3</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">CaculateWorldPosition(<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float4</span><span class="Apple-converted-space"> </span>LocalPos )\
   {\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">return</span><span class="Apple-converted-space"> </span>mul( LocalPos, matWorldViewProj);\
   }</span>
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">这样，当我们在另外一个文件中include这个头文件时，上面所有的定义都可以直接使用了。</span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">文件client.fx:</span>

+--------------------------------------------------------------------------+
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">\#include                                                            |
| "public.fh"</span>                                                       |
|                                                                          |
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">\                                                                    |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">VS\_OUTPUT< |
| /span><span                                                              |
| class="Apple-converted-space"> </span>VS\_main( VS\_INPUT In )<span      |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//          |
| 可以直接使用结构体定义VS\_OUTPUT和VS\_INPUT</span>\                      |
|  {\                                                                      |
|     <span class="Apple-converted-space"> </span>VS\_OUTPUT Out = 0;\     |
|     <span class="Apple-converted-space"> </span>Out.WorldPos =           |
| CaculateWorldPosition( In.LocalPos );<span                               |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//          |
| 可以直接使用函数</span>\                                                 |
|     <span class="Apple-converted-space"> </span>Out.Color = In.Color;\   |
|     <span class="Apple-converted-space"> </span>Out.Texcoord =           |
| In.Texcoord;\                                                            |
|  }</span>                                                                |
+--------------------------------------------------------------------------+

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">这样不仅可以复用代码，还可以使变量名、结构体、函数名的定义统一。</span>

而\#define不仅仅可以使某些常量具有比较有意义的名称，通过与\#ifdef，\#ifndef,
\#else, \#endif等结合使用，还可以用来根据一些配置控制编译过程。

变量表

每个FX文件都可以有若干参数变量，通过Effect
Framework可以在程序中识别出这些参数的类型、名称和用途，这样就可以将程序中的一些参数输送到Effect中去，从而更加灵活的控制效果。参数的类型很多，可以是int,
float, matrix, texture等等。例如：

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">matrix</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">matWorld;    <span style="line-height:18px;word-wrap:normal;word-break:normal;">//定义一个名为matWorld的矩阵类型参数变量</span>\
   <span style="line-height:18px;word-wrap:normal;word-break:normal;">float</span><span class="Apple-converted-space"> </span>time;         <span style="line-height:18px;word-wrap:normal;word-break:normal;">//定义一个名为time的浮点类型参数变量</span>\
   <span style="line-height:18px;word-wrap:normal;word-break:normal;">texture</span><span class="Apple-converted-space"> </span>texDiffuse;<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//定义一个名为texDiffuse的纹理类型参数变量</span></span>
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

另外，每个变量还有前缀修饰符、Semantic、Annotation等，限于篇幅，在这里不再赘述，具体的介绍请参考DirectX
C++帮助文档的DirectX Graphics \> Reference \> HLSL Shader Reference \>
Variable Declaration Syntax条目。

结构定义

在FX文件中可以定义结构体，这些结构体一般用于Shader函数的参数和返回值。结构体的定义与C语言方式及其类似，例如：

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">struct</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">VS\_OUTPUT<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//结构名称</span>\
   {\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float4</span><span class="Apple-converted-space"> </span>Pos : POSITION;<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//成员变量。</span>\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float4</span><span class="Apple-converted-space"> </span>Color : COLOR;\
      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">float2</span><span class="Apple-converted-space"> </span>Texcoord : TEXCOORD0;\
   };</span>
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

上面每个成员变量后面的标识符是该变量的semantic，HLSL编译器根据这个标识符来确定该变量的用处。不一定非得是结构体成员变量才有semantic，一般来说Shader的输入输出参数变量都可以有semantic。

函数

函数部分是在Effect Framework加入了对Vertex<span
class="Apple-converted-space"> </span>Shader和Pixel
Shader的扩充后才加入到FX文件中的。FX文件中的函数的内容可以用汇编形式书写，也可以用HLSL编写。目前一般都是使用HLSL。用这种语言书写的函数与C语言函数十分类似，可以说，只要学过C语言，书写Shader函数就绰绰有余了。在同一个fx文件中可以定义很多函数，在函数中也可以互相调用，但是最终Shader程序的入口将在fx文件的Technique部分中指定。对于哪个函数是Vertex
shader函数，哪个是Pixel
shader函数，也是在Technique中指定的。关于Technique，将在下文中介绍。例子：

+--------------------------------------------------------------------------+
| <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">float4</span></span><span                                            |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">CalcDiffuseColor(                                                    |
| float3 Normal )\                                                         |
|  {\                                                                      |
|     <span class="Apple-converted-space"> </span><span                    |
| style="line-height:18px;word-wrap:normal;word-break:normal;">float4</spa |
| n><span                                                                  |
| class="Apple-converted-space"> </span>Color; ...<span                    |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//用于实现该函数功能 |
| 的多条语句</span>\                                                       |
|     <span class="Apple-converted-space"> </span><span                    |
| style="line-height:18px;word-wrap:normal;word-break:normal;">return</spa |
| n><span                                                                  |
| class="Apple-converted-space"> </span>Color;\                            |
|  }</span>                                                                |
|                                                                          |
| <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">VS\_OUTPUT</span></span><span                                        |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">Vertex\_Shader(<span                                                 |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">float4</spa |
| n><span                                                                  |
| class="Apple-converted-space"> </span>InPos : POSITION,\                 |
|                          <span                                           |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">float3</spa |
| n><span                                                                  |
| class="Apple-converted-space"> </span>InNor : NORMAL, \                  |
|                          <span                                           |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">float3</spa |
| n><span                                                                  |
| class="Apple-converted-space"> </span>InTexcoord : TEXCOORD )\           |
|  {\                                                                      |
|     <span class="Apple-converted-space"> </span><span                    |
| style="line-height:18px;word-wrap:normal;word-break:normal;">VS\_OUTPUT< |
| /span><span                                                              |
| class="Apple-converted-space"> </span>Out; ...<span                      |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//用于实现该函数功能 |
| 的多条语句</span>\                                                       |
|     <span class="Apple-converted-space"> </span>Out.Color =              |
| CalcDiffuseColor(InNor);<span                                            |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//函数调用</spa |
| n>\                                                                      |
|     <span class="Apple-converted-space"> </span><span                    |
| style="line-height:18px;word-wrap:normal;word-break:normal;">return</spa |
| n><span                                                                  |
| class="Apple-converted-space"> </span>Out;\                              |
|  }</span>                                                                |
+--------------------------------------------------------------------------+

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

正如上文中所说，Shader程序分为两种：Vertex shader和Pixel
shader。在fx函数中就有两种相应的函数：Vertex shader函数和Pixel
Shader函数。Vertex
shader函数的输入参数是网格模型中的每一个顶点数据，其输出是经过该函数特殊处理的顶点数据；而Pixel
Shader函数的输入，则是经过硬件光栅化过程后经过插值的Vertex
shader输出结果。至于Pixel
shader的输出，一般就是经过该函数计算得到的一个颜色值，即要画到后备缓冲中一个象素上的颜色值。但是这个“颜色值”有时并不一定代表颜色。而且对于支持多RenderTarget的硬件，Pixel
shader还可以有多个输出，分别对应不同的RenderTarget。

technique

technique是FX文件的主体，是真正设置各种渲染状态的地方，也是指定所使用的Shader程序入口的地方。在理解Technique前首先要理解Pass的概念。Pass是Technique的组成部分，一个Pass就代表了绘制时的一遍。通常为了达到一种效果，仅仅绘制一遍网格模型是不够的，需要向framebuffer中多次绘制，并利用设置渲染状态中的BlendState进行Alpha混合。这就是经常提到的“Muli-pass
Rendering”。但是随着硬件越来越强大，Shader程序的功能越来越强，目前的趋势是所有的特效材质都将可以用越来越少个Pass来完成。一个technique中，可以存在一个或多个Pass，但是至少要有一个Pass时该technique才会起实际作用。当存在多个pass时，默认情况下在渲染时将会按照pass在文件中的前后顺序作为渲染时的前后顺序。technique和Pass中的内容都是以大括号括起来。

technique的例子：

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">technique</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">Tec\_Shader\_1\_X<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//定义一个名为Tec\_Shader\_1\_X的technique</span>\
   {\
      <span class="Apple-converted-space"> </span>pass P0<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//一个名为P0的pass</span>\
      <span class="Apple-converted-space"> </span>{\
          <span class="Apple-converted-space"> </span>VertexShader = compile vs\_1\_1 Vertex\_Shader();<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//设置Vertex Shader程序入口函数</span>\
          <span class="Apple-converted-space"> </span>PixelShader = compile ps\_1\_1 Pixel\_Shader();  <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//设置Pixel Shader程序入口函数</span>\
          <span class="Apple-converted-space"> </span>AlphaBlendEnable= true;                       <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//设置渲染状态       </span>\
          <span class="Apple-converted-space"> </span>SrcBlend = SrcAlpha;  \
          <span class="Apple-converted-space"> </span>DestBlend = InvSrcAlpha; \
          <span class="Apple-converted-space"> </span>...<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//其他设置</span>\
      <span class="Apple-converted-space"> </span>}\
      <span class="Apple-converted-space"> </span>pass P1<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//一个名为P1的pass</span>\
      <span class="Apple-converted-space"> </span>{\
          <span class="Apple-converted-space"> </span>...\
      <span class="Apple-converted-space"> </span>}\
   }</span>
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;">****ID3DXEffect接口****</span>

上面介绍了很多fx文件相关内容，但是在程序中如何读取和分析这些fx文件呢？在程序中对于读取fx文件，控制渲染状态、设置Shader程序等工作都是通过D3DX库中的ID3DXEffect接口来实现的。ID3DXEffect接口提供了大量的方法，基本上分为几个方面：

-   获得Effect参数变量信息
-   设置Effect参数变量
-   获得technique信息
-   设置当前使用的technique
-   开始和结束使用当前的technique
-   执行一个pass（渲染绘制遍）

ID3DXEffect接口的创建：
通过D3DX库中的D3DXCreateEffectFromFile()函数，可以根据一个指定的文件的内容来创建一个ID3DXEffect接口。在该函数执行成功后，所创建的接口中就包含了文件里所对应的
所有内容，包括参数变量表、Shader程序、technique和pass等。

ID3DXEffect接口的使用：
通过该接口的方法可以获得FX文件中的所有信息，并设置参数变量和当前的technique。所有的参数变量、technique、pass、shader等等都有自己的名称，根据这些名称，通过调用ID3DXEffect::GetParameterByName()、ID3DXEffect::GetTechniqueByName()和ID3DXEffect::GetPassByName()等方法就可以获得这些对象的句柄，从而在调用
ID3DXEFFECT::Set\*\*\*()进行设置时使用句柄而不是字符串进行索引来提高效率。

通过ID3DXEffect::GetParameterDesc()、ID3DXEffect::GetTechniqueDesc()和GetPassDecs等方
法可以获得关于指定对象的所有细节描述信息。
D3DX库中定义了一个D3DXPARAMETER\_DESC结构来专门表示参数的类型。通过ID3DXEffect::GetParameterDesc()方法，可以为一个参数获得这样一个结构的数据。

\

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">typedef struct</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">\_D3DXPARAMETER\_DESC\
   {\
      <span class="Apple-converted-space"> </span>LPCSTR Name;              <span class="Apple-converted-space"> </span>//参数变量名\
      <span class="Apple-converted-space"> </span>LPCSTR Semantic;          <span class="Apple-converted-space"> </span>//参数变量的Semantic\
      <span class="Apple-converted-space"> </span>D3DXPARAMETER\_CLASS Class; //参数变量的类别，可以是标量、矢量、矩阵、对象和结构\
      <span class="Apple-converted-space"> </span>D3DXPARAMETER\_TYPE Type;  <span class="Apple-converted-space"> </span>//参数变量的类型\
      <span class="Apple-converted-space"> </span>UINT Rows;                 //数组型参数的行数\
      <span class="Apple-converted-space"> </span>UINT Columns;             <span class="Apple-converted-space"> </span>//数组型参数的列数\
      <span class="Apple-converted-space"> </span>UINT Elements;            <span class="Apple-converted-space"> </span>//数组中的元素个数\
      <span class="Apple-converted-space"> </span>UINT Annotations;         <span class="Apple-converted-space"> </span>//参数变量的Annotation个数\
      <span class="Apple-converted-space"> </span>UINT StructMembers;       <span class="Apple-converted-space"> </span>//结构型参数变量成员的个数\
      <span class="Apple-converted-space"> </span>DWORD Flags;              <span class="Apple-converted-space"> </span>//参数属性\
      <span class="Apple-converted-space"> </span>UINT Bytes;               <span class="Apple-converted-space"> </span>//参数大小，以字节记\
   } D3DXPARAMETER\_DESC;</span>
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

其中的参数类型可以有下列几种：

\

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">typedef</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">enum \_D3DXPARAMETER\_TYPE\
   {\
      <span class="Apple-converted-space"> </span>D3DXPT\_VOID, //Void型指针\
      <span class="Apple-converted-space"> </span>D3DXPT\_BOOL, //Bool型\
      <span class="Apple-converted-space"> </span>D3DXPT\_INT, //整型\
      <span class="Apple-converted-space"> </span>D3DXPT\_FLOAT, //浮点型\
      <span class="Apple-converted-space"> </span>D3DXPT\_STRING, //字符串\
      <span class="Apple-converted-space"> </span>D3DXPT\_TEXTURE, //纹理\
      <span class="Apple-converted-space"> </span>D3DXPT\_TEXTURE1D, //一维纹理\
      <span class="Apple-converted-space"> </span>D3DXPT\_TEXTURE2D, //二维纹理\
      <span class="Apple-converted-space"> </span>D3DXPT\_TEXTURE3D, //三维纹理\
      <span class="Apple-converted-space"> </span>D3DXPT\_TEXTURECUBE, //立方体环境纹理\
      <span class="Apple-converted-space"> </span>D3DXPT\_SAMPLER, //纹理取样器\
      <span class="Apple-converted-space"> </span>D3DXPT\_SAMPLER1D, //一维纹理取样器\
      <span class="Apple-converted-space"> </span>D3DXPT\_SAMPLER2D, //二维纹理取样器\
      <span class="Apple-converted-space"> </span>D3DXPT\_SAMPLER3D, //三维纹理取样器\
      <span class="Apple-converted-space"> </span>D3DXPT\_SAMPLERCUBE, //立方体环境纹理取样器\
      <span class="Apple-converted-space"> </span>D3DXPT\_PIXELSHADER, //Pixel Shader程序\
      <span class="Apple-converted-space"> </span>D3DXPT\_VERTEXSHADER, //Vertex Shader程序\
      <span class="Apple-converted-space"> </span>D3DXPT\_PIXELFRAGMENT, //Pixel Shader片断\
      <span class="Apple-converted-space"> </span>D3DXPT\_VERTEXFRAGMENT, //Vertex Shader片断\
      <span class="Apple-converted-space"> </span>D3DXPT\_FORCE\_DWORD = 0×7fffffff\
   } D3DXPARAMETER\_TYPE;</span>
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

而真正要让Effect起作用，需要在绘制网格模型前后调用ID3DXEffect::BeginPass()和EndPass方法。在调用这两个函数之前和之后，还需调用ID3DXEffect::Begin()和
ID3DXEffect::End()方法来界定此次Effect设置的起止。大致的形式如下：

\

+--------------------------------------------------------------------------+
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">LPD3DXEffect                                                         |
| pd3dEffect；<span class="Apple-converted-space"> </span><span            |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//ID3DXEffe |
| ct接口指针</span>\                                                       |
|  …<span class="Apple-converted-space"> </span><span                      |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//初始化该指针</s |
| pan>\                                                                    |
|  …<span class="Apple-converted-space"> </span><span                      |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//程序中的其他部分< |
| /span>\                                                                  |
|  …</span>                                                                |
|                                                                          |
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">UINT                                                                 |
| numPasses;<span class="Apple-converted-space"> </span><span              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//用于接受当前所使用 |
| 的technique中的pass个数</span>\                                          |
|  pd3dEffect-\>Begin( & numPasses, 0 )<span                               |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//开始使用当前的te |
| chnique</span>\                                                          |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">for</span>( |
| UINT iPass = 0; iPass \< numPasses; iPass ++ )\                          |
|  {\                                                                      |
|     <span class="Apple-converted-space"> </span><span                    |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//遍历所有的pass |
| </span>\                                                                 |
|     <span class="Apple-converted-space"> </span>pd3dEffect-\>BeginPass(  |
| iPass );<span class="Apple-converted-space"> </span><span                |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//调用BeginPa |
| ss</span>\                                                               |
|     <span                                                                |
| class="Apple-converted-space"> </span>DrawMesh();                    <sp |
| an                                                                       |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//然后进行模型的绘制 |
| 。</span>\                                                               |
|     <span                                                                |
| class="Apple-converted-space"> </span>pd3dEffect-\>EndPass();         <s |
| pan                                                                      |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//调用EndPass |
| </span>\                                                                 |
|  }\                                                                      |
|  pd3dEffect-\>End();                 <span                               |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//不要忘记结束当前t |
| echnique</span></span>                                                   |
+--------------------------------------------------------------------------+

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

**3DS MAX对DirectX 9 Shader Material的支持；Effect数据获取和导出**

在FX文件中的参数，大部分都是用来调整FX文件所指定的Effect的一些细节，例如，一种带有凹凸纹理的效果，可能在FX中就有一个参数控制着凹凸不平的程度。而这些参数是需要由美工来调整的。另外，美工也需要有一个途径能够将FX文件定义的Effect赋予到一个模型或它的一部分上去。同时美工也应该能够实时的预览该Effect在模型上的实际效果。
在以前，实现这些要求只能通过自制效果预览器、模型编辑器或者为DCC软件编写插件来完成。这对于小的工作组和工期较短的项目来说是非常困难的。幸运的是，目前的DCC软件
已经开始为游戏制作提供丰富的支持功能。通过DCC软件自身就可以预览到实时Effect的效果，并调整其参数。在《龙的传说》这个项目中，我们使用3DS
MAX 6.0来作为模型建立 工具和Shader预览工具。

在3DS MAX 6.0中，新加入了一种材质类型——DirectX 9<span
class="Apple-converted-space"> </span>Shader材质。这种材质是基于FX文件的。一个FX文件就可以代表一种材质。它可以同MAX中的其他材质一样赋予到模型上
。在MAX的Viewport中可以实时地观察到FX文件中设计的效果。通过为FX中的参数设置特定的Semantic，可以将这些参数与MAX中的场景信息联系起来，如摄像机位置、世界变换矩
阵等。对于控制Effect效果的一些本地参数，可以通过为它们添加特定的Annotation，使MAX能够直接识别这些参数并在用户界面中显示它们的名称和调节控件。对应不同类型的参
数，MAX可以为它们生成不同的调节控件。这样，这种材质就和MAX的其他材质一样，可以更改纹理等等的参数了。
对于美工来说，通过这种用户界面就可以调整该FX材质的参数达到最好的效果。

但是美工所调整的结果必须要能够保存下来才有意义。这个工作就得由程序员来完成了。要保存3DS
MAX中编辑的所有内容，需要为3DS
MAX编写文件导出插件，将其内部数据保存在特定格式的文件中。在《龙的传说》这个项目中，我们使用Microsoft
DirectX .X
文件。如果从头开始写导出插件，工作量是相当大的；幸运的是，在Microsoft
DirectX SDK Extra中提供了一个能够导出模型和3DS
MAX标准材质到X文件的插件源代码。通过修改该源代码，可以使它能够导出DirectX
9 Shader材质。在3DS MAX 6
SDK中新增加了一个IDxMaterial接口，通过查询一个IMaterial接口是否为IDxMaterial接口，就可以确定该材质是否为DirectX
9
Shader材质。通过IDxMaterial接口可以获得该材质对应的FX文件的文件名，以及其参数信息。这样就可以将它们导出了。

**.X文件中对Effect的支持；EffectInstance和EffectDefault**

Microsoft DirectX
.X文件的格式是基于模板的、可扩展的文件格式。通过为其制定新的模板，就可以在其中加入新的内容。一般的.X文件中的内容有三维场景的物体层级关系、网格模型几何数据、材质信息、动画信息等。在DirectX的众多X文件模板中有一个模板是专门用来代表Effect的实例的。当一个FX文件的参数被美工加以调整从而具备一些特定的值之后，该
FX文件和这些参数值的集合就形成了一个Effect实例。该模板的定义如下：

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">template</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">EffectInstance\
   {\
      <span class="Apple-converted-space"> </span>\< E331F7E4-0559-4cc2-8E99-1CEC1657928F \>\
      <span class="Apple-converted-space"> </span>STRING EffectFilename;\
      <span class="Apple-converted-space"> </span>[ ... ]\
   }</span>
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

其中， EffectFilename代表了该Effect实例中的FX文件名， [ ...
]代表在其中可以插入任何X文件模板对应的数据。这样就可以代表任何类型的参数值。

然而要想让Direct3D程序能够识别[ ...
]中的内容，需要使用X文件模板中的EffectParam系列模板，包括EffectParamDWord,
EffectParamFlaots,
EffectParamString。通过这三种模板对应的数据，所有类型的Effect参数值都可以被记录在X文件中。

最后，EffectInstance数据需要被放置在Material数据中才可以被识别。

Material模板：

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">template</span></span><span class="Apple-converted-space"> </span><span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">Material\
   {\
      <span class="Apple-converted-space"> </span>\< 3D82AB4D-62DA-11CF-AB39-0020AF71E433 \>\
      <span class="Apple-converted-space"> </span>ColorRGBA faceColor;\
      <span class="Apple-converted-space"> </span>FLOAT power;\
      <span class="Apple-converted-space"> </span>ColorRGB specularColor;\
      <span class="Apple-converted-space"> </span>ColorRGB emissiveColor;\
      <span class="Apple-converted-space"> </span>[...]\
   }</span>
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

前面的一些颜色模板表明在Material数据中这些颜色信息是必须有的，而最后的[
...
]则代表可以插入任何X文件模板对应的数据。我们的EffectInstance数据就可以放置在这里
。

举一个简单的例子：

\

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  <span style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:normal;">Material {<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//材质</span>\
      <span class="Apple-converted-space"> </span>0.500000;0.500000;0.500000;1.000000;;<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//faceColor</span>\
      <span class="Apple-converted-space"> </span>0.000000;<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//power</span>\
      <span class="Apple-converted-space"> </span>0.900000;0.900000;0.900000;;<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//specularColor</span>\
      <span class="Apple-converted-space"> </span>0.000000;0.000000;0.000000;;<span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//emissiveColor</span>\
      <span class="Apple-converted-space"> </span>EffectInstance\
      <span class="Apple-converted-space"> </span>{                            <span style="line-height:18px;word-wrap:normal;word-break:normal;">//[...]，这里是EffectInstance</span>\
          <span class="Apple-converted-space"> </span>"SkyboxNew01.fx";       <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//fx文件的文件名。通过D3DXCreateEffectFromFile()可以</span>\
                                   <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//建立该文件对应的D3DXEffect对象\
          <span class="Apple-converted-space"> </span>//下面是EffectInstance中的[...]</span>\
          <span class="Apple-converted-space"> </span>EffectParamString \
           {                       <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//EffectParamString，即字符串型参数值</span> \
               "TexCloudTop";      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//参数的名称，通过该名称调用ID3DXEffect::GetXXXByName()方法</span>\
                                   <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//可以得到与fx文件中对应的参数</span>。\
              <span class="Apple-converted-space"> </span>"DarkClouds01.jpg"; <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//参数的值 </span>\
           } \
           EffectParamString\
          <span class="Apple-converted-space"> </span>{                       <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//同上</span>\
              <span class="Apple-converted-space"> </span>"TexCloudBottom";\
              <span class="Apple-converted-space"> </span>"DarkClouds02.jpg";\
          <span class="Apple-converted-space"> </span>}\
          <span class="Apple-converted-space"> </span>EffectParamFloats\
          <span class="Apple-converted-space"> </span>{                      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//EffectParamFloats，即浮点数组型参数值</span>\
              <span class="Apple-converted-space"> </span>"Brightness";      <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//参数名称</span>\
              <span class="Apple-converted-space"> </span>1;                 <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//浮点数组大小</span>\
              <span class="Apple-converted-space"> </span>0.500000;          <span class="Apple-converted-space"> </span><span style="line-height:18px;word-wrap:normal;word-break:normal;">//值</span>\
          <span class="Apple-converted-space"> </span>}\
      <span class="Apple-converted-space"> </span>}\
   }</span>
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

当我们在程序中调用D3DXLoadMeshFromX()或D3DXLoadMeshHierarchyFromX()时，就可以通过其LPD3DXBUFFER \*ppEffectInstances参数来接收到网格所用的所有EffectInstance的信息。

在程序中，对应于X文件中的EffectInstance模板和EffectParam系列模板，有两个结构体用来代表Effect数据：

\

+--------------------------------------------------------------------------+
| <span style="line-height:18px;word-wrap:normal;word-break:normal;"><span |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">typedef                                                              |
| struct</span></span><span class="Apple-converted-space"> </span><span    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">\_D3DXEFFECTINSTANCE\                                                |
|  {<span class="Apple-converted-space"> </span><span                      |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//EffectIns |
| tance</span>\                                                            |
|     <span class="Apple-converted-space"> </span>LPSTR                    |
| pEffectFilename; <span                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//fx文件名</sp |
| an>\                                                                     |
|     <span class="Apple-converted-space"> </span>DWORD NumDefaults;<span  |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//参数个数</spa |
| n>\                                                                      |
|     <span class="Apple-converted-space"> </span>LPD3DXEFFECTDEFAULT      |
| pDefaults;<span class="Apple-converted-space"> </span><span              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//参数数组</spa |
| n>\                                                                      |
|  } D3DXEFFECTINSTANCE, \*LPD3DXEFFECTINSTANCE;</span>                    |
|                                                                          |
|                                                                          |
|                                                                          |
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;"><span                                                                |
| style="line-height:18px;word-wrap:normal;word-break:normal;">typedef     |
| struct</span><span                                                       |
| class="Apple-converted-space"> </span>\_D3DXEFFECTDEFAULT\               |
|  {<span class="Apple-converted-space"> </span><span                      |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//EffectDef |
| ault，即EffectParam</span>\                                              |
|     <span class="Apple-converted-space"> </span>LPSTR                    |
| pParamName;          <span class="Apple-converted-space"> </span><span   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//参数名</span |
| >\                                                                       |
|     <span class="Apple-converted-space"> </span>D3DXEFFECTDEFAULTTYPE    |
| Type;<span class="Apple-converted-space"> </span><span                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//参数类型</spa |
| n>\                                                                      |
|     <span class="Apple-converted-space"> </span>DWORD                    |
| NumBytes;            <span class="Apple-converted-space"> </span><span   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//参数大小，以字节记 |
| </span>\                                                                 |
|     <span class="Apple-converted-space"> </span>LPVOID                   |
| pValue;             <span class="Apple-converted-space"> </span><span    |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//指向参数的值的指针 |
| </span>\                                                                 |
|  } D3DXEFFECTDEFAULT, \*LPD3DXEFFECTDEFAULT;</span>                      |
|                                                                          |
| 需要注意的是，从文件中得到的参数类型只有以下几种：\                      |
|  <span                                                                   |
| style="line-height:18px;word-wrap:normal;word-break:normal;">typedef</sp |
| an><span                                                                 |
| class="Apple-converted-space"> </span>enum \_D3DXEFFECTDEFAULTTYPE\      |
|  {\                                                                      |
|     <span class="Apple-converted-space"> </span>D3DXEDT\_STRING =        |
| 1,<span class="Apple-converted-space"> </span><span                      |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//字符串</span |
| >\                                                                       |
|     <span class="Apple-converted-space"> </span>D3DXEDT\_FLOATS =        |
| 2,<span class="Apple-converted-space"> </span><span                      |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//浮点数组</spa |
| n>\                                                                      |
|     <span class="Apple-converted-space"> </span>D3DXEDT\_DWORD =         |
| 3, <span class="Apple-converted-space"> </span><span                     |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//长整型</span |
| >\                                                                       |
|     <span class="Apple-converted-space"> </span>D3DXEDT\_FORCE\_DWORD =  |
| 0×7fffffff<span class="Apple-converted-space"> </span><span              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//此值不使用</sp |
| an>\                                                                     |
|  } D3DXEFFECTDEFAULTTYPE;                                                |
|                                                                          |
|                                                                          |
+--------------------------------------------------------------------------+

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

在调用了D3DXLoadMeshFromX()和D3DXLoadMeshHierarchyFromX()之后，X文件中的所有Effect数据信息就以上述结构体的形式放置在ppEffectInstances中了。
另外，在从3DS
MAX导出参数到X文件时，对于整型和浮点数组型的变量，它们的值将直接导出到X文件中去；而对于所有的纹理贴图文件参数，导出的仅仅是该文件的文件名。所以
在程序中需要再根据这些文件名来建立纹理对象。
在《龙的传说》中，我们使用一个自定义的CEffectInstance类来处理将文件名转换为纹理对象的过程。
一般来说，建立一个完整的CEffectInstance的过程如下：

根据D3DXEFFECTINSTANCE结构中的pEffectFilename字符串寻找对应的FX文件;\
 根据该FX文件建立ID3DXEffect，并将指针保存在CEffectInstance中;\

根据D3DXEFFECTINSTANCE结构中的pDefaults设置CEffectInstance中的参数信息： 

> \
>  对于长整型和浮点数组，直接拷贝； \
>
> 对于字符串，首先调用ID3DXEffect接口中的GetParameterByName()和GetParameterDesc()方法，得到该参数的类型；
> 然后进一步判断：
>
> > \
> >  如果确实是字符串参数，则直接拷贝\
> >
> > 如果是纹理参数，则将该字符串作为纹理文件名建立纹理对象，并将指针保存在CEffectInstance中。

而在最新推出的DirectX 9 SDK Summer
2004中，通过ID3DXEffect::BeginParameterBlock()和ID3DXEffect::EndParameterBlock()方法，我们可以将Effect参数设置过程统一绑定到一个ParamBlock句柄上。这样，在调用ID3DXEffect::Begin()之前就可以直接使用ID3DXEffect::ApplyParameterBlock()方法来设置所有被绑定的参数值。例如：

[**以前的做法**]：

在读取参数时：获得每一个参数的句柄

\

+--------------------------------------------------------------------------+
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">hParam1                                                              |
| = pEffect-\>GetParameterByName( NULL, "LightPos" );\                     |
|  hParam2 = pEffect-\>GetParameterByName( NULL, "LightColor" );\          |
|  …</span>                                                                |
|                                                                          |
| 在实时绘制时：分别设置每一个参数                                         |
|                                                                          |
| pEffect-\>SetValue( hParam1, value1 );\                                  |
|  pEffect-\>SetValue( hParam2, value2 );\                                 |
|  …\                                                                      |
|  pEffect-\>Begin();\                                                     |
|  <span style="line-height:18px;word-wrap:normal;word-break:normal;">//   |
| 绘制</span>\                                                             |
|  …                                                                       |
|                                                                          |
|                                                                          |
+--------------------------------------------------------------------------+

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

[**在DirectX 9 SDK Summer 2004中的做法**]：

在读取参数时：绑定所有参数设置到同一句柄

\

+--------------------------------------------------------------------------+
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">hParam1                                                              |
| = pEffect-\>GetParameterByName( NULL, "LightPos" );\                     |
|  hParam2 = pEffect-\>GetParameterByName( NULL, "LightColor" );\          |
|  …\                                                                      |
|  pEffect-\>BeginParameterBlock();<span                                   |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//          |
| 开始绑定</span>\                                                         |
|  pEffect-\>SetValue( hParam, value1 );\                                  |
|  pEffect-\>SetValue( hParam, value2 );\                                  |
|  …\                                                                      |
|  hParamBlock = pEffect-\>EndParameterBlock();<span                       |
| class="Apple-converted-space"> </span><span                              |
| style="line-height:18px;word-wrap:normal;word-break:normal;">//          |
| 结束绑定，返回句柄</span></span>                                         |
|                                                                          |
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">在实时绘制时：统一设置绑定值</span>                                  |
|                                                                          |
|                                                                          |
|                                                                          |
| <span                                                                    |
| style="line-height:18px;font-family:宋体;word-wrap:normal;word-break:norma |
| l;">pEffect-\>ApplyParameterBlock(                                       |
| hParamBlock );\                                                          |
|  pEffect-\>Begin;\                                                       |
|  <span style="line-height:18px;word-wrap:normal;word-break:normal;">//   |
| 绘制</span>\                                                             |
|  …</span>                                                                |
|                                                                          |
|                                                                          |
+--------------------------------------------------------------------------+

 

<span
style="line-height:21px;font-family:宋体;word-wrap:normal;word-break:normal;"> </span>

这样不仅简化了在读取时对参数的分析过程，而且提高了实际绘制时参数设置过程的效率。

**总结**

以上就是一些对于在DirectX 9.0中对Effect
Framework的使用的简要介绍。总之，使用Effect来替代以前的标准材质是目前实时图形领域的发展趋势。通过Effect
Framework，程序员和美工可以为实时三维程序实现多种多样的材质效果和视觉效果。
由于内容实在太多，限于篇幅，本文只是对Effect
Framework中相关概念的一个总体概括和简要介绍，所以显得有些晦涩。在以后的文章中，将分批对这个Framework以及在其之上进行工作的流程进行比较详细的介绍

 

 







