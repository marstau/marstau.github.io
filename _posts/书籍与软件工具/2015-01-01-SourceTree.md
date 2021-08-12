---
layout: post
title: SourceTree
category: 书籍与软件工具
tags: software／tool
keywords: SourceTree,mac
description: 
---

#### checkout到历史版本
  
  双击
  
  ![](/Resources/SourceTree usage_1.png)
  
  此界面的指定行，即可。
  
#### 提交的时候使用右键->Add to Index速度比直接Check左上角速度更快(mac版)
#### 快捷键
**刷新** ⌘ + R

**提交记录浏览时抵至列表的最上面** ⌥ + ⌘ + ↑ 

#### push的提示标签不更新(显示1等数字)，手动pull一下即可。

#### stash

#### Repository->修改远程地址

本地保存

#### cherry->pick
将一个分支的提交更新到当前分支下


#### 跳过注册[More](https://www.cnblogs.com/lucio110/p/8192792.html)

创建`C:\Users\mars\AppData\Local\Atlassian\SourceTree\accounts.json`文件

```
[
  {
    "$id": "5",
    "$type": "SourceTree.Api.Host.Identity.Model.IdentityAccount, SourceTree.Api.Host.Identity",
    "Authenticate": true,
    "HostInstance": {
      "$id": "6",
      "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountInstance, SourceTree.Host.AtlassianAccount",
      "Host": {
        "$id": "7",
        "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountHost, SourceTree.Host.AtlassianAccount",
        "Id": "atlassian account"
      },
      "BaseUrl": "https://id.atlassian.com/"
    },
    "Credentials": {
      "$id": "8",
      "$type": "SourceTree.Model.BasicAuthCredentials, SourceTree.Api.Account",
      "Username": "taumars@hotmail.com",
      "Email": null
    },
    "IsDefault": false
  },
  {
    "$id": "9",
    "$type": "SourceTree.Model.ScmAccount, SourceTree.Api.Host.Scm",
    "Authenticate": true,
    "HostInstance": {
      "$id": "10",
      "$type": "SourceTree.Host.GitHub.GitHubInstance, SourceTree.Host.GitHub",
      "Host": {
        "$id": "11",
        "$type": "SourceTree.Host.GitHub.GitHubHost, SourceTree.Host.GitHub",
        "Id": "github"
      },
      "BaseUrl": "https://github.com/",
      "Protocol": "HTTPS"
    },
    "Credentials": {
      "$id": "12",
      "$type": "SourceTree.Model.BasicAuthCredentials, SourceTree.Api.Account",
      "Username": "taumars@hotmail.com",
      "Email": null
    },
    "IsDefault": true
  }
]
```

## ERROR

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


#### you may need to install the SVN::Core module[More](https://blog.meathill.com/perl/set-up-perl-on-new-mac.html)

```
brew install perl
sudo cpan install SVN::Core
```

#### `configuring SVN failed at inc/My/SVN/Builder.pm line 118, <STDIN> line 3 Something went wrong with the Subversion configuration`

使用
```
--with-apr=/usr/local/opt/apr --with-apr-util=/usr/local/opt/apr-util
```

而不是
```
/usr/local/opt/apr --with-apr-util=/usr/local/opt/apr-util
```

#### 提交失败,明明有密钥

SourceTree->选项->ssh客户端选择OpenSSH

## Reference



