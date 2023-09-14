---
layout: post
title: The SSL certificate is invalid
category: errors
tags: error-unresolved
keywords: cargo
description: 
---	


## ERROR

```
$ cargo build --verbose
    Updating registry `https://github.com/rust-lang/crates.io-index`
error: failed to load source for a dependency on `rand`
Caused by:
  Unable to update registry https://github.com/rust-lang/crates.io-index
Caused by:
  failed to fetch `https://github.com/rust-lang/crates.io-index`
Caused by:
  [16/-17] The SSL certificate is invalid
```

## Solution

```
cargo 版本问题

yum install rust
yum install cargo
```

## Reference
