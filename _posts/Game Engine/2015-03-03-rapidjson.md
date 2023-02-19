---
layout: post
title: rapidjson
category: 编程开发
tags: GameEngine
keywords: 
description: 
---

```
filenameValue.SetString(temp.c_str(), static_cast<int>(temp.size()));
```
Value::SetString need to allocate memory, so you have to pass allocator.

```
filenameValue.SetString(temp.c_str(), static_cast<int>(temp.size()), document.GetAllocator());
```

## Reference
