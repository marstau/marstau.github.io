---
layout: post
title: TortoiseSVN
category: 书籍与软件工具
tags: software／tool
keywords: TortoiseSVN, svn
description: 
---

-   **SVN提交失败**\
     先清除 所有缓存(settings-\>saved data),然后再clean up,顺序不能颠倒.
-   **文件夹图标不能正常显示**\

    Win7上,在安装了TortoiseSVN之后，发现本应在windows资源管理器出现的版本状态显示图标覆盖并没有出现。但能够正常进行各种svn操作。

    查看了各种设置都没什么问题。最后发现直接重新安装一次TortoiseSVN，电脑重启之后这些图标覆盖效果就自动正常显示了。

    **应该是网络还不正常导致没有及时连接到svn服务器的原因**。

-   **<span style="color:#e53333;">TortoiseSVN</span><span
    style="color:#e53333;">右下角图标无法正常显示</span>**

    近日，突然发现，TortoiseSVN 的几个覆盖图标消息了，包括：忽略图标、未版本化

    图标。奇怪，好端端的覆盖图标为什么会消失呢？为什么只有这两个图标消失呢，而别的覆

    盖图标（如：已版本化图标、已修改图标、新增图标等）都还好端端的呢？

    开始以为是 TortoiseSVN 坏了，于是重装，但结果还是一样。于是找了好多资料，终

    于发现症结所在－－原来是Windows 对覆盖图标类型的数据限制的原因。Windows 最多

    只允许15 个覆盖图标，它自己又用了几个，结果给用户用的就11 个左右了（这个限制一

    直都Windows 7 都没有放宽，真不知微软是怎么想的）。TortoiseSVN 标准会使用７个

    （普通图标、已修改图标、冲突指示图标、已删除图标、新增文件图标、忽略图标、未版本

    化图标等），这样剩下可用的就少之又少了。如果再安装了网盘软件（如：快盘，Dropbox

    等），那就更惨了，它们各自又会使用3 个左右的覆盖图标，这样，覆盖图标当然远远不

    够用了。

    那么，覆盖图标的设置保存在Windows 的哪个地方呢？如果有超过11 个的覆盖图标，

    Windows 如何选择显示哪些屏蔽哪些呢？

    所有应用程序的覆盖图标都需要在注册表

    **“HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVer**

    **sion\\Explorer\\ShellIconOverlayIdentifiers”**下面增加一个项目，当需要显示覆

    盖图标时，Windows 会按照项目名称的字母顺利依次查询在这些项目里所指示的接口，以

    检测是否有覆盖图标，当检测到11 个有效的接口后，Windows 就会自动停止继续向下检

    测，这样，后来的覆盖图标就不会显示了。

    知道原理了，解决问题就好办了。我们可以分析一下在这个注册表项下的所有项目，

    看哪些覆盖图标是需要的，哪些是不需要的，把不需要的项目的名称改一下，前面加个“z”，

    这样，这个表项按字母排序就自动排到最后面了。哪些是不需要的呢？比如：网盘的“正在

    同步图标”就没什么用，可以去掉。其它的，可以自己看着办了。

    如果你进行调整后，把TortoiseSVN 的所有覆盖图标全部提前，但TortoiseSVN 仍

    然不会显示忽略图标、未版本化图标。为什么呢？研究了TortoiseSVN 的源代码才发现，原

    来TortoiseSVN 会自己分析在ShellIconOverlayIdentifiers 中注册的覆盖图标数，如果注

    册了太多，TortoiseSVN 会自动屏蔽一些无关紧要的图标，目的是让别人软件的覆盖图标尽

    可能有机会显示。也就是说，如果你希望，显示TortoiseSVN 的这些它自己认为“无关紧

    要”的覆盖图标，你需要删除一些别的程序的图标，把覆盖图标的总数减小到13 个以下，

    这时，TortoiseSVN 才会正常显示忽略图标、未版本化图标等无关紧要的图标。

    ![](http://files.note.sdo.com/XbPJ4~kcsZ12wE2C400ilD)

-   **TortoiseSVN提交提示423 Locked**

    "TortoiseSVN-\>get locks"在对话框的左下角有个steal the locks选项，勾选这个选项，你就可以窃取别人的锁。然后你就成为锁的拥有者，TortoiseSVN-\>release locks,释放锁，然后commit提交即可。(not
    implemented, what does it mean?)

-   **<span style="color:#e53333;">从服务端check
    out下资源,地址格式是</span>**

    <http://192.168.1.39/svn/xc2d/client/3guu/syjt>\
     (记住末尾没有加**/**)

-    path not found\

    ![](maiku://attachment/{3AE5A903-A378-4CC0-85DA-D24A5F06A3F5}.png)将此目录下的.svn文件删除,重新提交即可。

-   405 Method Not Allowed\
     删除此目录,到上一层目录更新此目录所有文件,然后\
      删除出现错误的文件夹

    SVN Update

    这时服务器上存在的文件夹会出现在本地

    删除原有的文件夹

    SVN Commit

    重新创建文件夹

    SVN Commit

-   SVN的文件删除后,然后commit即可，就可以在服务器上删除此文件\
     ps:提交的时候显示的是deleted或者missing
-   **<span style="color:#e53333;">若提交后,</span><span
    style="color:#e53333;">还是未改变</span>**\
     执行clean up即可。
-   自己可以连VisualSVN服务器，局域网内的其他人无法连接\

    将address设为ip的格式(包含了端口就可以正常连了一开始用的是[https://www-2c1adf32d78/svn/wmw/，所以对方无法连。)](https://www-2c1adf32d78/svn/wmw/)<https://192.168.1.100:8443/svn/wmw/>









