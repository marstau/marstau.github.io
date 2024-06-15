---
layout: post
title: Android Studio
category: 软件工具
tags: software
keywords: anroid,game
description: 
---

#### 删除项目[More](http://jingyan.baidu.com/article/c74d6000813b2b0f6b595d48.html)

```
File->Project Structure
```

#### 快捷键

```
import package -> Alt + Enter
Go to File... ⇧⌘O(Mac)/Ctrl + Shift + N(Windows) => ⌘ + P # 快速查找文件
File Structure ⌘F12(Mac)/Ctrl + F12(Windows) => ⌘ + R # 快速查找当前文件的方法名
```

## FAQ

#### 代理配置路径

`~/.gradle/gradle.properties`

#### 快速调试[More](https://droidyue.com/blog/2017/05/14/a-little-but-useful-debug-skill_for_android/)

```
adb shell am set-debug-app -w --persistent  com.example.jishuxiaoheiwu.appdebugsample

adb shell am clear-debug-app
```

## Errors


#### Modules 'fast_follow_asset_pack' and 'install_time_asset_pack' contain entry 'assets/.DS_Store' with different content.[More](https://stackoverflow.com/questions/18080950/google-play-developer-console-shows-ds-store-in-native-platforms-section-of-uplo)

Solution:
You need to close Finder and remove these files (named .DS_Store) from console with "rm".

Don't open finder when compiling, then running `find . -name '.DS_Store' -type f -delete`

#### Install repository and sync project[More](https://stackoverflow.com/questions/43495549/cannot-install-repository-and-sync-project-in-android-studio)

```
Install repository and sync project
Show in File
Show in Project Structure dialog
```

```
allprojects {
    repositories {
        jcenter()
        maven {
            url "https://maven.google.com"
        }
   }
}
```

#### `Error:Execution failed for task ':app:compileDebugKotlin'. > Compilation error. See log for more details`[More](https://stackoverflow.com/questions/43848845/errorexecution-failed-for-task-appcompiledebugkotlin-compilation-error)

```
Click on Gradle (on the right side bar) then under :app choose assembleDebug (or assembleYourFlavor if you use flavors). Error will show up in Run tab. 
```

#### `Lint found fatal errors while assembling a release target. To proceed, either fix the issues iden`[More](https://blog.csdn.net/lplj717/article/details/105434364)

```
Lint found fatal errors while assembling a release target.
 
To proceed, either fix the issues identified by lint, or modify your build script as follows:
...
android {
    lintOptions {
        checkReleaseBuilds false
        // Or, if you prefer, you can continue to check for errors in release builds,
        // but continue the build even when errors are found:
        abortOnError false
    }
}
...
```

Solution:
```
android{
	 buildTypes {
        release {
           //在此添加：
            lintOptions {
                checkReleaseBuilds false
                abortOnError false
            }
            minifyEnabled false
            shrinkResources false
            zipAlignEnabled false
            signingConfig signingConfigs.signing
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        debug {
            minifyEnabled false
            shrinkResources false
            zipAlignEnabled false
        }
    }
}
```

#### 编译报错

```
No resource identifier found for attribute
```

试试改成如下

```
compile 'com.android.support:appcompat-v7:26+'
compile 'com.android.support:percent:26.0.0'
compile 'com.android.support.constraint:constraint-layout:1.0.2'
```


#### Android实现Multidex及指定主dex中的class[More](https://developer.android.com/studio/build/multidex?hl=zh-cn), More2[https://blog.csdn.net/u010746456/article/details/80150267]

#### 部分手机安卓崩溃,提示`only fullscreen opaque activities can request orientation`

```
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" />
修改为
android:theme="@android:style/Theme.NoTitleBar" />

添加
<uses-permission android:name="android.permission.OBSERVE_GRANT_REVOKE_PERMISSIONS"
    tools:ignore="ProtectedPermissions"/>
```

#### `错误: 加载主类 com.android.sdklib.tool.sdkmanager.SdkManagerCli 时出现 LinkageError java.lang.UnsupportedClassVersionError: com/android/sdklib/tool/sdkmanager/SdkManagerCli has been compiled by a more recent version of the Java Runtime (class file version 61.0), this version of the Java Runtime only recognizes class file versions up to 55.0`

rename cmdline-tools/8.0 to cmdline-tools/latest

## Reference

