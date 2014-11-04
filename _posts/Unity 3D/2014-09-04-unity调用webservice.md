---
layout: post
title: unity调用webservice
category: 游戏技术
tags: Unity　3D
keywords: 
description: 
---

1.  运行VS2010的命令提示工具(开始菜单中找得到)
2.  通过命令提示工具进入到当前的unity工程目录下的WebClient(创建一个文件夹)(eg:我的是E:\\Visual Studio 2010\\Projects\\UnityTest\\Assets\\WebClient)。
3.  输入
    wsdl -out:MyService.cs <http://172.16.45.38:8899/axis2/services/MyService?wsdl>,便会自动生成一个MyService.cs,然后按照往常c\#调用webservice的方法调用即可
    ：\

            string url = "http://172.16.45.38:8899/axis2/services/MyService?wsdl";

            WWW w = new WWW(url);

            MyService d = new MyService();

            Debug.Log(ML.TAG + " - " + d.test("1") );

 

 

references :

<http://wiki.unity3d.com/index.php?title=Webservices_In_Unity>

<http://blog.csdn.net/wuxin651885019/article/details/8602304>






