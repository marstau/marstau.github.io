---
layout: post
title: err 1005 Can't create table error 150
category: 编程开发
tags: error-unresolved
keywords: 
description: 
---

## Error

```
导入有外键约束的sql语句出现[Err] 1005 - Can't create table 'wack.w_active_codes' (errno: 150)
```

## Solutions
因为现在表未创建,所以修改外键约束会出问题，所以可以先运行创建表的.sql文件，然后再将外键约束的.sql文件执行一遍就可以了。

## Reference
