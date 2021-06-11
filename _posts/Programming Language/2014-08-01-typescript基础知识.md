---
layout: post
title: typescript基础知识
category: 编程开发
tags: css
keywords: css
description: 
---

## 基础语法


```
this.logger.info("obj="+JSON.stringify(obj)); // 打印对象
```

## ERROR


#### Expected property shorthand in object literal[More](https://www.cnblogs.com/zhongxia/p/5440112.html)

```
let bar = 1111;
let obj = {bar:bar};   // error  报这个错
 
如何修改:
let obj = {bar:111}  // 使用最简单的方式,不要赋值给对象,在赋值到对象里面
```

#### Access to fetch at 'http://www.abc.com' from origin 'http://localhost:8140' has been blocked by CORS policy: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.[More](https://stackoverflow.com/questions/54301686/how-to-fixed-set-the-requests-mode-to-no-cors)


```
fetch(url, {
    mode: "no-cors",
    ...
})
```

## Reference
