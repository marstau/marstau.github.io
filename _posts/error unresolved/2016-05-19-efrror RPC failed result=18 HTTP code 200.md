---
layout: post
title: efrror RPC failed result=18 HTTP code 200
category: errors
tags: error-unresolved
keywords: github
description: 
---

## Error

内容太大clone不下来。提示：

```
efrror: RPC failed; result=18, HTTP code = 200
```


## Solutions

调整postBuffer

```
git config --global http.postBuffer 524288000
```


然后使用

```
git clone git@git.oschina.net:marstau/test.git
```

而不是

```
git clone https://git.oschina.net/marstau/test.git
```

## Reference

# <http://stackoverflow.com/questions/17683295/git-bash-error-rpc-failed-result-18-htp-code-200b-1kib-s>