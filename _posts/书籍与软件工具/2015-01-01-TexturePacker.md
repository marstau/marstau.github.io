---
layout: post
title: TexturePacker
category: 书籍与软件工具
tags: software／tool
keywords: TexturePacker,mac,ios
description: 
---


anti texturepacker无法解析:
缺少如下部分


```
<key>sourceColorRect</key>
<string> { { 463,193}, { 34,34 } } </string>
```

命令行打包

```
TexturePacker --enable-rotation --scale 1.0 --multipack --border-padding 2 --pack-mode Good --shape-padding 2 --padding 0 --max-size 4096 --algorithm Basic --basic-sort-by Name --basic-order Ascending --size-constraints AnySize --trim-mode None --data $OutputPath/$withouSuffix".plist" --format cocos2d --texture-format pvr2ccz --opt RGBA8888 --content-protection 39a8624bdf7cdd8416dddbeec7e61299 --sheet $OutputPath/$withouSuffix".pvr.ccz" $SRCPath/$withouSuffix
```