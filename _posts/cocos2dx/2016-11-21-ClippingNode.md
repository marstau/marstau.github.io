---
layout: post
title: ClippingNode
category: 编程开发
tags: cocos2dx
keywords: 
description: 
---

```
self.mask_node = cc.Sprite:create("res/ui/novice_hole.png")
self.fuzzy_node = ccui.Scale9Sprite:create("res/ui/novice_blocks.png")
self.stencil_node = cc.Node:create()
self.stencil_node:addChild(self.mask_node)
self.clipping_node = cc.ClippingNode:create()
self.clipping_node:setPosition(320, 420)
self.clipping_node:setStencil(self.stencil_node)
self.clipping_node:addChild(self.fuzzy_node)
self.clipping_node:setInverted(false)
self.clipping_node:setAlphaThreshold(0.5)
top_node:addChild(self.clipping_node)
```

## Reference

* <http://shahdza.blog.51cto.com/2410787/1561937/>
