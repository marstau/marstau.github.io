---
layout: post
title: XCode： duplicate symbol error when using global variable - Stack Overflow
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

<div>

<div itemprop="text"
style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Arial, 'Liberation Sans', 'DejaVu Sans', sans-serif;height:470.4375px;padding:0px;text-align:left;text-decoration:none;width:660px;word-wrap:break-word;">

From
: <http://stackoverflow.com/questions/14402320/xcode-duplicate-symbol-error-when-using-global-variable>

Here's my code:

A.h

``` {style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;height:119px;margin:0px 0px 10px;max-height:600px;overflow:auto;padding:5px;text-align:left;text-decoration:none;white-space:pre;width:650px;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
class Foo { public:     int bar; }; Foo myFoo;
```

main.cpp

``` {style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;height:102px;margin:0px 0px 10px;max-height:600px;overflow:auto;padding:5px;text-align:left;text-decoration:none;white-space:pre;width:650px;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
#include "A.h" int main() {     myFoo.bar = 2;     return 0; }
```

Xcode gives me the error (paraphrased):

``` {style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;height:17px;margin:0px 0px 10px;max-height:600px;overflow:auto;padding:5px;text-align:left;text-decoration:none;white-space:pre;width:650px;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
duplicate symbol _myFoo in main.o & A.o
```

I'd like to keep the
`Foo myFoo`{style="display:inline;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;margin:0px;padding:1px 5px;text-align:left;text-decoration:none;white-space:pre-wrap;word-wrap:break-word;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
within the A.h file.

So why is XCode throwing this error and how can I rectify it?

</div>

</div>

<div>

<div itemprop="text"
style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Arial, 'Liberation Sans', 'DejaVu Sans', sans-serif;height:393.125px;padding:0px;text-align:left;text-decoration:none;width:660px;word-wrap:break-word;">

You define the global variable in header and it breaks the **[one
definition rule](http://en.wikipedia.org/wiki/One_Definition_Rule)**.\
 Each TU where you include the header will have its own copy of the
object.

You need to use
`extern`{style="display:inline;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;margin:0px;padding:1px 5px;text-align:left;text-decoration:none;white-space:pre-wrap;word-wrap:break-word;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
keyword:

1.  Declare the object as extern in header.
2.  Define it one and only one source file.
3.  Include the header wherever you want to use the global variable

------------------------------------------------------------------------

**A.h**

``` {style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;height:17px;margin:0px 0px 10px;max-height:600px;overflow:auto;padding:5px;text-align:left;text-decoration:none;white-space:pre;width:650px;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
extern Foo myFoo;
```

**main.cpp**

``` {style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;height:51px;margin:0px 0px 10px;max-height:600px;overflow:auto;padding:5px;text-align:left;text-decoration:none;white-space:pre;width:650px;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
#include "A.h" Foo myFoo;
```

**XXXX.cpp**

``` {style="display:block;font-style:normal;font-variant:normal;font-weight:normal;font-size:14px;line-height:17.804800033569336px;font-family:Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, serif;height:17px;margin:0px 0px 10px;max-height:600px;overflow:auto;padding:5px;text-align:left;text-decoration:none;white-space:pre;width:650px;background:none 0% 0% / auto repeat scroll padding-box border-box #eeeeee;"}
#include "A.h"
```

</div>

</div>







