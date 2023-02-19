---
layout: post
title: Invalid Code Signing Entitlements
category: 编程开发
tags: error-unresolved
keywords: windows
description: 
---	


## Error

app store发布应用时提示

```
ERROR ITMS-90164: "Invalid Code Signing Entitlements. The entitlements in your app bundle signature do not match the ones that are contained in the provisioning profile. According to the provisioning profile, the bundle contains a key value that is not allowed: '[ "merchant.com.*.*.*" ]' for the key 'com.apple.developer.in-app-payments' in 'Payload/Demo.app/Demo'"
```


## Solution[More](http://my.oschina.net/u/1245365/blog/205770)

```
删除*.entitlements文件
```

## Reference