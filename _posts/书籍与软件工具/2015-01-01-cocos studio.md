---
layout: post
title: cocos studio
category: 书籍与软件工具
tags: software
keywords: cocos2dx
description: 
---

#### 锚点使用错觉
锚点设为(0.5,0.5)

![](/Resources/cocos_studio_1.png)

显示效果却为:

![](/Resources/cocos_studio_2.png)

将锚点设置为(0,0)

![](/Resources/cocos_studio_3.png)

则可以达到期望的显示效果:

![](/Resources/cocos_studio_4.png)

#### 使用基础对象无法执行setVisible方法

添加节点

```
root_node:getChildByName("node"):setVisible(false)
```

却报错.

将此节点修改为控件图片

## Reference

* []()
