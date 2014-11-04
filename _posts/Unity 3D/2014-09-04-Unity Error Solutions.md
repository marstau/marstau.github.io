---
layout: post
title: Unity Error Solutions
category: 游戏技术
tags: Unity　3D
keywords: 
description: 
---

1.  **<span
    style="color:#e53333;">Error while importing package: Couldn't decompress package</span>**\
     将.unitypackage拷贝的项目的目录下,然后在Project的视图中解压即可.

2.  Error :
    Some objects were marked as DontDestroyOnLoad, but since their parent game objects were not marked as DontDestroyOnLoad they have been destroyed anyway.

    If you want to keep them around, please ensure their parent is marked as DontDestroyOnLoad or make sure they are unparented before loading a new level.

    将所有empty对象放在MainRoot下,在MainRoot下建立一个新脚本,然后在Awake下加入语句

    DontDestroyOnLoad(gameObject);

3.  **<span
    style="color:#e53333;">Trying to Invoke method: TownBehaviour.ShowTown2DDelayed couldn't be called.</span>**\
     Invoke("ShowTown2DDelayed", 1.0f);\
     void ShowTown2DDelayed(**GameObject obj**){}\
     Invoke调用的不能带任何参数，将参数去掉即可。

4.  **<span
    style="color:#e53333;">Unable to find an appropriate UIRoot for "MissionScene/MainPanel/scroll bar/background"</span>**

    **<span
    style="color:#e53333;">Please make sure that there is at least one game object above this widget!</span>**\
     在父节点上加上一个GameObject即可。

5.  NGUI创建字体库的时候显示Font must be created with only 1 texture,
    not 2\
     创建的字体内容太多，一张texture无法容下，尽量减少一些字体。

6.  **<span
    style="color:#e53333;">error CS0246: The type or namespace name \`UnityEditor' could not be found. Are you missing a using directive or an assembly reference?</span>** 

    Built game cannot use the UnityEditor namespace. This namespace comes with the UnityEditor.dll assembly that is not shipped (and not compatible) with any build made by Unity.

    Scripts that use this namespace are only meant to be executed inside Unity Editor.

7.  **<span
    style="color:#e53333;">Unsafe code requires the \`unsafe' command line option to be specified</span>**\

    1.去除MONO编辑器中的Unsafe错误，Assembly-CSharp鼠标右键 找到Options-\>Build-\>General 。Allow 'unsafe' code 打钩。这个只能去除MONO报错，但是依然无法运行。

    2.首先看下面一段比较长的 

    在你的Assets目录下面添加smcs.rsp文件，里面只加一行字不要有空格  -unsafe。 OK搞定。记得一定要重启Unity3d, 因为这个预编译是在启动U3D时候运行的。工程文件名别带中文。

    原理是编辑器中的smcs.exe 添加编译命令，也可以在CMD下运行编辑器目录下的smcs.exe  逐个添加，会很累的。\
    \
     VS编译器中在项目-\>属性-\>生成-\>勾选
    允许不安全代码,然后重新编译一下即可不报错。

8.  **<span
    style="color:#e53333;">The Assembly System.Drawing is referenced by System.Web. But the dll is not allowed to be included or could not be found.</span>**\

    It's likely that the library is either missing or implemented in a rudimentary way for Unity. Not all of the .NET library is deemed applicable to games work, so we cut parts of it out to save memory and download time. Whenever you see something like this, it is worth checking the API compatibility level in the inspector (menu: Edit \> Project Settings \> Player). When the Subset option is chosen, as it is by default, then a even further reduced version of the .NET library is used, again for reasons of economy. Setting it to 2.0 compatibility will give you everything that is implemented in Unity, although as I have mentioned, this isn't all of .NET.(reference
    : <http://forum.unity3d.com/threads/57839-Unity-3-Build-Error> )

9.  **<span
    style="color:#e53333;">Error building Player: Exception: android (invokation failed)</span>**\
     先配置好java和android的环境变量,并下载好需要的sdk即可。\

    （As a technologist, somebody solved one problem, you also would and should solve it, through a certain way, did you try to run "android -h" in cmd?

    Just download the android sdk, then set user variable: name - "PATH", value - "D:\\android-sdk-windows\\tools" // tools directory.

    in Android SDK Manager, ensure you have download "Android SDK Tools", "Android SDK Platform-tools".

    Hope helps, guy.）

10.  

    \







