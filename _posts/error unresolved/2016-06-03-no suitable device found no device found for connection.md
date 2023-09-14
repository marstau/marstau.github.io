---
layout: post
title: no suitable device found no device found for connection
category: errors
tags: error-unresolved
keywords: linux
description: 
---	


## ERROR

When execute `service network restart`, prompting following:

```
Bringing up interface eth0: Error: No suitable device found： no device found for connection 'System eth0'.
```

## Solution[More](http://www.uptimemadeeasy.com/vmware/fixing-eth0-mac-address-vmware-clone-restore/)

Execute `ifconfig`, known HWaddr of eth1, replace to HWaddr where in `/etc/sysconfig/network-scripts/ifcfg-eth0`.

## Reference

* 