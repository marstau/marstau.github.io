---
layout: post
title: COMMON ERROR - python
category: errors
tags: error-unresolved
keywords: 
description: 
---

#### 运行protoc-gen-lua报:
```
--lua_out: protoc-gen-lua: plugin failed with status code 9009.
```

Solution:
python-2.7.12未安装protobuf, pip2 install protobuf即可。


#### `EOF occurred in violation of protocol`

Solution:
python使用2.7.12


