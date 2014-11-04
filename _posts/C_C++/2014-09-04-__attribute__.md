---
layout: post
title: __attribute__
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

<div>

[]()[]()[]()[]()[]()[]()[]()[]()[]()[]()[]()[]()[]()[]()[]()[]()[]() In
GNU C, you declare certain things about functions called in your program
which help the compiler optimize function calls and check your code more
carefully.

</div>

<div>

The keyword
`__attribute__`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"}
allows you to specify special attributes when making a declaration. This
keyword is followed by an attribute specification inside double
parentheses. The following attributes are currently defined for
functions on all targets:
`aligned`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`alloc_size`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`alloc_align`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`assume_aligned`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`noreturn`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`returns_twice`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`noinline`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`noclone`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`always_inline`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`flatten`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`pure`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`const`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`nothrow`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`sentinel`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`format`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`format_arg`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`no_instrument_function`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`no_split_stack`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`section`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`constructor`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`destructor`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`used`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`unused`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`deprecated`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`weak`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`malloc`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`alias`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`ifunc`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`warn_unused_result`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`nonnull`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`returns_nonnull`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`gnu_inline`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`externally_visible`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`hot`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`cold`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`artificial`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`no_sanitize_address`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`no_address_safety_analysis`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`no_sanitize_undefined`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"},
`error`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"}
and
`warning`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"}.
Several other attributes are defined for functions on particular target
systems. Other attributes, including
`section`{style="display: inline; font-style: normal; font-variant: normal; font-weight: normal; font-size: 13px; line-height: normal; font-family: monospace; margin: 0px; padding: 0px; text-decoration: none;"}
are supported for variables declarations (see [Variable
Attributes](https://gcc.gnu.org/onlinedocs/gcc/Variable-Attributes.html#Variable-Attributes)),
labels (see [Label
Attributes](https://gcc.gnu.org/onlinedocs/gcc/Label-Attributes.html#Label-Attributes))
and for types (see [Type
Attributes](https://gcc.gnu.org/onlinedocs/gcc/Type-Attributes.html#Type-Attributes)).

From : https://gcc.gnu.org/onlinedocs/gcc/Function-Attributes.html

</div>






