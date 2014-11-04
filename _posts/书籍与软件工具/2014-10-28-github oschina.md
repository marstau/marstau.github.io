---
layout: post
title: github oschina
category: 书籍与软件工具
tags: software／tool
keywords: markdown
description: 
---

#[github](https://github.com/)
####difference among *master*, *HEAD* and *origin* 
* *master*: The name of the default branch that git creates for you when first creating a repo. In most cases, "master" means "the main branch". Most shops have everyone pushing to master, and master is considered the definitive view of the repo. But it's also common for release branches to be made off of master for releasing. Your local repo has its own master branch, that almost always follows the master of a remote repo.
* *HEAD*: The current commit your repo is on. Most of the time HEAD points to the latest commit in your branch, but that doesn't have to be the case. HEAD really just means "what is my repo currently pointing at". means not the lastest version, but the current version.
* *origin*: A name commonly given to the main remote. remote is another repository that you can pull from and push to. Usually it's on some server, like github.

####reset
* git reset --hard b61ed27
  
  reset head to b61ed27 version.
* jekyll serve

####gihub.io

* jekyll doesn't support `{ {` joining together.
* not support table

First Header | Second Header | Third Header
:----------- | :-----------: | -----------:
Left         | Center        | Right
Left         | Center        | Right
* jekyll not support 

```
  [^1] [^1]: desc
```

####clone specific branch

```
git clone -b [branch_name] --single-branch [url]
```
eg:

```
git clone -b 2 --single-branch https://git.oschina.net/marstau/testing.git
```

#[oschina](http://git.oschina.net/)

####不支持的命令

```
git submodule update --init --recursive
```
#windows下gitignore失效[更多参考](http://blog.lixiphp.com/gitignore-not-flush/#axzz3HvTN3dbF)

用命令行强制执行此命令,
eg:


```
git add ./filename
```

#查看ignore的文件

```
git config core.excludesfile
```

#Reference
* <http://stackoverflow.com/questions/4386959/difference-between-head-and-master>
* <http://stackoverflow.com/questions/8196544/what-are-the-git-concepts-of-head-master-origin>
