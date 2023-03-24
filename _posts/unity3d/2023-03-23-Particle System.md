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
```

## Reference

