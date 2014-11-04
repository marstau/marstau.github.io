---
layout: post
title: mul(inPos, matViewProjection) and mul(matViewProjection, inPos)
category: 游戏技术
tags: Game　Engine
keywords: 
description: 
---

<div
style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

float4x4 matViewProjection;\
\
 <span style="color:#0000ff;">struct</span> VS\_OUTPUT{\
    float4 Pos : POSITION;\
    float2 Tex : TEXCOORD;\
 };\
\
 VS\_OUTPUT vs\_main(\
    float4 inPos : POSITION,\
    float2 inTex : TEXCOORD )\
 {\
    VS\_OUTPUT output;\
    <span style="color:#008000;">/\*</span><span
style="color:#008000;">\
    \*\* Using mul(matViewProjection, inPos)\
    \*\* and   mul(inPos, matViewProjection)\
    \*\* may produce the same results.\
    </span><span style="color:#008000;">\*/</span>\
    output.Pos = mul(inPos, matViewProjection);\
    output.Tex = inTex;\
    <span style="color:#0000ff;">return</span> output;\
 }

 

RenderMonkey workes with transposed matrices

as opposed to regular non-transposed ones. **I think it does this for**

**consistancy with OpenGL rendering. **Now, that being said, when

multipliying two matrices, if one is the transpose, you can get the

same result by changing the order of the multiplication.

As for your App... Well if you plan on using render monkey shaders

directly, you may want to transpose your matrices before uploading

them (note that there is a SetMatrixTransposed, or something similar

in the DirectX api to automate this for you).

</div>





