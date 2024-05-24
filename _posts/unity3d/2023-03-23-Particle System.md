---
layout: post
title: Particle System
category: 编程开发
tags: unity3d
keywords: 
description: 
---


#### 修改粒子Max Particles


```
ParticleSystem ps = objTrans.GetComponent<ParticleSystem>();
ParticleSystem.MainModule module = ps.main;
module.maxParticles = 30;

粒子性能测试:
低端机: 1000
中端机: 3000

注意点:
128x128的贴图 Start Size: 2 就意味着变成了256x256贴图了
```

#### overdraw计算[More](https://blog.uwa4d.com/archives/TechSharing_230.html?hmsr=joyk.com&utm_source=joyk.com&utm_medium=referral)

## Reference

* [Overdraw计算](https://github.com/sunbrando/ParticleEffectProfiler)