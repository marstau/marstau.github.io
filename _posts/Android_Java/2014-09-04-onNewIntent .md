---
layout: post
title: onNewIntent 
category: 游戏技术
tags: android／java
keywords: 
description: 
---

#### <span class="normal" style="font-weight:normal;">protected void<span class="Apple-converted-space"> </span></span><span class="sympad" style="margin-right:2px;">onNewIntent</span><span class="Apple-converted-space"> </span><span class="normal" style="font-weight:normal;">([Intent](http://developer.android.com/reference/android/content/Intent.html)<span class="Apple-converted-space"> </span>intent)</span> {.jd-details-title style="padding-right:95px;padding-left:3px;font-size:1.15em;padding-bottom:3px;margin:1.5em 0px 0.6em;word-spacing:0px;text-transform:none;color:#333333;text-indent:0px;line-height:20px;padding-top:3px;font-style:normal;font-family:Roboto, sans-serif;white-space:normal;letter-spacing:normal;background-color:#e2e2e2;font-variant:normal;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;"}

<div class="api-level"
style="padding-right:8px;margin-top:-30px;padding-left:8px;float:right;padding-bottom:0px;word-spacing:0px;font:0.8em/19px Roboto, sans-serif;text-transform:none;color:#999999;text-indent:0px;padding-top:0px;white-space:normal;letter-spacing:normal;background-color:#f9f9f9;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">

<div>

Added in<span class="Apple-converted-space"> </span>[API level
1](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html#ApiLevels)

</div>

</div>

<div class="jd-details-descr"
style="padding-right:0px;padding-left:0px;padding-bottom:0px;margin:0.5em 0.25em;word-spacing:0px;font:14px/19px Roboto, sans-serif;text-transform:none;color:#222222;text-indent:0px;padding-top:0px;white-space:normal;letter-spacing:normal;background-color:#f9f9f9;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">

<div class="jd-tagdata jd-tagdescr" style="margin:0.25em 0px 0.75em;">

This is called for activities that set launchMode to "singleTop" in
their package, or if a client used the<span
class="Apple-converted-space"> </span>`FLAG_ACTIVITY_SINGLE_TOP`{style="font:bold 14px/1.5 'courier new', courier, monospace;color:#006600;"}<span
class="Apple-converted-space"> </span>flag when calling<span
class="Apple-converted-space"> </span>`startActivity(Intent)`{style="font:bold 14px/1.5 'courier new', courier, monospace;color:#006600;"}.
In either case, when the activity is re-launched while at the top of the
activity stack instead of a new instance of the activity being started,
onNewIntent() will be called on the existing instance with the Intent
that was used to re-launch it.

An activity will alw chmod ays be paused before receiving a new intent,
so you can count
on `onResume()`{style="font-weight:bold;line-height:1.5;font-family:'courier new', courier, monospace;color:#006600;"} being
called after this method.

Note that<span
class="Apple-converted-space"> </span>`getIntent()`{style="font:bold 14px/1.5 'courier new', courier, monospace;color:#006600;"}<span
class="Apple-converted-space"> </span>still returns the original Intent.
You can use<span
class="Apple-converted-space"> </span>`setIntent(Intent)`{style="font:bold 14px/1.5 'courier new', courier, monospace;color:#006600;"}<span
class="Apple-converted-space"> </span>to update it to this new Intent.

**References:**

<http://developer.android.com/reference/android/app/Activity.html#onNewIntent(android.content.Intent)>
 

</div>

</div>







