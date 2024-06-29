---
layout: post
title: Unity3D UIWidgets
category: 编程开发
tags: unity3d
keywords: 
description: 
---

## Samples

## FAQ

#### 包体

初始包体20.9MB

## Error

####  The name 'UIWidgetsInternal' does not exist in the current context

```
public class UIWidgetsInternal
{
  public static RenderTexture CreateBindableRenderTexture(RenderTextureDescriptor desc)
  {
    desc.enableHWSharable = true;
    return new RenderTexture(desc);
  }
}
```

## Reference

* [属于 Unity 的 Flutter——UIWidgets](https://frankorz.com/2019/04/01/uiwidgets-practice/index.html)

* [[Unity 活动]-官方直播-UIWidgets - 不止游戏！如何使用Unity开发跨平台应用](https://www.bilibili.com/video/av47558897/?vd_source=3c786b79942015ab0f27038d72c371f9)

