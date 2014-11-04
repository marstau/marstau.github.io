---
layout: post
title: GetAsyncKeyState（）& 0x8000f 
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

<span style="color:#38761d;"> </span>

<div
style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

<span
style="color:#000000;">GetAsyncKeyState函数功能：读取的是物理键状态，也是就是不管你怎么鼠标键盘映射，它只读取实际的按键状态。MSDN上给出了例子很恰当For example, the call GetAsyncKeyState(VK\_LBUTTON) always returns the state of the left physical mouse button, regardless of whether it </span><span
style="color:#0000ff;">is</span><span
style="color:#000000;"> mapped to the left or right logical mouse button.也就是说如果你重新设置了映射，GetAsyncKeyState还是只读取物理状态\
\

GetAsyncKeyState的返回值：表示两个内容，一个是最高位bit的值，代表这个键是否被按下，按下为1，抬起为0；一个是最低位\

bit的值，在windowsCE下要忽略（参考自MSDNIf the most significant bit </span><span
style="color:#0000ff;">is</span><span
style="color:#000000;"> </span><span
style="color:#0000ff;">set</span><span
style="color:#000000;">, the key </span><span
style="color:#0000ff;">is</span><span
style="color:#000000;"> down. The least significant\
 bit </span><span style="color:#0000ff;">is</span><span
style="color:#000000;"> not valid </span><span
style="color:#0000ff;">in</span><span
style="color:#000000;"> Windows CE, and should be ignored.）\
  \
 note:\
 GetAsyncKeyState（</span><span style="color:#000000;">'</span><span
style="color:#000000;">M</span><span
style="color:#000000;">'</span><span
style="color:#000000;">）</span><span
style="color:#000000;">&</span><span
style="color:#000000;"> </span><span
style="color:#000000;">0x8000f</span><span
style="color:#000000;"> </span><span
style="color:#008000;">//</span><span
style="color:#008000;"> 要大写M, f的意思是float的意思</span>

</div>

\







