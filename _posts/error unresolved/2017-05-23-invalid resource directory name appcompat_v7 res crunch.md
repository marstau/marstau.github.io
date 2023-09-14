---
layout: post
title: invalid resource directory name appcompat_v7 res crunch
category: errors
tags: error-unresolved
keywords: eclipse
description: 
---	


## ERROR

ant编译时提示

```
[aapt] invalid resource directory name: /Users/marstau/projects/appcompat_v7/bin/res crunch

BUILD FAILED
/Users/marstau/softwares/android-sdk-macosx/tools/ant/build.xml:601: The following error occurred while executing this line:
/Users/marstau/softwares/android-sdk-macosx/tools/ant/build.xml:653: The following error occurred while executing this line:
/Users/marstau/softwares/android-sdk-macosx/tools/ant/build.xml:698: null returned: 1
```


## Solution[More](https://stackoverflow.com/questions/19746319/how-to-solve-invalid-resource-directory-name-resource-crunch/22057171#22057171)

```
删除整个bin目录
```

## Reference