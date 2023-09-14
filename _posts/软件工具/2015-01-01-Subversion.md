---
layout: post
title: Subversion
category: 软件工具
tags: software
keywords: Subversion
description: 
---


## Installation[More](https://github.com/linode/docs/blob/master/docs/development/version-control/manage-source-code-versions-with-subversion/index.md),[More2](https://www.csoft.net/docs/svnserve.html)

```
yum install subversion # for CentOS
```


#### Creating the repositories

```
svnadmin create ~/my-repository
```

#### Tweaking `svnserve.conf`

Open up and edit the `svnserve.conf` file located in the `$HOME/my-repo/conf/` directory.

```
#
# Sample $HOME/my-repo/conf/svnserve.conf
#
[general]

# Path to the file containing svn users and passwords.
password-db = $HOME/my-repo/conf/passwd

# Authentication realm of the repository. Two repositories using the
# same password-db should have the same realm.
realm = My-test-repository

# Deny all anonymous access
anon-access = none

# Grant authenticated users read and write privileges
auth-access = write
```

#### Setting up password authentication

Open up and edit the `password-db` file (ie. `$HOME/my-repo/conf/passwd`). A sample entry might look like this:

```
[users]
user1 = password1
user2 = password2
```

#### Starting up the server


```
svnserve -d --listen-port 60003 --listen-host 127.0.0.1 -r /var/opt/svn-repository
svn co svn://127.0.0.1:60003
svn checkout svn+ssh://root@119.28.15.110:60003/svn-repository REPOS
@reboot svnserve -d --listen-host 96.47.74.x -r $HOME/my-repo
```

## ERROR

#### svnserve: E000099: Can't bind server socket: Cannot assign requested address

```
netstat -ntlp
kill -9 15358
```

#### svn: E200002: /var/opt/svn-rep/conf/svnserve.conf:39: Option expected

## Reference
