---
layout: post
title: warning C4996： 'strcpy'： This function or variable may be unsafe. 
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

使用VS2005以上版本（VS2005、VS2008、VS2010）编译在其他编译器下正常通过的C语言程序，你可能会遇到类似如下的警告提示：
引用内容 warning C4996: 'strcpy': This function or variable may be
unsafe. Consider using strcpy\_s instead. To disable deprecation, use
\_CRT\_SECURE\_NO\_WARNINGS. See online help for details. 1\> c:/program
files/microsoft visual studio 10.0/vc/include/string.h(105) :
参见“strcpy”的声明 warning C4996: 'fopen': This function or variable may
be unsafe. Consider using fopen\_s instead. To disable deprecation, use
\_CRT\_SECURE\_NO\_WARNINGS. See online help for details. 1\> c:/program
files/microsoft visual studio 10.0/vc/include/stdio.h(234) :
参见“fopen”的声明原因解释这种微软的警告，主要因为那些C库的函数，很多函数内部是不进行参数检测的（包括越界类的），微软担心使用这些会造成内存异常，所以就改写了同样功能的函数，改写了的函数进行了参数的检测，使用这些新的函数会更安全和便捷。关于这些改写的函数你不用专门去记忆，因为编译器对于每个函数在给出警告时，都会告诉你相应的安全函数，查看警告信息就可以获知，在使用时也再查看一下MSDN详细了解。库函数改写例子：
mkdir改写为 \_mkdir fopen”改写为 fopen\_s stricmp改写为 stricmp\_s
strcpy改写为strcpy\_s 解决方案： 1\>
根据下面的warning提示：参见“fopen”的声明 消息:“This function or variable
may be unsafe. Consider using fopen\_s instead. To disable deprecation,
use \_CRT\_SECURE\_NO\_DEPRECATE. See online help for details.”
所以可以将函数按warning提示的第二句，改为使用fopen\_s函数即可：
例如:FILE \*pFile=fopen("1.txt", "w"); 改为： FILE\* pFile;
fopen\_s(&pFile, "1.txt", "w"); 2\> 还是根据warning提示的地三句话:use
\_CRT\_SECURE\_NO\_DEPRECATE
项目|属性|配置属性|C/C++|命令行|附加选项,加入【/D
"\_CRT\_SECURE\_NO\_DEPRECATE" 】(注：加入中括号中完整的内容) 3\>
降低警告级别：项目|属性|配置属性|C/C++|常规,自己根据情况降低警告级别（此法不推荐）
注意：高度重视警告：使用编译器的最高警告级别。应该要求构建是干净利落的（没有警告）。理解所有警告。通过
修改代码而不是降低警告级别来排除警告。
编译器是你的朋友。如果它对某个构造发出警告，这经常是说明你的代码中存在潜在的问题。成功的构建应该是无声无息的（没有警告的）。【《C++编程规
范》】

**** 








