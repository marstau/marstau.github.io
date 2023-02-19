---
layout: post
title: gorm查询sqlite3报错
category: 编程开发
tags: error-unresolved
keywords: gorm
description: 
---

## Error

使用gorm查询sqlite3报错

```
near "OFFSET": syntax error
```

## Solution

gorm/go-sqlite3 对于limit<1的会忽略掉，

## Reference

* <https://github.com/jinzhu/gorm/issues/1045>

