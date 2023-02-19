---
layout: post
title: eclipse的devices上不显示调试程序包名
category: 编程开发
tags: android java
keywords: 
description: 
---

本来想要如图显示:

![](/Resources/eclipse的devices上不显示调试程序包名_2.png)

其实却如下图显示,以致不便于调试:

![](/Resources/eclipse的devices上不显示调试程序包名_1.png)


在AndroidManifest.xml中加入

```
android:debuggable="true"
```

```
<application android:label="@string/app_name" android:icon="@drawable/icon" android:debuggable="true">
```

## Reference