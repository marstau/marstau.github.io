---
layout: post
title: Unity3D Editor
category: 编程开发
tags: unity3d
keywords: 
description: 
---

#### 调用python

```
string pythonScriptPath = $"JsonToSkel.py -Ids {spineId1},{spineId2},{spineId3}";

// 创建进程信息
ProcessStartInfo psi = new ProcessStartInfo();
psi.FileName = "python3"; // 或者使用 python，具体根据你的环境配置
psi.Arguments = pythonScriptPath;
psi.UseShellExecute = false;
psi.RedirectStandardOutput = true;
psi.CreateNoWindow = true;

// 启动进程
Process process = new Process();
process.StartInfo = psi;
process.Start();

// 读取 Python 脚本的输出
string output = process.StandardOutput.ReadToEnd();

// 等待进程结束
process.WaitForExit();

// 输出 Python 脚本的输出到 Unity 控制台
UnityEngine.Debug.Log("RunPythonJsonToSkel Python Output: " + output);
```

#### 在unity编辑器界面中显示

```
[SerializeField]
private float mSpeed = 3.0f;
```

#### 如果在打AssetBundle的时候，选定的构建目标是安卓。那么在windows操作系统下，编辑器的默认渲染模式为DX11，我们需要修改编辑器的渲染模式，可以通过UnityHub来修改启动项目的编辑器渲染模式，参考官方文档。[More](https://docs.unity3d.com/Manual/EditorCommandLineArguments.html)[More2](https://www.yooasset.com/docs/FAQ)

在Vulkan下打包的编辑器需要加个command `-force-vulkan`

windows平台添加命令: `-force-gles`

## Reference

