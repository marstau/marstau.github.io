---
layout: post
title: googleplay支付
category: 编程开发
tags: googleplay pay
keywords: 
description: 
---


## FAQ

#### invalid key hash. the key hash does not match any stored key hashes GooglePlay 二次签名，造成Facebook ,Google 登录失败[More](https://blog.csdn.net/Jason_HD/article/details/124443963)

google 后台会重新签名导致的

#### `Error checking for billing v3 support. (response: 3:Billing Unavailable`

要用美国VPN,香港VPN都不行

#### 无法购买您要买的商品？

1. 上传到到alpha版或beta版后，点发布，三个小时候生效，要封闭测试，而不是开放测试。
2. 测试账号要重新点加入测试链接。

#### `Can't start async operation (launchPurchaseFlow) because another async operation(launchPurchaseFlow) is in progress`

第一次支付完，要调用handleActivityResult,否则会报错。

```
@Override  
protected void onActivityResult(int requestCode, int resultCode, Intent data) {  
    Log.d(TAG, "onActivityResult(" + requestCode + "," + resultCode + "," + data);  
    if (mHelper == null) return;  

    // Pass on the activity result to the helper for handling  
    if (!mHelper.handleActivityResult(requestCode, resultCode, data)) {  
        // not handled, so handle it ourselves (here's where you'd  
        // perform any handling of activity results not related to in-app  
        // billing...  
        super.onActivityResult(requestCode, resultCode, data);  
    }  
    else {  
        Log.d(TAG, "onActivityResult handled by IABUtil.");  
    }  
} 

``` 

#### facebook密钥散列读取

```
keytool -exportcert -alias androiddebugkey -keystore ~/.android/debug.keystore | openssl sha1 -binary | openssl base64
```


## ERROR

#### 登录一直提示，正在核对信息

环境:MIUI 9.8.29开发版

方法1:
下载[ourplay](https://www.ourplay.net/)

方法2[More](https://www.zhihu.com/question/48890950/answer/344714468)
1. 无论从Go谷歌安装器还是任意其他安装器安装的谷歌四件套，先卸载干净。一般软件内部提供卸载功能。卸载完重启；下载提供的网盘文件夹（链接: https://pan.baidu.com/s/1aWJhb6xOdljFMShLQsN9wQ 密码: 35rk），整个文件夹下载下来；进入 MIUI 本地备份功能（设置 - 更多设置 - 备份和重置 - 本地备份）新建一个备份，随便备份一个程序；将网盘下载的文件夹整个放进 MIUI 备份文件夹目录（\MIUI\backup\AllBackup\）切回本地备份功能，出现了一个包含 4 个备份的新备份，全选，开始恢复；重启手机
2. 清除软件所有缓存信息并开启所有权限，全程开启vpn
3. 到酷安市场下载最新的google play store
4. 打开后等一阵，频繁试几次
5. 将套件去 www.apkmirror.com 更新到最新版本

#### google play审核报SSL Error Handler[More](https://ask.dcloud.net.cn/question/52727)

```
要纠正这个问题，请在服务器提供的证书满足您的期望时更新您的应用程序代码以调用SslErrorHandler.proceed（），否则请调用SslErrorHandler.cancel（）。
如果您使用负责此事的第三方库，请通知第三方并与他们合作解决问题。
```
## Reference

* <https://developer.android.com/google/play/billing/billing_integrate.html>
* [google-services-framework](https://www.apkmirror.com/apk/google-inc/google-services-framework/)
* [google-play-services](https://www.apkmirror.com/apk/google-inc/google-play-services/)
* [google-play-store](https://www.apkmirror.com/apk/google-inc/google-play-store/)
