---
layout: post
title: CCActionInterval
category: 游戏技术
tags: cocos2dx
keywords: 
description: 
---

##Version

```
cocos2d-x 3.2
```

##MoveTo和MoveBy

MoveTo继承MoveBy,使用的是MoveBy的update,reverse.

```
class CC_DLL MoveTo : public MoveBy
```

MoveBy和MoveTo同样的接口,但是前者表示向量运动,后者表示目标位置(absolute coordinate).

```
/* 按deltaPosition的方向运动|deltaPosition|的向量长度 */
    static MoveBy* create(float duration, const Vec2& deltaPosition);

/* 运动到位置position */
    static MoveTo* create(float duration, const Vec2& position);

```

##ScaleBy和ScaleTo

ScaleBy继承ScaleTo,使用的是ScaleTo的update.

```
class CC_DLL ScaleBy : public ScaleTo
```

ScaleBy是Scale的倍数a上再翻b倍,而ScaleTo仅仅是Scale到b倍,startWithTarget下的_deltaX计算为例:

```
void ScaleBy::startWithTarget(Node *target)
{
	// ...
    _deltaX = _startScaleX * _endScaleX - _startScaleX;
    // ...    
}

void ScaleTo::startWithTarget(Node *target)
{
	// ...
    _startScaleX = target->getScaleX();
    // ...
    _deltaX = _endScaleX - _startScaleX;
    // ...
}
```

