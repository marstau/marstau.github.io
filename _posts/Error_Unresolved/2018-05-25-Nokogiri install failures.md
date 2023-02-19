---
layout: post
title: Nokogiri install failures
category: 编程开发
tags: error-unresolved
keywords: web
description: 
---	


## Error

```
ld: warning: ignoring file /usr/local/Cellar/xz/5.2.3/lib/liblzma.dylib, file was built for x86_64 which is not the architecture being linked (i386): /usr/local/Cellar/xz/5.2.3/lib/liblzma.dylib
Undefined symbols for architecture i386:
  "_lzma_auto_decoder", referenced from:
      _xz_head in libxml2.a(xzlib.o)
  "_lzma_code", referenced from:
      _xz_decomp in libxml2.a(xzlib.o)
  "_lzma_end", referenced from:
      ___libxml2_xzclose in libxml2.a(xzlib.o)
  "_lzma_properties_decode", referenced from:
      _is_format_lzma in libxml2.a(xzlib.o)
ld: symbol(s) not found for architecture i386
clang: error: linker command failed with exit code 1 (use -v to see invocation)
make[2]: *** [xmllint] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
========================================================================
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.
```

## Solution

```
brew unlink xz
```

## Reference

* <https://github.com/sparklemotion/nokogiri/issues/1483>