---
layout: post
title: APP_STL := gnustl_static  APP_CPPFLAGS := -frtti  APP_CPPFLAGS += -fexceptions 
category: 编程开发
tags: cocos2dx
keywords: 
description: 
---

<span style="color:#011993;">\
 </span>

In file included from
/Users/mars/Working/projects/zhanguo/sengoku/trunk/xinchang/sengoku/proj.android.OPPO/../libs/cocos2dx/platform/android/CCApplication.h:4:0,

                 from jni/../../Classes/AppDelegate.h:12,

                 from jni/sengoku/main.cpp:1:

jni/../../libs/cocos2dx/platform/CCCommon.h:29:20: fatal error:
iostream: No such file or directory

compilation terminated.

make: \*\*\* [obj/local/armeabi/objs/game\_shared/sengoku/main.o] Error
1

make: \*\*\* Waiting for unfinished jobs....

In file included from jni/../../Classes/AppCommon.h:32:0,

                 from
jni/../../Classes/Scenes/City/Layers/Menus/Promotion/CMFirstPurchase.h:4,

                 from
jni/../../Classes/Scenes/City/Layers/Menus/Promotion/CMFirstPurchase.cpp:1:

jni/../../libs/plugin/protocols/include/ProtocolAnalytics.h:28:15: fatal
error: map: No such file or directory

compilation terminated.

make: \*\*\*
[obj/local/armeabi/objs/game\_shared/\_\_/\_\_/Classes/Scenes/City/Layers/Menus/Promotion/CMFirstPurchase.o]
Error 1

In file included from jni/../../Classes/AppCommon.h:32:0,

                 from
jni/../../Classes/Scenes/City/Layers/Menus/Leaderboard/CMLeaderboardSub.h:4,

                 from
jni/../../Classes/Scenes/City/Layers/Menus/Leaderboard/CMLeaderboardSub.cpp:1:

jni/../../libs/plugin/protocols/include/ProtocolAnalytics.h:28:15: fatal
error: map: No such file or directory

compilation terminated.

make: \*\*\*
[obj/local/armeabi/objs/game\_shared/\_\_/\_\_/Classes/Scenes/City/Layers/Menus/Leaderboard/CMLeaderboardSub.o]
Error 1

make: Leaving directory
\`/Users/mars/Working/projects/zhanguo/sengoku/trunk/xinchang/sengoku/proj.android.OPPO'

<span style="color:#011993;">solution:</span>

<span style="color:#011993;">在Application.mk中添加</span>

<span style="color:#011993;">APP\_STL :</span>= gnustl\_static

APP\_CPPFLAGS :<span style="color:#000000;">= -frtti</span>

APP\_CPPFLAGS +<span style="color:#000000;">= -fexceptions</span>






