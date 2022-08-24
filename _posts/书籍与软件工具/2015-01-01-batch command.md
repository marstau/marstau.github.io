---
layout: post
title: batch command
category: 书籍与软件工具
tags: software／tool
keywords: windows,bat
description: 
---

## 命令

```
rd /s/q bzip2-1.0.5 # 删除整个目录
rename %ToDir%\%FromDir%.vcxproj %ToDir%.vcxproj #重命名
```

### 读取文件内容

```
for /f %%a in ('type 1.txt') do echo %%readycopy
从1.txt中读取文件内容到readycopy中
// Caution: 例如文件中的内容为"abc def",则只能读到abc,默认空格为分隔符的
```

### set，定义变量

```
set FileToBeCopied="Generic Algorithm"
set FromDir=%FileToBeCopied%
// Caution: 不能写为 FromDir = "Generic Algorithm"(中间赋值不能有空格)
```

### 文件复制

```
xcopy %FromDir%\*.* %ToDir%\*.*  /E /Y (提示出错?)

copy /Y %FromDir%\*.* %ToDir%\*.*
```

### 暂停

```
ping -n 30 127.1>nul
pause
```

### 复合语句中使用输入[More](https://zhidao.baidu.com/question/744717720920092492.html)

```
setlocal EnableDelayedExpansion

if %a%==12 (
	set /p c=请输入:
	echo !c!
)
```

### 注释

```
::注释内容

::rem的内容会被显示
rem 注释内容

echo 注释内容>nul
```

### 判断某个命令在cmd中是否可用

```
WHERE git
IF %ERRORLEVEL% NEQ 0 (echo git wasn't found) else (echo git found.)
```

### errorlevel[More](http://www.cnblogs.com/SunShineYPH/archive/2011/12/13/2285570.html)

很多DOS程序在运行结束后会返回一个数字值用来表示程序运行的结果(或者状态)，称为错误码errorlevel或称返回码。

常见的返回码为0、1。通过if errorlevel命令可以判断程序的返回值，根据不同的返回值来决定执行不同的命令。

**函数调用**[More](http://blog.sina.com.cn/s/blog_58f9df5e0101efdv.html)

使用exit /b或goto :eof来退出调用。使用%0表示函数名，%1、%2等表示参数。

批处理函数使用call来调用，标签前面必须有:，以和批处理脚本区分。

```
@echo off
call :function1 h g
call :function2 x y
exit /b 0
:function1
echo %1
echo %2
echo %0
exit /b 0
:function2
echo %1
echo %2
echo %0
goto :eof
```

### 打开windows exploerer

```
start explorer %UserProfile%\AppData\LocalLow\
```

### 路径

```
@echo off

echo 当前盘符：%~d0
echo 当前盘符和路径：%~dp0
echo 当前批处理全路径：%~f0
echo 当前盘符和路径的短文件名格式：%~sdp0
::以管理员身份运行的时候,%cd%为C:\Windows\system32
echo 当前CMD默认目录：%cd%
echo 目录中有空格也可以加入""避免找不到路径


output:
当前盘符：C:
当前盘符和路径：C:\Users\mars\Desktop\
当前批处理全路径：C:\Users\mars\Desktop\test.bat
当前盘符和路径的短文件名格式：C:\Users\mars\Desktop\
当前CMD默认目录：C:\Users\mars\Desktop
目录中有空格也可以加入""避免找不到路径
```

### 设置环境变量

```
setx JAVA_HOME "C:\Program Files\LightenBSM Server\jdk1.6.0_16"
```

### 获取文件路径

```
:FetchParentPath
for /f "tokens=1,2* delims=\" %%a in (%1) do (
	if "%%c" NEQ "" (
		if %parentPath% NEQ "" (set parentPath=%parentPath%\%%a) else (set parentPath=%%a)
		call :FetchParentPath "%%b\%%c"
	)
)
exit /b 0

```

### 同时运行多个bat

```
start "" cmd /k call ../test.bat
```

### 去掉字符串变量的引号[More](http://blog.sina.com.cn/s/blog_4ad042e50100p7zx.html)

```
1. 若为命令行参数 %1 => %~1
2. 若为for替代变量 %%i => %%~i
3. 若为环境变量 %var% => %var:"=%
```

#### 字符串比较

```
if "%tag%" equ "str" (
)
```

## Reference

* [Command-line reference](http://technet.microsoft.com/en-us/library/bb490890.aspx)

* [字符串操作](http://www.dostips.com/DtTipsStringManipulation.php#Snippets.Replace)

