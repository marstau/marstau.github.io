---
layout: post
title: TextMeshPro
category: 编程开发
tags: unity3d
keywords: TextMeshPro
description: 
---

## 基础

创建动态字体
选中ttf->Create->TextMeshPro->Font Asset

创建静态字体[More](https://zhuanlan.zhihu.com/p/90937163)

## 限制

描边：同一个材质球的描边必须一样
静态字体+动态字体 频繁生成动态字体会导致掉帧严重

## FAQ

#### outline的hdr color设置和rgb不一样

textmeshpro使用的linear space的hdr color 所以需要将rgb转换成对应的hdr color的rgb

## Reference

* <https://juejin.cn/post/7067844455310573582>
* <https://developer.aliyun.com/article/879539>
* <https://www.bilibili.com/video/av814969954/?vd_source=3c786b79942015ab0f27038d72c371f9>
* [基于Unity TextMeshPro的图文混排和超链接功能](https://www.lfzxb.top/unity-textmeshpro-something/)
* [TMP耗时较高的优化问题](https://mp.weixin.qq.com/s/pIbNUm7c9W3krGzNq7a7ww)
* <https://www.lfzxb.top/unity-textmeshpro-something/>