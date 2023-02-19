---
layout: post
title: Failed to git submodule update --recursive --init
category: 编程开发
tags: error-unresolved
keywords: git,xcode
description: 
---
# Error

run git submodule update --init --recursive occurred error

Failed to git submodule update --recursive --init

# Solution

Run

    git submodule sync
    git submodule update --init

## Reference
* <https://github.com/karelia/ConnectionKit/issues/40>