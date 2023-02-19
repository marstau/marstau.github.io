---
layout: post
title: Unity3D NGUI
category: 编程开发
tags: GameEngine
keywords: Unity3D
description: 
---

#### NGUI中,若如文字等被覆盖住,可将localPosition.z移近一个单位(-1).

#### NGUI添加了碰撞盒,可是却没有得到预期的效果,可能原因是将碰撞盒的z值设为了其他值(如-2),改为0即可。

#### NGUI中的Example 7 - Scroll View (Panel)中items的图片显示不正常
     修改edit-\>Graphics Emulation-\>Generic OpenGL2.0

#### 修改layer之后,之前的效果消失
     camera下的UICamera的event receiver mask也要同步修改.

#### scroll view(panel)裁剪,items却不显示,若勾选UIPanel，则没有裁剪效果。
     item上绑定了UIPanel,所以无法显示,将UIPanel去掉即可。

#### NGUI的某个slicedsprite层级无法设置
     其panel
    parent的层级没有改变,无法直接修改其层级，要通过修改父层级才能一起修改子层级。

#### NGUI的scroll view(panel)裁剪问题\
     Clip view的Clipping未设置为soft
    Clip,裁剪。（caution:UIGrid的直系子对象要设置scale因子为1）\
     Clip view会随着items一起运动,将clip view的Scale因子设为1即可。

#### NGUI中若button的字和底边其实设置正确了,但是在scene视图中无法正常显示,而在Game视图中却正常显示,则可以在右上角的坐标旋转上先旋转到其他角度,然后旋转回来即可。

#### NGUI中用同一图集,先后层次可以通过深度来表现,若不是同一图集,则用z坐标来表现,深度意义不大，当新加入同一图集的元素,即使深度更深,还是会被遮挡,所以这个时候要设置z坐标了。(个人之见)

#### NGUI中press
    button没有任何反应
     虽然button加了collider,但是和没有加一样的,原来是Camera的UICamera的Every
    Receiver Mask的层级没有修改为相应的层级.

#### NGUI图片用九宫格拉伸形变，记得要选择sliced sprite，而不是sprite

#### NGUI中2D camera和3D
    camera设置的时候,只能显示一个
     3D camera的clear flags必须设置为depth only.

#### 制作atlas图集的时候被自动裁掉一半
     设置Edit -\> Graphics Emulation -\> Generic OpenGL ES2.0

#### NGUI不管调深度还是调z都无法调成正确的遮挡
     因为这些遮挡不正确的是在不同panel下
    所以z和depth值没有什么意义，将所有这些置于同一panel下即可。

#### NGUI的camera裁剪左右移动,而不是上下移动
     将UIDraggable Camera的Scale(1,0)(水平)设置为Scale(0,1)（竖直）

#### NGUI中的Camera无法设置Camera的Size\
     在UIViewPort中调整Full Size即可。

#### NGUI列表中同时显示2D和3D时,用Grid可以正确裁剪2D的,但却无法裁剪3D的

    运用camera裁剪,将3D的裁剪掉,然后用Grid裁剪就行了。(@todo，详细地请见下回分解)

#### NGUI拖拽
     (1) 添加各个组件: UIDraggable panel(Scale设置为(1,0,0))、Box
    Collider、UIDrag Panel Contents，\
     (2) UIPanel的Clipping设置为Soft Clip,并设置center、Size参数\
     (3)
    若还是无法正常拖拽，看下camera的UICamera组件是否启用，若item在不同的layer也拖不动,所以得在一个层次(如统一的default层)

#### EasyMotion2D中Render只要一次，可以有各种animation


#### EasyMotion2D动画动得很突兀
     将Sprite Renderer中的Anchor设置为none

#### NGUI中2D摄像机和3D摄像机，每次只能显示一种,必须得重设才能显示两个
     将2D camera中的Culling
    Mask(假设原来仅有layer\_2D)增加3D物体的层(layer\_3D)。

#### NGUI如果不用同一图集，不仅z和depth不好设置,而且一些公用的资源同时占用显存，得不偿失。

#### NGUI中有些没有layer(也不是default layer) 为此UI设置Add layer，然后返回,即可设置为空layer。

#### UISlicedSprite改变图集中的名字用sprite.name,这样在停止运行后，图集中的命名就变
    了，如果仅仅要获取图集中的其它图片，则用spriteName。

#### NGUI的scroll bar滚动条随着大小变化而移动

    因为图集中的padding位移了一定位置，所以位置改变了，将padding修改为0即可。

#### EasyMotion2D不同的animation挡住了

    设置不同的层级，就可以显示出来了，然后用不同层级的render分别渲染，就可以显示出来了。

#### NGUI为UIPanel增加光照
     勾选UIPanel脚本的Normals.

#### NGUI中明明应该在中心点的位置却没在中心点
     因为某些sprite设置为top-left的pivot等。

#### NGUI的UITable当items一多的时候，字体就移位了
    因为localPosition.z设置为了非0值，将其设置为0即可，为了不遮挡，所以也要将这些文字的图集与遮挡其的图集合并为一个图集。

#### NGUI的颜色面板变成了HSVA
     右键点击Sliders正右边的那个条框即可。
