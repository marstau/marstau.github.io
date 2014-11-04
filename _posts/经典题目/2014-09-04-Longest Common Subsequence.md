---
layout: post
title: Longest Common Subsequence
category: 数据结构与算法
tags: data　structure／algorithm
keywords: 
description: 
---

<span id="__kindeditor_bookmark_start_28__"
style="display:none;"></span>

 

![](http://files.note.sdo.com/XbPJ4~j_r4pywE0jw004Lv)

<div
style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

\#include "stdafx.h"\
 <span style="color:#008000;">/\*</span><span style="color:#008000;">\
 求最长公共子串（Longest Common Subsequence, LCS）\

题目：如果字符串一的所有字符按其在字符串中的顺序出现在另外一个字符串二中，\
 则字符串一称之为字符串二的子串。\
 注意，并不要求子串（字符串一）的字符必须连续出现在字符串二中。\

请编写一个函数，输入两个字符串，求它们的最长公共子串，并打印出最长公共子串。\

例如：输入两个字符串BDCABA和ABCBDAB，字符串BCBA和BDAB都是是它们的最长公共子串，则输出它们的长度4，并打印任意一个子串。\
\
 </span><span style="color:#008000;">\*/</span>\
 <span style="color:#0000ff;">int</span> g\_LSCLength[256][256];\
 <span style="color:#0000ff;">int</span> GetLCS( <span
style="color:#0000ff;">const</span> <span
style="color:#0000ff;">char</span> \*str1, <span
style="color:#0000ff;">const</span> <span
style="color:#0000ff;">char</span> \*str2 ){\
     <span style="color:#0000ff;">int</span> len1 = strlen( str1 );\
     <span style="color:#0000ff;">int</span> len2 = strlen( str2 );\
     <span style="color:#0000ff;">for</span>( <span
style="color:#0000ff;">int</span> i = 0; i \< len1; i++ )\
         <span style="color:#0000ff;">for</span>( <span
style="color:#0000ff;">int</span> j = 0; j \< len2; j++ )\
         {\
             <span
style="color:#0000ff;">if</span>( i == 0 || j == 0 ){\
                 <span
style="color:#0000ff;">if</span>( str1[i] == str2[j] ){\
                     g\_LSCLength[i][j] = 1;\
                 }\
                 <span style="color:#0000ff;">else</span>\
                     g\_LSCLength[i][j] = 0;\
             }\
             <span style="color:#0000ff;">else</span>{\
                 <span
style="color:#0000ff;">if</span>( str1[i] == str2[j] )\
                     g\_LSCLength[i][j] = g\_LSCLength[i-1][j-1] + 1;\
                 <span style="color:#0000ff;">else</span>\

                    g\_LSCLength[i][j] = std::max(g\_LSCLength[i-1][j], g\_LSCLength[i][j-1]);\
             }\
         }\
\
     <span
style="color:#0000ff;">return</span> g\_LSCLength[len1-1][len2-1];\
 }\
\
 <span style="color:#0000ff;">int</span> main(){\
     <span style="color:#0000ff;">char</span> \*str1("BDCABA");\
     <span style="color:#0000ff;">char</span> \*str2("ABCBDAB");\
\
     cout \<\< GetLCS( str1, str2 ) \<\< endl;\
 }

</div>

 









