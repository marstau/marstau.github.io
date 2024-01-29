---
layout: post
title: Unity3D shader
category: 编程开发
tags: unity3d
keywords: 
description: 
---


## 基础知识

```
uniform
```

## FAQ

#### 同一shader修改起变量使其他材质球不影响


```
PropertyBlock = new MaterialPropertyBlock();
this.renderers = this.gameObject.GetComponentsInChildren<Renderer>();
foreach (var renderer in this.renderers) 
{
    renderer.GetPropertyBlock(PropertyBlock);
    PropertyBlock.SetColor("_FillColor", FillColor);
    renderer.SetPropertyBlock(PropertyBlock);
}
```

#### `_Time.y`的float精度问题[More](https://zhuanlan.zhihu.com/p/566209058)[More2](https://cloud.tencent.com/developer/article/1978450)

精度问题导致有些uv使用`_Time.y`会无法流动

之前有个特效在鸿蒙手机上会有问题 而其他手机正常, shader half全改成float就好了。

#### spine ab包导出后 贴图变脏了 但是直接导出包是没有问题的

spine shader需要与包体一同导出  

```

public void SetMeshRendererFillblend(int blendValue) {
    foreach (var renderer in this.renderers) 
    {
        renderer.GetPropertyBlock(PropertyBlock); // 如果不加 电脑模拟器好了 手机还是有问题
        PropertyBlock.SetFloat("_Fillblend", blendValue);
        renderer.SetPropertyBlock(PropertyBlock);
    }
}
```

#### grey

```
float grey = dot(col.rgb, fixed3(0.22, 0.707, 0.071));
return float4(grey,grey,grey, col.a);
```

#### 宏判断

```
// 根据关键字启用或禁用特定的功能
#pragma shader_feature GREY_TO_ORIGIN

// ...

fixed4 frag (v2f i) : COLOR
{
    // 根据关键字执行不同的操作
    #ifdef GREY_TO_ORIGIN
        // 执行与关键字相关的操作
    #else
        // 执行其他操作
    #endif
}
```

## Error

####  'vert', error X8000: D3D11 Internal Compiler Error: Invalid Bytecode: Incompatible min precision type for operand #1 of opcode #28 (counts are 1-based). Expected int or uint. (on gles3)[More](https://blog.csdn.net/sinat_25415095/article/details/121416839)

Solution:
```
将half改为float就可以了。

float min = 0.5 - halfWidth;
float max = 0.5 + halfWidth;
color.a *= step(min, IN.texcoord.y) * step(IN.texcoord.y, max);
```

## Reference

* [Unity Shader Document](https://docs.unity3d.com/Packages/com.unity.shadergraph@10.0/manual/Math-Nodes.html)
