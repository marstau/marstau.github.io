---
layout: post
title: Daytoday Accumulation
category: 点滴知识
tags: normal-knowledge
keywords: 
description: 
---

1.  the best possible visuals games must run at 60 fps (in countries
    with NTSC TV format; 50 fps in PAL territory).<span
    id="__kindeditor_bookmark_end_16__" style="display:none;"></span>
2.  <span class="Apple-style-span"
    style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">-128的补码不是0吗,当我用</span>\
     <span class="Apple-style-span"
    style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">MOV
    AL, -128</span>\
     <span class="Apple-style-span"
    style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">NEG
    AL;</span>\
     <span class="Apple-style-span"
    style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">之后,果不其然,AL结果还是80H</span>\
3.  <div>

     \_numTriangles = \_numCellsPerRow \* \_numCellsPerCol \* 2;

    </div>

    <div>

    // 三角形的数目 = 横边的数目\*竖边的数目\*2;

    </div>

4.  <div>

    // 求randfloat from lowBound to highBound
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#0000ff;">float</span><span
    style="color:#000000;"> d3d::GetRandomFloat(</span><span
    style="color:#0000ff;">float</span><span
    style="color:#000000;"> lowBound, </span><span
    style="color:#0000ff;">float</span><span
    style="color:#000000;"> highBound)\
     ![](/Images/OutliningIndicators/ContractedBlock.gif)</span><span
    id="Codehighlighter1_59_307_Closed_Text"
    style="border-right:#808080 1px solid;border-top:#808080 1px solid;display:none;border-left:#808080 1px solid;border-bottom:#808080 1px solid;background-color:#ffffff;">![](http://files.note.sdo.com/XbPJ4~jTZv6wLX0g4006Zs)</span><span
    id="Codehighlighter1_59_307_Open_Text"><span
    style="color:#000000;">{\
         </span><span style="color:#0000ff;">if</span><span
    style="color:#000000;">( lowBound </span><span
    style="color:#000000;">\>=</span><span
    style="color:#000000;"> highBound ) </span><span
    style="color:#008000;">//</span><span
    style="color:#008000;"> bad input</span><span
    style="color:#008000;">\
     </span><span style="color:#000000;">        </span><span
    style="color:#0000ff;">return</span><span
    style="color:#000000;"> lowBound;\
    \
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> get random float in [0, 1] interval</span><span
    style="color:#008000;">\
     </span><span style="color:#000000;">    </span><span
    style="color:#0000ff;">float</span><span
    style="color:#000000;"> f </span><span
    style="color:#000000;">=</span><span
    style="color:#000000;"> (rand() </span><span
    style="color:#000000;">%</span><span
    style="color:#000000;"> </span><span
    style="color:#000000;">10000</span><span
    style="color:#000000;">) </span><span
    style="color:#000000;">\*</span><span
    style="color:#000000;"> </span><span
    style="color:#000000;">0.0001f</span><span
    style="color:#000000;">; \
    \
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> return float in [lowBound, highBound] interval. </span><span
    style="color:#008000;">\
     </span><span style="color:#000000;">    </span><span
    style="color:#0000ff;">return</span><span
    style="color:#000000;"> (f </span><span
    style="color:#000000;">\*</span><span
    style="color:#000000;"> (highBound </span><span
    style="color:#000000;">-</span><span
    style="color:#000000;"> lowBound)) </span><span
    style="color:#000000;">+</span><span
    style="color:#000000;"> lowBound; \
     }</span></span>

    </div>

    </div>

5.  I'd really recommend staying away from DirectPlay. It's not been
    updated in ages, provides very little advantage over plain Windows
    Sockets, is a pain to set up, and isn't at all portable.

6.  **<span style="color:#e53333;">Pure Devices</span>**

    DirectX 8.0 introduces the concept of a "pure" device. When using a
    pure device the runtime does not track state or state blocks or
    perform any software vertex processing on behalf of the hardware.
    Furthermore, the application cannot query back state from the
    runtime. The lack of state tracking, particularly when state blocks
    are being used, can result in a significant performance boost for
    the application.

    Only vertex processing directly supported by the hardware is
    available to the application when using a pure device. For example,
    for cards that do not support hardware transform and lighting, only
    pretransformed vertices can be passed to Direct3D. Furthermore, the
    API functions SetClipStatus, GetClipStatus and ProcessVertices
    cannot be used with the pure device.

    In order to use a pure device the application must request it with
    the device creation flag **D3DCREATE\_PUREDEVICE** and the driver
    must report its ability to act as a pure device.

7.  **<span style="color:#e53333;">if(FAILED(CoInitialize(NULL))) return
    false;</span>**

    CoInitialize() return value:

    S\_OK

    The COM library was initialized successfully on this thread.

    S\_FALSE

    The COM library is already initialized on this thread.

    so, we should use\
     **if(S\_FALSE == CoInitialize(NULL) ) return false;**

8.  **<span
    style="color:#e53333;">你应该尽量注意域...(::这个要常用)</span>**
9.  返回E\_FAIL，是告诉调用程序－－某些地方出错，必须进行处理。否则，程序不能进行下去了。\
     而返回S\_FALSE，不是表示出现错误, 而是一种返回值。\

    S\_OK和S\_FALSE，就是程序返回值的不同表示。如果将它们表示成S\_1和S\_2可能更好理解些！

    调用程序只需对返回的S\_OK和S\_FALSE进行判断，然后决定程序的走向。

    最主要的误解是由S\_FALSE的名称带来的。

    关键－－S\_FALSE不是错误，是返回值。

10. **<span
    style="color:#e53333;">当出现播放音乐不能播放的时候,可能是因为初始化音乐后立刻播放,影响了正常播放具体原因哥也不知道</span>**

    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#008000;">//</span><span
    style="color:#008000;">载入音乐</span><span style="color:#008000;">\
     </span><span
    style="color:#0000ff;">if</span>(!g\_SoundSystem-\>AddSound("data/menu\_music.wav",UGP\_INFINITE,&g\_menuSound))\
         MessageBox(NULL,"AddSound()-失败","提示",MB\_OK);\
     <span style="color:#008000;">//</span><span
    style="color:#008000;">播放音乐</span><span style="color:#008000;">\
     </span>g\_SoundSystem-\>Play(g\_menuSound);\
    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> Change to\
     </span><span style="color:#008000;">//</span><span
    style="color:#008000;">载入音乐</span><span style="color:#008000;">\
     </span><span
    style="color:#0000ff;">if</span>(!g\_SoundSystem-\>AddSound("data/menu\_music.wav",UGP\_INFINITE,&g\_menuSound))\
         MessageBox(NULL,"AddSound()-失败","提示",MB\_OK);\
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> 中间其他函数代码\
     </span><span style="color:#008000;">//</span><span
    style="color:#008000;">播放音乐</span><span style="color:#008000;">\
     </span>g\_SoundSystem-\>Play(g\_menuSound);
     

    </div>

11. **<span style="color:#e53333;">D3DXMATRIX是否需要ZeroMemory</span>**
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    D3DXMATRIX matrix;\
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> no need to ZeroMemory( &matrix,sizeof(D3DXMATRIX) );\
     </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> D3DXMatrixTranslation will automatically initialize\
     </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> it, the same as D3DXMatrixRotationAxis</span><span
    style="color:#008000;">\
     </span>D3DXMatrixTranslation( &matrix, pos.x, pos.y, pos.z );

    </div>

12. **<span style="color:#e53333;">Device-\>SetRenderState(
    D3DRS\_SHADEMODE, D3DSHADE\_GOURAUD );</span>**

    You have to turn off the light, i.e.\
     Device-\>SetRenderState( D3DRS\_LIGHTING, false );

13. **<span
    style="color:#e53333;">当静态链接库中出现无法解析的问题的时候,有一种可能就是.lib文件没有重新编译,导致无法链接.</span>**
14. **<span style="color:#e53333;">Device-\></span><span
    style="color:#e53333;">LightEnable</span><span
    style="color:#e53333;">( </span><span style="color:#e53333;">0, 
    true </span><span style="color:#e53333;">);</span>**\
     Enables or disables a set of lighting parameters within a device.\
     See it?可以设置N个光源.
15. **<span style="color:#e53333;">限定FPS</span>**
16. **<span style="color:#e53333;">D3DXVec3TransformNormal</span>**\
     <span id="__kindeditor_bookmark_end_18__"
    style="display:none;"></span>Transforms the 3D vector normal by the
    given matrix.(将3D向量通过矩阵转换,并且normal化为法向量.)\
     If you want to transform a normal, the matrix you pass to this
    function should be the transpose of the inverse of the matrix you
    would use to transform a
    point.(如果你想要得到一条法线,你传递的矩阵就应该是这个用来转换point的函数的参数矩阵的逆的转置.)
17. **<span style="color:#e53333;">将坐标移到坐标原点</span>**

     float dx = x - col;

     float dz = z - row;\

    (x,z)相对于(col,row)的坐标,即(x-col,z-row),即(col,row)在坐标原点,(dx,dz)为变换后的坐标.

18. Single
    view:[ebp + (edx - 1)\*1]:寄存器减1后还要与其他的相乘的话就必须得先暂存edx-1的结果,所以是错的

19. 缺省实参只在单个文件有效,因为实参是在编译时刻提取出来,而不同文件在在链接时刻,即runtime.

20. CBoneMesh \*boneMesh = new CBoneMesh;

    memset( boneMesh, 0, sizeof(CBoneMesh) );\
     // 不能将CBoneMesh替换为boneMesh,因boneMesh为指针.

21. int和unsigned之间的转换例如80000000,int和unsigned都是一样的,只是解释的方式不一样而已,一个解释为复数,另一个解释为无符号数.
22. 通过了解结构体之间的各个变量了解结构关系.
23. 耗费两天

    void \*pDest = NULL;

    hr = pExXMeshContainer-\>\_pXMeshSkin-\>LockVertexBuffer(
    0, reinterpret\_cast\<void \*\*\>(&pDest) );\
     &pDest漏了pDest,于是,每次lock的时候都直接崩溃,弄得我都快崩溃了.

24. **静态链接库中尽量避免定义静态成员**

    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;">\
     </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> static link lib\
    \
     </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> test.h</span><span style="color:#008000;">\
     </span>\#ifndef \_\_test\_H\_\_\
     <span style="color:#0000ff;">\#define</span> \_\_test\_H\_\_\
    \
     \#include "..\\\\test3\\\\stdafx.h"\
    \
     <span style="color:#0000ff;">class</span> C{\
     <span style="color:#0000ff;">public</span>:\
         <span style="color:#0000ff;">static</span> <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">string</span> SC\_STR;\
     };\
    \
     <span style="color:#0000ff;">\#endif</span>\
    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> test.cpp</span><span
    style="color:#008000;">\
     </span>\#include "test.h"\
    \
     <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">string</span> C::SC\_STR("test string");\
    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;">\
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> test project. Unresolved or can't initialize
    noramlly.</span></span><span style="color:#008000;">\
     </span>\#include "stdafx.h"\
    \
     <span style="color:#0000ff;">int</span> main(){\
         cout \<\< C::SC\_STR \<\< endl;\
     }\
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> Unresolved or can't initialize
    noramlly.</span>

    </div>

25. 两个类,其中一个类想要另外一个类的内容,可以定义那个类的引用.

26. My
    guess:像D3DXVec3Transform、D3DXVec3TransformCoord等之类的旋转某个点的,其实都是绕着通过原点的轴旋转的.

27. My
    guess:SetRenderState你设置了并不代表会立刻执行,这只是通知一下等下应该以这样的状态执行而已.

28. VertexShader = compile vs\_1\_1 Main();\

    这大小写不敏感的丫,vertexshader也可以,VertexShader也可以,我勒个去.(貌似就这个大小写不敏感)

29. CTTransform-\>SetMatrix( Device, HWorldViewProj, &(MatObjWorld\*MatView\*MatProj) );

    是MatObjWorld \* MatView \* MatProj而不是MatView \* MatProj \*
    MatObjWorld,那是因为MatObjWorld在world space,然后变换至view
    space,然后进行投影,所以可以正常使用,反过来就不行了.

30. CTTransform-\>SetDefaults( Device );\
     // .fx:

    vector Blue = {0.0f, 0.0f, 1.0f, 1.0f};

    若是CTTransform-\>SetDefaults( Device );不设置的话,则Blue就不会自动赋值.

31. 调试的时候语句是正常的,但是调试的时候却跳过了如此正常的语句,那是因为修改了代码,由于某种原因,编译器没有识别出来,所以必须重建工程,重新导入源文件编译才可以.\
     eg：\
     ![](http://files.note.sdo.com/XbPJ4~jZghqiwE0gM00fDF)\
     按一下F10后

     

    直接跳过了

     ![](http://files.note.sdo.com/XbPJ4~jZghq2wE0gM00fDB) 

    这两个变量的定义

32. My guess: void fun( int \*&a );\

    a本质上还是指针的指针,\*&a只是让它增加可读性而已,仅此而已,从本质上并不能称作引用.

33. **<span style="color:#e53333;">.hpp文件定义模板:\
     </span>**定义template\<class
    T\>竟然不行(error C2061: 语法错误: 标识符“c1ass”),得换成template\<typename
    T\>

34. **<span style="color:#e53333;">引用未初始化的指针变量:</span>**\
     eg:\
     stNode \*head;

    head = Create(head, arr, C\_SIZE );

    必须改为\
     stNode \*head = NULL;\
     head = Create(head, arr, C\_SIZE );

    warning C4700: 使用了未初始化的局部变量“head”

35. ** memset对指针的指针置数注意**

    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#0000ff;">int</span> \*\*p = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">int</span> \*;\
         \*p = <span style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">int</span>[3];\
         memset( \*p, numeric\_limits\<<span
    style="color:#0000ff;">int</span>\>::max(), <span
    style="color:#0000ff;">sizeof</span>(<span
    style="color:#0000ff;">int</span>)\*3 );\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< 3; i++ )\
             cout \<\< (\*p)[i] \<\< " ";\
    \
         delete [](\*p);\
         delete p;

    **// -1 -1 -1**

    </div>

36. **<span style="color:#e53333;"> \<和</span><span
    style="color:#e53333;">\>比较的操作数顺序问题</span>**\
     eg:\
     if( min \> a ) min = a;\
     对于比较操作符,需要修改的放在左边.

37. **<span style="color:#e53333;">delete指针的指针</span>**\
     eg:\
     // int \*\*D;

    for( int i = 0; i \< n; i++ )

      delete []\*(D + i); // not delete [](\*D + i);

    delete []D;

38. **<span style="color:#e53333;">ch = new char[len +
    1]后使用指针还是数组.</span>**\
     eg:\
     ch[idx],当idx = -1的时候,是不会检查边界的.\
     而使用\*(ch + idx),当idx
    = -1的时候,则会出现如下错误:![](http://files.note.sdo.com/XbPJ4~jZB7_iwE0bs002z4)
39. **<span style="color:#e53333;">算移关位逻,条赋逗.</span>**
40. **<span style="color:#e53333;">subclass</span>**\
     eg:\
     create A, by subclassing B.\
     class A: public B{};

41. **<span style="color:#e53333;">(++a)+=3;</span>**\
     <span class="Apple-style-span"
    style="display:inline! important;float:none;word-spacing:0px;font:14px/21px verdana, 'courier new';text-transform:none;color:#000000;text-indent:0px;white-space:normal;letter-spacing:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">C++中,++a的结果是左值,返回给值本身,也就是说上面合法</span>

42. **<span style="color:#e53333;">四舍五入</span>**\
     inline
    int round( double number ){ return static\_cast\<int\>( floor(number + 0.5) );}

43. **<span style="color:#e53333;">返回局部变量值</span>**
44. 日常编程注意点\
     溢出、除数为0、题目中说正整数,那你定义变量就是unsigned、\
     for rendermonkey:\
     float1、float2还是float3、screen mapping大小是否要修改、render
    states、sample states是否设置、
45. **<span style="color:#e53333;">引用注意点</span>**<span
    style="color:#e53333;"> </span>

    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

        <span style="color:#0000ff;">short</span> b = 12;\
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> &a = b;\
         cout \<\< <span
    style="color:#0000ff;">sizeof</span>(b) \<\< endl;\
         <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
         2\
         </span><span style="color:#008000;">\*/</span>

    </div>

46. **<span style="color:#e53333;">程序一直不退出</span>**\
     ![](http://files.note.sdo.com/XbPJ4~k2ci92wE0gw0024d) \
     析构函数无法正常退出,比如死循环.

47. **<span style="color:#e53333;">私有继承</span>**

    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#0000ff;">class</span> B{\
     <span style="color:#0000ff;">public</span>:\
    \
     };\
    \
     <span style="color:#0000ff;">class</span> D : <span
    style="color:#0000ff;">private</span> B{\
     <span style="color:#0000ff;">public</span>:\
    \
     };\
     <span style="color:#0000ff;">void</span> fun( B &b ){\
    \
     }\
     <span style="color:#0000ff;">int</span> main(){\
         D d;\
         fun( d ); **// Error: 不允许对不可访问的基类"B"进行转换.**\
     }

    </div>

48. **vector在类构造函数中初始化的问题**

    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#0000ff;">class</span> CInteger{\
     <span style="color:#0000ff;">public</span>:\
         CInteger( <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> length )\
             :\_vecIData.reserve(length){} <span
    style="color:#008000;">//</span><span
    style="color:#008000;"> **error C2059: 语法错误".".**</span><span
    style="color:#008000;">\
     </span>    <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
         CInteger( const int length ){\
                 \_vecIData.reserve(length)\
             }\
         </span><span style="color:#008000;">\*/</span>\
         \
     <span style="color:#0000ff;">private</span>:\
         vector\<<span style="color:#0000ff;">int</span>\> \_vecIData;\
     };

    </div>

49. <span style="color:#e53333;">**运算开销**</span>\
     大多数运算开销需要约 10ns,而取模运算接近100ns.\<\<编程珠玑9.2\>\>

50. **<span style="color:#e53333;">itoa小技巧</span>**\
     p = "0123456789abcdef"[2%16];

51. **<span style="color:#e53333;">struct Derived : private
    Base{}</span>**
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    \#include "BigInt.h"\
     <span style="color:#0000ff;">class</span> Base{\
     <span style="color:#0000ff;">public</span>:\
         <span
    style="color:#0000ff;">void</span> baseFun(){ cout \<\< \_b \<\< endl; }\
     <span style="color:#0000ff;">protected</span>:\
         <span style="color:#0000ff;">static</span> <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> \_b = 3;\
     };\
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> 虽然是struct,但是继承的话还是跟class一样的,不会报错,就相当于struct默认设置成了class.</span><span
    style="color:#008000;">\
     </span><span style="color:#0000ff;">struct</span> Derived : <span
    style="color:#0000ff;">public</span> Base{\
     <span style="color:#0000ff;">public</span>:\
         <span
    style="color:#0000ff;">void</span> fun(){ cout \<\< "D" \<\< endl; }\
     };\
     <span style="color:#0000ff;">int</span> main(){\
         Derived d;\
         d.fun();\
         d.baseFun();\
     }\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     D\
     3\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

52. **<span style="color:#e53333;">类中const数组初始化问题</span>**
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    <span style="color:#0000ff;">class</span> A\
     {\
     <span style="color:#0000ff;">public</span>:\
       A();\
     <span style="color:#0000ff;">private</span>:\
       <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> a[3] = {1, 2, 3};\
     };

    </div>

    \(1) C++ 11中似乎支持如下语法\
     ![](http://files.note.sdo.com/XbPJ4~k3dEO2wE0dg004fJ)\
     (2)加上static\
     (3)用vector来代替
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    \#include "stdafx.h"\
    \
     <span style="color:#0000ff;">class</span> C{\
     <span style="color:#0000ff;">public</span>:\
         C( <span style="color:#0000ff;">int</span> \*a, <span
    style="color:#0000ff;">int</span> n )\
             :\_data(a, a + 3){}\
    \
         <span style="color:#0000ff;">void</span> printInfo(){\
             copy( \_data.begin(), \_data.end(), ostream\_iterator\<<span
    style="color:#0000ff;">int</span>\>(cout, " ") );\
             cout \<\< endl;\
         }\
     <span style="color:#0000ff;">private</span>:\
         <span style="color:#0000ff;">const</span> vector\<const <span
    style="color:#0000ff;">int</span>\> \_data;\
     };\
    \
     <span style="color:#0000ff;">int</span> main(){\
         <span style="color:#0000ff;">int</span> a[3] = {1, 2, 3};\
         C c(a, 3);\
         c.printInfo();\
     }\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     1 2 3\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

53. **<span style="color:#e53333;">类成员函数内定义static</span>**
54. picking\

    picking操作的时候,出了问题,无法正确获取射线与平面y=0的交点,原来是我设置\
     Device-\>SetTranform( D3DTS\_VIEW, &(view\*proj) );\
     这应该换为\
     Device-\>SetTransform( D3DTS\_VIEW, &view );\
     Device-\>SetTransform( D3DTS\_PROJECTION, &proj );
55. **<span style="color:#e53333;">delete</span>**
56. **<span style="color:#e53333;">头文件中声明同时定义函数</span>**\
     必须加上inline,这并不是成员函数,成员函数倒是可以不加.\

    inline D3DXMATRIX MatOfIdentity(){ D3DXMATRIX identity; return \*D3DXMatrixIdentity(&identity); }\
     否则会显示[已在 Utility.obj 中定义；已忽略第二个定义]之类的信息.
57. **<span style="color:#e53333;">类成员函数中定义静态变量</span>**
    <div
    style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

    \#include "stdafx.h"\
    \
     <span style="color:#0000ff;">class</span> C{\
     <span style="color:#0000ff;">public</span>:\
         <span style="color:#0000ff;">void</span> fun(){\
             <span style="color:#0000ff;">static</span> <span
    style="color:#0000ff;">int</span> a = 3;\
             a++;\
             cout \<\< a \<\< endl;\
         }\
     };\
     <span style="color:#0000ff;">int</span> main(){\
         C c1;\
         c1.fun();\
         C c2;\
         c2.fun();\
     }\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     4\
     5\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    **可见,不同的类只会作用在同一个静态变量上.**

    </div>

58. **<span
    style="color:#e53333;">类的静态成员和const成员变量初始化问题</span>**\
     const variable必须在类建立的时候初始化,所以是在constructor中.\
     static variable无法在constructor中初始化,必须在类外初始化.\
     所以static const
    variable衍生成了要么以static的方式初始化,如果是有序型的甚至还可以在类内定义呢.
59. **<span style="color:#e53333;">strlen( NULL )果然崩溃</span>**

60. **<span
    style="color:#e53333;">cout \<\< pNode -\> \_data \<\< endl;毫无问题,</span><span
    style="color:#e53333;">原来</span><span
    style="color:#e53333;">空格不要紧.</span>**

61. **<span style="color:#e53333;">15升的</span><span
    style="color:#e53333;">水杯</span><span
    style="color:#e53333;">和27升的</span><span
    style="color:#e53333;">水</span><span
    style="color:#e53333;">杯</span><span
    style="color:#e53333;">,装入容器中,能准确量出多少L的水.</span>**\

    比如这个问题的话,很容易知道,通过不断的加减法运算量出不同L的水,但是会发现一个规律,15L和27L水加减法运算总是可以提取公因子的3\*(5和9),所以最后量出来的水肯定是3的倍数.

62. **<span style="color:#e53333;">class Derived : Base {};
    默认为private继承.</span>**
63. **<span style="color:#e53333;">点转换到另外一个齐次空间中(如从world
    space</span><span style="color:#e53333;">转换到tangent
    space中</span><span style="color:#e53333;">)</span>**\
     XAxis = tangent, YAxis = binormal, ZAxis = normal.\
     matrix-1:\
     XAxis.x YAxis.x ZAxis.x\
     XAxis.y YAxis.y ZAxis.y\
     XAxis.z YAxis.z ZAxis.z\
     tangentPos = worldPos\*matrix-1 or tangentPos = matrix\*worldPos;\
     从world space转换到tangent
    space,其实是将tangent坐标系还原到world使两者重合,所以就像上面一样是逆矩阵.
64. **<span style="color:#e53333;">矩阵相乘</span><span
    style="color:#e53333;">行列表示</span>**\
     float4 pos;\
     floatx4x4 mat;\
     两者相乘, pos\*mat 和 mat-1\*pos-1是等价的.
65. **<span style="color:#e53333;">若从programming pipeline转为fixed
    pipeline,无法正常显示,则可能是projection,view未设置.</span>**\
     eg:

    Device-\>SetTransform( D3DTS\_PROJECTION, &ProjMatrix );\
     Device-\>SetTransform( D3DTS\_VIEW, &view );

66. **<span
    style="color:#e53333;">当同一个程序出现两种不同的结果的时候,那就是多线程的结果,例如WndProc和构造函数调用顺序不定影响不同的结果.</span>**
67. **<span style="color:#e53333;">\#include"header.h</span><span
    style="color:#e53333;">"包含上层的上层</span><span
    style="color:#e53333;">目录</span>**\
     上层目录:\#include "..\\\\folder1\\\\header.h"\
     再上层目录:\#include"..\\\\..\\\\folder2\\\\header.h"\
     以此类推
68. obj模型文件后缀名换成.txt就可以直接查看里面的内容.
69. **<span style="color:#e53333;">ZeroMemory指针注意</span>**\
     C \*c;\
     ZeroMemory( c, sizeof(c) ); **// sizeof(c) = 4, 不是sizeof(C)。**
70. **<span style="color:#e53333;">\#ifndef定义重复</span>**\
     明明在一个文件中定义了,却说错误,可能是\
     \#ifndef定义重复了,被其他文件掩盖而产生错误
71. **<span
    style="color:#e53333;">pow(f, e) will not work for negative f</span>**\
     ![](http://files.note.sdo.com/XbPJ4~kcMJ_ywE00o00ekX)\
     就算加条件判断也无法阻止pow报错\
     ![](http://files.note.sdo.com/XbPJ4~kcMJ_iwE00o00ekU)\
     改成\
     ![](http://files.note.sdo.com/XbPJ4~kcMJ_iwE00o00ekQ)

72. **<span style="color:#e53333;">\#ifndef大小写敏感</span>**\
     \#ifndef \_\_octree\_H\_\_ //
    对大小写敏感,如果定义了\_\_Octree\_H，还是表示不同的预定义。\
     \#define \_\_octree\_H\_\_
73. **cmd命令**\
     \\\>cd android-sdk-window 

    \\android-sdk-windows\>

74. **<span style="color:#e53333;">.m和.mm文件</span>**\
     .m文件是object-c文件

     .mm文件相当于c++或者c文件

75. DLL全局指针分配内存释放后要将指针设为NULL

76. **<span style="color:#e53333;">cmd命令</span>**\

    rename E:\\Workspaces\\syjt\\trunk\\project\\android\\obj\\local\\armeabi\\libsyjt.so a.so
    // 将libsyjt.so文件重命名为a.so

77. 尽量用栈变量而不是成员变量(比如new分配的,保存在heap中)，因栈读取效率高。


------------------------------------------------------------------------

**<span style="color:#e53333;">RenderMonkey</span>**:

1.  My guess:RenderMonkey1.82上当你定义一个mat4x4 color\_filter.\
     ![](http://files.note.sdo.com/XbPJ4~kaYhS2wE1cQ005M1)\
     在pixel shader中这样写的时候\
     float4 col = tex2D(Texture0,  texCoord);

    return mul(color\_filter,col);

    按理来说颜色是会变成红色的,但是却没有变,而shaders for game
    programmers and
    artists中却能正常变红色.我勒个去,如果转置一下就可以正常显示了.(只要替换成mul(col,color\_filter)即可,直接想象成rendermonkey会自动换成color\_filter\*col,不然在DirectX环境下它就会先实行转置,然后再color\_filter\*col,在DirectX下直接mul(col,color\_filter)这样就相当于让DirectX不会自动去转置了,rendermonkey便执行正确).

2.  vertex shader的输入参数设置为vs\_main( float4 pos : POSITION,
    float2 tex : TEXCOORD ){}\
     则相应的Stream Mapping也应作相应设置。\
     ![](http://files.note.sdo.com/XbPJ4~kaYhRiwE1cQ005LW)

3.  **<span
    style="color:#e53333;">rendermonkey非常不科学的一个BUG</span>**\
     **// 一**\
     凡是有"一"的注释一律报错.
4.  **<span style="color:#e53333;">cout \<\< endl和cout \<\<
    '\\n</span><span style="color:#e53333;">'</span>**\
     除了endl刷新缓冲区外,还有个小技巧有区别.\
     eg:\
     (1) outFile \<\< setw(50) \<\< setfill('-') \<\< endl;\
     outFile \<\< str \<\< endl;\
     (2) outFile \<\< setw(50) \<\< setfill('-') \<\< '\\n';\
     outFile \<\< str \<\< endl;\
     (1)中的endl并不会生效
5.  **<span
    style="color:#e53333;">Release版本和Debug版本运行结果不一样</span>**\
     Release版本会将一些变量未初始化的全部初始化，例如float \*block =
    new float[10];debug版本下不会初始化，而release版本会初始化。
     
* printf打印十六进制

  %08x表示打印8位十六进制数,不足8位则在前面补0
* 内存对齐[More](http://blog.csdn.net/musiccow/article/details/5817285)




