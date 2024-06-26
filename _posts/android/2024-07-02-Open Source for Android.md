---
layout: post
title: Open Source for Android
category: 编程开发
tags: android
keywords: 
description: 
---

#### [FBReaderJ](http://www.fbreader.org/FBReaderJ/)
FBReaderJ用于Android平台的电子书阅读器，它支持多种电子书籍格式包括：oeb、ePub和fb2。此外还支持直接读取zip、tar和gzip等压缩文档。

![bookinfo-rus.png](http://www.open-open.com/projectimage/bookinfo-rus.png)
[](http://www.cnblogs.com/TerryBlog/admin/open274375.htm)[](http://www.fbreader.org/FBReaderJ/)[](http://www.cnblogs.com/TerryBlog/admin/open274375.htm)[](http://www.fbreader.org/FBReaderJ/) 

#### [Angle](http://code.google.com/p/angle/)
Angle是一款专为Android平台设计的，适合快速开发的2D游戏引擎，基于OpenGL
ES技术开发。该引擎全部用Java代码编写，并且可以根据自己的需要替换里面的实现。

#### [android-shuffle](http://code.google.com/p/android-shuffle/)
android-shuffle是一个GTD（Getting Things Done）个人备忘记事本。
![3429748650_97b07951e5_o.png](http://www.open-open.com/projectimage/3429748650_97b07951e5_o.png)
![4299625001_01b6c3d1ef_o.png](http://www.open-open.com/projectimage/4299625001_01b6c3d1ef_o.png) 

#### [Open GPS Tracker](http://code.google.com/p/open-gpstracker/)
GPSTracker是一个能够使用Android地图记录你的驾车或旅行路线的项目，出发前打开软件选择开始记录，你所经过的路线就会实时显示在地图上，同时还会显示当前的行驶速度。程序会按用户自己设置的标题自动存路线留做日后查看，也可以把路线分享给朋友。GPSTracker项目是一个Map方面的完整应用，包括两个主要组成部分，第一部分是一个收集和存储GPS追踪数据的系统服务，第二部分是Map
Activity控制跟踪数据并在地图上显示提供接口。GPSTracker项目用到了osmdroid项目的部分功能，其中OpenStreetMap是一个可供自由编辑的世界地图，允许您查看，编辑或者使用世界各地的地理数据来帮助您。

#### [Rokon](http://code.google.com/p/rokon/)
Rokon是一个强大、可扩展、灵活的Android 2D游戏引擎，基于OpenGL
ES技术开发，物理引擎为Box2D，因此能够实现一些较为复杂的物理效果，有人将它称为Cocos2d-iPhone引擎的Android版（因为业务逻辑和编码风格上也确实很像）。
![drop_block_ss1.png](http://www.open-open.com/projectimage/drop_block_ss1.png)
![drop_block_ss3.png](http://www.open-open.com/projectimage/drop_block_ss3.png)

#### [LGame](http://code.google.com/p/loon-simple/)
LGame是一款国人开发的Java游戏引擎，有Android及PC(J2SE)两个开发版本。其底
层绘图器LGrpaphics封装有J2SE以及J2ME提供的全部Graphics
API（PC版采用Graphics2D封装，Android版采用Canvas模拟实现），所以能够将J2SE或J2ME开发经验直接套用其中，两版本
间主要代码能够相互移植。Android版内置有Admob接口，可以不必配置XML直接硬编码Admob广告信息。该引擎除了基本的音效、图形、物理、精灵等常用组件以外，也内置有Ioc、xml、http等常用Java组件的封装，代价是jar体积较为庞大，PC版
已突破1.2MB，Android版有所简化也在500KB左右。此外，该引擎还内置有按照1:1实现的J2ME精灵类及相关组件，可以将绝大多数
J2ME游戏平移到Android或PC版中。
 ![lgame_act.gif](http://www.open-open.com/projectimage/lgame_act.gif) 

#### [OpenIntents](http://code.google.com/p/openintents/)
通过"Intents"，Android给连接软件和动态替换组件提供了优秀的基础。Google定义了一批intents（如：打电话啊，联系人清单上选择一个联系人，打开浏览器，电池更换的时候提供提示，等等，详细清单请看：available
intents和intent class)
但是任何程序可以自由定义额外的intents和content-providers。我们可以很容易的联想到独立开发的程序（比如在这次的比赛中）极少有可能会和新定义的intents和接口良好的一起工作。
我们这个项目的目标是收集很可能在多个项目中都有用的想法（而且很可能已经被其他独立程序员实现了），定义一批比较合理且扩展性比较好的一批intents和接口，提供基础但稳定有效的实现，可以被其他Android程序所应用的，特别是其他参加比赛的程序员们。OpenIntents本身也会参加这次的比赛。我们提供小的样品程序来演示OpenIntents的用法和特性。
因为我们专注于经常被使用到的那些intents，Google也很可能在不久的将来提供他们自己的标准intents（比如关于日历的。。。）当那个发生的时候，我们会提供透明的接口来直接呼叫Google的实现方法，而你已有的程序可以直接使用Google的新功能而不需要改变任何东西。而且，由于你的程序在设计初期就是已经支持intents的了，当Google的intents出来的时候，你可以很方便的直接他们的intents。还有可能的是Google可能会借用一些OpenIntents开发的intents。无论如何，如果你的程序使用OpenIntents，在和其他使用OpenIntents程序提供互相支持的同时，你会得到额外的附加值，从而全面增强用户体验。
![openintents1.png](http://www.open-open.com/projectimage/openintents1.png)
![mainscreen2.png](http://www.open-open.com/projectimage/mainscreen2.png) 
#### [android-bluetooth](http://code.google.com/p/android-bluetooth/)
非常官方Android Bluetooth
API支持远程设备扫描、远程设备配对，服务发现（SDP）和客户端RFCOMM串行连接。

#### [Android apktool](http://code.google.com/p/android-apktool/)
Android
apktool是一个用来处理APK文件的工具,可以对APK进行反编译生成程序的源代码和图片、XML配置、语言资源等文件,也可以添加新的功能到APK文件中。用该工具来汉化Android软件然后重新打包发布是相当简单的。

#### [quake2android](http://code.google.com/p/quake2android/)
quake2android是一个将《雷神之锤2》（Quake2）游戏移植到Android平台上的开源项目。支持谷歌Nexus
One，三星Galaxy S，摩托罗拉Droid X等手机。
 ![Quake2.jpg](http://www.open-open.com/projectimage/Quake2.jpg) 
####  [AndEngine](http://code.google.com/p/andengine/)
AndEngine是一个开源的，基于OpenGL实现的Android 2D游戏引擎。
[这里](http://code.google.com/p/andengineexamples/)提供一些基于AndEngine实现的示例。

#### [android-opencv](http://code.google.com/p/android-opencv/)
 
android-opencv是一个将OpenCV移到Android手机平台的开源项目，该项目使用OpenCV最新的一个分枝并利用一个改良过的Android
NDK进行构建。

#### [android-dalvik-vm-on-java](http://code.google.com/p/android-dalvik-vm-on-java/)
 
android-dalvik-vm-on-java该项目的目标是开发一个采用Java实现的Android
Dalvik虚拟机。目的是为了学习Dalvik
VM的思想和架构。当前支持Dalvik可执行文件格式（.dex），完整的Dalvik指令系统，J2ME
CLDC API，多线程（包括同步阻塞，等待和通知）。


#### [Android PC_BCR](http://code.google.com/p/android-pcbcr/)
Android PC_BCR让你能够使用你的Android手机做为PC机的外围条形码扫描仪。扫描的条形码将通过WiFi网络连接传PC机中。这个开源项目由多个组件组成，在手机设备上PC_BCR使用ZXing扫描仪器来扫描条形码，然后程序通过网络传到PC中，PC中有专门的PC_BCR程序接收。

#### android-sms 
 
android-sms能够将Android SMS短信备份到Gmail中的Android开源程序。
项目地址：<http://code.google.com/p/android-sms/>

#### [jPCT-AE](http://www.jpct.net/jpct-ae)
 
jPCT-AE是一个将jPCT移植至Android平台上3D图形引擎。
 ![karga1.jpg](http://www.open-open.com/projectimage/karga1.jpg)

#### [AndTweet](http://code.google.com/p/andtweet)
 
AndTweet是一个轻量级Twitter客户端，支持利用触摸和键盘进行快速操作。
![3328108955_a142931f3f_o.png](http://www.open-open.com/projectimage/3328108955_a142931f3f_o.png)
![3236629233_b9396a131c.png](http://www.open-open.com/projectimage/3236629233_b9396a131c.png)


#### [android-smspopup](http://code.google.com/p/android-smspopup/)
android-smspopup这个Android应用程序能够拦截收到的短消息并在一个弹出框中显示消息内容和联系人头像。此外还可以自定义LED颜色，振动模式，当第一次提醒显示没有看到时会重复提醒用户哪些信息没有看过。

#### [MyTracks](http://code.google.com/p/mytracks/)
 
MyTracks能够记录你在户外活动的GPS轨迹并实时显示时间，速度，距离和海拔等信息。还可以将这些信息上传至Google
Spreadsheets并在Google My Maps中显示。


#### [i-jetty](http://code.google.com/p/i-jetty/)
 
 
![ijetty-screen2.jpg](http://www.open-open.com/projectimage/ijetty-screen2.jpg)
i-jetty是一个将开源Web容器Jetty移植到Google
Android手机平台上的开源项目。让你可以在手机上运行现有的Web应用。


#### [webOdroid](http://www.webodroid.com/)
 
webOdroid这个开源项目提供了一组完整的工具，能够根据现有网站创建一个Android应用程序。它提供的特性包括：
-   一个功能齐全的RSS浏览器
-   能够显示文章列表的ListView或GridView控件。
-   提供易于定制的模板
-   在网站上执行远程搜索
-   根据文章标题提供搜索建议
-   异步下载和缓存RSS供稿和图片
-   动态抽取和裁剪文章的图片
-   通过一个专用的Joomla组件能够集成Joomla网站的搜索功能
![](http://www.open-open.com/projectimage/list.small.png)
![](http://www.open-open.com/projectimage/grid.small.png)

#### [android-json-rpc](http://code.google.com/p/android-json-rpc)
 
android-json-rpc是一个在android程序中使用的JSON-RPC客户端类库。它提供了一个简单的API来执行JSON-RPC服务调用。

#### [BikeRoute](http://code.google.com/p/bikeroute/)

BikeRoute是一个Android应用程序提供基于GPS线路计划和定位功能。支持A到B路径规划，附近的单车停放处的位置，一步一步的指示，路线图，卫星导航等功能。
 ![BikeRoute.jpg](http://www.open-open.com/projectimage/BikeRoute.jpg)
![BikeRoute.jpg](http://www.open-open.com/projectimage/BikeRoute2.jpg)


#### [Andorid PDF Viewer](http://andpdf.sourceforge.net/)
 
Andorid PDF Viewer是一个运行在ANDROID手机上的PDF文件查看器。它是pdf-rendere： <https://pdf-renderer.dev.java.net/>的一个移植实现。


#### [Spring Android](http://www.springsource.org/spring-android)
 
Spring Android 是Spring框架的扩展，用于简化 Android 本地应用程序的开发。

#### [AchartEngine](http://code.google.com/p/achartengine)
 
AChartEngine是一个针对Android程序开发的开源图表生成类库。支持以下几种图表类型：
<span id="result_box" class="short_text" lang="zh-CN"><span title=""
style="color:#000000;">折线图</span></span>
区域图
散点图
time chart
柱状图
饼状图
bubble chart
doughnut chart

range (high-low) bar chart

![](http://home.open-open.com/attachment/201012/5/2869_1291542881tX10.jpg)
 
<http://www.cnblogs.com/TerryBlog/admin/open290275.htm>
#### [Opencore](http://www.opencore.net)
 
Opencore是google联合packetvideo推出的多媒体开源框架，其中的h.264解码器在目前所有的开源h.264解码器中最好的，在win32和armv4上测试通过，性能好很多，大概提升20%!
OpenCore的另外一个常用的称呼是PacketVideo，它是Android的多媒体核心。在防站的过程中，PacketVideo是一家公司的
名称，而OpenCore是这套多媒体框架的软件层的名称。在Android的开发者中间，二者的含义基本相同。对比Android的其它程序
库，OpenCore的代码非常庞大，它是一个基于C++的实现，定义了全功能的操作系统移植层，各种基本的功能均被封装成类的形式，各层次之间的接口多
使用继承等方式。

 OpenCore是一个多媒体的框架，从宏观上来看，它主要包含了两大方面的内容：

     *
PVPlayer：提供媒体播放器的功能，完成各种音频（Audio）、视频（Video）流的回放（Playback）功能
     *
PVAuthor：提供媒体流记录的功能，完成各种音频（Audio）、视频（Video）流的以及静态图像捕获功能

#### [Android Tools](http://fieldbird.sourceforge.net/AndroidTools)
 
Android Tools是一个轻量级IDE用于创建、构建、安装和测试Android应用程序。可方便的通过点击访问Android的命令、目录和文件。它还提供一个内置的文本编辑器。Android
Tools能够让学习和使用Android变得更加简便。
![AndroidToolsBasicTab.jpg](http://www.open-open.com/projectimage/AndroidToolsBasicTab.jpg)

#### [android-binding](http://code.google.com/p/android-binding)
android-binding这个开源项目提供了一个框架用于将android view
widgets与数据模型相绑定。帮助您在android应用程序中实现MVC或MVVM模式。

#### [Robotium](http://code.google.com/p/robotium)

Robotium是一个测试框架能够方便你为Android应用程序编写强大、健壮的自动黑盒测试用例。利用Robotium的支持，用例开发人员能够编写功能、系统和验收测试方案Robotium支持Activities、Dialogs、Toasts、Menus和Context Menus。

#### [QuiteSleep](http://code.google.com/p/quitesleep)

QuiteSleep是一个Android2.0+应用程序，可以设置免打扰时间段。这个时间段内，打进来的电话将会被阻止并通过SMS或E-Mail发送预定义好的信息给打电话者告知他你正忙或正在睡觉等。

#### [fanfoudroid](http://code.google.com/p/fanfoudroid)

安能饭否是一款开源的饭否Android客户端 。目前支持功能：
消息/私信收发，后台提醒，回复/转发/收藏，查看/关注用户，拍照/图片上传。即将支持功能：
关注管理，随便看看。 ![5344789918_58acfe070b.jpg](http://www.open-open.com/projectimage/5344789918_58acfe070b.jpg)

#### Skylight1

Skylight1是一个开源的Java手机应用程序开发框架和一些Android应用程序与示例。


## Reference

