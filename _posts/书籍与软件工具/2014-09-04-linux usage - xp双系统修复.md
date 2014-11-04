---
layout: post
title: linux usage -  xp双系统修复
category: 书籍与软件工具
tags: software／tool
keywords: linux, xp
description: 
---

<span style="font-size:18px;">**<span
style="color:#ff0000;font-size:10.5pt;">安装好grub后,进入（ enter the
key of c ）</span>**</span>
<div class="0" style="text-align:justify;margin-top:5pt;">

<span style="font-size:18px;">**<span
style="color:#ff0000;font-size:10.5pt;">grub\></span>**</span>

</div>

<div class="0" style="text-align:justify;margin-top:5pt;">

<span style="font-size:18px;">****</span>

</div>

<div class="0" style="text-align:justify;margin-top:5pt;">

<span style="font-size:18px;">**<span
style="color:#ff0000;font-size:10.5pt;">红色</span>**</span><span
style="font-size:10.5pt;">字体为输入的命令，</span><span
style="font-size:10.5pt;">输入命令后按“</span>**<span
style="color:#0000ff;font-size:10.5pt;">回车</span>**<span
style="font-size:10.5pt;">”键确定，</span>**<span
style="color:#0000ff;font-size:10.5pt;">蓝色</span>**<span
style="font-size:10.5pt;">为输入命令显示的信息</span><span
style="font-size:10.5pt;">：</span>

</div>

<div class="0">

<span style="font-size:10.5pt;"> </span><span
style="color:#ff0000;font-size:10.5pt;">sudo grub</span>

</div>

<div class="0">

<span style="font-size:10.5pt;">   </span><span
style="color:#0000ff;font-size:10.5pt;"> [ Minimal BASH-like line editing is supported.   For</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;">         the   first   word,  TAB  lists  possible  command</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;">         completions.  Anywhere else TAB lists the possible</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;">         completions of a device/filename. ]</span>

</div>

<div class="0">

<span style="color:#0000ff;font-size:10.5pt;">grub\> </span><span
style="color:#ff0000;font-size:10.5pt;">find /boot/grub/stage1</span>

</div>

<div class="0">

<span style="font-size:10.5pt;"> </span><span
style="color:#0000ff;font-size:10.5pt;">(hd0,6)</span>

</div>

<div class="0">

<span style="color:#0000ff;font-size:10.5pt;">grub\></span><span
style="font-size:10.5pt;"> </span><span
style="color:#ff0000;font-size:10.5pt;">root (hd0,6)</span>

</div>

<div class="0">

<span style="color:#0000ff;font-size:10.5pt;">grub\> </span><span
style="color:#ff0000;font-size:10.5pt;">setup (hd0)</span>

</div>

<div class="0">

<span style="font-size:10.5pt;"> </span><span
style="color:#0000ff;font-size:10.5pt;">Checking if "/boot/grub/stage1" exists... yes</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;"> Checking if "/boot/grub/stage2" exists... yes</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;"> Checking if "/boot/grub/reiserfs\_stage1\_5" exists... yes</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;"> Running "embed /boot/grub/reiserfs\_stage1\_5 (hd0)"...  19 sectors are embedded</span>

</div>

<div class="0">

<span style="color:#0000ff;font-size:10.5pt;">.</span>

</div>

<div class="0">

<span style="color:#0000ff;font-size:10.5pt;">succeeded</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;"> Running "install /boot/grub/stage1 (hd0) (hd0)1+19 p (hd0,6)/boot/grub/stage2</span>

</div>

<div class="0">

<span
style="color:#0000ff;font-size:10.5pt;">/boot/grub/menu.lst"... succeeded</span>

</div>

<div class="0">

<span style="color:#0000ff;font-size:10.5pt;">Done.</span>

</div>

<div class="0">

<span style="color:#0000ff;font-size:10.5pt;">grub\> </span><span
style="color:#ff0000;font-size:10.5pt;">quit</span>

</div>

<div class="0">

<span style="font-size:10.5pt;"><span style="color:#ff0000;">however,
mine is</span></span>

</div>

<div class="0">

<span style="font-size:10.5pt;"><span style="color:#0f13ef;">grub\>
<span style="color:#ff0000;">find /grub/stage1</span></span></span>

</div>

<div class="0">

<span style="font-size:10.5pt;"><span style="color:#0f13ef;">// some
hint information</span></span>

</div>

<div class="0">

<span style="font-size:10.5pt;"><span style="color:#0f13ef;">// ...
(hd0,7)</span></span>

</div>

<div class="0">

<span style="font-size:10.5pt;"><span style="color:#0f13ef;">grub \>
root (hd0,7)</span></span>

</div>

<div class="0">

<span style="font-size:10.5pt;"><span style="color:#0f13ef;">grub \>
<span style="color:#ff0000;">setup (hd0)</span></span></span>

</div>

<div class="0">

<span style="font-size:10.5pt;"><span style="color:#0f13ef;">//
OK</span></span>

</div>








