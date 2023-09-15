---
layout: post
title: git push Server error goroutine 1
category: errors
tags: error-unresolved
keywords: git
description: 
---	


## Error

when executing `git push origin master`

```
git-lfs/1.2.0 (GitHub; windows amd64; go 1.6.1; git 386c5d8)
git version 2.8.3.windows.1

$ git-lfs pre-push origin http://192.168.1.6/DungeonAndFighter/ClientTest3.git
Server error: http://192.168.1.6/DungeonAndFighter/ClientTest3.git/gitlab-lfs/objects/e181440bc1197e5cd03818998a6a35730e50554bda1c3829c9d7704ec96656dd/486912
Server error: http://192.168.1.6/DungeonAndFighter/ClientTest3.git/gitlab-lfs/objects/d5d6b1c459c86ea9d8f29b3c822af71131f4bde894d352242146b3ffad838dd2/710144

Server error: http://192.168.1.6/DungeonAndFighter/ClientTest3.git/gitlab-lfs/objects/d5d6b1c459c86ea9d8f29b3c822af71131f4bde894d352242146b3ffad838dd2/710144
goroutine 1 [running]:
github.com/github/git-lfs/lfs.Stack(0x0, 0x0, 0x0)
	C:/Users/techn/go/src/github.com/github/git-lfs/lfs/errors.go:566 +0x87
github.com/github/git-lfs/commands.logPanicToWriter(0x1742c0, 0xc08224e038, 0x2f17df8, 0xc0824af4c0)
	C:/Users/techn/go/src/github.com/github/git-lfs/commands/commands.go:195 +0xf87
github.com/github/git-lfs/commands.logPanic(0x2f17df8, 0xc0824af4c0, 0x0, 0x0)
	C:/Users/techn/go/src/github.com/github/git-lfs/commands/commands.go:159 +0x419
github.com/github/git-lfs/commands.handlePanic(0x2f17df8, 0xc0824af4c0, 0x0, 0x0)
	C:/Users/techn/go/src/github.com/github/git-lfs/commands/commands.go:134 +0x55
github.com/github/git-lfs/commands.LoggedError(0x2f17df8, 0xc0824af4c0, 0xc082405ae0, 0x9d, 0x0, 0x0, 0x0)
	C:/Users/techn/go/src/github.com/github/git-lfs/commands/commands.go:84 +0x89
github.com/github/git-lfs/commands.upload(0xc08210c9a0, 0xc08238c000, 0x2, 0x2)
	C:/Users/techn/go/src/github.com/github/git-lfs/commands/uploader.go:143 +0xb9f
github.com/github/git-lfs/commands.prePushCommand(0xc52000, 0xc08210e720, 0x2, 0x2)
	C:/Users/techn/go/src/github.com/github/git-lfs/commands/command_pre_push.go:81 +0x64d
github.com/github/git-lfs/vendor/_nuts/github.com/spf13/cobra.(*Command).execute(0xc52000, 0xc08210e560, 0x2, 0x2, 0x0, 0x0)
	C:/Users/techn/go/src/github.com/github/git-lfs/vendor/_nuts/github.com/spf13/cobra/command.go:477 +0x3fb
github.com/github/git-lfs/vendor/_nuts/github.com/spf13/cobra.(*Command).Execute(0xc536c0, 0x0, 0x0)
	C:/Users/techn/go/src/github.com/github/git-lfs/vendor/_nuts/github.com/spf13/cobra/command.go:551 +0x593
github.com/github/git-lfs/commands.Run()
	C:/Users/techn/go/src/github.com/github/git-lfs/commands/commands.go:99 +0x2a
main.main()
	C:/Users/techn/go/src/github.com/github/git-lfs/git-lfs.go:34 +0x135

ENV:
LocalWorkingDir=E:\projects\DNF\ClientTest3
LocalGitDir=E:\projects\DNF\ClientTest3\.git
LocalGitStorageDir=E:\projects\DNF\ClientTest3\.git
LocalMediaDir=E:\projects\DNF\ClientTest3\.git\lfs\objects
LocalReferenceDir=
TempDir=E:\projects\DNF\ClientTest3\.git\lfs\tmp
ConcurrentTransfers=3
BatchTransfer=true
GIT_CONFIG_PARAMETERS='color.branch=false' 'color.diff=false' 'color.status=false' 'diff.mnemonicprefix=false' 'core.quotepath=false'
GIT_LFS_PATH=e:\Program Files\Git LFS
GIT_PAGER=cat
GIT_PREFIX=
```

## Solution

```
git lfs push origin master
git push origin master
```

## Reference

* 