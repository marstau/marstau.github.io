---
layout: post
title: 不能在非主线程中使用OpenGL ES的UI函数
category: 游戏技术
tags: cocos2dx
keywords: 黑屏
description: 
---

在非主线程中创建纹理会出现如下黑屏情况:

![](/Resources/不能在非主线程中使用OpenGL ES的UI函数_1.png)

因为在新线程中调用了如下函数:

```
    cocos2d::SpriteFrameCache::getInstance()->addSpriteFramesWithFile("battle_map.plist");
```

因为**OpenGL ES的UI函数只能在主线程中调用**。
修改成异步加载:

```

    auto addFrameFunctor = [&](const string &plist, const string &suffix){
        const string image = plist.substr(0, plist.find_last_of('.')) + "." + suffix;
        GLOG(GDEBUG, "plist=" << plist << ", image=" << image);
        
        auto textureCache = Director::getInstance()->getTextureCache();
        textureCache->addImageAsync(image, [&, plist](Texture2D *tex){
            GLOG(GDEBUG, "addImageAsync plist=" << plist);
            cocos2d::SpriteFrameCache::getInstance()->addSpriteFramesWithFile(plist, tex);
        });
    };
    
    const string pvrccz = "pvr.ccz";
    const string png = "png";
    addFrameFunctor("battle_map.plist", pvrccz);
```