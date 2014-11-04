---
layout: post
title: D3DXVec3TransformCoord [projecting the result back into w=1]
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

<span
style="widows:2;text-transform:none;text-indent:0px;font:18px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">w是齐次坐标，用于表示verctor代表一个点还是一个向量。\

w=1代表vector是个点，w=0代表vector是个向量，平移向量后，向量是没有变化的。\
 也就是w决定了一个变换中，平移部分是否有效。</span>\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:18px/21px verdana, 'courier new';white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">w=0就是只让属于线性变换的变换有效。</span>






