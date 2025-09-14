---
layout: post
title: google chrome
category: 软件工具
tags: software
keywords: 
description: 
---

#### 功能

chrome未在extensions中显示的插件 
```
chrome://apps/
```

#### 扩展程序目录

```
C:\Users\mars\AppData\Local\Google\Chrome\User Data\Profile 1\Extensions\
~/Library/Application\ Support/Google/Chrome/Default/Extensions
```

#### mac下google chrome时不时弹出chrome图标 [More](http://zhidao.baidu.com/link?url=7oSB3pd_Z8ANGjGMaXn8OzvEBWhuY_GLyCVKKfCg-PAhsswMHqYHR_LIXp5pqCQbY2eUEvVlgXoRo7Ep10Cx__QwzZMXnZgMEAAvXk2jFxa)

如图:

![](/Resources/google_chrome_1.png)

```
系统偏好设置－通用－允许在这台Mac和iCloud设备之间使用Handoff， 将这个选项关闭即可
```

#### mac下禁止更新

删除文件
```
/Library/Google/GoogleSoftwareUpdate/GoogleSoftwareUpdate.bundle
```

#### 历史版本下载[More](https://www.izhangheng.com/chrome-and-chrome-os-download-collection)[More2](https://google_chrome.zh.downloadastro.com/old_versions/)

[安卓下载](https://www.wandoujia.com/apps/280309/history)
[Windows下载](http://mydown.yesky.com/pcsoft/416318/versions)
[mac下载](https://google-chrome.en.uptodown.com/mac/versions)
[免安装版下载](https://easylife.tw/dltag/GoogleChromePortable)
```好像失效了
http://dl.google.com/chrome/install/[版本号后两位]/chrome_installer.exe

要想下载历史版本 Chrome，必须先确定要下载的版本号，然后取版本号第二个小数点后的数字。比如4.0.266.0的下载地址就是：
eg:
http://dl.google.com/chrome/install/195.38/chrome_installer.exe

```

#### chrome 安装不再受支持的扩展插件时报错：无法安装扩展程序,因为它使用了不受支持的清单版本[More](https://www.cnblogs.com/shichq/p/18995207)

Solution1:

启用旧版清单支持（Chrome/Edge）

地址栏输入 `chrome://flags/#allow-legacy-mv2-extensions`
将 `Allow legacy extension manifest versions` 设置为 Enabled 并重启浏览器。

新版未找到这个选项：


Solution2:[More](https://www.reddit.com/r/chrome/comments/1n7d4oe/is_it_still_possible_to_enable_manifest_v2/)

```
open -b com.google.Chrome --new --args --disable-features=ExtensionManifestV2Unsupported,ExtensionManifestV2Disabled
```

• Create a new App with Automator passing custom flags • Hide the original Chrome from Spotlight search (to avoid duplicates)

Step by step:

Open Automator

Click "New Document"

Choose "Application"

Search and add "Run Shell Script"

Paste this script:

```
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --disable-features=ExtensionManifestV2Unsupported,ExtensionManifestV2Disabled "$@"
```

File > Save with name "Google Chrome" (or whatever you prefer)

Save location: Your custom folder (like ~/customApps or anything like that)


To hide original Chrome from Spotlight:

Go to System Settings > Spotlight

Click "Search Privacy" (bottom of the window) （聚焦）

Drag the original Chrome app from /Applications folder directly into the Privacy window

Final step:

Customize the Automator app icon to look like Chrome (right-click your new app > Get Info > drag Chrome icon from original app)




## Reference

* [Chrome Developer Dashboard](https://chrome.google.com/webstore/developer/dashboard)
* [Chrome Web Store](https://chrome.google.com/webstore/category/extensions)