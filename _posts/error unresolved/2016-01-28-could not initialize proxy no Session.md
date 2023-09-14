---
layout: post
title: could not initialize proxy no Session
category: errors
tags: error-unresolved
keywords: 
description: 
---

## ERROR

```
 could not initialize proxy - no Session
异常：
org.hibernate.LazyInitializationException: could not initialize proxy - no Session
at org.hibernate.proxy.AbstractLazyInitializer.initialize(AbstractLazyInitializer.java:57)
at org.hibernate.proxy.AbstractLazyInitializer.getImplementation(AbstractLazyInitializer.java:111)
```

## Solutions


有懒加载情况下， HibernateUtil.closeSession();不要滥用。
比如一些select语句是不用closesession的，而update和insert等就要用closesession了。

## Reference
