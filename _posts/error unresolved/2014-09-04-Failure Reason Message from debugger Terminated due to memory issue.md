---
layout: post
title:  Failure Reason Message from debugger Terminated due to memory issue
category: errors
tags: error-unresolved
keywords: 
description: 
---

游戏跑着跑着闪退了

```
The app “NativeOverseaTest” on XXX的 iPhone quit unexpectedly.
Domain: IDEDebugSessionErrorDomain
Code: 4
Failure Reason: Message from debugger: Terminated due to memory issue
User Info: {
    IDERunOperationFailingWorker = DBGLLDBLauncher;
}
--

Analytics Event: com.apple.dt.IDERunOperationWorkerFinished : {
    "device_model" = "iPhone10,3";
    "device_osBuild" = "14.7.1 (18G82)";
    "device_platform" = "com.apple.platform.iphoneos";
    "launchSession_schemeCommand" = Run;
    "launchSession_state" = 2;
    "launchSession_targetArch" = arm64;
    "operation_duration_ms" = 145065;
    "operation_errorCode" = 4;
    "operation_errorDomain" = IDEDebugSessionErrorDomain;
    "operation_errorWorker" = DBGLLDBLauncher;
    "operation_name" = IDEiPhoneRunOperationWorkerGroup;
    "param_consoleMode" = 0;
    "param_debugger_attachToExtensions" = 0;
    "param_debugger_attachToXPC" = 1;
    "param_debugger_type" = 5;
    "param_destination_isProxy" = 0;
    "param_destination_platform" = "com.apple.platform.iphoneos";
    "param_diag_MainThreadChecker_stopOnIssue" = 0;
    "param_diag_MallocStackLogging_enableDuringAttach" = 0;
    "param_diag_MallocStackLogging_enableForXPC" = 1;
    "param_diag_allowLocationSimulation" = 1;
    "param_diag_gpu_frameCapture_enable" = 0;
    "param_diag_gpu_shaderValidation_enable" = 0;
    "param_diag_gpu_validation_enable" = 1;
    "param_diag_memoryGraphOnResourceException" = 0;
    "param_diag_queueDebugging_enable" = 1;
    "param_diag_runtimeProfile_generate" = 0;
    "param_diag_sanitizer_asan_enable" = 0;
    "param_diag_sanitizer_tsan_enable" = 0;
    "param_diag_sanitizer_tsan_stopOnIssue" = 0;
    "param_diag_sanitizer_ubsan_stopOnIssue" = 0;
    "param_diag_showNonLocalizedStrings" = 0;
    "param_diag_viewDebugging_enabled" = 1;
    "param_diag_viewDebugging_insertDylibOnLaunch" = 1;
    "param_install_style" = 0;
    "param_launcher_UID" = 2;
    "param_launcher_allowDeviceSensorReplayData" = 0;
    "param_launcher_kind" = 0;
    "param_launcher_style" = 0;
    "param_launcher_substyle" = 0;
    "param_runnable_appExtensionHostRunMode" = 0;
    "param_runnable_productType" = "com.apple.product-type.application";
    "param_runnable_swiftVersion" = "5.5.1";
    "param_runnable_type" = 2;
    "param_testing_launchedForTesting" = 0;
    "param_testing_suppressSimulatorApp" = 0;
    "param_testing_usingCLI" = 0;
    "sdk_canonicalName" = "iphoneos15.0";
    "sdk_osVersion" = "15.0";
    "sdk_variant" = iphoneos;
}
--


System Information

macOS Version 11.4 (Build 20F71)
Xcode 13.1 (19466) (Build 13A1030d)
Timestamp: 2021-10-28T15:36:58+08:00
```

## Solution

内存暴增导致的崩溃[More](https://www.cnblogs.com/lu-diary/p/6945596.html)