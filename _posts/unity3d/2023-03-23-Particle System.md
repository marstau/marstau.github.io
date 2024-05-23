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

## Reference

