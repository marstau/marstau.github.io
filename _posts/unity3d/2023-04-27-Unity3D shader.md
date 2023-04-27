---
layout: post
title: Unity3D shader
category: 编程开发
tags: unity3d
keywords: 
description: 
---

## ERROR

####  'vert', error X8000: D3D11 Internal Compiler Error: Invalid Bytecode: Incompatible min precision type for operand #1 of opcode #28 (counts are 1-based). Expected int or uint. (on gles3)[More](https://blog.csdn.net/sinat_25415095/article/details/121416839)

Solution:
```
将half改为float就可以了。

float min = 0.5 - halfWidth;
float max = 0.5 + halfWidth;
color.a *= step(min, IN.texcoord.y) * step(IN.texcoord.y, max);
```

## Reference

