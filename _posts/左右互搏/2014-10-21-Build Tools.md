---
layout: post
title: Build Tools
category: 左右互搏
tags: software／tool
keywords:
description: 
---

## SCons
## make
This is the standard against which all other build systems are currently compared.
## GNU Autotools
GNU Autotools extends GNU Make with a larger library of default build rules, plus extensive dependency checking capability. It knows how to compile software (executables, shared libraries, plus documentation, etc) for a large number of targets, which is something that rapidly becomes tedious when using plain Makefiles.

## CMake
When compared to scons, CMake is :

* Faster
* Requires less code for common tasks
* Arguably more stable
* Supports outputting to projects like Code::Blocks, Xcode, etc. which scons does not.

But :

* Uses its own language, reinventing the wheel and not providing access to the extensibility and power of a real language.
* Arguably not as extensible as scons.
* For terminal builds, still requires the use of 'make' (which, depending on your point of view, may or may not be a disadvantage) while scons is self-contained, all-in-one.

To sum up, my very subjective opinion is that scons is a better idea, but CMake has a stronger implementation.

## Makeit
## Jam
## qmake
## A-A-P
## Ant
## Maven
## TWW tools from TWW Inc.
## Rake
## Rant
## Makepp
## Waf
## KConfig
## Other comparisons

## Reference

* <http://www.scons.org/wiki/SconsVsOtherBuildTools>