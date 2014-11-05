---
layout: post
title: batch command
category: 书籍与软件工具
tags: software／tool
keywords: windows,bat
description: 
---

**重命名**

```
rename %ToDir%\%FromDir%.vcxproj %ToDir%.vcxproj
```
**读取文件内容**

```
for /f %%a in ('type 1.txt') do echo %%readycopy
从1.txt中读取文件内容到readycopy中
// Caution: 例如文件中的内容为"abc def",则只能读到abc,默认空格为分隔符的
```
**set，定义变量**

```
set FileToBeCopied="Generic Algorithm"
set FromDir=%FileToBeCopied%
// Caution: 不能写为 FromDir = "Generic Algorithm"(中间赋值不能有空格)
```

**文件复制**

```
xcopy %FromDir%\*.* %ToDir%\*.*  /E /Y 
```

**暂停**

```
ping -n 30 127.1>nul

pause
```

**rd**

```
rd /s/q bzip2-1.0.5
```

**注释**

```
::注释

::rem的内容会被显示
rem 注释内容1

echo 注释内容1>nul
```

#Reference

* [Command-line reference](http://technet.microsoft.com/en-us/library/bb490890.aspx)



