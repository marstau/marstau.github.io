---
layout: post
title: UNICODE字符集之 UTF-8、UTF-16
category: 编程开发
tags: normal　knowledge
keywords: 
description: 
---

**unicode是一种编码方式，和ascii是同一个概念，而UTF是一种存储方式（格式）。**

**<span style="font-size:24px;color:#e53333;">UTF-8</span>**

UTF-8（transformation format 8 bits）,是UNICODE的一种变长字符编码,UTF-8用1到6个字节编码 UNICODE字符。如果UNICODE字符由2个字节表示，则编码成UTF-8很可能需要3个字节，而如果UNICODE字符由4个字节表示，则编码成 UTF-8可能需要6个字节。用4个或6个字节去编码一个UNICODE字符可能太多了，但很少会遇到那样的UNICODE字符。

**<span style="font-size:18px;">UTF-8编码表</span>**

     UNICODE        UTF-8 

00000000 \~ 0000007F 0xxxxxxx 

00000080 \~ 000007FF 110xxxxx 10xxxxxx 

00000800 \~ 0000FFFF 1110xxxx 10xxxxxx 10xxxxxx 

00010000 \~ 001FFFFF 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx 

00200000 \~ 03FFFFFF 111110xx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx 

04000000 \~ 7FFFFFFF 1111110x 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx

 

@remark

UNICODE用的是16进制表示,UTF-8是用二进制表示的。

如第一行,UNICODE为一个字节的时候,UTF-8用0xxxxxxx 7bits表示。(UTF-8是为了**兼容ASCII编码**)

第三行UTF-8为三字节,如汉字就属于这种,以此类推。

UTF-8前面的1的个数即为字节数,如第二行110xxxxx 10xxxxxx.

 

**<span style="font-size:18px;">UNICODE转UTF-8</span>**

如汉字"你"的编码为“u4F60”，把它转换为二进制为100111101100000，然后按照UTF-8的方法进行转换。

unicode:  0100 111101 100000                4F60

utf-8:    **1110**0100,**10**111101,**10**100000       E4BDA0

 

**<span style="font-size:24px;color:#e53333;">UTF-16</span>**

16bit编码, 是变长码, 大致相当于20位编码, 值在0到0x10FFFF之间, 基本上就是unicode编码的实现. 它是变长码, 与CPU字序有关, 但因为最省空间, 常作为网络传输的外码.

UTF-16是unicode的preferred encoding. 

UTF-16的大尾序（big-endian,BE）和小尾序（little-endian,LE）储存形式都在用。一般来说，以Macintosh制作或储存的文字使用大尾序格式，以Microsoft或Linux制作或储存的文字使用小尾序格式。

为了弄清楚UTF-16文件的大小尾序，在UTF-16文件的开首，都会放置一个U+FEFF字符作为Byte Order Mark

UTF-16LE：FF FE

UTF-16BE：FE FF

 

**UTF-16比起UTF-8，好处在于大部分字符都以固定长度的字节 (2字节) 储存，但UTF-16却无法兼容于ASCII编码。**

 

**<span style="font-size:24px;color:#e53333;">GB2312</span>**

中华人民共和国国家汉字信息交换使用码，全称《信息交换使用汉字编码字符集－基本集》，由国家标准总局发布，1981年5月1日实施，中国大陆和新加坡等地使用此编码。GB2312收录了简化汉字、符号、字母、日文假名等共计7445个字符，其中汉字占6763个。GB2312将代码表分区94个区(0xA1-0xFE)，对应第一个字节，每个区94个位(0xA1-0xFE)，对应了第二字节，两个字节的值分别为区号的值和位号的值加32(0x20)，因此也被称为区位码。GB2312的编码范7围是0x2121-0x777E，与ASCII有重叠，通常方法是将GB码的两个字节的最高位置1区别。

 

**<span style="font-size:24px;color:#e53333;">GBK</span>**

GB2312-80的扩展，向上兼容，包含了20902个汉字，编码范围是0x8140-0xFEFE，剔除高位0x80的字位，其他字符都可以一一映射到Unicode2.0.

GB18030-2000(GBK2K)在GBK的基础上增加了藏、蒙等少数民族的字符，GBK2K从根本上解决了字位不够、字形不足的问题。GBK2K首先要求实现能够完全映射到Unicode3.0标准的所有字形.






## Reference
[Unicode字符集和多字节字符集关系](http://hi.baidu.com/isfull/item/a272c020144170856f2cc345)
