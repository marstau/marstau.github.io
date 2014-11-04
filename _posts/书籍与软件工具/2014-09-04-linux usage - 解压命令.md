---
layout: post
title: linux usage - 解压命令
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---

-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tar**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解包：
    tar xvf FileName.tar</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">打包：tar
    cvf FileName.tar DirName</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">（注：tar是打包，不是压缩！）</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.gz**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压1：gunzip
    FileName.gz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压2：gzip -d
    FileName.gz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：gzip
    FileName</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tar.gz**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：tar
    zxvf FileName.tar.gz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：tar
    zcvf FileName.tar.gz DirName</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.bz2**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压1：bzip2 -d
    FileName.bz2</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压2：bunzip2
    FileName.bz2</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：
    bzip2 -z FileName</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：
    bzip2 FileName</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tar.bz2**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：tar
    jxvf FileName.tar.bz2</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：tar
    jcvf FileName.tar.bz2 DirName</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">bzip2
    a.bz2 file1 file2 file3 /etc</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">把文件file1file2file3及/etc下的内容压缩起来，放入a.bz2文件中。</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.bz**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压1：bzip2 -d
    FileName.bz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压2：bunzip2
    FileName.bz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：未知</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tar.bz**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：tar
    jxvf FileName.tar.bz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：未知</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.Z**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：uncompress
    FileName.Z</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：compress
    FileName</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tar.Z**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：tar
    Zxvf FileName.tar.Z</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：tar
    Zcvf FileName.tar.Z DirName</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tgz**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：tar
    zxvf FileName.tgz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：未知</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tar.tgz**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：tar
    zxvf FileName.tar.tgz</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：tar
    zcvf FileName.tar.tgz FileName</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.zip**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：unzip
    FileName.zip</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：zip
    FileName.zip DirName</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.rar**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：rar
    e FileName.rar</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：rar
    a FileName.rar</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">rar请到：</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压后请将cp
    rar /usr/bin</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.lha**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：lha -e
    FileName.lha</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：lha -a
    FileName.lha FileName</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">lha请到：</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">\>解压后请将lha拷贝到/usr/bin目录（其他由\$PATH环境变量指定的目录也可以）：</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">[root@www2
    tmp]\# cp lha /usr/bin/</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.rpm**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解包：rpm2cpio
    FileName.rpm | cpio -div</span>
-   <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span><span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">**.tar
    .tgz .tar.gz .tar.Z .tar.bz .tar.bz2 .zip .cpio .rpm .deb .slp .arj
    .rar .ace .lha .lzh .lzx .lzs .arc .sda .sfx .lnx .zoo .cab .kar
    .cpt .pit .sit .sea**</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压：sEx
    x FileName.\*</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">压缩：sEx
    a FileName.\* FileName</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">sEx只是调用相关程序，本身并无压缩、解压功能，请注意！</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">sEx请到：</span>\
     <span
    style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px 宋体, Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">解压后请将sEx拷贝到/usr/bin目录（其他由\$PATH环境变量指定的目录也可以）：</span>









