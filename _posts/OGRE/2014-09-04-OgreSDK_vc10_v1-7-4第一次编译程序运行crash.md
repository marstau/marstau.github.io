---
layout: post
title: OgreSDK_vc10_v1-7-4第一次编译程序运行crash
category: 游戏技术
tags: OGRE
keywords: 
description: 
---

**报错：**

new.exe 中的 0x75579617 处有未经处理的异常: Microsoft C++ 异常: 内存位置 0x0021f664 处的 Ogre::FileNotFoundException。

 

**定位：**

virtual void setupResources(void){

...

cf.load(mResourcePath + "resources\_d.cfg");

...

}

**分析：**

文件无法找到,所以将resources\_d.cfg及其资源文件拷贝到相应目录下即可。

.dll文件位置可通过修改[属性]-\>[配置属性]-\>[调试]-\>[工作目录]到其他文件夹.相对dll文件就会相应变化.

 

 

第一次编译OGRE配置：

1. Create a new empty project.

2. Create a new file for the code and name it main.cpp.

3. Add the main function:

int main (void)

{

return 0;

}

4. Include ExampleApplication.h at the top of the following source file:

\#include "Ogre\\ExampleApplication.h":

5. Add PathToYourOgreSDK\\include\\ to the include path of your project.

6. Add PathToYourOgreSDK\\boost\_1\_42 to the include path of your project.

7. Add PathToYourOgreSDK\\boost\_1\_42\\lib to your library path.

8. Add a new class to the main.cpp.

class Example1 : public ExampleApplication

{

public:

void createScene()

{

}

};

9. Add the following code at the top of your main function:

Example1 app;

app.go();

10. Add PathToYourOgreSDK\\lib\\debug to your library path.

11、12. Add

**OgreMain\_d.lib**

**OIS\_d.lib**

to your linked libraries.

13. Compile the project.

14. Set your application working directory to PathToYourOgreSDK\\bin\\debug.

15. Start the application. You should see the Ogre 3D Setup dialog.





