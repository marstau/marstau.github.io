---
layout: post
title: could not execute query nested exception
category: 编程开发
tags: error／unresolved
keywords: 
description: 
---

## Error

```
org.springframework.dao.DataAccessResourceFailureException: could not execute query; nested exception is org.hibernate.exception.JDBCConnectionException: could not execute query
```


## Solutions[More](http://blog.csdn.net/xingyunpi/article/details/7216016)

```
Show global variables like 'wait_timeout'

set global wait_timeout=1814400;
```

windows直接修改my.ini文件才行

## Reference
