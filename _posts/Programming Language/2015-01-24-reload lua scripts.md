---
layout: post
title: reload lua scripts
category: 编程开发
tags: lua
keywords: lua
description: 
---

```
> package.loaded.mymodule = nil
> mymodule = require "mymodule"
> mymodule.foo()
Hello Module!
```

## Reference

* <http://lua-users.org/wiki/ModulesTutorial>
* <http://www.lua.org/notes/ltn007.html>