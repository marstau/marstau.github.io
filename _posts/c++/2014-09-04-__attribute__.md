---
layout: post
title: __attribute__
category: 编程开发
tags: c＋＋
keywords: 
description: 
---
In GNU C, you declare certain things about functions called in your program which help the compiler optimize function calls and check your code more carefully.

The keyword \__attribute__ allows you to specify special attributes when making a declaration. This keyword is followed by an attribute specification inside double parentheses. The following attributes are currently defined for functions on all targets: aligned, alloc_size, alloc_align, assume_aligned, noreturn, returns_twice, noinline, noclone, always_inline, flatten, pure, const, nothrow, sentinel, format, format_arg, no_instrument_function, no_split_stack, section, constructor, destructor, used, unused, deprecated, weak, malloc, alias, ifunc, warn_unused_result, nonnull, returns_nonnull, gnu_inline, externally_visible, hot, cold, artificial, no_sanitize_address, no_address_safety_analysis, no_sanitize_undefined, error and warning. Several other attributes are defined for functions on particular target systems. Other attributes, including section are supported for variables declarations (see Variable Attributes), labels (see Label Attributes) and for types (see Type Attributes).

## Reference
* <https://gcc.gnu.org/onlinedocs/gcc/Function-Attributes.html>




