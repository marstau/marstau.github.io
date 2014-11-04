---
layout: post
title: linux usage - 新建用户
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---

<span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">建立一个新用户\
\
 </span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">　　修改用户的个人设置</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">文件目录的权限设置</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">两个重要文件：</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">passwd与group</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">建立一个新用户</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">建立一个新的用户包括两个步骤，第一步是使用useradd命令完成一个新用户的初始化设置工作；第二步是用passwd为这个新用户设置密码。例如，我们要给</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"
href="http://hi.baidu.com/hengcheng/blog/item/tag.php?name=%CF%B5%CD%B3">系统</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">添加一个用户叫floatboat，密码为fan2001z，那相关的操作是：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">useradd
floatboat \<回车\></span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">这时候系统没有任何显示。接着：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">passwd
floatboat \<回车\></span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">系统显示：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Changing
password for user floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">New
UNIX password:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">你输入：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">fan2001z\<回车\></span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">注意，由于linux并不采用类似windows的密码回显(显示为\*号)——为避免你输入密码时被人注意到有多少位——所以，输入的这些字符你是看不见的。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">系统显示：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Retype
new UNIX password:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">你再重新输入一次密码，然后回车确认，这时系统会显示：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">passwd:all
authentication tokens updated successfully</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">表示你修改密码成功了。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">到这里，新用户的创建工作就算完成了。下面，我们再补充一些有关增加新用户的常识：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1、useradd所做的初始化操作已经包括在/home目录下为floatboat帐号建立一个名为floatboat的主目录。如果你不想使用这个缺省的目录，而</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">希望把他的主目录放在/home/goal里</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">(还放在/home下，只是一种良好的习惯，没有其他什么特别的要求)，可以使用</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">useradd的参数-d</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，命令如下：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">useradd -d
/home/goal floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">2、useradd的初始化操作还包括为用户单独建立一个与用户名同名的组(floatboat组)。这叫用户私有组的机制，与默认组机制相对应。对用户分组一是方便管理，二是可以明确权限。复杂的我们将在以后的深入内容中探讨。</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">我们如果想让此用户加入一个已有的组的话，可以使用-g参数。例如我们想让floatboat加入webusers组</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，那么可以使用以下命令：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">useradd -g
webusers floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">同样的，我们还可以使用-G参数使他同时加入多个组，例如webusers和ftpusers：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">useradd -G
ftpusers,webusers floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">3、passwd命令为一个用户设置密码，但它实质上是一个修改密码的程序。只有超级用户和用户自己可以修改密码，其它的普通用户没有给他修改密码的
权利。用户密码的组成要尽量的复杂，最好包括字母、数字和特殊符号，而且最好设成6位以上。太短passwd程序不允许，只是单纯的字母或单纯的数
字，passwd也会有意见。你都会看见passwd出现的提示的，不要害怕，仔细看看到底它是怎么说的：)</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">4、你在增加一个新用户的时候，</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">也可以设置用户登录的shell</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">。缺省的，系统提供了/bin/bash。你如果非要指定的话，可以使用-s参数就可以了。例如</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">useradd -d
/www -s /usr/bin/passwd floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">注意，这些参数是可以一块使用的，如上例所示，它表示增加新用户，并把其主目录路径设置在/www，登录的shell为/usr/bin/passwd。关于shell的更详细的说明，请参考下面的修改用户的个人设置相关内容。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">5、</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">删除一个用户可以使用userdel命令</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，直接带用户名做参数就可以了。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改用户的设置</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">对现有用户的修改，比较常用的主要是修改密码(使用passwd就好了)，修改用户的登录shell，修改用户所属的默认组，设置帐号有效期，修改用户的说明信息等等，偶尔也会用到修改用户主目录。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">　修改用户的登录shell</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">使用chsh命令可以修改自己的shell，只有超级用户才能用chsh
username为其它用户修改shell设置。注意，指定的shell必须是列入/etc/shells文件中的shell，否则该用户将不能登陆。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">一般，比较常见的shells文件包括下面这些shell：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">/bin/bash2</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">/bin/bash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">/bin/sh</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">/bin/ash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">/bin/bsh</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">/bin/tcsh</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">/bin/csh</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">而网管们还喜欢在里面加上/usr/bin/passwd，这是为了不然用户通过控制台或telnet登录系统，却可以使用修改帐户密码(比如在FTP里
用)。以及/bin/false，也就是不让这个用户登录的意思喽\^&\^，连FTP也不能用。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">你也可以使用</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod命令修改shell信息</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，如下所示：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -s
/bin/bash floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">其中/bin/bash和floatboat应取相应的shell路径文件名及用户名。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">还有一种情况，就是你为用户设置了一个空的shell(就是"")，也就是说，这个用户没有shell。呵呵，绝对没有在我还未曾见过，因为这种用户登录后，系统还是会给它一个shell用的。不信你试试：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -s
"" floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">这种用户根据系统的不同，会有一个sh或bash进行操作，我也没有看出功能上和其它普通用户登录有什么不同。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改用户所属的默认组\
 </span>\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">这个功能也可以通过usermod命令来实现，使用-g参数，例如把floatboat的默认组改为nobody，可以使用如下命令：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -g
nobody floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">nobody在类UNIX系统中一般都意味着没有任何权限。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">设置帐号有效期</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">如果使用了影子口令，则可以使用如下命令来修改一个帐号的有效期：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -e
MM/DD/YY username</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">例如把用户floatboat的有效期定为2001年12月31日：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -e
12/31/01 floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">如果把该用户的有效期设为已经过去的时间，就可以暂时禁止该用户登录系统。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改用户的说明信息</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改用户的说明信息，最简单的方法莫过于直接修改/etc/passwd文件，找到对应的用户记录行，例如下列行：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">floatboat:x:503:503::/home/floatboat:/bin/bash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">你可以直接在第四个冒号和第五个冒号之间插入该用户的说明就可以了。其实，很多用户设置都可以在这修改，比如该行最后一部分/bin/bash就是用户登录shell的设置。关于这个/etc/passwd文件，我们后面将进一步的深入探讨。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改用户主目录</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改用户的主目录主要使用usermod命令的</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#f4a460;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">-d参数</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，例如：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -d
/www floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">这一行将floatboat的主目录改到/www。如果想将现有主目录的主要内容转移到新的目录，应该使用-m开关，如下所示：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -d -m
/www floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">文件目录的权限</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">linux下，每一个文件、每一个目录都有一个属主，并针对用户自己、用户所在组、其它所有帐号(组)分别设定读、写、执行三种权限。例如，我(假定是webusers组的floatboat帐户的拥有者)使用如下命令建立一个新的文件</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">touch</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
class="Apple-converted-space"> </span></span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">mytestfile\
 </span>\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">然后我们使用ls -l
mytestfile这一命令来查看这个文件的权限状态(关于ls命令，可以查阅本站的命令查询)，可以得到如下的屏幕输出显示：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">-rw-rw-r--
1 floatboat webusers 0 Feb 6 21:37 mytestfile</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">输出由空格分为9个部分，我们比较关心第一、三、四个字段，分别表示文件权限属性、文件所有者帐户、文件所属组。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">◆</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">使用chown命令修改文件的主人\
 </span>\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">当你新建立一个文件的时候，文件的所有者当然就是你了。这一事实只有超级用户(比如说root)才可以通过chown命令改变(例如chown
otheruser
mytestfile,把mytestfile文件的属主改为otheruser)。普通用户不能把自己的文件“送”给别人，不然你把有特殊目的的程序给
了root怎么办？：)</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chown命令的用法比较简单。这里我先假设你现在拥有超级用户权限，那么你就可以使用如下命令将一个文件“送给”floatboat了：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chown
floatboat
/home/floatboat/thefileisrootcreate.txt(假定该文件是由root创建的)</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改一个目录的所有者也是类似的：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chown
floatboat /home/newboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">当然，如</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">果这个目录还有子目录及文件需要同时送给floatboat，chown也是支持-R参数的</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chown -R
floatboat /home/newboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">如果你同时想修改文件/目录所属的组的话，你可以使用以下命令方便的达到目的：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chown -R<span
class="Apple-converted-space"> </span></span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff8c00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">floatboat.ftpusers</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
class="Apple-converted-space"> </span>/home/newboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">这样，不但文件主人得到了修改，文件所属的组也变成了ftpusers</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">◆</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">修改文件的组属性\
 </span>\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">文件所属组你倒是可以改变，前提是：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">　1、</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">你的超级用户。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">2</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">、你同时属于两个或两个以上的组。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">两个条件你至少具备一个，你才能够把文件所属旧组变为新组。使用如下的命令将当前目录下所有html文件所属的组改为httpd：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chgrp
httpd \*.html</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">和</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chown命令一样，chgrp也可以使用-R参数对一个目录内的所有文件和子目录进行递归的修改组属性</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">\<提示\>：你可以使用不带参数的</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
style="color:#ff0000;">groups</span>命令查看自己属于哪个组</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">文件权限的设定是我们这一小节讨论的核心，我们主要介绍chmod命令的两种用法。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">◆使用访问字符串设置文件目录权限</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">正如前面所说的，每一个文件、目录都针对用户自己、用户所在组、其它所有帐号(组)分别有读、写、执行三种权限及其组合。当一个普通用户新建一个文件
的时候，它默认的访问权限显示就如我们刚才所举例子的第一个字段所示。总共十位字符“-rw-rw-r--”，第一位是目录区分标志，如果是d的话，表示
这是一个目录。第二到四位分别表示文件所有者的读(r：read)、写(w:write)、执行(x:execute)属性，第五到七位是文件所属组的
读、写、执行权限，第八到第十位则是其它用户的读、写、执行权限。如果对应的位是相应的字母，就是有这相应权限，否则为“-”，表示没有获得这个许可。象
刚才例子中的文件就是自己可读写，本组可读写，其它用户可读，所有的用户(包括自己)都不能执行它。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">我们的用</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">u、</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#00ff00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">g、</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">o</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">分别来指代用户</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff00ff;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">(user)、</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#00ff00;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">组(group)、</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">其它帐户(other)，</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">就可以方便的设置文件和目录的权限了。当然，我们也可以用</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
style="color:#ff00ff;">a</span>来表示所有的这三项</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">例如，我们要对所有perl的脚本文件设定权限，对所有用户都可以读和执行，文件所有者还允许写许可，那么我们可以使用如下命令：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chmod
a+rx,u+w \*.pl</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">注意：</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">如果要使用多个访问字符串，它们之间要用<span
style="color:#ff00ff;">逗号</span>隔开</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">，各个许可字符串之间</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">不允许有空格</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">。正如上例所示。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">如果要修改目录中所有文件和子目录的权限属性，可以使用chmod提供的-R参数来递归修改。例如，下列命令将/www/site1目录及其下面的子目录的权限属性设定为所有者和组可读、写、执行，其它用户不可访问：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chmod -R
a+rwx,o-rwd /www/site1</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">注意，不要轻易使用-R选项，这可能会带来安全隐患。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">使用字符串方便了理解，单输入那么多字母还是有点累，如果你对8进制有些概念的话，可以使用下面介绍的方法来做权限设置。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">◆使用八进制数设置文件目录权限</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">我们知道，在ls -l的输出中，文件权限表示为“-rw-rw-r--”，前一位只和是否为目录有关，其它九位正好可以分成三段，每段三位，“rw-”、“rw-”和
“r--”,“-”代表无效“0”，其它字符代表有效“1”，那么这个文件的权限就是“110”、“110”、“100”，把这个2进制串转换成对应的8
进制数就是6、6、4，也就是说该文件的权限为664(三位八进制数)。我们也可以使用类似这种三位八进制数来设定文件授权，如上边两个例子，就也可以写
为：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chmod
755 \*.pl</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">chmod -R
770 /www/site1</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">是不是很简洁？关键在于你能根据你需要设定的权限正确的选择八进制数(利用八进制数的二进制表示可以非常轻易的做到这一点)。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">◆</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">读、写、执行的权限说明\
 </span>\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">1、所谓写的权限，也就是对文件修改和删除的权限。如果目录的写权限也对你开放了，则可以创建、删除或修改该目录下的任何文件或自目录——即使该文件和子目录并不属于你。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">2、对目录有只读许可的用户，不能用cd命令进入该目录；还必须同时有执行许可才可以进入该目录。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">3、必须同时拥有读和执行权限才可以使用ls这样的程序列出目录内容清单。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">4、只对目录有执行权限的用户，想访问该目录下的文件有读权限的文件，必须知道该文件名才可以访问。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">两个重要文件：passwd与group</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">在linux的安全机制里，/etc/passwd与/etc/group这两个文件占着非常重要的地位。它们控制着linux的用户和组一些重要设置。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">◆/etc/passwd文件说明</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">下面是一个RHlinux里普通的passwd文件的例子：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">root:x:0:0:root:/root:/bin/bash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">bin:x:1:1:bin:/bin:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">daemon:x:2:2:daemon:/sbin:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">……</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">operator:x:11:0</span>![](http://images.5d6d.net/dz60/smilies/default/shocked.gif)<span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">perator:/root:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">games:x:12:100:games:/usr/games:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">gopher:x:13:30:gopher:/usr/lib/gopher-data:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">ftp:x:14:50:FTP
User:/home/ftp:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">nobody:x:99:99:Nobody:/:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">xfs:x:43:43:X
Font Server:/etc/X11/fs:/bin/false</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">named:x:25:25:Named:/var/named:/bin/false</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">postgres:x:26:26</span>![](http://images.5d6d.net/dz60/smilies/default/tongue.gif)<span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">ostgreSQL
Server:/var/lib/pgsql:/bin/bash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">lanf:x:500:500::/home/hujm:/bin/bash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">mysql:x:101:101:MySQL
server:/var/lib/mysql:/bin/bash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">imnotroot:x:0:0::/home/imnotroot:/bin/bash</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">在这个文件里只有一个普通帐号lanf。其它都是系统或系统服务的进程需要的帐号，包括我们非常熟悉的root这个超级用户。在passwd的文件里，每一行被冒号(":")分成7个部分，分别是：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">[用户名]：[密码]：[UID]：[GID]：[身份描述]：[主目录]：[登录shell]\
 </span>\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">其中：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">⒈[用户名]是passwd文件里各记录行唯一的有"唯一性"要求的域。也就是说每一行的第一个区域的内容都不能相同，其它区域就无所谓了。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">⒉[密码]区域在以前，保存着一个经过不可逆的哈希算法进行DES加密的13位字符，但不包括单引号和冒号。这13位字符中，前两位是密钥，在加密的
时候随机生成的。由于这个字符串不包括单引号，所以以前有一种不修改密码又禁止用户登录的方式就是在密码前面加一个单引号。值得注意的是，现在由于使用了
shadow口令，在密码区域只有一个x字符。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">⒊[UID]虽然是系统用来标志文件归属，确定各种权限的标志，但这个区域的内容并不要求唯一的。比较常见而又与安全问题相关的一个例子是有多个
UID和GID均为0的用户帐号。注意到在该文件最后一行还有一个UID和GID为0的用户imnotroot，虽然它声称自己不是root，但是它却有
和root完全相同的权限，因为系统并非根据[用户名]，而是根据UID和GID来分用户的权力的。所以，这种情况无疑为系统埋下了安全的炸弹。但是，当
imnorroot做锁定屏幕等操作的时候，如果它的密码和root的不一样，它将无法解锁，因为系统只是查到第一个UID为0的用户(自然是root)
后，就不在往下查找了——它当UID也是唯一的。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">⒋[GID]用户默认的组ID，这个ID可以在文件/etc/group里查到对应的组名。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">⒌[身份描述]：就是用户的身份说明，默认的是无任何说明，可人工添加。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">⒍[主目录]：用户的主目录，可以使用前面介绍的命令修改。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">⒎[登录shell]：用户登录时系统提供的shell，请参考前面的有关内容。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">\<注意</span><span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#8b0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">\>：[UID]和[GID]小于500的一般都是系统自己保留，</span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">不做普通用户和组的标识的，所以新增加的用户和组一般都是UID和GID大于500的。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">◆/etc/group文件说明</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">下面是RH的一个group文件的例子：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">root:x:0:root,hujm,hjm</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">bin:x:1:root,bin,daemon</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">daemon:x:2:root,bin,daemon</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">sys:x:3:root,bin,adm</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">adm:x:4:root,adm,daemon</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">tty:x:5:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">disk:x:6:root</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">lp:x:7:daemon,lp</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">mem:x:8:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">kmem:x:9:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">wheel:x:10:root</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">mail:x:12:mail</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">news:x:13:news</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">uucp:x:14:uucp</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">……</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">hujm:x:503:root,mynoshell,hjm</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">mysql:x:101:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">mynoshell:x:505:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">ftpusers:x:506:</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">它总共分四个部分：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#ff0000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">[组名]：[密码域]：[GID]：[组员列表]</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">意思非常明显，需要说明一下的是，由于组一般都不用密码保护，所以虽然看起来密码域有个X字符，其实那只表示使用了SHADOW(对应文件为
gshadow)。组员列表用逗号分隔各个帐号。另外，一个组的组员如果默认登录组就是它的话，那么在组员列表里将不显示这个组员的帐号，例如用如下命令
增加的用户：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">useradd -g
ftpusers floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">在/etc/group文件里ftpusers的组员列表将不显示这个组员(真是失败)，而只是在passwd文件中的GID被设置为506。而使用如下命令：</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">usermod -G
ftpusers,mysql,webusers floatboat</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">就可以看见相关的组后边加上了floatboat帐号。当然，你可以直接用vi来直接编辑这个文件。</span>\
\
 <span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">group文件和passwd文件是通过GID联系在一起的，这有点象关系数据库。根据passwd文件中一个帐户的GID，可以在group文件中
找到对应的组名。如果采用了用户私有组机制的话，那么一般新增一个帐号，就会有对应的一个与帐号同名的组增加到group文件中。虽然这时passwd文
件中具有唯一性的[用户名]字段和group文件中具有唯一性的[组名]字段一样，并不代表着它们是通过这两个字段形成一一对应的关系的。千万别忘记，系
统对数字(UID，GID)更加敏感\^\_\^。</span>








