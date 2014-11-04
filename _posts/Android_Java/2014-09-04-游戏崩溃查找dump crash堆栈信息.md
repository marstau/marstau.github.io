---
layout: post
title: 游戏崩溃查找dump crash堆栈信息
category: 游戏技术
tags: android／java
keywords: 
description: 
---

 

1.  在android上运行程序至崩溃

2.  在cmd中输入\
     adb logcat | ndk-stack -sym \$PROJECT\_PATH/obj/local/armeabi

    ,即可找到崩溃地址比如

    ajundeMacBook-Pro:\~ ajun\$ adb logcat | ndk-stack -sym
    \$PROJECT\_PATH/obj/local/armeabi 

    Build fingerprint:
    'Coolpad/yulong89\_td\_jb/MT6589\_8190Q:4.1.2/JZO54K/4.1.027.P0.131126.8190Q:user/release-keys'

    pid: 9667, tid: 9686, name: Thread-6003  \>\>\>
    com.shbreak.xinchang.jd \<\<\<

    signal 11 (SIGSEGV), code 1 (SEGV\_MAPERR), fault addr 00000001

    Stack frame \#00  pc 00226c42
     /mnt/asec/com.shbreak.xinchang.jd-1/lib/libgame.so
    (TitleLayer::onStartClicked(cocos2d::CCObject\*, unsigned int)+17)

    Stack frame \#01  pc 002736f9
     /mnt/asec/com.shbreak.xinchang.jd-1/lib/libgame.so
    (cocos2d::CCActionInterval::startWithTarget(cocos2d::CCNode\*)+4)

3.  <span style="font-family:微软雅黑, sans-serif;">输入</span>

    <span style="font-family:微软雅黑, sans-serif;"><span
    style="font-family:Menlo;font-size:11px;line-height:normal;">arm-linux-androideabi-addr2line</span> -e
    obj/local/armeabi/libgame.so 00226c42</span>

    <span
    style="font-family:微软雅黑, sans-serif;">,即可找到崩溃的文件及其行号。</span>

    <span
    style="font-family:'微软雅黑, sans-serif';">如果没加参数-e，则会出现</span><span
    style="font-family:Menlo;font-size:11px;line-height:normal;">'a.out':
    No such file</span>

    <span style="font-family:Menlo;"><span
    style="font-size:11px;line-height:normal;">宏定义的无法用addr2line定位到。</span></span>









