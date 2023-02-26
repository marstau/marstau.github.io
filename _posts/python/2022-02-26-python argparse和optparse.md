---
layout: post
title: python argparse和optparse
category: 编程开发
tags: python
keywords: 
description: 
---


#### 推荐使用argparse

argparse和optparse都是Python中用于解析命令行参数的库。

optparse是Python 2.7及之前版本的标准库，而argparse则是Python 2.7及之后版本的标准库，被推荐作为命令行参数解析的标准库。

相比于optparse，argparse提供了更加灵活的命令行参数解析方式，支持互斥参数、子命令、类型检查等更多的功能。同时，argparse的文档和用法更加清晰易懂，而且在Python社区中得到了更广泛的支持。

在使用上，argparse和optparse的主要差别在于API的不同。如果您需要兼容Python 2.7及之前的版本，可以选择使用optparse。如果您的Python版本高于2.7，建议使用argparse。

## Reference

