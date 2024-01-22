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

## Reference

