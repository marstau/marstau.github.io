---
layout: post
title: xcode __nwlog_err_simulate_crash_libsystem
category: 编程开发
tags: error-unresolved
keywords: xcode
description: 
---	


## Error

```
2018-04-15 15:07:57.579996 be[3417:129361] [] __nwlog_err_simulate_crash_libsystem libsystem simulate crash unavailable "libsystem_network.dylib: nw_host_stats_add_src :: received error for SRC_ADDED: [22] Invalid argument"
2018-04-15 15:07:57.581091 be[3417:129361] [] nw_host_stats_add_src received error for SRC_ADDED: [22] Invalid argument, dumping backtrace:
        [x86_64] libnetcore-856.20.4
    0   libsystem_network.dylib             0x0000000116083682 __nw_create_backtrace_string + 123
    1   libsystem_network.dylib             0x000000011609a306 nw_get_host_stats + 1083
    2   libnetwork.dylib                    0x000000011658278b nw_endpoint_resolver_start_next_child + 1382
    3   libdispatch.dylib                   0x0000000115e00980 _dispatch_call_block_and_release + 12
    4   libdispatch.dylib                   0x0000000115e2a0cd _dispatch_client_callout + 8
    5   libdispatch.dylib                   0x0000000115e07e6b _dispatch_queue_serial_drain + 236
    6   libdispatch.dylib                   0x0000000115e08b9f _dispatch_queue_invoke + 1073
    7   libdispatch.dylib                   0x0000000115e0b3b7 _dispatch_root_queue_drain + 720
    8   libdispatch.dylib                   0x0000000115e0b08b _dispatch_worker_thread3 + 123
    9   libsystem_pthread.dylib             0x00000001161dd1ca _pthread_wqthread + 1387
    10  libsystem_pthread.dylib             0x00000001161dcc4d start_wqthread + 13
```

## Solution

```
Modify General->Deployment info->Deployment Target from 10.0 to 11.2
```

## Reference

* <https://stackoverflow.com/questions/46929989/xcode-9-running-app-on-ios-10-1-1-crashes-on-launch>