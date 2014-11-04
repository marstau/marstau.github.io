---
layout: post
title: Do remember
category: 数据结构与算法
tags: data　structure／algorithm
keywords: 
description: 
---

 Desc: 做出来了,或者理解了,但是速度太慢了,都记录在此.

**answer**:

**more**:

------------------------------------------------------------------------

<span></span> 

1.  <span
    style="color:#e53333;">**用天平（只能比较，不能称重）从一堆小球中找出其中唯一一个较轻的，使用**</span><span
    style="color:#e53333;"><span
    style="color:#e53333;">**x**</span></span><span
    style="color:#e53333;">**次天平，**</span>

    <span style="color:#e53333;">**最多可以从**</span><span
    style="color:#e53333;"><span
    style="color:#e53333;">**y**</span></span><span
    style="color:#e53333;">**个小球中找出较轻的那个，求**</span><span
    style="color:#e53333;"><span
    style="color:#e53333;">**y**</span></span><span
    style="color:#e53333;">**与**</span><span
    style="color:#e53333;"><span
    style="color:#e53333;">**x**</span></span>**<span
    style="color:#e53333;">的关系式。</span>**\
     **answer**:\
     x=1, y=3: if a=b, c is the lighter, else the lighter is the lighter...

    do this recursively. so y=3\^x;

    **more:**
    Q:球一个天平，现知道只有一个和其它的重量不同，问怎样称才能用三次就找到那个球?

    A:13个球也是可以做的。就是分成4个、4个、5个，先拿两个四个上去，如果平衡，则问题出在5个那组，就在5个里任拿三个设为C1C2C3，再拿三个正常的，分别放两边，若平衡就简单啦，若不平衡，就出现C1C2C3重，或C1C2C3轻，相当于就知道那个特别的球是比较重或者比较轻啦，接下就不用说了 

       如果不平衡，假设现在是A重B轻， 

       取A1+A2+B1放天平一边(设为左边)， 

       再取A3+A4+B2放另一边（右）， 

       若平衡，就在B3/B4任拿一个跟C1上去称就行了， 

       如果不平衡，那么假设 

       情况一：左重 

       则是A1/A2/B2有问题 

       直接把A1A2放两边称，重的那个有问题，如果平 

       衡就是B2有问题 

       情况二：右重 

       就是 A3/A4/B1有问题，方法同上

    ,,,,,称3次的话,最多可以辨别3的3次方,也就是27个球,传统的2的3次方只能辨别8个球.

2.  <span
    style="color:#e53333;">**输入一个字符串，打印出该字符串中字符的所有排列。**</span><span
    style="color:#e53333;">**例如输入字符串**</span><span
    style="color:#e53333;">**abc**</span><span
    style="color:#e53333;">**，则输出由字符**</span><span
    style="color:#e53333;">**a**</span><span
    style="color:#e53333;">**、**</span><span
    style="color:#e53333;">**b**</span><span
    style="color:#e53333;">**、**</span><span
    style="color:#e53333;">**c**</span><span
    style="color:#e53333;">**所能排列出来的所有字符串**</span><span
    style="color:#e53333;">**abc**</span><span
    style="color:#e53333;">**、**</span><span
    style="color:#e53333;">**acb**</span><span
    style="color:#e53333;">**、**</span><span
    style="color:#e53333;">**bac**</span><span
    style="color:#e53333;">**、**</span><span
    style="color:#e53333;">**bca**</span><span
    style="color:#e53333;">**、**</span><span
    style="color:#e53333;">**cab**</span><span
    style="color:#e53333;">**和**</span><span
    style="color:#e53333;">**cba**</span><span
    style="color:#e53333;">**。**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include \<iostream\>\
     \#include \<algorithm\>\
     \#include \<iterator\>\
     \#include \<cassert\>\
    \
     <span style="color:#0000ff;">using</span> std::cout;\
     <span style="color:#0000ff;">using</span> std::cin;\
     <span style="color:#0000ff;">using</span> std::endl;\
     <span style="color:#0000ff;">using</span> std::copy;\
     <span style="color:#0000ff;">using</span> std::ostream\_iterator;\
    \
     <span style="color:#0000ff;">void</span> PermuAuxi( <span
    style="color:#0000ff;">char</span> szStr[], <span
    style="color:#0000ff;">int</span> iStart, <span
    style="color:#0000ff;">int</span> iEnd ){\
         <span style="color:#0000ff;">if</span>( iStart \>= iEnd ){\
             copy( &szStr[0], &szStr[iEnd], ostream\_iterator\<<span
    style="color:#0000ff;">char</span>\>(cout, "") );\
             cout \<\< endl;\
             <span style="color:#0000ff;">return</span>;\
         }\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = iStart; i \< iEnd; i++ ){\
             std::swap( szStr[iStart], szStr[i] );\
             PermuAuxi( szStr, iStart + 1, iEnd );\
             std::swap( szStr[iStart], szStr[i] );\
         }\
     }\
     <span style="color:#0000ff;">void</span> Permutation( <span
    style="color:#0000ff;">char</span> \*szStr ){ 
        if( szStr == NULL ) return;

        PermuAuxi( szStr, 0, strlen(szStr) );\
     }\
    \
     <span style="color:#0000ff;">int</span> main( <span
    style="color:#0000ff;">int</span> argc, <span
    style="color:#0000ff;">char</span> \*argv[] ){\
         <span style="color:#0000ff;">char</span> szStr[256];\
         cout \<\< "Input string:\\n";\
         cin \>\> szStr;\
         cout \<\< "Permutation:\\n";\
         Permutation( szStr );\
     }\
     <span style="color:#008000;">/\*Sample output:</span><span
    style="color:#008000;">\
     Input string:\
     abc\
     Permutation:\
     abc\
     acb\
     bac\
     bca\
     cba\
     cab\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

3.  **<span
    style="color:#e53333;">给定链表的头指针和一个结点指针，在O(1)时间删除该结点。\
     </span>**链表结点的定义如下：

    struct ListNode

    {

          int        m\_nKey;

          ListNode\*  m\_pNext;

    };

    函数的声明如下：

    void DeleteNode(ListNode\* pListHead, ListNode\* pToBeDeleted);

    分析：这是一道广为流传的Google面试题，能有效考察我们的编程基本功，还能考察我们的反应速度，更重要的是，还能考察我们对时间复杂度的理解。\
     **answer**:\

    Copy the data from tobedeleted’s next to tobedeleted. then delete tobedeleted. The special case is

    tobedelete is the tail, then we must iterate to find its predecessor.

    The amortized time complexity is O(1).

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \
     <span
    style="color:#0000ff;">void</span> DeleteNode(stNode\* pListHead, stNode\* pToBeDeleted){\
         <span
    style="color:#0000ff;">if</span>( pListHead == NULL || pToBeDeleted == NULL ) <span
    style="color:#0000ff;">return</span>;\
    \
         \
         stNode \*pNode = pToBeDeleted-\>\_next;\
         <span style="color:#0000ff;">if</span>( pNode ){\
             pToBeDeleted-\>\_data = pNode-\>\_data;\
             pToBeDeleted-\>\_next = pNode-\>\_next;\
             delete pNode;\
         }\
     }

    </div>

4.  **<span
    style="color:#e53333;">一个岔路口分别通向诚实国和说谎国。来了两个人，已知一个是诚实国的，另一个是说谎国的。诚实国永远说实话，说谎国永远说谎话。现在你要去说谎国，但不知道应该走哪条路，需要问这两个人。请问应该怎么问？</span>**\
     **answer:**\
     <span lang="EN-US"><span
    style="font-family:'Times New Roman';">A:</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">路在左边</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">,B</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">说的话是错的</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">.</span></span>

    <span lang="EN-US"><span
    style="font-family:'Times New Roman';">B:</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">路在左边</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">,A</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">说的话是错的</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">.</span></span>

    <span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">如果有一个人说</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">F,</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">则那个人肯定是诚实国的人</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">.</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">并且相信他</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">,</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">路在右边</span>

    <span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">如果都说</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">T,</span></span><span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">则路肯定是在左边</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">..</span></span>

    <span
    style="font-family:宋体;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';">因为说谎国的人对于以上两句话都只会回答</span><span
    lang="EN-US"><span
    style="font-family:'Times New Roman';">T.</span></span>

5.  <span
    style="font-family:宋体;color:#e53333;font-size:10.5pt;mso-fareast-language:ZH-CN;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';mso-bidi-font-size:12.0pt;mso-font-kerning:1.0pt;mso-bidi-font-family:'Times New Roman';mso-ansi-language:EN-US;mso-bidi-language:AR-SA;">**用递归的方法判断整数组**</span><span
    style="font-family:'Times New Roman';color:#e53333;font-size:10.5pt;mso-fareast-language:ZH-CN;mso-bidi-font-size:12.0pt;mso-font-kerning:1.0pt;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;mso-fareast-font-family:宋体;"
    lang="EN-US">**a[N]**</span><span
    style="font-family:宋体;color:#e53333;font-size:10.5pt;mso-fareast-language:ZH-CN;mso-ascii-font-family:'Times New Roman';mso-hansi-font-family:'Times New Roman';mso-bidi-font-size:12.0pt;mso-font-kerning:1.0pt;mso-bidi-font-family:'Times New Roman';mso-ansi-language:EN-US;mso-bidi-language:AR-SA;">**是不是升序排列**</span>
6.  <span
    style="color:#e53333;font-size:10.5pt;">**不用乘法或加法**</span><span
    style="color:#e53333;font-size:10.5pt;">**增加**</span><span
    style="color:#e53333;font-size:10.5pt;">**7**</span><span
    style="font-size:10.5pt;">**<span
    style="color:#e53333;">倍：</span>**\
     </span>7 = 8 - 1 则：(x\<\<3)-x

    7 = (16-2)/2 则：(x\<\<4 - x\<\<1)\>\>1

7.  **<span
    style="color:#e53333;">输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。句子中单词以空格符隔开。为简单起见，标点符号和普通字母一样处理。</span>**

    **<span
    style="color:#e53333;">例如输入“I am a student.”，则输出“student. a am I”。</span>**

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#0000ff;">void</span> ReverseStrOrder( <span
    style="color:#0000ff;">char</span> \*szStr ){\
         assert( szStr );\
    \
         <span style="color:#0000ff;">int</span> len = strlen( szStr );

     

    <span style="color:#008000;">    //</span><span
    style="color:#008000;"> Reverse string.</span>\
         <span style="color:#0000ff;">int</span> iPost = len - 1;\
         <span style="color:#0000ff;">int</span> iPrev = 0;\
         <span style="color:#0000ff;">while</span>( iPrev \< iPost ){\
             szStr[iPrev] = szStr[iPrev] \^ szStr[iPost];\
             szStr[iPost] = szStr[iPrev] \^ szStr[iPost];\
             szStr[iPrev] = szStr[iPrev] \^ szStr[iPost];\
             iPrev++;\
             iPost--;\
         }\
         cout \<\< szStr \<\< endl;\
    \
         <span style="color:#0000ff;">char</span> \*p = szStr;\
         <span
    style="color:#0000ff;">char</span> \*pFirst = NULL, \*pLast = NULL;\
         <span style="color:#0000ff;">while</span>( \*p != '\\0' )\
         {\
             pFirst = p;\
             <span
    style="color:#0000ff;">while</span>( \*p != '\\0' && \*p != ' '<span
    style="color:#008000;">/\*</span><span
    style="color:#008000;"> && \*p != ',' && \*p != '.' && \*p != '!' && \*p != ';' </span><span
    style="color:#008000;">\*/</span>) p++;\
             pLast = p - 1;\
    \
             <span
    style="color:#0000ff;">while</span>( pFirst \< pLast ) std::swap( \*pFirst++, \*pLast-- );\
    \
             <span
    style="color:#0000ff;">if</span>( \*p != '\\0' ) p++;\
         }\
     }\
     <span style="color:#0000ff;">int</span> main(){\
         <span
    style="color:#0000ff;">char</span> szStr[256] = "I am a student.";\
         ReverseStrOrder( szStr );\
         cout \<\< szStr \<\< endl;\
     }\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">Sample output:\
     .tneduts a ma I\
     student. a am I\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

8.  <span style="font-size:10.5pt;">**<span
    style="color:#e53333;">用一种算法使含</span><span
    style="color:#e53333;">通配符</span><span
    style="color:#e53333;">字符串相匹配.</span>**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
    \
     <span style="color:#0000ff;">bool</span> IdxKMP( <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*szMain, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span>\* szSearch, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> pos, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> \*next ){\
         assert( szMain != NULL && szSearch != NULL && next != NULL );\
    \
         <span style="color:#0000ff;">int</span> i = pos, j = 0;\
         <span
    style="color:#0000ff;">int</span> lenMain = static\_cast\<<span
    style="color:#0000ff;">int</span>\>(strlen(szMain));\
         <span
    style="color:#0000ff;">int</span> lenSearch = static\_cast\<<span
    style="color:#0000ff;">int</span>\>(strlen(szSearch));\
    \
         <span
    style="color:#0000ff;">while</span>( i \< lenMain && j \< lenSearch )\
         {\
             <span
    style="color:#0000ff;">if</span>( j == -1 || szMain[i] == szSearch[j] || szSearch[j] == '?' ){\
                 i++;\
                 j++;\
             }\
             <span style="color:#0000ff;">else</span> <span
    style="color:#0000ff;">if</span>( szSearch[j] == '\*' ){\
                 j++;\
                 <span
    style="color:#0000ff;">while</span>( i \< lenMain && szMain[i] != szSearch[j] ) i++;\
             }\
             <span style="color:#0000ff;">else</span>\
                 j = next[j];\
         }\
    \
         <span style="color:#0000ff;">if</span>( j \>= lenSearch )\
             <span style="color:#0000ff;">return</span> <span
    style="color:#0000ff;">true</span>;\
         <span style="color:#0000ff;">else</span>\
             <span style="color:#0000ff;">return</span> <span
    style="color:#0000ff;">false</span>;\
     }\
    \
     <span style="color:#0000ff;">void</span> GetNext( <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*szSearch, <span
    style="color:#0000ff;">int</span> \*next ){\
         assert( szSearch != NULL && next != NULL );\
    \
         <span style="color:#0000ff;">int</span> i = 0, j = -1;\
         <span
    style="color:#0000ff;">int</span> len = strlen( szSearch );\
         next[0] = -1;\
         <span style="color:#0000ff;">while</span>( i \< len - 1 )\
         {\
             <span
    style="color:#0000ff;">if</span>( j == -1 || szSearch[i] == szSearch[j] ){\
                 i++;\
                 j++;\
                 next[i] = j;\
             }\
             <span style="color:#0000ff;">else</span>\
                 j = next[j];\
         }\
    \
     }\
     <span style="color:#0000ff;">bool</span> Wildcard( <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*szMain, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span>\* szSearch ){\
         assert( szMain != NULL && szSearch != NULL );\
    \
         <span style="color:#0000ff;">int</span> \*next = NULL;\
         next = <span style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">int</span>[strlen(szSearch)];\
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> Preprocess.</span><span
    style="color:#008000;">\
     </span>    GetNext( szSearch, next );\
    \
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> Process.</span><span
    style="color:#008000;">\
     </span>    <span
    style="color:#0000ff;">bool</span> ret = IdxKMP( szMain, szSearch, 0, next );\
    \
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> Postprocess.</span><span
    style="color:#008000;">\
     </span>    delete []next;\
    \
         <span style="color:#0000ff;">return</span> ret;\
     }\
     <span style="color:#0000ff;">int</span> main(){\
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*sMain("My notadepad");\
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*sSearch("\*not\*p?d");\

        cout \<\< std::boolalpha \<\< Wildcard( sMain, sSearch ) \<\< endl;\
     }

    </div>

9.  **有n个长为m+1的字符串，如果某个字符串的最后m个字符与某个字符串的前m个字符匹配，则两个字符串可以联接，问这n个字符串最多可以连成一个多长的字符串，如果出现循环，则返回错误。\
     Caution: 注意审清题,m+1的长度的字符串,m个字符要匹配,联接不是合并.**

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include \<iostream\>\
     \#include \<<span style="color:#0000ff;">string</span>\>\
     \#include \<climits\>\
     \#include \<cmath\>\
     \#include \<fstream\>\
     \#include \<vector\>\
    \
     <span style="color:#0000ff;">using</span> <span
    style="color:#0000ff;">namespace</span> std;\
    \
     <span style="color:#0000ff;">\#define</span> INFINITY    INT\_MAX\
     <span
    style="color:#0000ff;">\#define</span> MAX\_VERTEX\_NUM    100\
    \
     <span style="color:#0000ff;">int</span> m;\
     typedef <span style="color:#0000ff;">struct</span>{\
         <span style="color:#0000ff;">int</span>        \*vexs;\
         <span
    style="color:#0000ff;">int</span>        (\*arcs)[MAX\_VERTEX\_NUM];\
         <span style="color:#0000ff;">int</span>        vexnum, arcnum;\
     }MGraph;\
    \
     <span style="color:#0000ff;">struct</span> stMatGraph{\
         <span style="color:#0000ff;">explicit</span> stMatGraph( <span
    style="color:#0000ff;">int</span> nVex, <span
    style="color:#0000ff;">string</span> \*pVertices = NULL, <span
    style="color:#0000ff;">bool</span> \*\*ppArcs = NULL )\
             :\_nVex(nVex), \_pVertices(pVertices), \_ppArcs(ppArcs){}\
    \
         <span style="color:#0000ff;">string</span>    \*\_pVertices;\
         <span style="color:#0000ff;">bool</span>    \*\*\_ppArcs;\
    \
         <span style="color:#0000ff;">int</span>        \_nVex;\
     };\
    \
     <span style="color:#0000ff;">bool</span> IsMatched( <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">string</span> &str1, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">string</span> &str2 ){\
         <span style="color:#0000ff;">int</span> idx1 = m;\
         <span style="color:#0000ff;">int</span> idx2 = m - 1;\
         <span
    style="color:#0000ff;">while</span>( idx2 \>= 0 && str1[idx1] == str2[idx2] ){\
             idx1--;\
             idx2--;\
         }\
    \
         <span style="color:#0000ff;">if</span>( idx2 \< 0 )\
             <span style="color:#0000ff;">return</span> <span
    style="color:#0000ff;">true</span>;\
         <span style="color:#0000ff;">else</span>\
             <span style="color:#0000ff;">return</span> <span
    style="color:#0000ff;">false</span>;\
     }\
    \
     <span
    style="color:#0000ff;">void</span> CreateGraph( stMatGraph \*pGraph, vector\<<span
    style="color:#0000ff;">string</span>\> &vecStr ){\
    \
         pGraph-\>\_nVex = vecStr.size();\
         pGraph-\>\_pVertices = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">string</span>[pGraph-\>\_nVex];\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< pGraph-\>\_nVex; i++ )\
             pGraph-\>\_pVertices[i] = vecStr[i];\
    \
         pGraph-\>\_ppArcs = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">bool</span> \*[pGraph-\>\_nVex];\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< pGraph-\>\_nVex; i++ ){\
             pGraph-\>\_ppArcs[i] = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">bool</span>[pGraph-\>\_nVex];\
             memset( pGraph-\>\_ppArcs[i], 0, <span
    style="color:#0000ff;">sizeof</span>(<span
    style="color:#0000ff;">bool</span>)\*pGraph-\>\_nVex );\
         }\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< pGraph-\>\_nVex; i++ )\
             <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> j = 0; j \< pGraph-\>\_nVex; j++ ){\

                pGraph-\>\_ppArcs[i][j] = IsMatched( pGraph-\>\_pVertices[i], pGraph-\>\_pVertices[j] );\
             }\
     }\
    \
    \
     <span
    style="color:#0000ff;">void</span> DeleteMatGraph( stMatGraph \*pGraph ){\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< pGraph-\>\_nVex; i++ )\
             delete [](pGraph-\>\_ppArcs[i]); <span
    style="color:#008000;">/\*</span><span
    style="color:#008000;">[]pGraph-\>\_ppArcs[i]?</span><span
    style="color:#008000;">\*/</span>\
         delete []pGraph-\>\_ppArcs;\
         delete []pGraph-\>\_pVertices;\
     }\
    \
     <span
    style="color:#0000ff;">bool</span> g\_bVisited[MAX\_VERTEX\_NUM];\
     std::vector\<<span
    style="color:#0000ff;">string</span>\> g\_vecStrRecord;\
     <span style="color:#0000ff;">int</span> Count = 0;\
     <span
    style="color:#0000ff;">int</span> MaxCount = numeric\_limits\<<span
    style="color:#0000ff;">int</span>\>::min();\
     <span style="color:#0000ff;">bool</span> g\_bContinued = <span
    style="color:#0000ff;">true</span>;\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     void DFSAuxi( stMatGraph \*pGraph, int i ){\
         if( g\_bContinued )\
         {\
             g\_bVisited[i] = true;\
    \
             g\_vecStrRecord.push\_back( pGraph-\>\_pVertices[i] );\
             Count++;\
             if( MaxCount \< Count ){\
                 MaxCount = Count;\
    \
                 // Test circular.\
                 vector\<string\>::iterator iter = g\_vecStrRecord.begin();\
                 string strLast = g\_vecStrRecord.back();\
    \
                 int idx1 = 1, idx2 = 0;\

                while( idx1 \< m + 1 && (\*iter)[idx1++] == strLast[idx2++] )\
                     ;\
                 if( idx1 \>= m + 1 ){\
                     cerr \<\< "Have circular.\\n";\
                     g\_bContinued = false;\
                     return;\
                 }\
    \
                 for( ; iter != g\_vecStrRecord.end(); iter++ )\
                     cout \<\< \*iter \<\< " ";\
                 cout \<\< endl;\
             }\
             for( int j = 0; j \< pGraph-\>\_nVex; j++ ){\
                 if( pGraph-\>\_ppArcs[i][j] && !g\_bVisited[j] )\
                     DFSAuxi( pGraph, j );\
             }\
             Count--;\
             g\_vecStrRecord.pop\_back();\
             g\_bVisited[i] = false;\
         }\
     }\
     </span><span style="color:#008000;">\*/</span>\
     <span
    style="color:#0000ff;">void</span> DFSAuxi( stMatGraph \*pGraph, <span
    style="color:#0000ff;">int</span> i ){\
         g\_bVisited[i] = <span style="color:#0000ff;">true</span>;\
    \
         g\_vecStrRecord.push\_back( pGraph-\>\_pVertices[i] );\
         Count++;\
         <span style="color:#0000ff;">if</span>( MaxCount \< Count ){\
             MaxCount = Count;\
    \
             vector\<<span
    style="color:#0000ff;">string</span>\>::iterator iter = g\_vecStrRecord.begin();\
             <span
    style="color:#0000ff;">for</span>( ; iter != g\_vecStrRecord.end(); iter++ )\
                 cout \<\< \*iter \<\< " ";\
             cout \<\< endl;\
         }\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> j = 0; j \< pGraph-\>\_nVex; j++ ){\
             <span
    style="color:#0000ff;">if</span>( pGraph-\>\_ppArcs[i][j] && !g\_bVisited[j] )\
                 DFSAuxi( pGraph, j );\
         }\
         Count--;\
         g\_vecStrRecord.pop\_back();\
         g\_bVisited[i] = <span style="color:#0000ff;">false</span>;\
     }\
    \
     <span
    style="color:#0000ff;">void</span> DFSTraverse( stMatGraph \*pGraph ){\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< pGraph-\>\_nVex; i++ )\
             <span style="color:#0000ff;">if</span>( !g\_bVisited[i] )\
                 DFSAuxi( pGraph, i );\
     }\
     <span style="color:#0000ff;">int</span> main(){\
         <span style="color:#0000ff;">int</span> n;\
         ifstream inFile("2.txt");\
         cout \<\< "Input the number of string:\\n";\
         cin \>\> n;\
         cout \<\< "Input the length of string:\\n";\
         cin \>\> m;\
         m--;\
         vector\<<span style="color:#0000ff;">string</span>\> vecStr;\
         <span style="color:#0000ff;">string</span> str;\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< n; i++ ){\
             cin \>\> str;\
             vecStr.push\_back( str );\
         }\
         cout \<\< endl;\
    \
         stMatGraph \*pGraph = <span
    style="color:#0000ff;">new</span> stMatGraph( n );\
         CreateGraph( pGraph, vecStr );\
         DFSTraverse( pGraph );\
         cout \<\< "Maximum count:" \<\< MaxCount \<\< endl;\
    \
         DeleteMatGraph( pGraph );\
    \
         delete pGraph;\
     }\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     Input the number of string:\
     14\
     Input the length of string:\
     4\
     abcd\
     bcde\
     cdea\
     deab\
     eaba\
     abab\
     deac\
     cdei\
     bcdf\
     cdfi\
     dfic\
     cdfk\
     bcdg\
     babc\
    \
     abcd\
     abcd bcde\
     abcd bcde cdea\
     abcd bcde cdea deab\
     abcd bcde cdea deab eaba\
     abcd bcde cdea deab eaba abab\
     abcd bcde cdea deab eaba abab babc\
     bcde cdea deab eaba abab babc abcd bcdf\
     bcde cdea deab eaba abab babc abcd bcdf cdfi\
     bcde cdea deab eaba abab babc abcd bcdf cdfi dfic\
     Maximum count:10\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

10. <span>**一个整数数组，长度为**</span><span>**n**</span><span>**，将其分为**</span><span>**m**</span><span>**份，使各份的和相等，求**</span><span>**m**</span><span>**的最大值**\

    </span><span>**比如**</span><span>**{3**</span><span>**，**</span><span>**2**</span><span>**，**</span><span>**4**</span><span>**，**</span><span>**3**</span><span>**，**</span><span>**6} **</span><span>**可以分成**</span><span>**{3**</span><span>**，**</span><span>**2**</span><span>**，**</span><span>**4**</span><span>**，**</span><span>**3**</span><span>**，**</span><span>**6}
    m=1; **</span>

    <span>**{3,6}{2,4,3} m=2**</span>

    <span style="font-size:10.5pt;">**{3,3}{2,4}{6} m=3 **</span><span
    style="font-size:10.5pt;">**所以**</span><span
    style="font-size:10.5pt;">**m**</span><span
    style="font-size:10.5pt;">**的最大值为**</span><span
    style="font-size:10.5pt;">**3。**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> gc\_Size = 8;\
     <span
    style="color:#0000ff;">int</span> arr[gc\_Size] = {1,1,1,3,2,4,3,6};\
     <span style="color:#0000ff;">int</span> g\_iChosen[gc\_Size];\
    \
     <span style="color:#0000ff;">bool</span> StatSum( <span
    style="color:#0000ff;">int</span> nCntChosen, <span
    style="color:#0000ff;">int</span> leftSum ){\
         <span style="color:#0000ff;">bool</span> ret = <span
    style="color:#0000ff;">false</span>;\
         <span style="color:#0000ff;">if</span>( leftSum \< 0 ) <span
    style="color:#0000ff;">return</span> <span
    style="color:#0000ff;">false</span>;\
         <span style="color:#0000ff;">if</span>( leftSum == 0 ) <span
    style="color:#0000ff;">return</span> <span
    style="color:#0000ff;">true</span>;\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< gc\_Size; i++ ){\
             <span
    style="color:#0000ff;">if</span>( g\_iChosen[i] == 0 && !ret ){\
                 g\_iChosen[i] = nCntChosen + 1;\
                 <span
    style="color:#0000ff;">bool</span> tmpRet = StatSum( nCntChosen, leftSum - arr[i]);\
                 ret |= tmpRet;\
                 <span
    style="color:#0000ff;">if</span>( !tmpRet ) g\_iChosen[i] = 0;\
             }\
         }\
    \
         <span style="color:#0000ff;">return</span> ret;\
     }\
    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> Return maximum split pieces.</span><span
    style="color:#008000;">\
     </span><span style="color:#0000ff;">int</span> AverSplit(){\
         <span
    style="color:#0000ff;">int</span> sumTotal = accumulate( &arr[0], &arr[gc\_Size], 0 );\
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> You have to sort by ascending order.\
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> 当你选择的时候,越大的是在n个slice中唯一一个splitted的数组中的\
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> 例如: 1,1,1,2,3,3,4,6.\
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> 如果1,1,1,4入选,则不行.\
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> 6则是其中一个splitted数组的不二选择.</span><span
    style="color:#008000;">\
     </span>    sort( &arr[0], &arr[gc\_Size], greater\<<span
    style="color:#0000ff;">int</span>\>() );\
    \
         <span style="color:#0000ff;">int</span> maxSlice = 1;\
         <span style="color:#0000ff;">int</span> slice = 2;\
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> slice肯定是sumTotal的余数,并且不可能大于arr的最大的数.</span><span
    style="color:#008000;">\
     </span>    <span
    style="color:#0000ff;">while</span>( slice \< sumTotal/2
    && sumTotal/slice \>= arr[0] )\
         {\
             <span
    style="color:#0000ff;">while</span>( sumTotal % slice != 0 ){\
                 slice++;\
                 <span
    style="color:#0000ff;">if</span>( !(slice \< (sumTotal \>\> 2) && sumTotal/slice \>= arr[0]) )\
                     <span style="color:#0000ff;">break</span>;\
             }\
    \
             memset( g\_iChosen, 0, <span
    style="color:#0000ff;">sizeof</span>(<span
    style="color:#0000ff;">int</span>)\*gc\_Size );\
             <span style="color:#0000ff;">int</span> nCntChosen = 0;\
             <span
    style="color:#0000ff;">int</span> sumSplitted = sumTotal/slice;\
             <span
    style="color:#0000ff;">while</span>( nCntChosen \< slice ){\
                 <span
    style="color:#0000ff;">if</span>( StatSum( nCntChosen, sumSplitted) )\
                     nCntChosen++;\
                 <span style="color:#0000ff;">else</span>\
                     <span style="color:#0000ff;">break</span>;\
             }\
             <span
    style="color:#0000ff;">if</span>( nCntChosen \>= slice )\
                 maxSlice = slice;\
             slice++;\
         }\
    \
    \
         <span style="color:#0000ff;">return</span> maxSlice;\
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         cout \<\< AverSplit() \<\< endl;\
     }

    </div>

11. <span>**求一个数组的最长递减子序列**</span>
    <span>**比如**</span><span>**{9**</span><span>**，**</span><span>**4**</span><span>**，**</span><span>**3**</span><span>**，**</span><span>**2**</span><span>**，**</span><span>**5**</span><span>**，**</span><span>**4**</span><span>**，**</span><span>**3**</span><span>**，**</span><span>**2}**</span><span>**的最长递减子序列为**</span><span>**{9**</span><span>**，**</span><span>**5**</span><span>**，**</span><span>**4**</span><span>**，**</span><span>**3**</span><span>**，**</span><span>**<span>2}</span>**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\

    求一个数组的最长递减子序列 比如{9，4，3，2，5，4，3，2}的最长递减子序列为{9，5，4，3，2}.\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> gc\_iSize = 9;\
     <span
    style="color:#0000ff;">int</span> arr[gc\_iSize] = {7,9,4,6,2,5,4,3,5};\
     <span style="color:#0000ff;">int</span> seq[gc\_iSize][gc\_iSize];\
    \
     <span style="color:#0000ff;">int</span> GetLDS(){\
         <span style="color:#0000ff;">int</span> ret = 0;\
         seq[0][0] = 1;\
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> [i] 第i个序列.\
         </span><span style="color:#008000;">//</span><span
    style="color:#008000;"> [j] 选中第j个数.</span><span
    style="color:#008000;">\
     </span>    <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 1; i \< gc\_iSize; i++ )\
             <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> j = 0; j \< gc\_iSize; j++ )\
             {\
                 <span
    style="color:#0000ff;">if</span>( i == 0 || j == 0 ){\
                     <span
    style="color:#0000ff;">if</span>( arr[i] \<= arr[j] )\
                         seq[i][j] = 2;\
                     <span style="color:#0000ff;">else</span>\
                         seq[i][j] = 1;\
                 }\
                 <span style="color:#0000ff;">else</span> <span
    style="color:#0000ff;">if</span>( i \> j && arr[i] \<= arr[j] )\
                     seq[i][j] = std::max( seq[j][j] + 1, seq[i][j-1] );\
                 <span style="color:#0000ff;">else</span>\
                     seq[i][j] = seq[i][j-1];\
             }\
             <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< gc\_iSize; i++ )\
             {\
                 <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> j = 0; j \< gc\_iSize; j++ ){\
                     cout \<\< seq[i][j] \<\< " ";\
                 }\
                 cout \<\< endl;\
             }\
    \
             <span
    style="color:#0000ff;">return</span> seq[gc\_iSize-1][gc\_iSize-1];\
     }\
     <span style="color:#0000ff;">int</span> main(){\
         cout \<\< GetLDS() \<\< endl;\
     }\
    \
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     1 0 0 0 0 0 0 0 0\
     1 1 1 1 1 1 1 1 1\
     2 2 2 2 2 2 2 2 2\
     2 2 2 2 2 2 2 2 2\
     2 2 3 3 3 3 3 3 3\
     2 2 2 3 3 3 3 3 3\
     2 2 3 3 3 4 4 4 4\
     2 2 3 3 3 4 5 5 5\
     2 2 2 3 3 4 4 4 4\
     4\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

     

12. <span
    style="color:#e53333;">**输入一个正整数数组，将它们连接起来排成一个数，输出能排出的所有数字中最小的一个。**</span>

    <span style="color:#e53333;">**例如输入数组**</span><span>**<span
    style="color:#e53333;">{32,</span>**<span
    style="color:#e53333;">**  **</span>**<span
    style="color:#e53333;">321}</span>**</span><span
    style="color:#e53333;">**，则输出这两个能排成的最小数字**</span><span
    style="color:#e53333;">**32132**</span><span
    style="color:#e53333;">**。**</span>

    <span
    style="color:#e53333;">**请给出解决问题的算法，并证明该算法。**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
    \
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\

    输入一个正整数数组，将它们连接起来排成一个数，输出能排出的所有数字中最小的一个。\
     例如输入数组{32,  321}，则输出这两个能排成的最小数字32132。\
     请给出解决问题的算法，并证明该算法。\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> gc\_Size = 5;\
     <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> gc\_MaxNumLength = 10;\
     <span
    style="color:#0000ff;">int</span> arr[gc\_Size] = { 32, 321, 123, 422, 43 };\
     <span style="color:#0000ff;">char</span> \*g\_szStr1 = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">char</span>[gc\_MaxNumLength\*2+1];\
     <span style="color:#0000ff;">char</span> \*g\_szStr2 = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">char</span>[gc\_MaxNumLength\*2+1];\
    \
     <span style="color:#0000ff;">int</span> CMP( <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">void</span> \*str1, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">void</span> \*str2 ){\
         strcpy( g\_szStr1, \*(<span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span>\*\*)str1 );\
         strcat( g\_szStr1, \*(<span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span>\*\*)str2 );\
    \
         strcpy( g\_szStr2, \*(<span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span>\*\*)str2 );\
         strcat( g\_szStr2, \*(<span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span>\*\*)str1 );\
    \
         <span
    style="color:#0000ff;">return</span> strcmp( g\_szStr1, g\_szStr2 );\
     }\
     <span style="color:#0000ff;">void</span> DoTask(){\
         <span style="color:#0000ff;">char</span> \*\*ppStr = NULL;\
         ppStr = <span style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">char</span> \*[gc\_MaxNumLength+1];\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< gc\_Size; i++ ){\
             \*(ppStr + i) = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">char</span>[gc\_MaxNumLength+1];\
             sprintf( \*(ppStr +i), "%d", arr[i] );\
         }\
         qsort( ppStr, gc\_Size, <span
    style="color:#0000ff;">sizeof</span>(<span
    style="color:#0000ff;">char</span>\*), CMP );\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< gc\_Size; i++ )\
             cout \<\< \*(ppStr + i) \<\< " ";\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< gc\_Size; i++ )\
             delete [](\*(ppStr + i));\
         delete []ppStr;\
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         DoTask();\
         delete []g\_szStr1;\
         delete []g\_szStr2;\
     }

    </div>

13. **<span
    style="color:#e53333;">函数将字符串中的字符'\*'移到串的前部分，前面的非'\*'字符后移，但不能改变非'\*'字符的先后顺序，</span>**

    **<span
    style="color:#e53333;">函数返回串中字符'\*'的数量。如原始串为：ab\*\*cd\*\*e\*12，</span>**

    **<span
    style="color:#e53333;">处理后为\*\*\*\*\*abcde12，函数并返回值为5。（要求使用尽量少的时间和辅助空间）。</span>**

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\

    函数将字符串中的字符'\*'移到串的前部分，前面的非'\*'字符后移，但不能改变非'\*'字符的先后顺序，\
     函数返回串中字符'\*'的数量。如原始串为：ab\*\*cd\*\*e\*12，\

    处理后为\*\*\*\*\*abcde12，函数并返回值为5。（要求使用尽量少的时间和辅助空间）\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     \#include "stdafx.h"\
    \
     int MoveAsterisk( char \*str ){\
         assert( str != NULL );\
    \
         int len = strlen( str );\
         int iAsterisk = len - 1;\
         int iNonAsterisk = len - 1;\
         int nCnt = 0;\
         \
         // Find first asterisk.\
         while( iAsterisk \>= 0 && str[iAsterisk] != '\*' ) iAsterisk--;\
         iNonAsterisk = iAsterisk - 1;\
    \
         while( iAsterisk \>= 0 && iNonAsterisk \>= 0 )\
         {\

            while( iAsterisk \>= 0 && str[iAsterisk] != '\*' ) iAsterisk--;\

            while( iNonAsterisk \>= 0 && str[iNonAsterisk] == '\*' ){ iNonAsterisk--;}\
             if( iAsterisk \>= 0 && iNonAsterisk \>= 0 ){\
                 str[iAsterisk] = str[iAsterisk] \^ str[iNonAsterisk];\
                 str[iNonAsterisk] = str[iAsterisk] \^ str[iNonAsterisk];\
                 str[iAsterisk] = str[iAsterisk] \^ str[iNonAsterisk];\
                 nCnt++;\
             }\
         }\
    \
         return nCnt;\
     }\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#0000ff;">int</span> MoveAsterisk( <span
    style="color:#0000ff;">char</span> \*szStr ){\
         assert( szStr != NULL );\
    \
         <span style="color:#0000ff;">int</span> len = strlen( szStr );\
    \
         <span
    style="color:#0000ff;">char</span> \*pAsterisk = szStr + len - 1;\
         <span
    style="color:#0000ff;">char</span> \*pNonAsterisk = szStr + len - 1;\
    \
         <span
    style="color:#0000ff;">while</span>( pAsterisk \>= szStr ){\
             <span
    style="color:#0000ff;">if</span>( \*pAsterisk != '\*' )\
                 \*pNonAsterisk-- = \*pAsterisk;\
             pAsterisk--;\
         }\
    \
         <span
    style="color:#0000ff;">int</span> nCnt = pNonAsterisk - pAsterisk;\
         <span
    style="color:#0000ff;">while</span>( pNonAsterisk \>= szStr )\
             \*pNonAsterisk-- = '\*';\
    \
         <span style="color:#0000ff;">return</span> nCnt;\
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         <span
    style="color:#0000ff;">char</span> str[256] = "ab\*\*cd\*\*e\*12";\
         cout \<\< MoveAsterisk( str ) \<\< endl;\
         cout \<\< str \<\< endl;\
     }

    </div>

14. **<span style="color:#e53333;">求两个串中的第一个最长子串.</span>**

    **<span
    style="color:#e53333;">如"abractyeyt","dgdsaeactyey"的最大子串为"actyet"。</span>**

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     求两个串中的第一个最长子串.\
     如"abractyeyt","dgdsaeactyey"的最大子串为"actyet"。\
     </span><span style="color:#008000;">\*/</span>\
    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> Get first longest substring.</span><span
    style="color:#008000;">\
     </span><span style="color:#0000ff;">void</span> GetFLS( <span
    style="color:#0000ff;">char</span> \*pOut, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*str1, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*str2 ){\
         assert( pOut != NULL && str1 != NULL && str2 != NULL );\
    \
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*p1 = str1;\
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*p2 = str2;\
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*pMaxIdx = NULL;\
         <span style="color:#0000ff;">int</span> maxLen = 0;\
         <span style="color:#0000ff;">while</span>( \*p1 != '\\0' )\
         {\
             p2 = str2;\
             <span style="color:#0000ff;">while</span>( \*p2 != '\\0' )\
             {\
                 <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*pTmp1 = p1;\
                 <span
    style="color:#0000ff;">while</span>( \*p2 != '\\0' && \*pTmp1 != \*p2 ) p2++;\
    \
                 <span
    style="color:#0000ff;">while</span>( \*pTmp1 != '\\0' && \*p2 != '\\0' && \*pTmp1 == \*p2 ){\
                     pTmp1++;\
                     p2++;\
                 }\
    \
                 <span
    style="color:#0000ff;">if</span>( maxLen \< pTmp1 - p1 ){\
                     maxLen = pTmp1 - p1;\
                     pMaxIdx = p1;\
                 }\
             }\
    \
             p1++;\
         }\
    \
         <span style="color:#0000ff;">if</span>( pMaxIdx ){\
             <span
    style="color:#0000ff;">while</span>( maxLen-- ) \*pOut++ = \*pMaxIdx++;\
         }\
    \
         \*pOut = '\\0';\
    \
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         <span
    style="color:#0000ff;">char</span> str1[256] = "abractyeyt";\
         <span
    style="color:#0000ff;">char</span> str2[256] = "dgdsaeactyey";\
         <span style="color:#0000ff;">char</span> result[256];\
         GetFLS( result, str1, str2 );\
         cout \<\< result \<\< endl;\
     }\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     actyey\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

15. <span
    style="color:#e53333;font-size:10.5pt;">**给出洗牌的一个算法，并将洗好的牌存储在一个整形数组里.**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     给出洗牌的一个算法，并将洗好的牌存储在一个整形数组里.\
     </span><span style="color:#008000;">\*/</span>\
     inline <span style="color:#0000ff;">int</span> RandInt( <span
    style="color:#0000ff;">int</span> low,<span
    style="color:#0000ff;">int</span> high ){\
         <span
    style="color:#0000ff;">return</span> rand()%(high-low+1) + low;\
     }\
     <span style="color:#0000ff;">void</span> Shuffle( <span
    style="color:#0000ff;">int</span> \*poker, <span
    style="color:#0000ff;">int</span> N = 54 ){\
         srand( (unsigned)time(NULL) ) ;\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< N; i++ )\
             poker[i] = i;\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< N; i++ )\
             std::swap( poker[i], poker[RandInt(i,N-1)] );\
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
         0 \~ 12  代表红桃\
         13 \~ 25  代表黑桃\
         26 \~ 38  代表方块\
         39 \~ 51  代表梅花\
         52 \~ 53  代表大小王\
         </span><span style="color:#008000;">\*/</span>\
         <span style="color:#0000ff;">int</span> poker[54];\
         Shuffle( poker );\
         copy( &poker[0], &poker[54], ostream\_iterator\<<span
    style="color:#0000ff;">int</span>\>(cout, " ") );\
         cout \<\< endl;\
     }

    </div>

16. <span
    style="color:#e53333;">**写一个函数，检查字符串是否是整数，如果是，返回其整数值。**</span>

    <span
    style="color:#e53333;font-size:10.5pt;">**（或者：怎样只用**</span><span
    style="color:#e53333;font-size:10.5pt;">**4**</span><span
    style="color:#e53333;font-size:10.5pt;">**行代码编写出一个从字符串到长整形的函数？）**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     写一个函数，检查字符串是否是整数，如果是，返回其整数值。\
     （或者：怎样只用4行代码编写出一个从字符串到长整形的函数？）\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#0000ff;">long</span> Str2Long( <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*szStr, <span
    style="color:#0000ff;">int</span> len ){\
         <span style="color:#0000ff;">if</span>( len \> 2 )\
             <span
    style="color:#0000ff;">return</span> Str2Long( szStr, len - 1 )\*10 + (szStr[0] == '-' ? -(<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)szStr[len-1] + '0' : (<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)szStr[len-1] - '0');\
         <span style="color:#0000ff;">else</span>\
             <span
    style="color:#0000ff;">return</span> szStr[0] == '-' ? -(<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)szStr[1] + '0' : (szStr[0] == '+' ? (<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)szStr[1] - '0' : (((<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)szStr[0] - '0')\*10 + (<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)szStr[1] - '0'));\
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         <span style="color:#0000ff;">char</span> szStr[256] = "-1245";\
         cout \<\< Str2Long( szStr, 5 ) \<\< endl;\
     }

    </div>

17. <span>**求整数随机数构成的数组中找到长度\>**</span><span>**=3**</span><span>**的最长的等差数列**</span>

    <span>**输出等差数列由小到大**</span><span>**: **</span>

    <span>**如果没有符合条件的就输出**</span><span>**[0,0]**</span>

    <span>**格式：**</span>

    <span>**输入**</span><span>**[1,3,0,5,-1,6]**</span>

    <span>**输出**</span><span>**[-1,1,3,5]**</span>

    <span>**要求时间复杂度，空间复杂度尽量小.**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     求整数随机数构成的数组中找到长度\>=3的最长的等差数列\
     输出等差数列由小到大: \
     如果没有符合条件的就输出[0,0]\
     格式：\
     输入[1,3,0,5,-1,6]\
     输出[-1,1,3,5]\
     要求时间复杂度，空间复杂度尽量小.\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">int</span> gc\_iSize = 6;\
     <span
    style="color:#0000ff;">int</span> arr[gc\_iSize] = {1,3,0,5,-1,6};\
    \
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> Get longest Arithmetic Progression.</span><span
    style="color:#008000;">\
     </span><span style="color:#0000ff;">void</span> GetLAP(){\
         sort( &arr[0], &arr[gc\_iSize] );\
    \
         <span
    style="color:#0000ff;">int</span> len = arr[gc\_iSize-1] - arr[0];\
         <span style="color:#0000ff;">int</span> \*cntPro = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">int</span>[len];\
         memset( cntPro, 0, <span
    style="color:#0000ff;">sizeof</span>(<span
    style="color:#0000ff;">int</span>)\*len );\
    \
         <span style="color:#0000ff;">int</span> \*ai = <span
    style="color:#0000ff;">new</span> <span
    style="color:#0000ff;">int</span>[len];\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< gc\_iSize; i++ )\
             <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> j = i + 1; j \< gc\_iSize; j++ )\
             {\
                 <span
    style="color:#0000ff;">int</span> d = arr[j] - arr[i];\
                 <span
    style="color:#0000ff;">if</span>( cntPro[d] == 0 ){\
                     ai[d] = arr[j];\
                     cntPro[d]++;\
                 }\
                 <span style="color:#0000ff;">else</span>{\
                     <span
    style="color:#0000ff;">if</span>( d == arr[i] - ai[d] )\
                         cntPro[d]++;\
                 }\
             }\
    \
         <span style="color:#0000ff;">int</span> idxMax = 0;\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 1; i \< len; i++ )\
             <span
    style="color:#0000ff;">if</span>( cntPro[idxMax] \< cntPro[i] ){\
                 idxMax = i;\
             }\
    \
         <span style="color:#0000ff;">int</span> cnt = cntPro[idxMax];\
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< gc\_iSize; i++ )\
             <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> j = i + 1; j \< gc\_iSize; j++ )\
             {\
                 <span
    style="color:#0000ff;">if</span>( idxMax == arr[j] - arr[i] ){\
                     <span
    style="color:#0000ff;">if</span>( cnt-- == idxMax )\
                         cout \<\< arr[i] \<\< " ";\
                     cout \<\< arr[j] \<\< " ";\
                 }\
             }\
         cout \<\< endl;\
    \
         delete []cntPro;\
         delete []ai;\
     }\
     <span style="color:#0000ff;">int</span> main(){\
         GetLAP();\
     }

    </div>

18. <span>**输入一个字符串，输出该字符串中对称的子字符串的最大长度。**</span>

    <span>**比如输入字符串“**</span><span>**google**</span><span>**”，由于该字符串里最长的对称子字符串是“**</span><span>**goog**</span><span>**”，因此输出**</span><span>**4**</span><span>**。**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     输入一个字符串，输出该字符串中对称的子字符串的最大长度。\

    比如输入字符串“google”，由于该字符串里最长的对称子字符串是“goog”，因此输出4。\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#008000;">//</span><span
    style="color:#008000;"> Get longest symmetry substring.</span><span
    style="color:#008000;">\
     </span><span style="color:#0000ff;">void</span> GetLSS( <span
    style="color:#0000ff;">char</span> \*pOut, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*str ){\
         assert( pOut != NULL && str != NULL );\
    \
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*p = str;\
    \
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*maxP = NULL;\
         <span
    style="color:#0000ff;">int</span> maxNum = numeric\_limits\<<span
    style="color:#0000ff;">int</span>\>::min();\
         <span style="color:#0000ff;">if</span>( p[0] == p[1] ){\
             maxNum = 2;\
             maxP = p;\
         }\
         p++;\
         <span
    style="color:#0000ff;">while</span>( \*p != '\\0' && \*(p+1) != '\\0' )\
         {\
             <span style="color:#0000ff;">int</span> idx = 1;\
             <span
    style="color:#0000ff;">while</span>( (p-idx) \>= str && \*(p+idx) != '\\0' && \*(p-idx) == \*(p+idx) ){\
                 <span
    style="color:#0000ff;">if</span>( maxNum \< 2\*idx+1 ){ maxNum = 2\*idx+1; maxP = p-idx; }\
                 idx++;\
             }\
             \
             idx = 1;\
             <span
    style="color:#0000ff;">while</span>( (p-idx+1) \>= str && \*(p+idx) != '\\0' && \*(p-idx+1) == \*(p+idx) ){\
                 <span
    style="color:#0000ff;">if</span>( maxNum \< 2\*idx ){ maxNum = 2\*idx; maxP = p-idx+1; }\
                 idx++;\
             }\
             p++;\
         }\
    \
         cout \<\< maxNum \<\< endl;\
    \
         <span style="color:#0000ff;">for</span>( <span
    style="color:#0000ff;">int</span> i = 0; i \< maxNum; i++ )\
             \*(pOut + i) = \*(maxP + i);\
         \*(pOut + maxNum) = '\\0';\
     }\
     <span style="color:#0000ff;">int</span> main(){\
         <span
    style="color:#0000ff;">char</span> szStr[256] = "google";\
         <span style="color:#0000ff;">char</span> pOut[256];\
         GetLSS( pOut, szStr );\
    \
         cout \<\< pOut \<\< endl;\
     }

    </div>

19. <span
    style="color:#e53333;font-size:10.5pt;">**求最大连续递增数字串（如“**</span><span
    style="color:#e53333;font-size:10.5pt;">**ads3sl456789DF3456ld345AA**</span><span
    style="color:#e53333;font-size:10.5pt;">**”中的“**</span><span
    style="color:#e53333;font-size:10.5pt;">**456789**</span><span
    style="color:#e53333;font-size:10.5pt;">**”**</span><span
    style="color:#e53333;font-size:10.5pt;">**）.**</span>

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     求最大连续递增数字串（如“ads3sl456789DF3456ld345AA”中的“456789”.\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#0000ff;">void</span> GetMCID( <span
    style="color:#0000ff;">char</span> \*pOut, <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*szStr ){\
         assert( pOut != NULL && szStr != NULL );\
    \
         <span style="color:#0000ff;">int</span> nCnt = 0;\
         <span style="color:#0000ff;">int</span> nMaxCnt = 0;\
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*pRecord = NULL;\
         <span style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">char</span> \*p = szStr;\
         <span style="color:#0000ff;">while</span>( \*p != '\\0' )\
         {\
             <span style="color:#0000ff;">int</span> c = (<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)\*p;\
             nCnt = 0;\
             <span style="color:#0000ff;">if</span>( isdigit(c) )\
             {\
                 nCnt++;\
                 <span
    style="color:#0000ff;">if</span>( nMaxCnt \< nCnt ){ pRecord = p; nMaxCnt = nCnt; }\
                 p++;\
                 <span
    style="color:#0000ff;">while</span>( \*p != '\\0' && isdigit(c) ){\
                     <span style="color:#0000ff;">if</span>( (<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)\*p != c + 1 )\
                         <span style="color:#0000ff;">break</span>;\
    \
                     nCnt++;\
                     <span
    style="color:#0000ff;">if</span>( nMaxCnt \< nCnt ){ pRecord = p; nMaxCnt = nCnt; }\
                     c = (<span
    style="color:#0000ff;">int</span>)(unsigned <span
    style="color:#0000ff;">char</span>)\*p;\
                     p++;\
                 }\
             }\
             p++;\
         }\
    \
         \*(pOut + nMaxCnt) = '\\0';\
         <span style="color:#0000ff;">while</span>( --nMaxCnt \>= 0 ){\
             \*(pOut + nMaxCnt) = \*pRecord--;\
         }\
    \
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         <span
    style="color:#0000ff;">char</span> szStr[256] = "ads3sl456789DF3456ld345AA";\
         <span style="color:#0000ff;">char</span> szOut[256];\
         GetMCID( szOut, szStr );\
    \
         cout \<\< szOut \<\< endl;\
     }

    </div>

20. **一串首尾相连的珠子(m个)，有N种颜色(N\<=10)，设计一个算法，取出其中一段，要求包含所有N中颜色，并使长度最短。并分析时间复杂度与空间复杂度。**

    <div
    style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

    \#include "stdafx.h"\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     一串首尾相连的珠子(m个)，有N种颜色(N\<=10)，\
     设计一个算法，取出其中一段，要求包含所有N中颜色，并使长度最短。\
     并分析时间复杂度与空间复杂度。\
     </span><span style="color:#008000;">\*/</span>\
     <span style="color:#0000ff;">int</span> num[10];\
     <span
    style="color:#0000ff;">void</span> GetShortestStrContainN( <span
    style="color:#0000ff;">const</span> <span
    style="color:#0000ff;">string</span> &str, <span
    style="color:#0000ff;">string</span> &shortestStr ){\
         <span style="color:#0000ff;">int</span> iStart = 0, iEnd = 0;\
         <span style="color:#0000ff;">int</span> iDone = 0x0;\
         <span
    style="color:#0000ff;">int</span> iShortestLen = str.length();\
         <span style="color:#0000ff;">int</span> iLen = str.length();\
         <span style="color:#0000ff;">int</span> iRecordStart = 0;\
    \
         <span style="color:#008000;">//</span><span
    style="color:#008000;"> First, stat. the the string with N colors.</span><span
    style="color:#008000;">\
     </span>    <span
    style="color:#0000ff;">while</span>( iDone != 0x3ff ){\
             iDone |= 0x1 \<\< (str[iEnd] - '0');\
             num[str[iEnd] - '0']++;\
             iEnd++;\
         }\
         iEnd--;\
    \
         <span style="color:#0000ff;">while</span>( iStart \< iLen )\
         {\
             <span style="color:#0000ff;">int</span> iCurLen;\
             <span style="color:#0000ff;">if</span>( iEnd \> iStart )\
                 iCurLen = iEnd - iStart + 1;\
             <span style="color:#0000ff;">else</span>\
                 iCurLen = iEnd + iLen - iStart;\
    \
             <span
    style="color:#0000ff;">if</span>( iShortestLen \> iCurLen){\
                 iShortestLen = iCurLen;\
                 iRecordStart = iStart;\
             }\
    \
             <span
    style="color:#0000ff;">while</span>( iStart \< iLen && num[str[iStart] - '0'] \<= 1 ){\
                 iEnd = (iEnd + 1)%iLen;\
                 <span
    style="color:#0000ff;">if</span>( iEnd == iStart )\
                     iStart++;\
                 <span style="color:#0000ff;">else</span>\
                     num[str[iEnd]-'0']++;\
             }\
             num[str[iStart]-'0']--;\
             iStart++;\
         }\
    \

        cout \<\< "start:" \<\< iRecordStart \<\< ", len:" \<\< iShortestLen \<\< endl;\
         <span
    style="color:#0000ff;">if</span>( iLen - iRecordStart \< iShortestLen ){\
             shortestStr = str.substr( iRecordStart );\

            shortestStr += str.substr( 0, iShortestLen - iLen + iRecordStart );\
         }\
         <span style="color:#0000ff;">else</span>\
             shortestStr.assign( str, iRecordStart, iShortestLen );\
     }\
    \
     <span style="color:#0000ff;">int</span> main(){\
         <span style="color:#0000ff;">string</span> str;\
         <span style="color:#0000ff;">string</span> sMain;\
         cin \>\> sMain;\
         GetShortestStrContainN( sMain, str );\
         cout \<\< str \<\< endl; \
     }\
     <span style="color:#008000;">/\*</span><span
    style="color:#008000;">\
     0134521065768921201221411\
     start:2, len:12\
     345210657689\
     请按任意键继续. . .\
    \
     6576892120122141101345210\
     start:19, len:11\
     34521065768\
     请按任意键继续. . .\
     </span><span style="color:#008000;">\*/</span>

    </div>

     

21. **<span
    style="color:#e53333;">一个100米长的部队行军，一个传令兵从队伍尾到队伍头，然后再从队伍头返回队伍尾，这时队伍正好走了100米，整个过程队伍和传令兵的速度不变，那么传令兵走了多少米？</span>**

    设士兵速度x，队伍y 

    [100/(x-y)+100/(x+y)]\*y=100 

    解得 

    x=（1+根号2）y 

    路程与速度成正比（时间相同） 

    士兵路程为100（1+根号2） 

    就是241.4米左右。

22. **<span
    style="color:#e53333;">两个圆相交，交点是A1，A2。现在过A1点做一直线与两个圆分别相交另外一点B1，B2。</span>**

    **<span
    style="color:#e53333;">B1B2可以绕着A1点旋转。问在什么情况下，B1B2最长.</span>**\
     当A1A2⊥B1B2时B1B2最长

    设弦A1B1、A1B2所在圆分别为⊙O1、⊙O2，取A1B1、A1B2的中点C、D，连结O1C、O2D

    则B1B2＝A1B1＋A1B2＝2A1C＋2A1D＝2CD

    当A1A2与B1B2不垂直时，四边形O1O2DC是直角梯形，定有O1O2＞CD

    此时B1B2＝2CD＜2O1O2

    当A1A2⊥B1B2时，四边形O1O2DC是矩形，定有O1O2＝CD

    此时B1B2＝2CD＝2O1O2为最大.

23. <span
    style="color:#e53333;font-size:10.5pt;">**用测量器和**</span><span
    style="color:#e53333;font-size:10.5pt;">**50**</span><span
    style="color:#e53333;font-size:10.5pt;">**尺**</span><span
    style="color:#e53333;font-size:10.5pt;">** **</span><span
    style="font-size:10.5pt;">**<span
    style="color:#e53333;">如何测量河对岸的巨石高度？</span>**\
     ![](http://files.note.sdo.com/XbPJ4~k5mC_2wE13U001k2)\
     通过测量h和d求出θ角,然后沿河岸走一定距离\

    ![剪贴板20121801185954122.jpg](http://files.note.sdo.com/XbPJ4~j-0SJiwE02U007kJ "剪贴板20121801185954122.jpg")\
     成θ角的时候X即为所求.</span>

24. <span style="font-size:10.5pt;"></span> <span
    style="font-family:宋体;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-ascii-font-family:Arial;mso-hansi-font-family:Arial;mso-font-kerning:1.0pt;mso-bidi-font-family:Arial;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;">**求**</span><span
    style="font-family:Arial;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-font-kerning:1.0pt;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;mso-fareast-font-family:宋体;"
    lang="EN-US">**Fibonacci**</span><span
    style="font-family:宋体;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-ascii-font-family:Arial;mso-hansi-font-family:Arial;mso-font-kerning:1.0pt;mso-bidi-font-family:Arial;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;">**数列中第**</span><span
    style="font-family:Arial;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-font-kerning:1.0pt;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;mso-fareast-font-family:宋体;"
    lang="EN-US">**k**</span><span
    style="font-family:宋体;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-ascii-font-family:Arial;mso-hansi-font-family:Arial;mso-font-kerning:1.0pt;mso-bidi-font-family:Arial;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;">**个与前面所有数互质的数（除前面两个数**</span><span
    style="font-family:Arial;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-font-kerning:1.0pt;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;mso-fareast-font-family:宋体;"
    lang="EN-US"> **1**</span><span
    style="font-family:宋体;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-ascii-font-family:Arial;mso-hansi-font-family:Arial;mso-font-kerning:1.0pt;mso-bidi-font-family:Arial;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;">**，**</span><span
    style="font-family:Arial;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-font-kerning:1.0pt;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;mso-fareast-font-family:宋体;"
    lang="EN-US">**1** </span><span
    style="font-family:宋体;color:#e53333;font-size:9.5pt;mso-fareast-language:ZH-CN;mso-ascii-font-family:Arial;mso-hansi-font-family:Arial;mso-font-kerning:1.0pt;mso-bidi-font-family:Arial;mso-ansi-language:EN-US;mso-bidi-language:AR-SA;">**）。**</span>

25. 






