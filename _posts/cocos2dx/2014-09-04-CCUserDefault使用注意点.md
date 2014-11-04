---
layout: post
title: CCUserDefault使用注意点
category: 游戏技术
tags: cocos2dx
keywords: 
description: 
---

std<span style="color:#000000;">::</span>stringstream<span
style="color:#000000;"> oSS;</span>

<span style="color:#000000;"><span class="Apple-tab-span"
style="white-space:pre;"> </span>oSS \<\< </span><span
style="color:#e82300;">"showstory\_"</span><span
style="color:#000000;">\<\<</span><span
style="color:#c35900;">DeviceModule</span><span
style="color:#000000;">::</span>sharedDeviceModule<span
style="color:#000000;">()-\></span>getAppVersion<span
style="color:#000000;">();</span>

<span style="color:#000000;"><span class="Apple-tab-span"
style="white-space:pre;"> </span></span><span
style="color:#c35900;">CCUserDefault</span><span
style="color:#000000;">::</span>sharedUserDefault<span
style="color:#000000;">()-\></span>setBoolForKey<span
style="color:#000000;">(oSS.</span>str<span
style="color:#000000;">().</span>c\_str<span style="color:#000000;">(),
</span><span style="color:#35568a;">true</span><span
style="color:#000000;">);</span>

<span style="color:#000000;"><span class="Apple-tab-span"
style="white-space:pre;"> </span></span><span
style="color:#c35900;">CCUserDefault</span><span
style="color:#000000;">::</span>sharedUserDefault<span
style="color:#000000;">()-\></span>flush<span
style="color:#000000;">();</span>

<span class="Apple-tab-span" style="white-space:pre;"> </span>

如果oSS为空,则flush会清空之前的xml文件。






