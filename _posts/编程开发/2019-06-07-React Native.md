---
layout: post
title: React Native
category: 编程开发
tags: 
keywords: 
description: 
---


## Guide

#### create project and run app[More](https://www.tutorialspoint.com/react_native/react_native_quick_guide.htm)


```
npm install -g create-react-native-app
create-react-native-app MyReactNative
npm install -g react-native-cli
npm start
expo run:android
```

#### generate index.android.bundle

```
mkdir android/app/src/main/assets
react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
react-native run-android
```

#### index.android.bundle

```
__d(function (global, _$$_REQUIRE, _$$_IMPORT_DEFAULT, _$$_IMPORT_ALL, module, exports, _dependencyMap)
```


## FAQ

#### 官方的实现存在的问题是Id值从0开始分配，所以任意改动业务代码可能引起模块构建的顺序变动，致使同一个模块在两次构建分配了有2个不同的Id值。[More](https://juejin.cn/post/6844904192646053902#heading-1)

#### 热更新[More](http://www.phpheidong.com/blog/article/141487/811747775abfb2b381fd/)[More2](https://cloud.tencent.com/developer/article/1896497)[More3](https://juejin.cn/post/6844903477492056078)

## Error

#### The development server returned respose error code:404 react native[More](https://stackoverflow.com/questions/46773509/the-development-server-returned-respose-error-code404-react-native)

端口占用了 关闭端口即可。

#### zip END header not found

remove cache and then download by hand, replace in the directory.


#### Could not determine the dependencies of task ':app:compileDebugJavaWithJavac' Cannot query the value of this provider because it has no value available[More](https://github.com/expo/expo/issues/15183)

Did u install ANDROID_SDK_ROOT by android studio?

```
export ANDROID_SDK_ROOT=$HOME/softwares/AndroidStudioSDK
export PATH=$PATH:$ANDROID_SDK_ROOT
```


## Reference

* [Create Native Modules](https://facebook.github.io/react-native/docs/native-modules-android)