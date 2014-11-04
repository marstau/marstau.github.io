---
layout: post
title: Coding in RenderMonkey
category: 游戏技术
tags: Game　Engine
keywords: 
description: 
---

-   **<span style="color:#e53333;">tex2D( sampler, float2 );</span>**
    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    sampler Texture0;\
    \
     float4 ps\_main(\
        float4 inPos : POSITION,\
        float2 inTex : TEXCOORD ) : COLOR\
     {\
        <span
    style="color:#0000ff;">return</span> tex2D( inTex, Texture0 ); <span
    style="color:#008000;">//</span><span
    style="color:#008000;"> error:return tex2D( Texture0, inTex );</span><span
    style="color:#008000;">\
     </span>}

    </div>

-   **<span style="color:#e53333;">位移一定位置注意w值.</span>**\
     当绘制两个物体的时候，另一个物体位移offsetPos(a,b,c,**1**);\

    当如此设置的时候,因为Output.Position = mul( Input.Position + offsetPos, matViewProjection );\
     你会发现绘制出来的缩小了一半.\
     ![](http://files.note.sdo.com/XbPJ4~kaYm72wE1cQ0063B)\

    因为w值为1,当你与Input.Position相加的时候变成了2,rendermonkey内部需要将坐标投影到w=1上,so,**将w设置为0**即可解决问题.\
     ![](http://files.note.sdo.com/XbPJ4~kaYm7iwE1cQ0063E) 
-   绘制多个物体到同一个renderTarget,先前绘制的物体消失不见了.\
     本来想要这种结果:\
     ![](http://files.note.sdo.com/XbPJ4~kaYZ_2wE1cQ009gZ)\
     结果却是:\
     ![](http://files.note.sdo.com/XbPJ4~kaYZ_iwE1cQ009h1)\
     因为\
     ![](http://files.note.sdo.com/XbPJ4~kaY_biwE1cQ009iN)\
     第二次绘制的时候,**将render target的颜色清除了,去掉勾选即可**.
-   Add Renderable Texture命名不能renderTarget-H这样,不然Reference
    Node的时候就不能Reference it了.
-   pass也有绘制顺序的![](http://files.note.sdo.com/XbPJ4~kb2Nw2wE2pM004FR)\
     而将pass teapot和pass
    elephant调换顺序后,![](http://files.note.sdo.com/XbPJ4~kb2NvOwE2pM004FM)\
     因为pass teapot的render target
    clear了颜色,所以elephant无法正常显示了.
-   **<span
    style="color:#e53333;">在同一个position绘制多个同样的pass效果并不是叠加,而是不断覆盖.</span>**\
     如图,四个pass,![](http://files.note.sdo.com/XbPJ4~kb2NvOwE2pM004FP)\
     pass1和pass2相同    着色为红色,\
     pass3位移了一点位置 着色为黄色,\
     pass4是位置和前两个pass一样,但着色为magenta(品红).
-   **<span style="color:#e53333;">四分量和三分量相加竟然OK</span>**\
     float4 v;

    float4 vv = float4(**Pos.xyz + v**,1);\
     同理,float2 texCoord; float2 x = texCoord - 0.5;也OK。

-   纹理过滤模式设置\
     欲出现这种效果\
     ![](http://files.note.sdo.com/XbPJ4~kbbG0ywE0rM00cld)\
     但是却出现这种效果\
     ![](http://files.note.sdo.com/XbPJ4~kbbG0OwE0rM00clg)\

    因为纹理采样模式没有设置好,将D3DSAMP\_MAGFILTER设置为DEDTEXF\_LINEAR即可.\
     ![](http://files.note.sdo.com/XbPJ4~kbbG12wE0rM00cli)

-   **<span style="color:#e53333;">D3DRS\_CULLMODE效果</span>**\
     若未设置(缺省值为D3DCULL\_CCW),则\
     ![](http://files.note.sdo.com/XbPJ4~kbbG0ywE0rM00clb)\
     **设置为如图所示的D3DCULL\_NONE,**则\
     ![](http://files.note.sdo.com/XbPJ4~kbbF-OwE0rM00ck_)\
     ![](http://files.note.sdo.com/XbPJ4~kbbG02wE0rM00cl3)

-   想要实现这种效果，\
     ![](http://files.note.sdo.com/XbPJ4~kbdTjOwE0rM00nsj)\
     却是这种效果，\
     ![](http://files.note.sdo.com/XbPJ4~kbdTjiwE0rM00nse)\
     因为

    struct VS\_OUTPUT{

       float4 Pos : POSITION;

       float2 Tex : TEXCOORD;

       float**4** col : COLOR; // 改为float2即可.

    };

-   **<span style="color:#e53333;">pixel
    shader的输入顺序无所谓</span>**\
     例如:float4 ps\_main(float2 inTex : TEXCOORD0,
    float4 inCol: COLOR0) : COLOR{}\
     和float4 ps\_main(float4 inCol: COLOR0, float2 inTex
    : TEXCOORD0) : COLOR{}\
     都是一样的,因为他们都有标识符TEXCOORD0,COLOR0,可以正确识别.

-   HLSL 的implicit type conversion\
     float  d;\
     float4 a = d;\
     float3 b = a;
-   TEXCOORD0错写成TEXCOORD1\
     本来希望这种效果,\
     ![](http://files.note.sdo.com/XbPJ4~kbhmkywE2pE008ih)\
     却出现的这种效果,\
     ![](http://files.note.sdo.com/XbPJ4~kbhmkywE2pE008id)\
     原因是VS\_OUTPUT vs\_main( ..., float2 inTex : TEXCOORD**1** ){}\
     改成正确的TEXCOORD0即可.

-   **<span style="color:#e53333;">着色器属性设置</span>**\
     出现如图效果,\
     ![](http://files.note.sdo.com/XbPJ4~kbi8R2wE2pE00c3t)\
     将shader的**properties**设置为**Row Major**.\
     ![](http://files.note.sdo.com/XbPJ4~kbi8RiwE2pE00c3y)\
     正常显示:\
     ![](http://files.note.sdo.com/XbPJ4~kbiNgywE2pE00eyQ)

-   显示shadow出现N多重复阴影\
     ![](http://files.note.sdo.com/XbPJ4~kcoBJOwE2C4002Av)\
     寻址模式默认为WRAP,设置为CLAMP即可\
     ![](http://files.note.sdo.com/XbPJ4~kcoBJywE2C4002At)

-   \
      







