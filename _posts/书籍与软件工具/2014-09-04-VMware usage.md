---
layout: post
title: VMware usage
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---
#Linux

**安装VMware_Tools**

[root@localhost ~]# <span style="color:#F00;">cd /</span>

[root@localhost /]# <span style="color:#F00;">ls</span>

bin   dev home lost+found misc net proc sbin     srv tftpboot usr
boot etc lib   media       mnt   opt root selinux sys tmp       var
[root@localhost /]# cd /media
[root@localhost media]# ls
VMware Tools
[root@localhost media]# cd VMware\ Tools/
[root@localhost VMware Tools]# ls
manifest.txt VMwareTools- 8.1.3-203739.tar.gz
[root@localhost VMware Tools]# cp VMwareTools-8.1.3-203739.tar.gz    /tmp
[root@localhost VMware Tools]# cd /tmp
[root@localhost tmp]# ls
gconfd-root                                 scim-helper-manager-socket-root
keyring-lbbFvv                              scim-panel-socket:0-root
mapping-root                                scim-socket-frontend-root
orbit-root                                  ssh-FmnVlj2751
scim-bridge-0.3.0.lockfile-0@localhost:0.0 virtual-root.ZxmHUV
scim-bridge-0.3.0.socket-0@localhost:0.0    VMwareTools-8.1.3-203739.tar.gz
[root@localhost tmp]# tar -zxf VMwareTools-8.1.3-203739.tar.gz
[root@localhost tmp]# ls
gconfd-root                                 scim-panel-socket:0-root
keyring-lbbFvv                              scim-socket-frontend-root
mapping-root                                ssh-FmnVlj2751
orbit-root                                  virtual-root.ZxmHUV
scim-bridge-0.3.0.lockfile-0@localhost:0.0 VMwareTools-8.1.3-203739.tar.gz
scim-bridge-0.3.0.socket-0@localhost:0.0    vmware-tools-distrib
scim-helper-manager-socket-root
[root@localhost tmp]# cd vmware-tools-distrib/
[root@localhost vmware-tools-distrib]# ls
bin doc etc FILES INSTALL installer lib vmware-install.pl
[root@localhost vmware-tools-distrib]# ./vmware-install.pl
Creating a new VMware Tools installer database using the tar4 format.

Installing VMware Tools.

In which directory do you want to install the binary files?
[/usr/bin] yes  

The path "yes" is a relative path. Please enter an absolute path.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc/rc.d]

What is the directory that contains the init scripts?
[/etc/rc.d/init.d]

In which directory do you want to install the daemon files?
[/usr/sbin]

In which directory do you want to install the library files?
[/usr/lib/vmware-tools]

The path "/usr/lib/vmware-tools" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

yes  

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware-tools]
The path "yes" is a relative path. Please enter an absolute path.

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware-tools]
The path "/usr/share/doc/vmware-tools" does not exist currently. This program
is going to create it, including needed parent directories. Is this what you
want? [yes]
The installation of VMware Tools 8.1.3 build-203739 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want
this program to invoke the command for you now? [yes]

Stopping VMware Tools services in the virtual machine:
Guest operating system daemon:                          [确定]
Virtual Printing daemon:                                [确定]
Unmounting HGFS shares:                                 [确定]
Guest filesystem driver:                                [确定]

Found a compatible pre-built module for vmmemctl. Installing it...

Found a compatible pre-built module for vmhgfs. Installing it...

Found a compatible pre-built module for vmxnet. Installing it...

Found a compatible pre-built module for vmblock. Installing it...

[EXPERIMENTAL] The VMware FileSystem Sync Driver (vmsync) is a new feature that
creates backups of virtual machines. Please refer to the VMware Knowledge Base
for more details on this capability. Do you wish to enable this feature?
[no]

Found a compatible pre-built module for vmci. Installing it...

Found a compatible pre-built module for vsock. Installing it...

Found a compatible pre-built module for vmxnet3. Installing it...

Found a compatible pre-built module for pvscsi. Installing it...

Detected X.org version 7.1.

Host resolution detected as "1440 x 900".

Please choose one of the following display sizes that X will start with:

[1] "320x200"
[2] "320x240"
[3] "400x300"
[4] "512x384"
[5] "640x400"
[6] "640x480"
[7] "720x480"
[8] "800x480"
[9] "854x480"
[10] "720x576"
[11] "800x600"
[12] "1024x768"
[13] "1280x720"
[14] "1280x768"
[15] "1152x864"
[16] "1280x800"
[17]< "1366x768"
Please enter a number between 1 and 17:

[17] 12  


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.18-128.1.16.el5 i686 Red Hat, Inc.
Current Operating System: Linux localhost.localdomain 2.6.18-164.el5 #1 SMP Tue Aug 18 15:51:54 EDT 2009 i686
Build Date: 22 July 2009
Build ID: xorg-x11-server 1.1.1-48.67.el5
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/vmware-config0/XF86ConfigLog.16172", Time: Thu Apr 1 02:40:28 2010
(++) Using config file: "/tmp/vmware-config0/XF86Config.16172"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Multiple symbols for level 1/group 1 on key <I5F>
>                   Using XF86Sleep, ignoring XF86Standby
> Warning:          Symbol map for key <I5F> redefined
>                   Using last definition for conflicting fields
Errors from xkbcomp are not fatal to the X server

X is running fine with the new config file.

FreeFontPath: FPE "unix/:7100" refcount is 2, should be 1; fixing.
Creating a new initrd boot image for the kernel.
Starting VMware Tools services in the virtual machine:
Switching to guest configuration:                       [确定]
Paravirtual SCSI module:                                [确定]
Guest filesystem driver:                                [确定]
Mounting HGFS shares:                                   [失败]
Guest memory manager:                                   [确定]
Guest vmxnet fast network device:                       [确定]
VM communication interface:                             [确定]
VM communication interface socket family:               [确定]
Blocking file system:                                   [确定]
File system sync driver:                                [确定]
Guest operating system daemon:                          [确定]
Virtual Printing daemon:                                [确定]

The configuration of VMware Tools 8.1.3 build-203739 for Linux for this running
kernel completed successfully.

You must restart your X session before any mouse or graphics changes take
effect.

You can now run VMware Tools by invoking the following command:
"/usr/bin/vmware-toolbox" during an X server session.

To enable advanced X features (e.g., guest resolution fit, drag and drop, and
file and text copy/paste), you will need to do one (or more) of the following:
1. Manually start /usr/bin/vmware-user
2. Log out and log back into your desktop session; and,
3. Restart your X session.

To use the vmxnet driver, restart networking using the following commands:
/etc/init.d/network stop
rmmod pcnet32
rmmod vmxnet
modprobe vmxnet
/etc/init.d/network start

Enjoy,

--the VMware team

Found VMware Tools CDROM mounted at /media/VMware Tools. Ejecting device
/dev/hdc ...
[root@localhost vmware-tools-distrib]#

#Mac
#Windows








