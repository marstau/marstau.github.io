---
layout: post
title: apple store审核
category: 点滴知识
tags: 
keywords: 
description: 
---


## ERROR

#### 输入沙盒账号支付完成后,提示支付失败

可能沙盒账号配置地域有问题等

#### Apple审核机制（4.3）[More1](https://www.csdn.net/gather_2f/MtjaIg2sNTU1OC1ibG9n.html),[More2](https://blog.csdn.net/lyzz0612/article/details/80390362)

可行性方法一:
如果确认这个包不是马甲包,只是跟之前的包有什么区别，联系苹果说明清楚原因即可。

方法一：
* 资源文件路径修改

* 所有plist文件md5值修改
* 类前缀修改

这种情况基本要改源码，第一步：工程中的文件夹的名字全部进行修改。第二步：每一个工程都有一个类前缀, 我们需要取一个长一点的类前缀, 并且这个类前缀在你的整个工程一定是一个唯一的字符串, 我们假设这个类前缀是PayDayLoan, 现在我们需要生成一个控制器, 控制器的结尾Controller也需要用一个特定的字符去代替, 比如:Director,剩下的View以及object做法类似, 就不一一介绍了,做马甲的时候就是把这些名字用另一个唯一的字符去代替, 尽量长一点。第三步：把另一个其他的工程中的类全部导入进来, 主要是混淆代码, 在现有的工程中调用, 可以没有任何效果, 只是单纯调用方法。[More](https://www.jianshu.com/p/29507a331ff2)

1.出包必做二进制处理，加入废弃代码或者完全不同的废弃注，随便加入多个几M一个的无用文件，加入三五个并且放在苹果会检测的目录，让包体大小至少10M的差异
2.app加固混淆,字符串混淆,类名混淆,url编码加密,要用手动混淆，最好不要直接使用工具
3.打包的本地化图片的命名改掉，各个马甲的本地化图片命名不同
4.资源全部重加密,资源文件加密，资源文件修改名字，更改资源目录,尽量用虚拟机打包
5.增加一些空的方法和类，在不同的编译值下随机将他们编入,动态代码调用结构

* [More]()
方法二:

* 把所有资源打成加密zip包+xor加密，启动时再解压执行。这样苹果机审应该不可能扫出重复资源来[More](https://github.com/lyzz0612/iosMixTools)

#### `No .app bundles found in the package`[TEST More](https://www.shuzhiduo.com/A/MAzAnX4MJ9/)

#### 提交审核后后台一直没看到构建信息

可能是被打回来了要留意邮箱

## Reference

* [ZFJObsLib-iOS代码混淆工具-马甲包混淆工具（Python脚本混淆iOS工程）](https://zfj1128.blog.csdn.net/article/details/95482006)