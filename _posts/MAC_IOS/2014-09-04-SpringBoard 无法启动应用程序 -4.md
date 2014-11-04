---
layout: post
title: SpringBoard 无法启动应用程序 -4
category: 书籍与软件工具
tags: mac／ios
keywords: 
description: 
---

build Phases-\>copy bundle resources的部分文件未包含进来

留意xcschememanagement.plist的配置中<span
style="line-height:1.2;">SuppressBuildableAutocreation</span><span
style="line-height:1.2;">是否有重复的，将重复的删掉。</span>

将build Phases-\>copy bundle resources中得info.plist文件不能包含进来






