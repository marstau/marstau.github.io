---
layout: post
title: provider： 共享内存提供程序, error： 0 管道的另一端上无任何进程 and sa登陆失败 错误：18456
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---
#Error
* 错误1: 共享内存提供程序, error： 0 管道的另一端上无任何进程
* 错误2: sa登陆失败 错误：18456


#Solution
第一个错误解决：

<span
style="color:#e53333;">首先选中服务器(右键)-\>属性-\>安全性-\>服务器身份验证修改为"SQL
SERVER和WINDOWS身份验证模式"</span>

<span
style="color:#e53333;">其次展开服务器上的"安全性"-\>登陆名-\>选中SA登陆帐号(右键)-\>状态-\>登陆修改为启用</span>

## 
第一个解决后可能还会出现如下错误:

1 windows身份登录数据库-》安全 -》登录名 双击sa 里面设置密码
点击左边菜单中的状态 登录选中“启动” 确定

2 关闭连接 用sa登录到数据库 成功

记住执行完第一步后要<span style="color:#e53333;">重启</span>才能登陆成功

