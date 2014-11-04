---
layout: post
title: android开发中遇到sqlite3 not found
category: 游戏技术
tags: android／java
keywords: 
description: 
---

From :<http://www.189works.com/article-53490-1.html>

今天发现小米中竟然没有<span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">sqlite3, </span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">敲入命令竟然是</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">sqlite3:not found</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">错误</span>

解决方法<span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">:</span>

1)挂载 <span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">/system</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">目录为可读写</span>

\>adb shell

\# mount -o remount,rw -t yaffs2 /dev/block/mtdblock3 /system

2)把<span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">sqlite3 push</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">到设备中</span>

\> adb push sqlite3 /system/xbin

3)修改权限

\# <span style="color:#e53333;">ch</span><span
style="color:#e53333;">m</span><span
style="color:#e53333;">o</span><span
style="color:#e53333;">d </span>4755 /system/xbin/sqlite3

<span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;color:#ff0000;padding-top:0px;word-wrap:break-word;">// <span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">非常非常重要的测试 试着执行</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">sqlite3</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">看是否能执行</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">,</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">如果不能执行则需要把</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">sqlite3</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">的依赖库文件再</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">push</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">到设备中</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">, </span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">如果</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">sqlite3</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">可以正常执行则不用</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">push libncurses.so(</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">此库文件是从</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">2.3.5</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">中提取</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">,</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">不保证都能用</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">,</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">经测试</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">4.0.3</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">上可用</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">.</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">如果不肯用</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">,</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">大家方可自行创建虚拟机</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">,</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">从虚拟机中提取</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">)</span></span>

\# sqlite3

\> adb push libncurses.so /system/lib

4)还原 <span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">/system</span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">为只读</span>

\#mount -o remount,ro -t yaffs2 /dev/block/mtdblock3 /system

 

注<span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:'Times New Roman';word-wrap:break-word;">: </span><span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">相关文件在压缩包中</span>

<span
style="padding-right:0px;padding-left:0px;font-size:14px;padding-bottom:0px;margin:0px;padding-top:0px;font-family:宋体;word-wrap:break-word;">[下载](http://www.189works.com/data/attachment/portal/et2/201204/ET27910201204120936351.rar)</span>








