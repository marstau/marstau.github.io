---
layout: post
title: mobile devices information
category: 编程开发
tags: android／java mac／ios
keywords: resolution
description: 
---
## resolution

### ios


iphone分辨率参数:

```
    型号         屏幕尺寸   分辨率
    ------------ ---------- --------------
    iPhone       3.5英寸    480x320像素
    iPhone 3G    3.5英寸    480x320像素
    iPhone 3GS   3.5英寸    480x320像素
    iPhone 4     3.5英寸    960x640像素
    iPhone 4S    3.5英寸    960x640像素
    iphone5(S)   4英寸      1136x640像素
```

ipad分辨率参数：

    型号        屏幕尺寸   分辨率
    ----------- ---------- ---------------
    ipad1       9.7英寸    1024x768像素
    ipad2       9.7英寸    1024x768像素
    new ipad    9.7英寸    2048x1536像素
    iPad 4      9.7英寸    2048x1536像素
    ipad mini   7.9英寸    1024x768像素

### android[More](http://developer.android.com/guide/practices/screens_support.html)



图标尺寸大全：

29x29

36x36

48x48

50x50

57x57

58x58

72x72

96x96

114x114

144x144

512x512


Note:原先使用的small, normal, large, and xlarge已经废弃.

ldpi:36*36px,0.75倍密度，一般不用提供，系统会从hdpi取图缩小1倍。

mdpi:48*48px, 1倍密度

hdpi:72*72px,1.5倍密度

xhdpi:96*96px,2倍密度

xxhdpi:144*144px，3倍密度


## architectures each device

* ARMv8/ARM64: iPhone 5s, iPad Air, Retina iPad Mini
* ARMv7s: iPhone 5, iPhone 5c, iPad 4
* ARMv7: iPhone 3GS, iPhone 4, iPhone 4S, iPod 3G/4G/5G, iPad, iPad 2, iPad 3, iPad Mini
* ARMv6: iPhone, iPhone 3G, iPod 1G/2G

## Reference

* <http://stackoverflow.com/questions/22328882/xcode-5-1-no-architectures-to-compile-for-only-active-arch-yes-active-arch-x>