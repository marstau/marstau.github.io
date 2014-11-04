---
layout: post
title: use static Variables in static library
category: 书籍与软件工具
tags: mac／ios
keywords: 
description: 
---

<div>

Use the -all\_load linker option to load all members of static
libraries. Or for a specific library, use -force\_load
path\_to\_archive.

</div>

<div>

\

</div>

<div>

In Xcode, you'll want to add these options under "Other Linker Flags"
for your executable (not your static library).

</div>

<div>

\

</div>

<div>

From
: http://gamedev.stackexchange.com/questions/37813/variables-in-static-library-are-never-initialized-why

</div>





