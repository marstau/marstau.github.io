---
layout: post
title: My Naming Convention
category: 游戏技术
tags: normal　knowledge
keywords: 
description: 
---

命名规范确立,使用\<\<Introductin To 3D Game Programming With DirectX 9.0\>\>上的命名规范.

-   **全局变量**:首字母大写
-   <div>

    <span style="font-size:9pt;"><span
    style="font-size:14px;">**全局函数**:首字母大写.</span></span>

    </div>

-   <div>

    <span style="font-size:9pt;"><span
    style="font-size:14px;">**成员函数**:首字母小写.</span></span>

    </div>

-   **成员变量**:\_ + 变量名.
-   不加类型如:dw、i等等.
-   other、rhs

------------------------------------------------------------------------

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    **全局变量**:首字母大写

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    <span
    style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
    style="font-size:14px;">**全局函数**:首字母大写.</span></span>

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    <span
    style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
    style="font-size:14px;">**成员函数**:public首字母大写,以动词开头,表示行为.private则首字母小写.</span></span>

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    <span style="font-family:宋体;">**成员变量**:\
     非公有成员变量: \_ + 变量名.\
     公有成doxygen员变量:m\_ + 变量名.</span>

    </div>

-   **MACRO：**\_NAME\_
-   **enum**：\_NAME\_OTHER
-   **const常量**： C + TYPE+ \_NAME\_OTHER
-   变量名: 均一属性 + 细分属性
    <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

     

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

     
    //////////////////////////////////////////////////////////////////////////

    // class CCube functions.

    //////////////////////////////////////////////////////////////////////////\
     多个类类定义时候的注释区分各个类

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    尽量用乘法或其它方法代替除法，特别是浮点运算中的除法。

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    MACRO:\_NAME\_ enum:\_NAME\_OTHER CONST:NAME\_OTHER

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

     

    if (

    (stationaryBox.min.y \>= movingBox.max.y) ||

    (stationaryBox.max.y \<= movingBox.min.y)

    ) {\
     // ...\
     }

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    变量和函数都不用复数.

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    D3DXCreateTexture(

        \_device, \_nCellPerRow, \_nCellPerCol, 0, 0, D3DFMT\_X8R8G8B8, D3DPOOL\_MANAGED, &\_tex );

     

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

    **注释**\
     doxygen 

    </div>

-   <div class="MsoNormal" style="margin:0cm 0cm 0pt;">

     

    </div>

 

------------------------------------------------------------------------

**缩写变量名**:

1.  Coord：Coordinate;
2.  Inc：Increment;
3.  Tex: Texture;
4.  Gen: Generate;
5.  Matrix: Mat;
6.  Animation: Anim;
7.  right hand side: rhs;
8.  Auxiliary: Auxi;
9.  distance: dist;

 auxi(for functions),iEnd/iLast(\<iEnd and \<=
iLast),iStart,iBack,iFront,szStr,iPost,iPrev,iKey,num,ret,\
 vex,SearchData,mid,DoTask,DoTaskAuxi,iLow,iHigh,Widget(for class)

------------------------------------------------------------------------

没太有收藏价值的题目直接放在.cpp中,否则放在麦库记事中.

 

------------------------------------------------------------------------

 

<span lang="HI" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">匈牙利命名法是一种编程时的命名规范。基本原则是：</span><span
style="font-size:14px;background:yellow;mso-highlight:yellow;">变量名＝属性＋类型＋对象</span><span
style="font-size:14px;">描述，其中每一对象的名称都要求有明确含义，可以取对象名字全称或名字的一部分。命名要基于容易记忆容易理解的原则。保证名字的连贯性是非常重要的。</span></span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;mso-spacerun:yes;">   </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">举例来说，表单的名称为</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">form</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">，那么在匈牙利命名法中可以简写为</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">frm</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">，则当表单变量名称为</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">Switchboard</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">时，变量全称应该为</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">frmSwitchboard</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">。这样可以很容易从变量名看出</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">Switchboard</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">是一个表单，同样，如果此变量类型为标签，那么就应命名成</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">lblSwitchboard</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">。可以看出，匈牙利命名法非常便于记忆，而且使变量名非常清晰易懂，这样，增强了代码的可读性，方便各程序员之间相互交流代码。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;mso-spacerun:yes;">   </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">这种命名技术是由一位能干的</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">Microsoft</span><span lang="HI"
style="font-size:14px;font-family:宋体;">程序员查尔斯</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">·</span><span
lang="HI" style="font-size:14px;font-family:宋体;">西蒙尼</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">(Charles Simonyi)
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">提出的，他出生在匈牙利。在</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> Microsoft
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">公司中和他一起工作的人被教会使用这种约定。这对他们来说一切都很正常。但对那些</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> Simonyi
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">领导的项目组之外的人来说却感到很奇特，他们认为这是死板的表达方式，甚至说带有这样奇怪的外观是因为它是用匈牙利文写的。从此这种命名方式就被叫做匈牙利命名法。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">据说这种命名法是一位叫</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> Charles Simonyi
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">的匈牙利程序员发明的，后来他在微软呆了几年，于是</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">这种命名法就通过微软的各种产品和文档资料向世界传播开了。现在，大部分程序员不管自己使用</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">什么软件进行开发，或多或少都使用了这种命名法。这种命名法的出发点是把量名变按：属性</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">+</span><span
lang="HI" style="font-size:14px;font-family:宋体;">类型</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">+</span><span lang="HI"
style="font-size:14px;font-family:宋体;">对象
描述的顺序组合起来，以使程序员作变量时对变量的类型和其它属性有直观的了解，下面</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="HI" style="font-size:14px;font-family:宋体;">是</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">HN</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">变量命名规范，其中也有一些是我个人的偏向：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

**<span lang="HI"
style="font-size:14px;background:yellow;font-family:宋体;mso-highlight:yellow;">属性部分</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>**

**<span lang="HI"
style="font-size:14px;font-family:宋体;">全局变量</span>**<span
lang="HI"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;">
</span><span lang="EN-US" style="font-size:14px;font-family:宋体;">g\_
</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

**<span lang="HI"
style="font-size:14px;font-family:宋体;">常量</span>**<span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
c\_ </span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">c++</span><span lang="HI"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">类</span>**<span
style="font-size:14px;">成员变量</span>**</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
m\_ </span></span>

**<span lang="HI"
style="font-size:14px;font-family:宋体;">静态变量</span>**<span
lang="EN-US" style="font-size:14px;font-family:宋体;"> s\_ </span><span
lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

**<span lang="HI"
style="font-size:14px;background:yellow;font-family:宋体;mso-highlight:yellow;">类型部分</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>**

**<span lang="HI"
style="font-size:14px;font-family:宋体;">指针</span>**<span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;"> p
</span></span>

**<span lang="HI"
style="font-size:14px;font-family:宋体;">函数</span>**<span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
fn </span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">cb :
count of bytes</span><span lang="EN-US"
style="font-size:14px;mso-fareast-language:ZH-CN;">(</span><span
lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;">used for a variable that denotes a byte
size)</span></span>

<span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;">hbr: handle to a brush</span></span>

**<span lang="HI"
style="font-size:14px;font-family:宋体;">无效</span>**<span lang="EN-US"
style="font-size:14px;font-family:宋体;"> v </span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

**<span lang="HI"
style="font-size:14px;font-family:宋体;">句柄</span>**<span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;"> h
</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">long
int :</span><span lang="EN-US" style="font-size:9pt;font-family:宋体;">
</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;mso-spacerun:yes;"> </span></span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">l </span><span
lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">bool</span><span
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">：</span><span
style="font-size:9pt;font-family:宋体;"> </span><span
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;mso-spacerun:yes;"> </span></span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">b </span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">浮点型（有时也指文件）</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> f </span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">双字</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
dw </span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">字符串</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
sz </span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">短整型</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;"> n
</span></span>

<span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;">near : n </span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">双精度浮点</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> d </span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">计数</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> c</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（通常用</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">cnt</span><span
lang="HI" style="font-size:14px;font-family:宋体;">）</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">character</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">:
</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">ch</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（通常用</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">c</span><span
lang="HI" style="font-size:14px;font-family:宋体;">） </span><span
lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">int
: </span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">i</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（通常用</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">n</span><span
lang="HI" style="font-size:14px;font-family:宋体;">）</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">byte
:</span><span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> by </span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">word
: </span><span lang="EN-US" style="font-size:14px;font-family:宋体;">w
</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span lang="HI" style="font-size:14px;font-family:宋体;">实型
</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">r</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;">(real number)</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">unsigned
: </span><span lang="EN-US" style="font-size:14px;font-family:宋体;">u
</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

**<span lang="HI"
style="font-size:14px;font-family:宋体;">描述部分</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>**

<span lang="HI"
style="font-size:14px;font-family:宋体;">最大</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
Max </span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">最小</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
Min </span></span>

<span lang="HI" style="font-size:14px;font-family:宋体;">初始化
</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">:
</span><span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">Init </span></span>

<span lang="HI" style="font-size:14px;font-family:宋体;">临时变量
</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;mso-fareast-language:ZH-CN;">:
</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">T</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（或</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">Temp</span><span lang="HI"
style="font-size:14px;font-family:宋体;">） </span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span lang="HI" style="font-size:14px;font-family:宋体;">源对象
</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">Src</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">目的对象</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> Dest </span></span>

<span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;">Wide character wc</span></span>

<span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">这里顺便写几个例子：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">hwnd
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">：</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> h </span><span lang="HI"
style="font-size:14px;font-family:宋体;">是类型描述，表示句柄，</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> wnd </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">是变量对象描述，表示窗口，所以</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> hwnd </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">表示窗口句柄；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">pfnEatApple
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">：</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> pfn </span><span lang="HI"
style="font-size:14px;font-family:宋体;">是类型描述，表示指向函数的指针，</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> EatApple
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">是变量对象描述，所以它表示</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">指向</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> EatApple </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">函数的函数指针变量。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">g\_cch
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">：</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> g\_ </span><span lang="HI"
style="font-size:14px;font-family:宋体;">是属性描述，表示全局变量，</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">c </span><span
lang="HI" style="font-size:14px;font-family:宋体;">和</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> ch </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">分别是计数类型和字符类型，一起表示变量类</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">型，这里忽略了对象描述，所以它表示一个对字符进行计数的全局变量。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">上面就是</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">HN</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">命名法的一般规则。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">小结</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">:</span><span lang="HI"
style="font-size:14px;font-family:宋体;">匈牙利命名法</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">匈牙利命名法</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">MFC</span><span lang="HI"
style="font-size:14px;font-family:宋体;">、句柄、控件及结构的命名规范</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">
Windows</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型 样本变量</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> MFC</span><span
lang="HI" style="font-size:14px;font-family:宋体;">类
样本变量</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HWND
hWnd</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CWnd\* pWnd</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HDLG
hDlg</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CDialog\* pDlg</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HDC
hDC</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CDC\* pDC</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HGDIOBJ
hGdiObj</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CGdiObject\*
pGdiObj</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HPEN
hPen</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CPen\* pPen</span><span
lang="HI" style="font-size:14px;font-family:宋体;">； </span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HBRUSH
hBrush</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CBrush\* pBrush</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HFONT</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hFont</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">CFont\* pFont</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HBITMAP</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hBitmap</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CBitmap\* pBitmap</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HPALETTE</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hPaltte</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CPalette\*
pPalette</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HRGN</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hRgn</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CRgn\* pRgn</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HMENU</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hMenu</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CMenu\* pMenu</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HWND</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hCtl</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
CState\*</span><span style="font-size:14px;mso-spacerun:yes;"> 
</span><span style="font-size:14px;">pState</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HWND</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hCtl</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CButton\* pButton</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HWND</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hCtl</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CEdit\* pEdit</span><span
lang="HI" style="font-size:14px;font-family:宋体;">；</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HWND</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hCtl</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CListBox\*
pListBox</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HWND</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hCtl</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CComboBox\*
pComboBox</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HWND</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hCtl</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> CScrollBar\*
pScrollBar</span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">HSZ</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">hszStr</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
CString</span><span style="font-size:14px;mso-spacerun:yes;"> 
</span><span style="font-size:14px;">pStr</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">POINT</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">pt</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
CPoint</span><span style="font-size:14px;mso-spacerun:yes;"> 
</span><span style="font-size:14px;">pt</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">SIZE</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">size</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
CSize</span><span style="font-size:14px;mso-spacerun:yes;"> 
</span><span style="font-size:14px;">size</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">RECT</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">rect</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
CRect</span><span style="font-size:14px;mso-spacerun:yes;"> 
</span><span style="font-size:14px;">rect</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">；</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;color:blue;font-family:宋体;">一般前缀命名规范</span><span
lang="HI" style="font-size:14px;font-family:宋体;"> 前缀 类型
实例</span><span lang="EN-US" style="font-size:9pt;font-family:宋体;">
</span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">C
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类或结构</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">
CDocument</span><span lang="HI"
style="font-size:14px;font-family:宋体;">，</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">CPrintInfo </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">m\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">成员变量</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">
m\_pDoc</span><span lang="HI"
style="font-size:14px;font-family:宋体;">，</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">m\_nCustomers </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">变量命名规范 </span><span
style="font-size:14px;background:#ffffcc;">前缀 类型 描述
实例</span></span><span lang="EN-US"
style="font-size:9pt;background:#ffffcc;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">ch char
8</span><span lang="HI"
style="font-size:14px;font-family:宋体;">位字符</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
chGrade </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">ch</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">TCHAR </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">如果</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">\_UNICODE</span><span lang="HI"
style="font-size:14px;font-family:宋体;">定义，则为</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">16</span><span
lang="HI" style="font-size:14px;font-family:宋体;">位字符</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> chName </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">b BOOL
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">布尔值</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
bEnable </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">n</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">int </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">整型（其大小依赖于操作系统）</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> nLength </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">n</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">UINT</span><span
style="font-size:14px;mso-spacerun:yes;">  </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">无符号值（其大小依赖于操作系统）</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> nHeight </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">w</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">WORD</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">16</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">位无符号值</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> wPos </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">l</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">LONG</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">32</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">位有符号整型</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lOffset </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">dw</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">DWORD</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">32</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">位无符号整型</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">dwRange </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">p</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">\*</span><span
style="font-size:14px;mso-spacerun:yes;">  </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">指针</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
pDoc </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">lp</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">FAR\*</span><span
style="font-size:14px;mso-spacerun:yes;">  </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">远指针</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">lpszName </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">lpsz</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">LPSTR</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">32</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">位字符串指针</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lpszName </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">lpsz</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">LPCSTR</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">32</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">位常量字符串指针</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lpszName </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">lpsz</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">LPCTSTR</span><span
style="font-size:14px;mso-spacerun:yes;">  </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">如果</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">\_UNICODE</span><span lang="HI"
style="font-size:14px;font-family:宋体;">定义，则为</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">32</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">位常量字符串指针</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lpszName </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">h</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">handle</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">Windows</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">对象句柄</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> hWnd </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">lpfn</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">callback </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">指向</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">CALLBACK</span><span lang="HI"
style="font-size:14px;font-family:宋体;">函数的远指针</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;mso-spacerun:yes;">   </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI" style="font-size:14px;font-family:宋体;">前缀
符号类型实例 范围</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">IDR\_</span><span
style="font-size:14px;mso-spacerun:yes;">  </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">不同类型的多个资源共享标识</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> IDR\_MAIINFRAME
1</span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x6FFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">IDD\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">对话框资源</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> IDD\_SPELL\_CHECK</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">1</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x6FFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HIDD\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">对话框资源的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">Help</span><span
lang="HI" style="font-size:14px;font-family:宋体;">上下文</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> HIDD\_SPELL\_CHECK</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">0x20001</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x26FF </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">IDB\_</span><span
style="font-size:14px;mso-spacerun:yes;">  </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">位图资源</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> IDB\_COMPANY\_LOGO</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">1</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x6FFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">IDC\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">光标资源</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> IDC\_PENCIL</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">1</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x6FFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">IDI\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">图标资源</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> IDI\_NOTEPAD</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">1</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x6FFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">ID\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">来自菜单项或工具栏的命令</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> ID\_TOOLS\_SPELLING</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">0x8000</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0xDFFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HID\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">命令</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">Help</span><span lang="HI"
style="font-size:14px;font-family:宋体;">上下文</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
HID\_TOOLS\_SPELLING</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">0x18000</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x1DFFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">IDP\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">消息框提示</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> IDP\_INVALID\_PARTNO</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">8</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0xDEEF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">HIDP\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">消息框</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">Help</span><span lang="HI"
style="font-size:14px;font-family:宋体;">上下文</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
HIDP\_INVALID\_PARTNO</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">0x30008</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x3DEFF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">IDS\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">串资源</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
IDS\_COPYRIGHT</span><span style="font-size:14px;mso-spacerun:yes;"> 
</span><span style="font-size:14px;">1</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0x7EEF </span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">IDC\_
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">对话框内的控件</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> IDC\_RECALC</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">8</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">～</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">0xDEEF </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US"
style="font-size:14px;color:blue;font-family:宋体;">Microsoft
MFC</span><span lang="HI"
style="font-size:14px;color:blue;font-family:宋体;">宏命名规范</span><span
lang="HI" style="font-size:14px;font-family:宋体;"> 名称
类型</span><span lang="EN-US" style="font-size:9pt;font-family:宋体;">
</span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">\_AFXDLL
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">唯一的动态连接库（</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">Dynamic Link
Library</span><span lang="HI"
style="font-size:14px;font-family:宋体;">，</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">DLL</span><span lang="HI"
style="font-size:14px;font-family:宋体;">）版本</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">\_ALPHA
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">仅编译</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">DEC Alpha</span><span lang="HI"
style="font-size:14px;font-family:宋体;">处理器</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">\_DEBUG
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">包括诊断的调试版本</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">\_MBCS
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">编译多字节字符集</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">\_UNICODE
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">在一个应用程序中打开</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">Unicode </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">AFXAPI</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">MFC</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">提供的函数</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">CALLBACK
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">通过指针回调的函数</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;mso-spacerun:yes;">  </span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;color:blue;font-family:宋体;">库标识符命名法</span><span
lang="HI" style="font-size:14px;font-family:宋体;"> 标识符
值和含义</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">u</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">ANSI</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">（</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">N</span><span lang="HI"
style="font-size:14px;font-family:宋体;">）或</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">Unicode</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">U</span><span lang="HI"
style="font-size:14px;font-family:宋体;">）</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">d</span><span
style="font-size:14px;mso-spacerun:yes;">  </span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">调试或发行：</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">D = </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">调试；忽略标识符为发行。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">静态库版本命名规范库
描述</span><span lang="EN-US" style="font-size:9pt;font-family:宋体;">
</span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">NAFXCWD.LIB
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">调试版本：</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">MFC</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">静态连接库</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">NAFXCW.LIB
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">发行版本：</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">MFC</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">静态连接库</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">UAFXCWD.LIB
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">调试版本：具有</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">Unicode</span><span lang="HI"
style="font-size:14px;font-family:宋体;">支持的</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">MFC</span><span lang="HI"
style="font-size:14px;font-family:宋体;">静态连接库</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">UAFXCW.LIB
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">发行版本：具有</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">Unicode</span><span lang="HI"
style="font-size:14px;font-family:宋体;">支持的</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">MFC</span><span lang="HI"
style="font-size:14px;font-family:宋体;">静态连接库</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;color:blue;font-family:宋体;">动态连接库命名规范</span><span
lang="HI" style="font-size:14px;font-family:宋体;"> 名称
类型</span><span lang="EN-US" style="font-size:9pt;font-family:宋体;">
</span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">\_AFXDLL
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">唯一的动态连接库（</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">DLL</span><span
lang="HI" style="font-size:14px;font-family:宋体;">）版本</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">WINAPI</span><span
style="font-size:14px;mso-spacerun:yes;">  </span><span
style="font-size:14px;">Windows</span></span><span lang="HI"
style="font-size:14px;font-family:宋体;">所提供的函数</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">Windows.h</span><span lang="HI"
style="font-size:14px;font-family:宋体;">中新的命名规范 类型
定义描述</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">WINAPI
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">使用在</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">API</span><span lang="HI"
style="font-size:14px;font-family:宋体;">声明中的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">FAR
PASCAL</span><span lang="HI"
style="font-size:14px;font-family:宋体;">位置，如果正在编写一个具有导出</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">API</span><span
lang="HI" style="font-size:14px;font-family:宋体;">人口点的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">DLL</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">，则可以在自己的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">API</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">中使用该类型</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">CALLBACK
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">使用在应用程序回叫例程，如窗口和对话框过程中的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">FAR
PASCAL</span><span lang="HI"
style="font-size:14px;font-family:宋体;">的位置</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">LPCSTR
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">与</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">LPSTR</span><span lang="HI"
style="font-size:14px;font-family:宋体;">相同，只是</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">LPCSTR</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">用于只读串指针，其定义类似（</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">const char
FAR\*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">）</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">UINT
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">可移植的无符号整型类型，其大小由主机环境决定（对于</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">Windows
NT</span><span lang="HI"
style="font-size:14px;font-family:宋体;">和</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">Windows 9x</span><span
lang="HI" style="font-size:14px;font-family:宋体;">为</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">32</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">位）；它是</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">unsigned
int</span><span lang="HI"
style="font-size:14px;font-family:宋体;">的同义词</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">LRESULT
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">窗口程序返回值的类型</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">LPARAM
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">声明</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">lParam</span><span lang="HI"
style="font-size:14px;font-family:宋体;">所使用的类型，</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">lParam</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">是窗口程序的第四个参数</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">WPARAM
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">声明</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">wParam</span><span lang="HI"
style="font-size:14px;font-family:宋体;">所使用的类型，</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">wParam</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">是窗口程序的第三个参数</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">LPVOID
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">一般指针类型，与（</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">void \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">）相同，可以用来代替</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">LPSTR </span></span>

<span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">变量命名</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">命名必须具有一定的实际意义</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI" style="font-size:14px;font-family:宋体;">形式为</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">xAbcFgh,x</span><span lang="HI"
style="font-size:14px;font-family:宋体;">由变量类型确定</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,Abc</span><span
lang="HI" style="font-size:14px;font-family:宋体;">、</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">Fgh</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">表示连续意</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">义字符串</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">如果连续意义字符串仅两个</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI" style="font-size:14px;font-family:宋体;">可都大写</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">.</span><span
lang="HI" style="font-size:14px;font-family:宋体;">如</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">OK.</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">具体例程</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">:</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">BOOL</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> bEnable;</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">ch</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> char</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> chText</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">c</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　
类对象　　　　　　　　　　　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> cMain</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（对象实例）</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">h</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">
Handle</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（句柄）　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> hWnd</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">i</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> int</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">n</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　
无符号整型</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">p</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　 指针</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">sz,str \*</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　 字符串</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">w</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> WORD</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">x,y</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　
坐标</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">Char</span><span lang="HI"
style="font-size:14px;font-family:宋体;">或者</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">TCHAR</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　 与</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">Windows
API</span><span lang="HI"
style="font-size:14px;font-family:宋体;">有直接联系的用</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">szAppName[10]</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">形式否则用</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">FileName[10]</span><span
lang="HI" style="font-size:14px;font-family:宋体;">形式</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">单个字符也可用小写字母表示</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">Int</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> nCmdShow;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">LONG</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lParam;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">UINT</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> uNotify;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">DWORD</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> dwStart;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">PSTR</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> pszTip;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">LPSTR</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lpCmdLine</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">LPTSTR</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lpszClassName;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">LPVOID</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lpReserved</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">WPARAM</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> wParam,</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">LPARAM</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> lParam</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">HWND</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> hDlg;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">HDC</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> hDC;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">HINSTANCE</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> hInstance</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">HANDLE</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> hInstance,</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">HICON</span><span lang="HI"
style="font-size:14px;font-family:宋体;">类型　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> hIcon;</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">int</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> iTmp</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">float</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> fTmp</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">DWORD</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> dw\*</span></span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">String ,
AnsiString</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> str \*</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">m\_</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　
类成员变量　　　　　　　　　　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
m\_nVal, m\_bFlag</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">g\_</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　
全局变量　　　　　　　　　　　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
g\_nMsg, g\_bFlag</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">局部变量中可采用如下几个通用变量：</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">nTemp</span><span
lang="HI" style="font-size:14px;font-family:宋体;">，</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">nResult</span><span lang="HI"
style="font-size:14px;font-family:宋体;">，</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">I</span><span lang="HI"
style="font-size:14px;font-family:宋体;">，</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">J</span><span lang="HI"
style="font-size:14px;font-family:宋体;">（一般用于循环变量）。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">其他资源句柄同上</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">.3</span><span lang="HI"
style="font-size:14px;font-family:宋体;">常量命名和宏定义</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">常量和宏定义必须具有一定的实际意义</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">常量和宏定义在</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">\#include</span><span lang="HI"
style="font-size:14px;font-family:宋体;">和函数定义之间</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">常量和宏定义必须全部以大写字母来撰写</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">中间可根据意义的连续性用下划线连接</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI" style="font-size:14px;font-family:宋体;">每一</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">条定义的右侧必须有一简单的注释</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">说明其作用</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">资源名字定义格式</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">:</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">菜单</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">:IDM\_XX</span><span lang="HI"
style="font-size:14px;font-family:宋体;">或者</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">CM\_XX</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">位图</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">:IDB\_XX</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">对话框</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">:IDD\_XX</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">字符串</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">:IDS\_XX</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">DLGINIT:DIALOG\_XX</span></span>

<span lang="HI" style="font-size:14px;font-family:宋体;">　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">ICON:IDR\_XX</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">.4</span><span lang="HI"
style="font-size:14px;font-family:宋体;">函数命名</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">函数原型说明包括引用外来函数及内部函数，外部引用必须在右侧注明函数来源：模</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">块名及文件名</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">, </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">如是内部函数，只要注释其定义文件名</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">第一个字母必须使用大写字母</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">要求用大小写字母组合规范函数命名</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">必要时可用下划线</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">间隔</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">,</span><span lang="HI"
style="font-size:14px;font-family:宋体;">示例如下：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">void</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">UpdateDB\_Tfgd
(TRACK\_NAME);</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;"> file://Module</span><span
lang="HI" style="font-size:14px;font-family:宋体;">　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">Name :r01/sdw.c</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">void</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">PrintTrackData (TRACK\_NAME); file://Module Name
:r04/tern.c</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">void</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">ImportantPoint
(void);</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">
file://Module</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">Name :r01/sdw.c</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">void</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">ShowChar (int , int ,
chtype);</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
file://Local Module</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">void</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">ScrollUp\_V</span><span
lang="HI" style="font-size:14px;font-family:宋体;">　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">(int ,
int);</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> file://Local Module</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">.5</span><span lang="HI"
style="font-size:14px;font-family:宋体;">结构体命名</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">结构体类型命名必须全部用大写字母</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">原则上前面以下划线开始</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">;</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">结构体变量命名必须用</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">大小写字母组合，第一个字母必须使用大写字母</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">必要时可用下划线间隔。对于私有数</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">据区，必须注明其所属的进程。</span>**<span
style="font-size:14px;">全局数据定义只需注意其用途。</span>**</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　示例如下：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> typedef struct</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> {</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> char </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> szProductName[20];</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> char </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> szAuthor[20];</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> char </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> szReleaseDate[16];</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> char </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> szVersion[10];</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> unsigned
long</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
MaxTables;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> unsigned
long</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span style="font-size:14px;">
UsedTables;</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">}DBS\_DATABASE;</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">DBS\_DATABASE GdataBase;</span></span>

<span
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"><span
style="font-size:14px;">：</span><span lang="EN-US"><span
style="font-size:14px;">st\_....</span></span></span>

<span lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:14px;font-family:宋体;">6
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">控件的命名：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">用小写前缀表示类别</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">用小写前缀表示类别：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">fm</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　窗口</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">cmd</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　 按钮</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">cob</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> combo</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">，下拉式列表框</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">txt</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　
文本输入框</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">lab</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> labal</span><span
lang="HI" style="font-size:14px;font-family:宋体;">，标签</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">img</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> image</span><span
lang="HI" style="font-size:14px;font-family:宋体;">，图象</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">pic</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> picture</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">grd</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> Grid</span><span
lang="HI" style="font-size:14px;font-family:宋体;">，网格</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">scr</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　 滚动条</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">lst</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　 列表框</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">frm</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;"> fram</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">7</span><span lang="HI"
style="font-size:14px;font-family:宋体;">注释</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">原则上注释要求使用中文</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">文件开始注释内容包括</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">:</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">公司名称、版权、作者名称、时间、模块用途、背景介绍等</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI" style="font-size:14px;font-family:宋体;">复</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">杂的算法需要加上流程说明</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">函数注释包括</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">:</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">输入、输出、函数描述、流程处理、全局变量、调用样例等</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">复杂的函数</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">需要加上变量用途说明</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">程序中注释包括</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">:</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">修改时间和作者、方便理解的注释等</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">;</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

在C++ 语法中，类的成员函数可以在声明的同时被定义，并且自动成为内联函数。

这虽然会带来书写上的方便，但却造成了风格不一致，弊大于利。建议将成员函数的定

义与声明分开，不论该函数体有多么小。

/\*

\* Copyright (c) 2001,上海贝尔有限公司网络应用事业部

\* All rights reserved.

\*

\* 文件名称：filename.h

\* 文件标识：见配置管理计划书

\* 摘 要：简要描述本文件的内容

\*

\* 当前版本：1.1

\* 作 者：输入作者（或修改者）名字

\* 完成日期：2001年7月20日

\*

\* 取代版本：1.0

\* 原作者 ：输入原作者（或修改者）名字

\* 完成日期：2001年5月10日

\*/

 

<span lang="EN-US" style="font-size:14px;font-family:宋体;">8
</span><span lang="HI"
style="font-size:14px;font-family:宋体;">程序</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">a.</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　
程序编码力求简洁，结构清晰，避免太多的分支结构及太过于技巧性的程序，</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">尽量不采用递归模式。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">b.</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　
编写程序时，亦必须想好测试的方法，换句话说，</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">”</span><span lang="HI"
style="font-size:14px;font-family:宋体;">单元测试</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">” </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">的测试方案应</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">在程序编写时一并拟好。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">c.</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　
注释一定要与程序一致。</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">d.</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　
版本封存以后的修改一定要将老语句用</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">/\* \*/ </span><span lang="HI"
style="font-size:14px;font-family:宋体;">封闭，不能自行删除或修改</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,</span><span
lang="HI" style="font-size:14px;font-family:宋体;">并要</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">在文件及函数的修改记录中加以记录。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">e.</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　 程序中每个</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">block </span><span
lang="HI" style="font-size:14px;font-family:宋体;">的开头</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> ”{" </span><span
lang="HI" style="font-size:14px;font-family:宋体;">及</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> "}” </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">必须对齐，嵌套的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">block </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">每进一套，</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">缩进一个</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">tab</span><span
lang="HI" style="font-size:14px;font-family:宋体;">，</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">TAB </span><span
lang="HI" style="font-size:14px;font-family:宋体;">为</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">4</span><span
lang="HI" style="font-size:14px;font-family:宋体;">个空格</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">,block</span><span
lang="HI" style="font-size:14px;font-family:宋体;">类型包括</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">if</span><span
lang="HI" style="font-size:14px;font-family:宋体;">、</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">for</span><span
lang="HI" style="font-size:14px;font-family:宋体;">、</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">while</span><span
lang="HI" style="font-size:14px;font-family:宋体;">、</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">do</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">等关键字引出的。</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">f.</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　对于比较大的函数，每个</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">block </span><span
lang="HI"
style="font-size:14px;font-family:宋体;">和特殊的函数调用，都必须注明其功能，举例如下</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI" style="font-size:14px;font-family:宋体;">：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">count.divisor = 1193280 /
freq;</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　　　　　</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;"> //</span><span
lang="HI" style="font-size:14px;font-family:宋体;">　</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">compute the proper count</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">OutByte((unsigned short)67,
(unsigned char)182);</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">//</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">tell 8253 that a</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">count is coming</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">OutByte((unsigned short)66,
count. c[0]);</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">//</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">send low-order byte</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">OutByte((unsigned short)66,
count. c[1]);</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　　　</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">//</span><span lang="HI"
style="font-size:14px;font-family:宋体;">　</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">send high-order byte</span></span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span style="font-size:14px;"> </span>

<span lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">×××××××××××××××××××××××××××××××××××××××</span></span>

<span lang="EN-US"
style="font-size:14px;font-family:宋体;">bcb</span><span lang="HI"
style="font-size:14px;font-family:宋体;">，</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">delphi</span><span lang="HI"
style="font-size:14px;font-family:宋体;">中的变量命名：</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　遵循匈牙利命名法，命</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">名必须有意义，制定如下规定</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">　窗体：以大写的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">W</span><span
lang="HI" style="font-size:14px;font-family:宋体;">开始，如</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">About</span><span
lang="HI" style="font-size:14px;font-family:宋体;">版权窗体，
命名为</span><span lang="EN-US"
style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">WAbout</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">文件：以大写的</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">F</span><span
lang="HI" style="font-size:14px;font-family:宋体;">开始，如</span><span
lang="EN-US" style="font-size:14px;font-family:宋体;">About</span><span
lang="HI"
style="font-size:14px;font-family:宋体;">版权窗体，文件命名为</span><span
lang="EN-US" style="font-size:9pt;font-family:宋体;"><span
style="font-size:14px;">FAbout.cpp</span></span>

<span lang="HI"
style="font-size:14px;font-family:宋体;">按钮</span><span lang="EN-US"
style="font-size:14px;font-family:宋体;">(Button)</span><span lang="HI"
style="font-size:14px;font-family:宋体;">：如退出按钮，命名为</span><span
lang="EN-US"
style="font-size:14px;font-family:宋体;">btnExit</span><span
lang="EN-US"
style="font-size:9pt;font-family:宋体;mso-fareast-language:ZH-CN;"></span>

 

函数注释:

//-----------------------------------------------------------------------------

// Barycentric:

// ------------

// Compute barycentric coordinates(u, v, w) for point p with respect

// to triangle(A, B, C).

//

// Parameters:

// [A] one point coordinate of triangle.

// [B] one point coordinate of triangle.

// [C] one point coordinate of triangle.

//-----------------------------------------------------------------------------






