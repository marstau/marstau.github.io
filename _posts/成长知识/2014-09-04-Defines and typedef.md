---
layout: post
title: Defines and typedef
category: 游戏技术
tags: normal　knowledge
keywords: 
description: 
---

**<span style="color:#e53333;"></span>** Format:

name

\#define

DESC

**<span style="color:#e53333;"></span>** 

------------------------------------------------------------------------

defines: 

1.  **<span style="color:#e53333;">E\_FAIL</span>**\
     \#define E\_FAIL \_HRESULT\_TYPEDEF\_ (0x80004005)L\
     Unspecified error.
2.  **<span style="color:#e53333;">D3D\_OK</span>**\
    \#define D3D\_OK S\_OK\
     Direct3D Errors.
3.  **<span style="color:#e53333;">S\_OK</span>**\
     \#define S\_OK ((HRESULT)0L)
4.  **<span style="color:#e53333;">S\_FALSE</span>**\
     \#define S\_FALSE ((HRESULT)1L)\
     Success codes.

5.  **<span style="color:#e53333;">FAILED(Status)</span>**\
     \#define FAILED(Status) ((HRESULT)(Status)\<0)
6.  **<span style="color:#e53333;">D3DX\_PI</span>**\
     \#define D3DX\_PI ((FLOAT)3.141592654f)
7.  **<span style="color:#e53333;">D3DCOLOR、D3DCOLORVALUE、</span><span
    style="color:#e53333;">D3DXCOLOR、</span><span
    style="color:#e53333;">D3DCOLOR\_ARGB、D3DCOLOR\_XRGB</span>**\
     (1) typedef DWORD D3DCOLOR;\
     <span id="__kindeditor_bookmark_end_200__"
    style="display:none;"></span><span
    id="__kindeditor_bookmark_end_198__"
    style="display:none;"></span><span
    id="__kindeditor_bookmark_end_196__"
    style="display:none;"></span><span
    id="__kindeditor_bookmark_end_194__"
    style="display:none;"></span><span
    id="__kindeditor_bookmark_end_192__"
    style="display:none;"></span><span
    id="__kindeditor_bookmark_end_190__"
    style="display:none;"></span><span
    id="__kindeditor_bookmark_end_188__"
    style="display:none;"></span>(2) typedef struct \_D3DCOLORVALUE{\
             float r, g, b, a;\
         }D3DCOLORVALUE;\
     (3) D3DXCOLOR is the eXtension of D3DCOLORVALUE.\
     (4) \#define D3DCOLOR\_ARGB(a,r,g,b)\\\
                 ((D3DCOLOR)((((a)&0xff)\<\<24) | (((r)&0xff)\<\<16) |
    (((g)&0xff)\<\<8) | ((b)&0xff) ))\
     (5) \#define D3DCOLOR\_XRGB(r,g,b) D3DCOLOR\_ARGB(0xff,r,g,b)
8.  **<span style="color:#e53333;">FLT\_MAX</span>**\
     3.402823466e+38F\
     Maximum value.

------------------------------------------------------------------------

 typedef:

1.  **<span style="color:#e53333;">HRESULT</span>**\
     typedef long HRESULT;
2.  **<span style="color:#e53333;">DWORD</span>**\
     typedef unsinged long DWORD;
3.  **<span style="color:#e53333;">WORD</span>**\
     typedef unsigned short WORD;\
     16-bit unsigned integer.
4.  




