---
layout: post
title: UI Engines
category: 编程开发
tags: GameEngine
keywords: 
description: 
---

## CEGUI

![](/Resources/UI引擎_1.jpg)

CEGUI是老牌的开源界面库了，最新版本是0.7.1，完全免费，也是Ogre官方推荐使用的界面库，Ogre1.6及以前的版本，都是内置支持的。使用它的商业游戏也非常多，比如天龙八部，火炬之光，仙剑四等。这也就证明CEGUI确实强大，可以完全达到商业应用级别，而且相关资料非常丰富，至少不用担心某个功能无法实现，因为你能碰到的问题，网上基本都有解决方案，经过这些大作的证明，就不要怀疑了：）。
但是功能强大是有代价的，就是它太庞大、复杂了，上手很困难。这些大作没有一个不修改CEGUI的，也就是说要真正用起来，或者说要用的好，还是要做点事的。那需要做多少事呢？不清楚。
PS:选择CEGUI的另一个好处是网上有流传的天龙八部的源代码，大概是天龙08或09年早期的版本，其中包含一套比较完善的CEGUI，比如中文显示，中文输入，字体颜色，表情，自适应窗口等都已实现，并且做了优化，效率上不用太担心，毕竟天龙用下来是没问题的。所以使用CEGUI碰到问题时，有现成的东西可以参考，非常难得。不过这个版本的CEGUI是0.4版的，0.7版CEGUI做了大量优化（请查阅相应的ChangeLog），还用老版本觉得有点太老了……（我没有具体测试过，不清楚效率到底提高了多少），而且这个项目也相当于也处在无人维护的状态，如果有问题或者要新增功能可能要自己解决。

## Ogre SDKTray

从Ogre1.7开始就不再内置支持CEGUI了，转而使用Ogre自己的SDKTray，“tray”是在ogre的overlay和material的基础上实现的，使用很容易理解和使用，但目前它还只是个半成品，无法应用到商业游戏中。

## QuickGUI

![](/Resources/UI引擎_2.jpg)

最新版本10.1，专为Ogre写的UI库，支持Ogre1.7，比起CEGUI来说，小巧了很多。
但是很遗憾，至今还有没有编辑器（作者的Blog上说正在开发，但是还没有发布），要靠手动编写xml文件，囧啊～～Ogre社区里从来没有人推荐使用这个。我只是简单看了下，感觉像是作者练手的项目（个人观点）。

## Hikari

![](/Resources/UI引擎_3.jpg)

Hikari可以让你使用Flash制作界面，最新版本0.3，完全免费，大家知道Flash动画是非常流行的，如果将Flash应用到游戏中，一定很拉风！Hikari就实现了这个功能，通过Flash.ocx将swf渲染成Ogre的Texture，然后你就可以任意操作这个Texture了，正是因为如此，Hikari支持Flash的所有版本，不存在兼容性问题。因为Flash本身就支持多国语言，所以中文显示也没有问题。可以把界面开发的大部分内容放到Flash那边，从而使客户端简洁很多（简单就是美啊）。
但是Hikari最致命的问题的效率太低，它使用的是Flash的ocx，先将动画内容渲染到DC上，然后拷到Texture中，所以很慢，而且慢的是第二步，使得Flash优秀的脏矩形优势无法发挥，根本无法应用到商业游戏中。我做了个动画，30张图片随机飘动，1023×768的窗口，使Flash占满，Release版只能跑到15帧（集成显卡），这还没有显示任何文字呢：
## Scaleform

![](/Resources/UI引擎_4.jpg)

Scaleform跟Hikari的作用是一样的，都是用Flash来做游戏界面，不同的是Scaleform非常牛X，它的效率很高，可以说是最强游戏界面解决方案了！而且对亚洲语言显示和输入都完美支持。目前最新版本是3.2，据说4.0将支持Actionscript 3.0, 并全方位支持3D UI。超过600款游戏使用Scaleform做界面，比如超大作StarCraft II，Crysis，Fable II，Civilization IV，Halo Wars，Princes of Persia，Mess Effect 2，Prototype，Resistance 2，Splinter Cell等。
心动了吧，可惜Scaleform是收费的，而且授权费相当的高，3.X版的目标售价是每一款游戏2.5万美金。如果你不在乎钱的话，这绝对是不二之选，在乎钱的话，这是二B之选。PS：有不少商业引擎已经将Scaleform集成进去了，比如Gamebryo，Unreal3等，如果你不用Ogre，买了商业引擎也爽了

## ogreSwf/vektrix

Hikari效率太低，Scaleform太贵，ogreSwf/vektrix就是出来解决这个矛盾的。ogreSwf跟Scaleform一样都由开源的gameSwf发展起来，Scaleform开始商业化，ogreswf继续开源，后来ogreswf项目停掉了。2010年ogreSwf的作者重起了该项目，在原来的基础上改进并改名为vektrix，2010年4月发布了新的demo，可能是SourceForge的原因，我下的demo文件无法解压，又觉得vektrix目前还无法达到Scaleform的高度，所以后来就没有再试了。

## Awesomium

![](/Resources/UI引擎_5.jpg)

Awesomium的功能有点类似Hikari，只不过它是将网页渲染成Texture，而且效率方面也做的比较好。Awesomium 采用了目前业界速度最快的浏览器内核webkit和v8，其实是把Chrome内核嵌入到了里面，同时还很好地支持flash，可以通过javascript使游戏和网页交互。该项目最初也是开源的，后来商业化了，但是不太贵，最便宜的版本只要400多美金。
Awesomium的效率之所以高，估计也是脏矩形方面做的好，我把上面那个动画嵌到网页中，用Awesomium打开，帧数马上就下来了，所以还是不能做UI，但是游戏中的帮助页面则可以考虑用这个。Awesomium也不方便根据网页内的内容做半透明效果，也就是网页中部分半透明很难实现，全透明，也就是镂空效果则可以通过模板实现。

## MYGUI

![](/Resources/UI引擎_6.jpg)

MyGUI最新版本3.0.1，是俄罗斯人写的，要么没有注释，要么注释是俄文的，而且相关的资料实在是太缺乏了，虽然小修改一下可以支持中文显示，但是效果太差了，根本不能用，更别说多种文字，多种效果了，目前也没有什么商业游戏是用这个库做的。
但我最终选择了这个UI库。
就像MYGUI的介绍一样“MyGUI – fast, simple and flexible GUI.”这确实是一个，高效，轻便，灵活的库。首先它的设计很好，所以即使没有注释，也不难理解。换肤的设计避免了CEGUI里的很多中间层，使用要简单很多，资源文件的管理也要清爽（清楚+爽）一些。没有使用ogre的overlay，用底层直接画了，效率比CEGUI要高。LayoutEdit，ImageSetEdit等比CEGUI的要好用的多，CEGUI的工具经常当掉- -。中文显示可以模仿CEGUI去做，我已经完全实现，效率并不低，完全可以接受。
载入layout文件后返回一个窗口的vector，你可以自己写一个类似BaseLayout的类去管理，然后像MYGUI一样大量用C++委托做回调函数，就可以把各个Dialog分开去写，就像写MFC的Dialog一样，这一点做的实在太好了。如果再学一点CEGUI，把Lua脚本集成进去，载入layout文件时把窗口注册到lua中，这样就可以在脚本里写逻辑了，客户端-UI-脚本，很清晰。
为什么没有商业游戏使用MYGUI呢？MYGUI比较稳定的版本2.2.3是09年10月份发布的，是少要1年才能有游戏出来，火炬之光是09年11月上市的，在开发的时候MYGUI还很不完善，以后一定会有不少游戏使用MYGUI：）
跟使用CEGUI一样，MYGUI也要做大量修改才能用到游戏中，但我觉得是少比CEGUI好改一点>_<。我目前也刚做到登录，选人界面，大部分功能尚未开始，真正的问题可能还在后面，但到目前为止还是对MYGUI挺满意的，这也只是我个人的选择，诸位看官还请三思！

## Reference
* <http://www.mobilegamebase.com/?p=35>