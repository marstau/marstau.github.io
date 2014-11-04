---
layout: post
title: NDK和Eclipse的集成
category: 游戏技术
tags: android／java
keywords: 
description: 
---

要执行 **build/host-setup.sh**进行ndk安装，但找不到这个文件

在docs里面查install.txt，发现：

  Previous releases required you to run the 'build/host-setup.sh' script to

  configure the NDK. However, this step has been removed in release 4 (a.k.a. r4).

  原来这个版本不用手动安装

 recommended:<http://blog.csdn.net/goldroc/article/details/5444005>

 

**<span style="COLOR: #e53333">FIRST:</span><span
style="COLOR: #e53333"></span>**

Android NDK是什么,  NDK：Native Develpment Kit.

众所周知，Android是基于Linux的支持，自然对C、C++提供原生的支持，Android的开发也是基于Java的语言。应用程序的运行环境主要是**Dalvik**虚拟机。虽然开发语言是Java但是我们总可以通过各种方式用C等语言开发。

至于用NDK开发的流程，请阅读NDK附带的文档。

 

关于具体的信息了解，请访问Android开发网阅读文档了解基本的信息。

[点这里了解基本信息](http://developer.android.com/sdk/ndk/index.html)(需要设置代理访问或者翻墙)

建议通读上面链接的全文(英文版)，很多东西按照上面介绍的步骤就可以完全的成功。一些基本的命令和操作也在里面可以看到，相信看过以后会对你有启发。

在其中有这么一句话：

Please note that the NDK<span class="Apple-converted-space"></span>*does
not*<span class="Apple-converted-space"></span>enable you to develop
native-only applications. Android’s primary runtime remains the Dalvik
virtual machine

在NDK文档中也有这样的描述：

The NDK is \*not\* a good way to write generic native code that runs on
Android devices. In particular, your applications should still be
written in the Java programming language, handle Android system events
appropriately to avoid the "Application Not Responding" dialog or deal
with the Android application<span
class="Apple-converted-space"></span>life-cycle.

也就是说，Android的Application不能完全用C或者C++开发，其运行环境主要是Dalvik的JVM，而且NDK没有关于组件声明周期和事件处理的东西。

其实据我的了解和理解，NDK的原理大体就是Java中声明接口然后通过JNI(Java
Native Interface )调用NDK开发的C和C++代码，文档中也提到，A good
understanding of JNI is highly recommended。native
code被**静态编译**为.so的模块，然后加载到.apk中，然后安装到Android中运行。这些信息都可以通过google关键字Android
NDK和阅读NDK的文档获取，形成你自己的理解。

当然按照本文的介绍的步骤也可以配置，但还是建议读一下。

 

第一步，下载Android
的SDK，注意，SDK要1.5以后的版本(链接中有提到,原因在NDK的文档里有介绍)。

当然，配置好的Eclipse+ADT也是需要的。

第二步，下载Android NDK。

下载完成后即解压到适当的目录。设置Android
SDK的环境变量。NDK目前只需要解压到适当目录即可。

解压后可大致浏览下目录的结构。当然，在上面的链接中，有关于其目录结构的介绍。

第三步，安装Cygwin([www.cygwin.com](http://www.cygwin.com/))。最新版本1.7，我用的1.6的版本，也会我建议的版本。Cygwin是什么，有关于一些交叉编译的知识请自己通过搜索引擎了解。(XP不会自动生成/home目录下的文件，解决方案：我的电脑-\>属性-\>高级-\>环境变量-\>找到系统变量HOME，删除之，重启再次运行cygwin即可生成home目录下的几个文件)

下载后运行Setup，点击next，选择Install from Internet：

然后下一步，选择适当的目录，

下一步，再选择相应的包的下载存放位置，默认，

下一步，网络配置，默认，

下一步，会搜索站点，下载站点选择台湾的，速度比较快，

等待其更新软件的列表后，就是比较关键的一步。

上面链接的文档和NDK附带文档中的INSTALL.TXT中也提到了，我们需要以下的工具：

1\. GNU make

2\. bash shell

3\. Nawk或者GNU awk

所以在这里我们安装上面所需要的组件，找到Devel，并点击后面的循环箭头，将其改为Install

Devel中就包含了make及gcc等组件，可以点开前面的+号浏览。

然后找到Shell 选项，改为install

然后在上面的搜索框中搜索awk，找到两条，其默认已经包含了，这里确认一下，改为install。

next，开始安装。

安装完成后，找到Cygwin的安装目录下\<cygwin\>/home/\<你的用户名\>/.bash\_profile文件，UltraEdit打开，据说用记事本等的打开也会出问题。不要转换格式，否则出问题。最后一行，添加上

**ANDROID\_NDK\_ROOT=/cygdrive/c/android-ndk-r3\
export ANDROID\_NDK\_ROOT**

其中的c/android-ndk-r3是我的安装的目录。改为你的。

保存退出。

桌面或者开始菜单打开Cygwin的bash shell，

到这步之前，请确保你了解什么是Cygwin以及Cygwin是干什么的。

进入NDK的目录，

cd \$ANDROID\_NDK\_ROOT

下面就是配置Android的NDK了

<span style="TEXT-DECORATION: underline">运行一下命令：</span>

<span style="TEXT-DECORATION: underline">build/host-setup.sh</span>

注意无空格。运行后会提示安装完毕。

到此，NDK的配置就完毕了。

提示中有着么一句话：如果你不知道接下来干什么，请阅读docs目录下的OVERVIEW.txt。这个文档是非常有用，建议细读。

接下来是如何运行NDK中自带的samples。

首先还是在Cygwin的bash shell中：

cd \$ANDROID\_NDK\_ROOT

make APP=hello-jni

此命令会在\<ndk-dir\>/apps/apps/hello-jni/project/libs/armeabi下生成.so文件，其实这个.so文件就相当于Windows下的dll。

然后，打开你配置好的Eclipse+ADT的环境。

新建Android Project。

新建选项中，选择create Project from existing source,
目录选择NDK下的hello-jni目录下的Project文件夹

然后编译运行，看到从.c文件返回的hello from JNI字符串：

**<span style="COLOR: #e53333">SECOND:</span>**

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">一：什么是</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">？</span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">     </span>NDK </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">提供了一系列的工具，帮助开发者快速开发</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">C</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">（或</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">C++</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">）的动态库，并能自动将</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">so </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">和</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">java </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">应用一起打包成</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">apk</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">。这些工具对开发者的帮助是巨大的。</span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">     </span>NDK </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">集成了交叉编译器，并提供了相应的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">mk </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">文件隔离</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">CPU</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、平台、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">ABI </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">等差异，开发人员只需要简单修改</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">mk </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">文件（指出</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">“</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">哪些文件需要编译</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">”</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">“</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">编译特性要求</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">”</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">等），就可以创建出</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">so</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">可以自动地将</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">so </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">和</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Java </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">应用一起打包，极大地减轻了开发人员的打包工作。比较简单的说，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">是一套交叉编译工具，它可以帮你把你用</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">C</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">或</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">C++</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">书写的代码，编译为</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">.so</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">（类似与</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">win</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">下的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">.dll</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">）格式的文件，使你可以在你的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Android</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">程序当中用</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Java</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">语言（</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">JNI</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">）调用这些代码</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">.</span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">二：下载安装</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">    </span></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">由于</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">编译代码时必须要用到</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">make</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">和</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">gcc</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，所以你必须先搭建一个</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">linux</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">环境，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">是一个在</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">windows</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">平台上运行的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">unix</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">模拟环境</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">,</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">它对于学习</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">unix/linux</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">操作环境，或者从</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">unix</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">到</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">windows</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的应用程序移植，非常有用。通过它，你就可以在不安装</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">linux</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的情况下使用</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">来编译</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">C</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">C++</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">代码了。下面我们一步一步的安装</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">吧。</span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">    </span></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">首先，你得先跑到</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; TEXT-DECORATION: underline; PADDING-TOP: 0px"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: #333333; PADDING-TOP: 0px"
lang="EN-US">[http://www.cygwin.com/<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">下载</span></span>setup.exe](http://www.cygwin.com/%E4%B8%8B%E8%BD%BDsetup.exe)</span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">1</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">然后双击运行吧，运行后你将看到安装向导界面：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">2</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">点击下一步，此时让你选择安装方式：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span>1</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">）</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Install from Internet</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">：直接从</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Internet</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">上下载并立即安装（安装完成后，下载好的安装文件并不会被删除，而是仍然被保留，以便下次再安装）。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span>2</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">）</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Download Without Installing</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">：只是将安装文件下载到本地，但暂时不安装。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span>3</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">）</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Install from Local Directory</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">：不下载安装文件，直接从本地某个含有安装文件的目录进行安装。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">3</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、选择第一项，然后点击下一步：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">4</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、选择要安装的目录，注意，最好不要放到有中文和空格的目录里，似乎会造成安装出问题，其它选项不用变，之后点下一步：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">5</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、上一步是选择安装</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的目录，这个是选择你下载的安装包所在的目录，默认是你运行</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">setup.exe</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的目录，直接点下一步就可以：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">6</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、此时你共有三种连接方式选择：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span>1) Direct
Connection</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">：直接连接。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span>2) Use IE5
Settings</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">：使用</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">IE</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的连接参数设置进行连接。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span>3) Use HTTP/FTP
Proxy</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">：使用</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">HTTP</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">或</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">FTP</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">代理服务器进行连接（需要输入服务器地址、端口号）。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">　 根据自己的网络连接的实情情况进行选择，一般正常情况下，均选择第一种，也就是直接连接方式。然后再点击</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">“</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">下一步</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">”</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">7</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">这是选择要下载的站点，我用的是</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">[<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: #333333; PADDING-TOP: 0px">http://mirrors.kernel.org/</span>](http://student.csdn.net/link.php?url=http://mirrors.kernel.org%2F)</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，速度感觉还挺快，选择后点下一步</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">.(</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">有的网友说选择台湾的站点也比较快</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">)</span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">8</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">此时会下载加载安装包列表</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">9</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Search</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">是可以输入你要下载的包的名称，能够快速筛选出你要下载的包。那四个单选按钮是选择下边树的样式，默认就行，不用动。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">View</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">默认是</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Category</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，建议改成</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">full</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">显示全部包再查，省的一些包被隐藏掉。左下角那个复选框是是否隐藏过期包，默认打钩，不用管它就行，下边开始下载我们要安装的包吧，为了避免全部下载，这里列出了后面开发</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">用得着的包：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">autoconf2.1</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">automake1.10</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">binutils</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gcc-core</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gcc-g++</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gcc4-core</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gcc4-g++</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gdb</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">pcre</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">pcre-devel</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gawk</span></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">make</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">共</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">12</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">个包</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">10</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、然后开始选择安装这些包吧，点</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">skip</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，把它变成数字版本格式，要确保</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Bin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">项变成叉号，而</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">Src</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">项是源码，这个就没必要选了。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">11</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、下面测试一下</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">是不是已经安装好了。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">运行</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，在弹出的命令行窗口输入：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">cygcheck -c cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">命令，会打印出当前</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的版本和运行状态，如果</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">status</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">是</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">ok</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的话，则</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">运行正常。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px">        <span
class="Apple-converted-space"></span></span></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">然后依次输入</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gcc –version</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">g++ --version</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">make –version</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">gdb –version</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">进行测试，如果都打印出版本信息和一些描述信息，非常高兴的告诉你，你的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">安装完成了！</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

**PATH环境变量最终设置：**

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

**D:\\android-sdk-windows\\platform-tools;%SystemRoot%\\system32;%SystemRoot%;%SystemRoot%\\System32\\Wbem;C:\\Program Files\\ATI Technologies\\ATI.ACE\\Core-Static;D:\\Program Files\\TortoiseSVN\\bin;C:\\Program Files\\Microsoft SQL Server\\90\\Tools\\binn\\;D:\\Program Files\\Java\\jdk1.7.0\_04\\bin**

 

 

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">三：配置</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">环境变量</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">1</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、首先找到</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的安装目录，找到一个</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">home\\\<</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">你的用户名</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">\>\\.bash\_profile</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">文件，我的是：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">E:\\cygwin\\home\\Administrator\\.bash\_profile</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">2</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、打开</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">bash\_profile</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">文件，添加</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK=/cygdrive/\<</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">你的盘符</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">\>/\<android ndk </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">目录</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">\> </span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">例如：</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"></span></span>

**NDK\_ROOT=/cygdrive/d/android-ndk-r7-crystax-5.beta3-windows**

**export NDK\_ROOT**

**NDK\_SYJT=/cygdrive/d/xc2d/trunk/project/android**

**export NDK\_SYJT**

 

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">(NDKRoot</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">这个名字是随便取的，为了方面以后使用方便，选个简短的名字，然后保存</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">)</span>

 

 

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">3</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、打开</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，输入</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cd \$NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，如果输出上面配置的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">/cygdrive/e/android-ndk-r5</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">信息，则表明环境变量设置成功了。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">四：用</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">来编译程序</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">1</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、现在我们用安装好的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">来编译一个简单的程序吧，我们选择</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">ndk</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">自带的例子</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">hello-jni</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，我的位于</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">E:\\android-ndk-r5\\samples\\hello-jni(</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">根据你具体的安装位置而定</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">).</span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">2</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、运行</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cygwin</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，输入命令</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">cd /cygdrive/e/android-ndk-r5/samples/hello-jni</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，进入到</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">E:\\android-ndk-r5\\samples\\hello-jni</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">目录。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">3</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">输入</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">\$NDK/ndk-build</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">，执行成功后，它会自动生成一个</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">libs</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">目录，把编译生成的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">.so</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">文件放在里面。</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">(\$NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">是调用我们之前配置好的环境变量，</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">ndk-build</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">是调用</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">ndk</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的编译程序</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">)</span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

 

Administrator@VJHWE1ENO \~

**\$ cd \$NDK\_ROOT**

 

Administrator@VJHWE1ENO /cygdrive/d/android-ndk-r7-crystax-5.beta3-windows

\$ ls

build               ndk-build      platforms    samples

docs                ndk-build.cmd  prebuilt     sources

documentation.html  ndk-gdb        README.TXT   tests

GNUmakefile         ndk-stack.exe  RELEASE.TXT  toolchains

 

Administrator@VJHWE1ENO /cygdrive/d/android-ndk-r7-crystax-5.beta3-windows

**\$ cd samples/**

 

Administrator@VJHWE1ENO /cygdrive/d/android-ndk-r7-crystax-5.beta3-windows/samples

**\$ ls**

bitmap-plasma  hello-neon       native-audio   san-angeles

hello-gl2      module-exports   native-media   test-libstdc++

hello-jni      native-activity  native-plasma  two-libs

 

Administrator@VJHWE1ENO /cygdrive/d/android-ndk-r7-crystax-5.beta3-windows/samples

**\$ cd san-angeles/**

 

Administrator@VJHWE1ENO /cygdrive/d/android-ndk-r7-crystax-5.beta3-windows/samples/san-angeles

**\$ cd jni/**

 

Administrator@VJHWE1ENO /cygdrive/d/android-ndk-r7-crystax-5.beta3-windows/samples/san-angeles/jni

**\$ ls**

Android.mk     app-linux.c  demo.c      license.txt       README.txt

app.h          app-win32.c  importgl.c  license-BSD.txt   shapes.h

app-android.c  cams.h       importgl.h  license-LGPL.txt

 

Administrator@VJHWE1ENO /cygdrive/d/android-ndk-r7-crystax-5.beta3-windows/samples/san-angeles/jni

****

\$ \$NDK\_ROOT/ndk-build -j3 APP\_OPTIM=release

 

Cygwin         : Generating dependency file converter script

StaticLibrary  : libcrystax.a

Prebuilt       : libcrystax\_static.a \<= \<NDK\>/sources/crystax/libs/armeabi/4.6.3/

Compile thumb  : sanangeles \<= importgl.c

Compile thumb  : sanangeles \<= demo.c

Compile thumb  : sanangeles \<= app-android.c

SharedLibrary  : libsanangeles.so

Install        : libsanangeles.so =\> libs/armeabi/libsanangeles.so

 

 

 

 

**<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">(</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">早期</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">NDK</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">版本是</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">make APP=hello-jni ,</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">还要对应</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">app</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">和</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">source2</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">个目录的项目目录，现在改成了</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; COLOR: red; PADDING-TOP: 0px"
lang="EN-US">\$NDK/ndk-build</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: red; PADDING-TOP: 0px">）</span>**<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US"></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; COLOR: #444444; FONT-SIZE: small; PADDING-TOP: 0px"
color="#444444" face="宋体" size="3"></span></span>

<span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">4</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">、此时去</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">hello-jni</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">libs</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">目录下看有没有生成的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">.so</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">文件，如果有，你的</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; PADDING-TOP: 0px"
lang="EN-US">ndk</span><span
style="PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FONT-FAMILY: 宋体; PADDING-TOP: 0px">就运行正常啦！</span>

四、ADT

下载ADT并安装之<https://developer.android.com/sdk/installing/installing-adt.html>

五、重新打开Eclpise安装

一. 无法创建新android项目

在eclipse创建新项目时出现： 

1 2 3 4  this template depends on the android support library,which is either not installed,or the template depends on a more recent version than the one you have installed。   Required version :8

解决办法：

运行sdk manager，勾选中Extras–\>Android Support Library，下载完成后重启eclipse。

 

二. 无法更新和下载androidSDK

 

打开SDK Manager时底部进度条一直不动，打开详细信息，发现卡在：

 

1  Fetching https://dl-ssl.google.com/android/repository/addons\_list-2.xml

解决办法：

修改hosts文件。

（1）windows下打开C:\\Windows\\System32\\drivers\\etc，以管理员身份编辑hosts文件，在最后添加：

74.125.237.1 dl-ssl.google.com

（2）linux下使用命令sudo vim /etc/hosts编辑hosts文件,同样在文件最后添加

74.125.237.1 dl-ssl.google.com

然后重新运行sdk manager，就可以下载了。

 

 

 

 

 

 

 

 









