---
layout: post
title: TortoiseGit
category: 书籍与软件工具
tags: software
keywords: TortoiseGit, git
description: 

#### 图标不显示[More](http://blog.csdn.net/lishehe/article/details/8257545)

win+R，输入regedit，调出注册表信息，按下Ctrl+F,在注册表里搜索“ShellIconOverlayIdentifiers”
3。将TortoiseAdded、TortoiseConflict……TortoiseUnversioned分别重命名，命名为0TortoiseAdded、1TortoiseConflict……8TortoiseUnversioned。

#### 保存账号密码[More](http://my.oschina.net/jjyuangu/blog/232798?p=1)
在.git/config文件下添加如下代码：

```
[credential]
	helper = store
```

输入一次密码后，下次就会记住密码了。
