---
layout: post
title: Fibonacci
category: 数据结构与算法
tags: data　structure／algorithm
keywords: 
description: 
---

  

矩阵快速幂。利用![](http://files.note.sdo.com/XbPJ4~jZB7_OwE0bs002za)可化为矩阵快速幂，即：由于矩阵乘法具有结合律，因此对于矩阵A，有A\^4 = A \* A \* A \* A = (A\*A) \* (A\*A) = A\^2 \* A\^2。我们可以得到这样的结论：当n为偶数时，A\^n = A\^(n/2) \* A\^(n/2)；当n为奇数时，A\^n = A\^(n/2) \* A\^(n/2) \* A （其中n/2取整）。

 直接递归计算复杂度是O(1.618\^n),DP算法是O(n),矩阵方法则是O(lgn).

<div
style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

\#include "stdafx.h"\
\
 <span style="color:#0000ff;">struct</span> mat2x2{\
     mat2x2( unsigned m00, unsigned m01, unsigned m10, unsigned m11 )\
         :\_m00(m00), \_m01(m01), \_m10(m10), \_m11(m11){}\
\
     unsigned \_m00, \_m01;\
     unsigned \_m10, \_m11;\
 };\
\
 mat2x2 matBase( 0, 1, 1, 1 );\
\
 <span style="color:#0000ff;">int</span> M = 10000;\
 mat2x2 <span style="color:#0000ff;">operator</span> \*( <span
style="color:#0000ff;">const</span> mat2x2 &mat1, <span
style="color:#0000ff;">const</span> mat2x2 &mat2 ){\
     <span style="color:#008000;">//</span><span
style="color:#008000;"> Remainder to escape overflow.</span><span
style="color:#008000;">\
 </span>    <span style="color:#0000ff;">return</span> mat2x2(\

        (mat1.\_m00\*mat2.\_m00 + mat1.\_m01\*mat2.\_m10)%M, (mat1.\_m00\*mat2.\_m01 + mat1.\_m01\*mat2.\_m11)%M,\

        (mat1.\_m10\*mat2.\_m00 + mat1.\_m11\*mat2.\_m10)%M, (mat1.\_m10\*mat2.\_m01 + mat1.\_m11\*mat2.\_m11)%M );\
 }\
 <span style="color:#008000;">//</span><span
style="color:#008000;"> In case of passing a negative value.</span><span
style="color:#008000;">\
 </span>mat2x2 MatPower( mat2x2 &mat, unsigned n ){\
     <span style="color:#0000ff;">if</span>( n \< 2 ) <span
style="color:#0000ff;">return</span> mat;\
     mat = MatPower( mat, n \>\> 1 );\
     <span style="color:#0000ff;">if</span>( n % 2 == 0 )\
         <span style="color:#0000ff;">return</span> mat\*mat;\
     <span style="color:#0000ff;">else</span>\
         <span style="color:#0000ff;">return</span> mat\*mat\*matBase;\
 }\
\
 unsigned Fibonacci( unsigned n ){\
     mat2x2 mat( 0, 1, 1, 1 );\
     mat = MatPower( mat, n );\
\
     <span style="color:#0000ff;">return</span> mat.\_m01;\
 }\
 <span style="color:#0000ff;">int</span> main(){\
     unsigned n;\
     cin \>\> n;\
     cout \<\< Fibonacci( n ) \<\< endl;\
 }\
\
 <span style="color:#008000;">/\*</span><span
style="color:#008000;">Sample output:\
 10\
 55\
\
 100\
 5075\
\
 120\
 1840\
 </span><span style="color:#008000;">\*/</span> 

</div>

 f(n-1) f(n)

 f(n)   f(n+1)

 

Fibonacci: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987 ...(0\~n)
 ![](http://files.note.sdo.com/XbPJ4~jZB7_ywE0bs002z6)

 









