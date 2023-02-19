---
layout: post
title: HybridCLR
category: 编程开发
tags: unity3d
keywords: 
description: 
---

## 相关库

#### [Assemblies-Hotfix-Toolkit-Unity](https://github.com/Bian-Sh/Assemblies-Hotfix-Toolkit-Unity)

#### [glot-docker-huatuo](https://github.com/eelgame/glot-docker-huatuo)

#### [StarForce_HuaTuo](https://github.com/GREAT1217/StarForce_HuaTuo)

#### [Deer_GameFramework_Wolong](https://github.com/It-Life/Deer_GameFramework_Wolong)

#### [UnityGameFramework_HybridCLR](https://github.com/Dango1992/UnityGameFramework_HybridCLR)

#### [BundleMaster](https://github.com/mister91jiao/BundleMaster)

#### [TEngine](https://github.com/ALEXTANGXIAO/TEngine)


## FAQ

#### Windows第一次使用`ab中添加AOT补充元数据`

```
ab中添加AOT补充元数据dll:projectname/HybridCLRData/AssembliesPostIl2CppStrip/StandaloneWindows64/mscorlib.dll 时发生错误,文件不存在。裁剪后的AOT dll在BuildPlayer时才能生成，因此需要你先构建一次游戏App后再打包。
```

Solution:
```
Player->Configuration->Scripting Backend改成IL2CPP
```

#### TypeLoadException: Could not load type 'UnityEngine.Networking.DownloadHandlerTexture '

## Reference

* <https://focus-creative-games.github.io/hybridclr/recommended-tools/>