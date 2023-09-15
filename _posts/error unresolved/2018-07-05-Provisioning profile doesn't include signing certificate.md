---
layout: post
title: Provisioning profile doesn't include signing certificate
category: errors
tags: error-unresolved
keywords: web
description: 
---	


## Error

```
Provisioning profile "" doesn't include signing certificate
```

## Solution

```
描述文件和证书不匹配，即开发的描述文件不能在xcode选择生产证书进行codeSign，反过来也不行，只能完全对应

![](/Resources/1530771671594.jpg)

```

## Reference
