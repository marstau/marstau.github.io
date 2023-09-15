---
layout: post
title: Unity DOTS
category: 编程开发
tags: unity3d
keywords: 
description: 
---


## 概念[More](https://www.u3dc.com/archives/3509)[More2](https://www.cnblogs.com/bylle/p/11762557.html)[More3](https://www.cnblogs.com/bylle/p/11876201.html)[More4](https://connect.unity.com/p/shi-yong-unityde-ecshe-job-systemshi-xian-liu-ti-mo-ni-xiao-guo)[More5](https://blog.codingnow.com/2017/06/overwatch_ecs.html)


DOTS:Data-Oriented-Tech-Stack

## Error


#### `error CS0103: The name 'RenderPipeline' does not exist in the current context`[More](https://forum.unity.com/threads/issue-adding-entities-package-to-2019-3-0a10.715652/)

```
RenderPipeline.beginCameraRendering += OnPreCull;
```
Solution:
```
using UnityEngine.Rendering;

    RenderPipelineManager.beginCameraRendering += OnPreCull;
}

void OnPreCull(ScriptableRenderContext context, Camera camera) => OnPreCull(camera);
```

#### `error CS1061: 'EntityQuery' does not contain a definition for 'SetFilter' and no accessible extension method 'SetFilter' accepting a first argument of type 'EntityQuery' could be found (are you missing a using directive or an assembly reference?)`

```
m_Characters.SetFilter(character);
```
Solution:
```
m_Characters.SetSharedComponentFilter(character);
```

#### `error CS1501: No overload for method 'ToComponentDataArray' takes 2 arguments`

```
JobHandle jobA, jobB;
var coords = m_Characters.ToComponentDataArray<AnimationTextureCoordinate>(Allocator.TempJob, out jobA);
var localToWorld = m_Characters.ToComponentDataArray<LocalToWorld>(Allocator.TempJob, out jobB);
JobHandle.CompleteAll(ref jobA, ref jobB);
```
Solution:
```
var coords = m_Characters.ToComponentDataArray<AnimationTextureCoordinate>(Allocator.TempJob);
var localToWorld = m_Characters.ToComponentDataArray<LocalToWorld>(Allocator.TempJob);
```

#### `error CS1061: 'TimeData' does not contain a definition for 'deltaTime' and no accessible extension method 'deltaTime' accepting a first argument of type 'TimeData' could be found (are you missing a using directive or an assembly reference?)`

```
Time.deltaTime
```
Solution:
```
UnityEngine.Time.deltaTime
```

#### `perator '+' cannot be applied to operands of type 'Chunk.<Buffer>e__FixedBuffer'`[More](https://forum.unity.com/threads/solved-issues-with-dots-editor-package.887056/)

Solution:
```
If you're using .NET 4.x try to switch to .NET Standard 2.0 and reimport the DOTS Editor package 
```

## Reference

* [Job System](https://zhuanlan.zhihu.com/p/47920129)
* <https://github.com/liuhaopen/UnityMMO>
* [Burst](https://blogs.unity3d.com/cn/2020/08/17/enhancing-mobile-performance-with-the-burst-compiler/)
* [Unity项目技术方案Dots架构方案简介](https://blog.csdn.net/qq_42672770/article/details/123458808)