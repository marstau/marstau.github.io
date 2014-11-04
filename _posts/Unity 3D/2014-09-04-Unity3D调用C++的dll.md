---
layout: post
title: Unity3D调用C++的dll
category: 游戏技术
tags: Unity　3D
keywords: 
description: 
---

以windows平台为例

1.  创建dll项目\
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#008000;">//</span><span
    style="color:#008000;"> test.h</span><span style="color:#008000;">\
     </span><span
    style="color:#0000ff;">\#if</span> defined (EXPORTBUILD)\
     <span
    style="color:#0000ff;">\#define</span> \_DLLExport \_\_declspec (dllexport)\
     <span style="color:#0000ff;">\#else</span>\
     <span
    style="color:#0000ff;">\#define</span> \_DLLExport \_\_declspec (dllimport)\
     <span style="color:#0000ff;">\#endif</span>\
    \
     <span style="color:#0000ff;">extern</span> "C" <span
    style="color:#0000ff;">int</span> \_DLLExport  func();\
    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> test.cpp</span><span
    style="color:#008000;">\
     </span><span style="color:#0000ff;">\#define</span> EXPORTBUILD\
     \#include "test.h"\
    \
     <span style="color:#0000ff;">int</span> func(){\
         <span style="color:#0000ff;">return</span> 110;\
     }

    </div>

    用release版本编译。
2.  在Unity3D的Project视图下创建Plugins目录,将生成的NativeInvoke.dll链接库拷贝到Plugins目录下.
3.  在脚本中(以C\#为例),写入如下代码即可调用\
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#0000ff;">using</span> UnityEngine;\
     <span
    style="color:#0000ff;">using</span> System.Runtime.InteropServices;\
    \
     <span
    style="color:#0000ff;">class</span> NativeInvoke : MonoBehaviour\
     {\
    \
     <span
    style="color:#0000ff;">\#if</span> UNITY\_IPHONE || UNITY\_XBOX360\
    \
        <span style="color:#008000;">//</span><span
    style="color:#008000;"> On iOS and Xbox 360 plugins are statically linked into\
        </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> the executable, so we have to use \_\_Internal as the\
        </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> library name.</span><span
    style="color:#008000;">\
     </span>   [DllImport ("\_\_Internal")]\
    \
     <span style="color:#0000ff;">\#else</span>\
    \
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> Other platforms load plugins dynamically, so pass the name\
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> of the plugin's dynamic library.</span><span
    style="color:#008000;">\
     </span>\
         <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\*\
          \* @note\
          \*      the name is "NativeInvoke", but not "NativeInvoke.dll"\
          </span><span style="color:#008000;">\*/</span>\
         [DllImport("NativeInvoke")]\
    \
     <span style="color:#0000ff;">\#endif</span>\
    \
         <span style="color:#0000ff;">private</span> <span
    style="color:#0000ff;">static</span> <span
    style="color:#0000ff;">extern</span> <span
    style="color:#0000ff;">int</span> func();\
    \
         <span style="color:#0000ff;">void</span> Awake()\
         {\
             <span style="color:#008000;">//</span><span
    style="color:#008000;"> Calls the FooPluginFunction inside the plugin\
             </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> And prints 5 to the console</span><span
    style="color:#008000;">\
     </span>        print("DLL");\
             print(func());\
         }\
     }

    </div>

4.  





