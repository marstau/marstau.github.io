---
layout: post
title: Microsoft Visual Studio
category: 书籍与软件工具
tags: software／tool
keywords: linux,mac
description: 
---

##Versions[更多参考](http://en.wikipedia.org/wiki/Microsoft_Visual_Studio#History)

![](/Resources/Microsoft_Visual_Studio_1.jpg)


#Visual Studio 2010

##添加DLL库工程
eg:

引用simpledll项目。

右键单击usesimpledll项目，选择Properties->Common Properties->Framework and References。点击Add New Reference，选择simpledll项目，单击OK。

##去除UNICODE

  项目-\>配置属性-\>C/C++-\>预处理器-\>预处理器定义-\>去掉继承选项  

##嵌入汇编模块前基本配置

1. Create an empty project in Visual C++
2. right-click project in solutionexplorer, Build customizations, tick "masm", Then tap the right of mouse, select Add Now, select C++ File(.cpp), enter the sourcefile name with .asm as extend file name.
3. Tap right of mouse, choose Properties: Expand the entry under ConfigurationProperties. Then expand the entry named Microsoft Macro Assembler. Notice that the Include Paths option hasbeen set to the x:\\file
directory\\include directory. In this example, include directory isc:\\Irvine.
4. Next, select the Listing File entry, also in theMicrosoft Macro Assembler group. Notice that the Assembled Code Listing Fileentry (shown below) has been assigned a macro name (starting with \$) thatidentifies
the name of the source input file, with a file extension of .lst.So, if your program were named main.asm, the listing file would be named main.lst:
  
    Find the Linker entry under ConfigurationProperties. Select the Input entry, and notice that two filenameshave been added to the Additional Dependencies entry. The user32.libfile is a standard MS-Windows file.
The irvine32.lib file is the linklibrary file supplied with this book. There must be at least one spaceseparating the file names:
5. Next, select Linker underConfiguration Properties, and then select General. The AdditionalLibrary Directories option equals c:\\Irvine, so the linker can findthe Irvine32.lib library file(you also can copy
irvine32.lib to .../VC/LIB direcotry, so this would needn't to be done):
Select Linker under the ConfigurationProperties and select Debugging.
Notice that the Generate DebugInfo option is set to Yes: Select System under the Linkerentry. Notice that the SubSystem option has been set to Console: We use the Console settingbecause it is easy for assembly language
programs to write output to a textconsole (Command) window. This is the window you see when running cmd.exe fromthe Start \> Run menu in
Windows.
6. Click the OK button to close theProject Property Pages window.

##命令行编译

VS做的很智能，一个F7就完成了预处理、编译、链接的所有工作。但是当工程比较大，使用的文件模块比较多， 一旦出现编译错误定位问题时就比较困难。因此，有时候需要对每个模块单独编译，就像Linux下编写的 makefile文件一下，分别编译每一个.o目标文件然后再链接成为一个.exe可执行程序。总结下在VS下使用命令行分别编译程序的方法。

在dos下编译的前提环境配置要求：

1.找到vs的cl.exe所在目录，在vs2010为D:\\Program Files\\Microsoft Visual Studio 10.0\\VC\\bin，可参考。

2.点击“我的电脑”进行环境变量的配置，找到"path"变量加分号后加入刚才的路径。

3.重新运行cmd开启新的命令窗口，输入cl检查path设置是否生效。（只需配置一次即可，以后再次运行的时候不用再运行此命令）。

caution:如果输入cl命令出现如下所示错误(cl.exe
系统错误，无法启动此程序，因为计算机中丢失mspdb100.dll):

![](Resources/Visual Studio common usage_1.png)

将D:\\Program Files\\Microsoft Visual Studio 10.0\\Common7\\IDE目录下的mspdb100.dll拷贝到D:\\Program Files\\Microsoft Visual Studio 10.0\\VC\\bin目录下。

4.输入vcvars32,这条命令是运行同路径下的vcvars32.bat设置它的环境变量。

5.输入cl hello.cpp即可正常编译。

下面总结一些常用的命令：

通过快捷方式Visual Studio Command Prompt (2010)可以打开VS的命令行界面。

(1) 在命令行提示符窗口中输入：cl  /?   或者   cl -help 可以查看cl所有的命令选项。

(2) 在默认情况下cl编译完后会自动调用link进行链接，可以使用/c选项阻止链接。

(3) 编译一个文件命令：cl /FeMyapp 1.cpp，然后输入程序名Myapp执行程序。(注意1.h在本地，可以通过/I选 项指定头文件路径)

(4) 编译多个文件命令：cl /FeMyapp 1.cpp 2.cpp 3.cpp，然后输入程序名Myapp执行程序。

(5) 只输出 .i 预编译文件命令：cl /FiA /P A.cpp，然后会生成 A.i 预编译文件。这个方法类似Linux下的  gcc -E A.cpp -o A.i 命令。此命令的主要作用是用于检查未定义情况的错误。

(6) 只输出 .o 目标文件命令：cl /FoA /c A.cpp，然后会生成 A.obj 目标文件，类似Linux下的 .o 文件。注 意这里应该带上 /c 选项，原因见(2)，即默认情况下，cl会自动对编译好的目标文件进行链接，如果此时，所 编译的目标文件引用了其他目标文件中的符号的话，就会出现链接错误。 

##逆向工程

体系结构->生成依赖关系图->自定义
但VS2010默认只支持C#和Java的逆向工程,所以当逆向C++的时候会报错[当前解决方案不包含要进行反向工程的程序集],所以需安装[Microsoft Visual Studio 2010 可视化和建模功能包(visualization modeling feature pack).

##空格显示绿点

Ctrl + r,然后Ctrl + w,空格就会以绿点显示。

##为Visual Assist设置快捷键


** // Ctrl + B :** **Create Implementation** ( in <span
style="color:#e53333;">VAssistX.RefactorCreateImplementation </span>)

Visual Assist（以下称VA）是一款非常棒的Visual
Studio插件工具，特别是在VS2005中，提供了很多很好用的

辅助功能。如下图的“Create Implementation”，就很方便。

[![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206367152.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206354220.png)

 

但是每次都要点鼠标，是不是太烦呢？ 如果能设置一个快捷键就好了。

探索了一番， 找到了设置快捷键的方法，分享给大家。

方法如下：

<div id="AssignKeyboard"
style="word-spacing:0px;font:14px/26px Arial;text-transform:none;color:#333333;text-indent:0px;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">

1.  **Visual Studio 的“Tools”→”Customize”选项。 （中文版：
    工具→定制)<span class="Apple-converted-space"> </span>\
    \
    **
    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206388840.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206375940.png)<span
    class="Apple-converted-space"> </span>\
    \

    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206397346.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206393791.png)<span
    class="Apple-converted-space"> </span>\
2.  **在“Customize”对话框中选择“Keyboard”**<span
    class="Apple-converted-space"> </span>\
    \

    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206465506.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206427953.png)<span
    class="Apple-converted-space"> </span>\
3.  **在“Show commands containing:”中输入“vassistx.”
    就可以看到所有可以设置的快捷键了**<span
    class="Apple-converted-space"> </span>\
    \

    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206538368.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/20110531220649782.png)<span
    class="Apple-converted-space"> </span>\
4.  **如图，可以继续输入“vassistx.refactorcr”就出现了“Create
    Implementation”， 选中“<span
    style="color:#e53333;">VAssistX.RefactorCreateImplementation</span>”**<span
    class="Apple-converted-space"> </span>\
    \

    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207008514.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312206559532.png)<span
    class="Apple-converted-space"> </span>\
5.  **在Press shortcut
    keys那里的编辑框里点一下，出现闪烁的光标，这时候在键盘上按你想要的快捷键即可。如Ctrl+Alt+C<span
    class="Apple-converted-space"> </span>\
    \
    **
    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207072804.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207025774.png)<span
    class="Apple-converted-space"> </span>\
6.  图中显示这个快捷键已经在“Global”范围里分配给了Debug.CallStatck了，
    当然你也可以换一个其它没有用过的快捷键，不过<span
    class="Apple-converted-space"> </span>\
           我觉得这个挺好，而且VS可以设置快捷键的有效范围，我设置在“Text
    Editor”中就好了，那里我不需要调用Debug功能。<span
    class="Apple-converted-space"> </span>\
           如图，在“Use new shortcut in”中选择"“Text Editor ”<span
    class="Apple-converted-space"> </span>\
    \
          <span
    class="Apple-converted-space"> </span>[![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207145076.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/20110531220710522.png)<span
    class="Apple-converted-space"> </span>\
7.  **啊，选择后快捷键没有了。**<span
    class="Apple-converted-space"> </span>\
    \

    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207208593.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207169546.png)<span
    class="Apple-converted-space"> </span>\
8.  **再按一次，然后点击“Assign”按钮<span
    class="Apple-converted-space"> </span>\
    \
    **
    [![image](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207251902.png "image")](http://images.cnblogs.com/cnblogs_com/greenerycn/201105/201105312207228395.png)<span
    class="Apple-converted-space"> </span>\
9.  **再按“OK” 确认，并关闭“Customize”对话框。**

</div>

 

      这时候，这个快捷键也就生效了。试试吧。



#Visual Studio 2008

##程序数据库管理器不匹配；请检查安装

之前用了VS2008命令行编译，复制了mspdb80.dll文件过来，删除即可，目录:D:\\Program Files\\Microsoft Visual Studio 9.0\\VC\\bin。


#Reference
* <http://msdn.microsoft.com/zh-cn/library/ff636699.aspx>
* <http://blog.csdn.net/tszhao/article/details/6753276>

