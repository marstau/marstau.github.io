---
layout: post
title: NDK工具之 addr2line
category: 游戏技术
tags: android／java
keywords: 
description: 
---

<span style="font-size:12px;font-family:SimSun;"> </span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
---------------------------------------------------------

C:\\Documents and Settings\\Lione\><span
style="color:#e53333;">E:</span>

E:\\\><span
style="color:#e53333;">cd E:\\Workspaces\\syjt\\trunk\\project\\android</span>

E:\\Workspaces\\syjt\\trunk\\project\\android\><span
style="color:#e53333;">addr2line -C -f -e obj/local/armeabi/libsyjt.so 00425185</span>

mapping0\_forward

D:/Development/Software/android-ndk-r7/samples/3guu/XC/trunk/project/android/jni/../../../src/libvorbis/mapping0.c:681

E:\\Workspaces\\syjt\\trunk\\project\\android\>

<span style="font-size:12px;font-family:SimSun;"><span style="color:#e53333;">From : </span>[<span style="color:#e53333;">http://blog.csdn.net/lcaliang/article/details/7388916</span>](http://blog.csdn.net/lcaliang/article/details/7388916)</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">Usage: arm-eabi-addr2line [option(s)] [addr(s)]</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">for example:</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
--------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">D:\\gat\\iBox\\TRUNK\\lib\>arm-eabi-addr2line -e "D:\\\*.out.symbols\\alps\\out\\target\\product\\\*\\symbols/../../../../../kernel/vmlinux" c0037aa0\
 </span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">The options are:\
   @\<file\>                Read options from \<file\>\
   -b --target=\<bfdname\>  Set the binary file format\
   -e --exe=\<executable\>  Set the input file name (default is a.out)\
   -i --inlines           Unwind inlined functions\
   -j --section=\<name\>    Read section-relative offsets instead of addresses\
   -s --basenames         Strip directory names\
   -f --functions         Show function names\
   -C --demangle[=style]  Demangle function names\
   -h --help              Display this information\
   -v --version           Display the program's version.</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">常用-f， -C， -e.</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------

<span style="font-family:SimSun;"></span><span style="font-size:12px;"> </span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">KE debug的方法：</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">首先在在dump的kernel log中找[\<\>]这样的东西，然后再通过addr2line在vmlinux中找到其对应的line</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
----------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">有的地址，比如bf开头的是debug不了的，因为3GB-8MB \~ 3GB是kernel module载入的地址，而vmlinux中没有module的symbol table.</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">NE debug的方法</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
----------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">首先在ne log中找signal 11 (SIGSEGV), fault addr baae8fd1</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
----------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">的东西，找到后</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
----------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">通过分析，如果fault addr 是deaddead，那就表示heap error出现，然后再看是deadadd0，就是heap corruption,如果是deadadd0，就是heap usage error.</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">然后将heap信息保存下载</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">然后再通过将signal 11 (SIGSEGV), fault addr baae8fd1中的地址通过addr2line来进行转换得道C库出错的地址</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
------------------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">NE的decode是通过</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">         \#01  pc 0001cd4a  /system/lib/libc.so</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">中间后面libc.so的路径，将其加到symbols path后面，然后再通过addr2line来解析出来。</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
----------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">arm-eabi-addr2line -f -C -e D:\\gat\\Department\\SP\_SS\\OSS5\_ST\_Share\\GAT\\TRUNK\\Test\_Cases\\NE\\ztemt73v2\_ALPS.GB.p52\_eng.out.symbols\\alps\\out\\target\\product\\ztemt73v2\\symbols\\system\\lib\\libc.so 0001cd0e</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">输出的话就是</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
--------------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;">\_\_findenv\
 /alps/GB/Of/alps/bionic/libc/stdlib/getenv.c:90</span> {style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;"> </span> {.entry-title style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
---------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;"> </span> {.entry-title style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
---------------------------------------------------------

<span style="font-size:12px;font-family:SimSun;"> </span> {.entry-title style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
---------------------------------------------------------

[<span style="font-size:12px;font-family:SimSun;">Android 调试中 addr2line 命令的使用</span>](http://blog.163.com/bjtornado@yeah/blog/static/695104842011412104151898) {.entry-title style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span style="font-family:SimSun;">\
 <span style="font-size:12px;">关于调试：调试中addr2line命令的使用。\
 问题引出：i850的wifi定位开启后，在使用goole maps时出现rootfs重启现象，打印的log信息如下：\
 ／／／／／／／／／／／／／／／／／／／／／／／／／／\
 I/DEBUG   ( 3411): \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\* \*\*\*</span></span> {.entry-title style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
-------------------------------------------------------------------------------------------------------------------------------------------------

 {.entry-title style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}

  ----------------------------------------------------------
  <span style="font-size:12px;font-family:SimSun;"></span>
  ----------------------------------------------------------

\
 <span style="font-size:12px;font-family:SimSun;">I/DEBUG   ( 3411): Build fingerprint: 'PROWAVE/i850/i850/:Eclair/ECLAIR/eng.zhangjiejing.20100430.113200:eng/test-keys'\
 I/DEBUG   ( 3411): pid: 3436, tid: 3475  \>\>\> system\_server \<\<\<\
 I/DEBUG   ( 3411): signal 11 (SIGSEGV), fault addr 00000000\
 I/DEBUG   ( 3411):  r0 26ba7eec  r1 403f3c49  r2 e98cf6f4  r3 405e58ae\
 I/DEBUG   ( 3411):  r4 00000000  r5 00000000  r6 4229b6cc  r7 48fecec8\
 I/DEBUG   ( 3411):  r8 490ecd84  r9 48feceb4  10 48fece9c  fp 00314d30\
 I/DEBUG   ( 3411):  ip ad3527cd  sp 490ecd68  lr ad3527eb  pc 00000000  cpsr 00000010\
 I//system/bin/dhcpcd( 3673): wlan0: looping\
 I//system/bin/dhcpcd( 3673): wlan0: signal\_fd: 4,fd:5\
 I/ActivityManager( 3436): Starting activity: Intent { act=</span>[<span style="font-size:12px;font-family:SimSun;">Android</span>](http://www.linuxidc.com/topicnews.aspx?tid=11 "Android")<span style="font-size:12px;font-family:SimSun;">.intent.action.MAIN cat=[android.intent.category.HOME] flg=0x10200000 cmp=com.android.launcher/.Launcher }\
 D/LocationManager( 3777): removeUpdates: listener = P.a@43da64b8\
 </span><span style="color:red;"><span style="font-size:12px;font-family:SimSun;">I/DEBUG   ( 3411):          \#00  pc 00000000 \
 I/DEBUG   ( 3411):          \#01  pc 000527e8  /system/lib/lib</span>[<span style="font-size:12px;font-family:SimSun;">Android</span>](http://www.linuxidc.com/topicnews.aspx?tid=11 "Android")<span style="font-size:12px;font-family:SimSun;">\_runtime.so\
 I/DEBUG   ( 3411):          \#02  pc 0000f1f4  /system/lib/libdvm.so</span></span><span style="font-family:SimSun;">\
 <span style="font-size:12px;">I/DEBUG   ( 3411):<span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411): code around lr:\
 I/DEBUG   ( 3411): ad3527d8 69e19806 694c9000 1c191c10 9b059a04<span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411): ad3527e8 b00247a0 46c0bd10 00017868 00006728<span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411): ad3527f8 4c0fb570 447c4d0f 6b2e1965 d1112e00<span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411):<span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411): stack:\
 I/DEBUG   ( 3411):     490ecd28  00000013 <span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411):     490ecd2c  ad05f661  /system/lib/libdvm.so\
 I/DEBUG   ( 3411):     490ecd30  410c2aec  /dalvik-LinearAlloc (deleted)\
 I/DEBUG   ( 3411):     490ecd34  ad0560f7  /system/lib/libdvm.so\
 I/DEBUG   ( 3411):     490ecd38  400292d8  /mspace/dalvik-heap/zygote/0 (deleted)\
 I/DEBUG   ( 3411):     490ecd3c  410c2aec  /dalvik-LinearAlloc (deleted)\
 I/DEBUG   ( 3411):     490ecd40  000003dc <span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411):     490ecd44  ad0591f5  /system/lib/libdvm.so\
 I/DEBUG   ( 3411):     490ecd48  42200d44  /data/dalvik-cache/system@@classes.dex\
 I/DEBUG   ( 3411):     490ecd4c  42200d44  /data/dalvik-cache/system@@classes.dex\
 I/DEBUG   ( 3411):     490ecd50  4232b87d  /data/dalvik-cache/system@@classes.dex\
 I/DEBUG   ( 3411):     490ecd54  00000000 <span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411):     490ecd58  4264aa04  /data/dalvik-cache/system@@classes.dex\
 I/DEBUG   ( 3411):     490ecd5c  410c1cbc  /dalvik-LinearAlloc (deleted)\
 I/DEBUG   ( 3411):     490ecd60  df002777 <span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411):     490ecd64  e3a070ad <span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411): \#01 490ecd68  43160000 <span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411):     490ecd6c  ad05f661  /system/lib/libdvm.so\
 I/DEBUG   ( 3411):     490ecd70  490ecda8 <span class="Apple-converted-space"> </span>\
 I/DEBUG   ( 3411):     490ecd74  ad00f1f8  /system/lib/libdvm.so\
 W/ActivityManager( 3436): Activity pause timeout for HistoryRecord{43d6cd48 com.google.</span></span>[<span style="font-size:12px;font-family:SimSun;">Android</span>](http://www.linuxidc.com/topicnews.aspx?tid=11 "Android")<span style="font-size:12px;font-family:SimSun;">.apps.maps/com.google.android.maps.MapsActivity}\
 wait for fb sleep Enter\
 D/WifiService( 3436): releaseWifiLockLocked: WifiLock{NetworkLocationProvider type=2 binder=</span>[<span style="font-size:12px;font-family:SimSun;">Android</span>](http://www.linuxidc.com/topicnews.aspx?tid=11 "Android")<span style="font-size:12px;font-family:SimSun;">.os.Binder@43bfb998}\
 binder: release 3436:3560 transaction 22233 in, still active\
 binder: send failed reply for transaction 22233 to 3777:3777\
 I/DEBUG   ( 3411): debuggerd committing suicide to free the zombie!\
 I/DEBUG   ( 3855): debuggerd: Apr 14 2010 14:24:22\
 I/ServiceManager( 2066): service 'usagestats' died\
 I/ServiceManager( 2066): service 'account' died\
 ／／／／／／／／／／／／／／／／／／／／／／／／／／\
 </span><span style="color:blue;"><span><span style="font-size:12px;font-family:SimSun;">注意到红色部分，这就是程序执行时的栈！显然第一个pc指针的值为0，也就是pc指针为空，这就是问题之所在，接下来就是要定位这个问题，上边说了，这里是程序执行时的栈，那么\#01  pc 000527e8  /system/lib/lib</span>[<span style="font-size:12px;font-family:SimSun;">Android</span>](http://www.linuxidc.com/topicnews.aspx?tid=11 "Android")<span style="font-size:12px;font-family:SimSun;">\_runtime.so   这个地址就是我们要找的问题的范围，因为显然是后者先入栈的，所以显然前者包含于后者，那么通过如下命令用地址定位一下源码的位置：</span></span><span style="font-family:SimSun;">\
 </span><span style="color:green;"><span style="font-family:SimSun;"><span style="font-size:12px;">cpp@cpp:\~/r7\_0422\$   ../gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-addr2line  -e out/target/product/i850/<span style="font-weight:bold;">symbols</span>/system/lib/lib</span></span>[<span style="font-size:12px;font-family:SimSun;">Android</span>](http://www.linuxidc.com/topicnews.aspx?tid=11 "Android")<span style="font-size:12px;font-family:SimSun;">\_runtime.so 000527e8\
 frameworks/base/core/jni/</span>[<span style="font-size:12px;font-family:SimSun;">Android</span>](http://www.linuxidc.com/topicnews.aspx?tid=11 "Android")<span style="font-size:12px;font-family:SimSun;">\_location\_GpsLocationProvider.cpp:397\
 cpp@cpp:\~/r7\_0422\$</span></span><span style="font-family:SimSun;"><span style="font-size:12px;"><span class="Apple-converted-space"> </span>\
\
 <span>看 到源码的397行是一个函数，那么000527e8就是这个函数的入口地址了。继而，pc 000000  对应的调用就应该在该函数内部，看到该函数内部只是做了对另一个函数指针的调用而已，所以我们可以断定这个函数指针的值为空，显然调用一个空的指针函数是 错误的。所以需要给这个函数指针在早些时候赋值一下问题就可以解决了！</span></span></span></span>\
\
 <span style="font-size:12px;font-family:SimSun;">关于addr2line的一点补 充：如果可执行文件中没有包括调试符号，您将获得??:0 作为响应。 还有在linux中的readelf命令可以读取可执行文件的相关信息，比如有一个可执行文件 aa.elf 则可以这么使用： readelf -h aa.elf 参数－h读取可执行文件的head信息。</span> {.entry-title style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0px;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:26px;padding-top:0px;font-style:normal;font-family:Arial;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------







