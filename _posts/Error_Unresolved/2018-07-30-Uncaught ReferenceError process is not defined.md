---
layout: post
title: Uncaught ReferenceError process is not defined
category: 编程开发
tags: error-unresolved
keywords: preact
description: 
---	


## Error

```
index.js?8854:3 Uncaught ReferenceError: process is not defined
    at eval (index.js?8854:3)
    at Object.../node_modules/process-nextick-args/index.js (bundle.js:1278)
    at __webpack_require__ (bundle.js:708)
    at fn (bundle.js:113)
    at Object.eval (_stream_readable.js?2936:26)
    at eval (_stream_readable.js:1020)
    at Object.../node_modules/readable-stream/lib/_stream_readable.js (bundle.js:1326)
    at __webpack_require__ (bundle.js:708)
    at fn (bundle.js:113)
    at eval (readable-browser.js?d7b6:1)
```

## Solution

a quick fix is just to add a file name `preact.config.js` at the root of your app created with preact-cli.

The content:

```
import { DefinePlugin } from 'webpack';

export default function(config, env, helpers) {
  config.plugins.push(
    new DefinePlugin({
      process: {
        env: {},
      },
    })
  );
}
```

With that I make it work locally.

## Reference

* <https://github.com/algolia/react-instantsearch/issues/264>