---
layout: post
title: Beyond Compare
category: 软件工具
tags: software
keywords: 
description: 
---

## Installation

#### MAC[More](https://github.com/qq5889/learn/blob/master/Beyond%20Compare%20for%20Mac%20%E6%97%A0%E9%99%90%E8%AF%95%E7%94%A8%E6%96%B9%E6%B3%95.md) - TODO


1. 选中图标，右键点击“显示包内容”，逐步进入 Beyond Compare 应用程序的 MacOS 目录下(/Applications/Beyond Compare.app/Contents/MacOS)
2. 将主启动程序 BCompare 重命名为 BCompare_real

3. 在同级目录下新建一个脚本文件,命名为 BCompare,这样 BCompare 在启动的时候就会执行该脚本文件,修改权限`chmod a+x BCompare`

```
#!/bin/bash
# 修改删除路径为你确认的路径
rm "/Users/$USER/Library/Application Support/Beyond Compare 5/registry.dat"
"`dirname "$0"`"/BCompare_real $@
```

即可无限试用


## FAQ

#### 相同文件比较却标红[More](http://blog.chinaunix.net/uid-20753106-id-3966647.html)

打开后，再关闭，就变黑了。因为，BC有一个快速比较，比较文件名再比较时间，就认为是不同的文件了。

选择“会话”->“会话设置”里面的 “比较”选项卡，勾上“比较内容”->“二进制比较”

#### BeyondCompare之忽略换行符(pc/mac/unix)比较文件[More](https://blog.csdn.net/husion01/article/details/104309821)

```
1 打开要比较的两个文件夹。

2 任意打开一个不同的文件。

3 选择 会话–>会话设置–>重要 (打开文件后再打开会话设置才能看得到)
去掉下方的“比较行终止符的勾选”
选择最下面的“用于父会话中的所有文件”
点确定。

4 关闭文件比较窗口，回到文件夹比较窗口。

5 点击 会话–>会话设置–>比较
比较内容，选择 “基于规则的比较”。
点确定。

6 编辑–>完全刷新。
```

#### 过滤

```
*[0-9].asset
```

## Error

#### 这个授权密钥已被吊销

删除目录
```
C:\Users\user\AppData\Roaming\Scooter Software\Beyond Compare 4
```
下的所有文件(但需要重新注册)

4.2.9:
```
H1bJTd2SauPv5Garuaq0Ig43uqq5NJOEw94wxdZTpU-pFB9GmyPk677gJ
vC1Ro6sbAvKR4pVwtxdCfuoZDb6hJ5bVQKqlfihJfSYZt-xVrVU27+0Ja
hFbqTmYskatMTgPyjvv99CF2Te8ec+Ys2SPxyZAF0YwOCNOWmsyqN5y9t
q2Kw2pjoiDs5gIH-uw5U49JzOB6otS7kThBJE-H9A76u4uUvR8DKb+VcB
rWu5qSJGEnbsXNfJdq5L2D8QgRdV-sXHp2A-7j1X2n4WIISvU1V9koIyS
NisHFBTcWJS0sC5BTFwrtfLEE9lEwz2bxHQpWJiu12ZeKpi+7oUSqebX+
```



## Reference

* []()
