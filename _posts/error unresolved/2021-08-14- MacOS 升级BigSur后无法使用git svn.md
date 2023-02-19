---
layout: post
title:  MacOS 升级BigSur后无法使用git svn
category: 编程开发
tags: error-unresolved mac
keywords: 
description: 
---


## Error


#### `git: 'svn' is not a git command`

#### run `brew install subversion` prompt `We do not provide support for this pre-release version.`

```
brew update
```

#### TODO git svn 在mac上使用报错[More](http://comdyn.hy.tsinghua.edu.cn/from-web/server/589-git-svn-%E9%94%99%E8%AF%AF-%E2%80%9Ccan-t-locate-svn-core-pm-in-inc%E2%80%9D-%E7%9A%84%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88)

```
Can't locate SVN/Core.pm in @INC
```


#### `Can't locate Git/SVN.pm in @INC (you may need to install the Git::SVN module)`[More](https://github.wangkaimin.com/2018/09/05/git-svn-mac-error.html)

mac下,SourceTree管理svn,拉取报错。
```
Can't locate Git/SVN.pm in @INC (you may need to install the Git::SVN module)

BEGIN failed--compilation aborted at
/Applications/Sourcetree.app/Contents/Resources/git_local/libexec/git-core/git-svn line 21.
```

10.13.x Solution:
```
sudo cpan Git::SVN
sudo ln -s /Applications/Xcode.app/Contents/Developer/Library/Perl/5.18/darwin-thread-multi-2level/SVN/ /Library/Perl/5.18/SVN 
sudo mkdir /Library/Perl/5.18/auto
sudo ln -s /Applications/Xcode.app/Contents/Developer/Library/Perl/5.18/darwin-thread-multi-2level/auto/SVN/ /Library/Perl/5.18/auto/SVN
```


10.15.4 Solution:[More](https://blog.meathill.com/perl/set-up-perl-on-new-mac.html)
```
sudo cpan install YAML
sudo cpan install SVN::Core
--with-apr=/usr/local/opt/apr --with-apr-util=/usr/local/opt/apr-util
```


cpan install自动commit导致无法输入配置,直接在`~/.cpan/xxx`目录下修改build.PL

```
$configure_args = $configure_args.'--with-apr=/usr/local/opt/apr --with-apr-util=/usr/local/opt/apr-util';
然后在安装当前目录sudo cpan install .
```

## Reference

* <https://blog.csdn.net/weixin_42703602/article/details/113358569?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-13.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-13.control>