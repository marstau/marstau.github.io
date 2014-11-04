---
layout: post
title: android assets常见问题
category: 游戏技术
tags: android／java
keywords: 
description: 
---

 

我们知道在res目录下可以存放资源文件外，在assets目录下也可以存放这些资源文件，注意一点是assets目录下的资源文件是不会在R.java文件中动生成ID号的，使用assets目录下的文件必须指定文件的路径。那我们该如何选择放置资源呢？walfred总结几点区别，知道了这些区别就好灵活放置自己的资源了： 

1、res目录下的文件会自动生成ID号，所以替换资源时不会影响代码。

2、assets目录下的文件不会被压缩，放置在res目录下的文件会被压缩(raw除外)，所以为防止你的文件失真，可以考虑放置在assets目录下。

3、另外我们在处理文件流的时候会有异常情况，所以一般会将文件放置在assets目录下。

 

 将zip压缩文件放到assets中，然后在android上解压出压缩文件,但出现了些困难：

 assets用右键run as -\> android application的时候可以正常读取文件路径,
而当用build.xml编译的时候无法正常读取文件路径。

String []str = getAssets().list("zips");

zips

    - 1.zip

    - 2.zip

这是因为assets用build.xml打包后改变了的文件路径,所以无法读到.

    \<target name="generate"\>

        \<echo\>Generating R.java / Manifest.java from the resources...\</echo\>

        \<exec executable="\${tools-aapt}" failonerror="true"\>

            \<arg value="package"/\>

            \<arg value="-m"/\>

            \<arg value="-J"/\>

            \<arg value="\${absolute-gen}"/\>

            \<arg value="-M"/\>

            \<arg value="\${absolute-file-manifest-out}"/\>

**<span style="color:#e53333;">            \<arg value="-A" /\></span>**

**<span
style="color:#e53333;">      \<arg value="\${absolute-asset}" /\></span>**

            \<arg value="-S"/\>

            \<arg value="\${absolute-res}"/\>

            \<arg value="-I"/\>

            \<arg value="\${tools-android-core}"/\>

      \<arg value="--auto-add-overlay" /\>

        \</exec\>

    \</target\>








