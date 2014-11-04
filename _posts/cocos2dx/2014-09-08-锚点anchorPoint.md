---
layout: post
title: 锚点anchorPoint
category: 游戏技术
tags: cocos2dx
keywords: 
description: 
---

锚点，当设置完position后，这个点到底是指向一张texture的哪一部分呢，锚点的作用就是指示这个position指向纹理图的左下角还是中间点还是右上角等等。

左下角是原点，向右为x轴正方向，向上为y轴正方向

锚点的取值范围一般是：**x[0,1],y[0,1]**.

*caution: 当然并没有限定其取值范围*,取anchor_point(-1,-1):

直观的设定便是，设置锚点坐标的时候即是texture的[0,width][0,height]这个范围映射为[0,1][0,1]相对应的点设置为当前位置position(x,y).

其真实的坐标公式是：

    actualPosition.x = position.x + width*(0.5 - anchor_point.x);
    acturalPosition.y = position.y + height*(0.5 - anchor_point.y)。


具体效果如下:

![](/Resources/锚点anchorPoint_1.gif)


根据上面的公式： 假设精灵的width = height = 10.

    actualPosition.x = 0 + 10*(0.5 - (-1)) = 15;
    actualPosition.y = 0 + 10*(0.5 - (-1)) = 15;

(15, 15) 这个结果正是现在图片的在屏幕上的实际位置。

**actualPosition指的就是纹理的中心点的坐标.**

例子三

    CCSprite *sprite = [CCSprite spritewithFile:@"blackSquare.png"];
    sprite.anchorPoint=ccp(1,1);
    sprite.position=ccp(sprite.contentSize.width , sprite.contentSize.height);
    [self addChild:sprite];
    

![](/Resources/锚点anchorPoint_2.gif)

根据上面的公式： 假设精灵的width = height = 10.

    actualPosition.x = 10 + 10*(0.5 - (1)) = 5;
    actualPosition.y  = 10 + 10*(0.5 - (1)) = 5; 

(5, 5) 这个结果正是现在图片的在屏幕上的实际位置。



