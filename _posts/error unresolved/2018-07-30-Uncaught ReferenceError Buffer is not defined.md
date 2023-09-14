---
layout: post
title: Uncaught ReferenceError Buffer is not defined
category: errors
tags: error-unresolved
keywords: preact
description: 
---	


## ERROR

```
Uncaught ReferenceError: Buffer is not defined
    at eval (util.js?923f:103)
    at Object.../node_modules/core-util-is/lib/util.js (bundle.js:867)
    at __webpack_require__ (bundle.js:708)
    at fn (bundle.js:113)
    at Object.eval (_stream_readable.js?2936:67)
    at eval (_stream_readable.js:1020)
    at Object.../node_modules/readable-stream/lib/_stream_readable.js (bundle.js:1326)
    at __webpack_require__ (bundle.js:708)
    at fn (bundle.js:113)
    at eval (readable-browser.js?d7b6:1)
```

## Solution

add following code on startup.

```
global.Buffer = global.Buffer || require("buffer").Buffer;
```


## Reference

* <https://github.com/ethereumjs/ethereumjs-util/issues/82>
