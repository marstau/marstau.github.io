---
layout: post
title: tor browser
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---


#### 查ip和浏览器指纹[More](https://browserleaks.com/ip)[More2](https://whoer.net/)


#### 自己搭建网桥[More](https://community.torproject.org/relay/setup/bridge/)[More2](https://community.torproject.org/relay/setup/bridge/post-install/)[More3](https://blog.csdn.net/windwenguan/article/details/90172805)


[reachable test](https://bridges.torproject.org/scan/)


非公开网桥`telegram @GetBridgesBot`

```
yum install epel-release
```

```
vi /etc/yum.repos.d/Tor.repo
```

add following contents:
```
[tor]
name=Tor for Enterprise Linux $releasever - $basearch
baseurl=https://rpm.torproject.org/centos/$releasever/$basearch
enabled=1
gpgcheck=1
gpgkey=https://rpm.torproject.org/centos/public_gpg.key
cost=100
```

```
yum install tor
yum install git golang policycoreutils-python-utils
```

```
export GOPATH='mktemp -d'
go install gitlab.com/yawning/obfs4.git/obfs4proxy
sudo cp $GOPATH/bin/obfs4proxy /usr/local/bin/
# chcon --reference=/usr/bin/tor /usr/local/bin/obfs4proxy
```

Edit your Tor config file, usually located at `/etc/tor/torrc` and replace its content with:

```
Log notice file /var/log/tor/notices.log
RunAsDaemon 1
ORPort 4443
Exitpolicy reject *:*
BridgeRelay 1
ServerTransportPlugin obfs4 exec /usr/local/bin/obfs4proxy
ExtORPort auto
PublishServerDescriptor 0
```

```
systemctl enable --now tor
systemctl restart tor
systemctl status tor
```

output following means success, log file:


```
[notice] Your Tor server's identity key fingerprint is '<NICKNAME> <FINGERPRINT>'
[notice] Your Tor bridge's hashed identity key fingerprint is '<NICKNAME> <HASHED FINGERPRINT>'
[notice] Registered server transport 'obfs4' at '[::]:46396'
[notice] Tor has successfully opened a circuit. Looks like client functionality is working.
[notice] Bootstrapped 100%: Done
[notice] Now checking whether ORPort <redacted>:3818 is reachable... (this may take up to 20 minutes -- look for log messages indicating success)
[notice] Self-testing indicates your ORPort is reachable from the outside. Excellent. Publishing server descriptor.
```


```
vi /var/lib/tor/pt_state/obfs4_bridgeline.txt
```

```
Bridge obfs4 <IP ADDRESS>:<PORT> <FINGERPRINT> cert=k27hqWApaAmlRzDdkekpXnRcLGI3XJQgGh6PvSfPV8ejWWQqkXmZxO37yYe5HzLvMuJ0dg iat-mode=0
```

#### 网站



* [Hidden Wiki](https://thehiddenwiki.org/)[More1](http://zqktlwiuavvvqqt4ybvgvi7tyo4hjl5xgfuvpdf6otjiycgwqbym2qad.onion/)

* [Dread - the Reddit of Dark Web](http://dreadytofatroptsdj6io7l3xptbet6onoyno2yv7jicoxknyazubrad.onion/)

* [The Hidden Wallet](http://d46a7ehxj6d6f2cf4hi3b424uzywno24c7qtnvdvwsah5qpogewoeqid.onion/)

* [Facebook on Dark Web](facebookwkhpilnemxj7asaniu7vnjjbiltxjqhye3mhbshg7kx5tfyd.onion)

* [MegaTor - anonymous file-sharing](http://crqkllx7afomrokwx6f2sjcnl2do2i3i77hjjb4eqetlgq3cths3o6ad.onion/)

* [Onion Wallet](http://p2qzxkca42e3wccvqgby7jrcbzlf6g7pnkvybnau4szl5ykdydzmvbid.onion/)

* [Torch - search engine](xmh57jrknzkhv6y3ls3ubitzfqnkrwxhopf5aygthi7d6rplyvk3noyd.onion)

* [Dark Web search engine](http://haystak5njsmn2hqkewecpaxetahtwhsbsa64jom2k22z5afxhnpxfid.onion/)

* [Tor Hacker Services](http://zkllmhuxmf3u6lh4cl3lueyoxjvxoocnwv7k2wrhatyhw2mknfjtnrid.onion/)

* [Elude - hiden email](http://eludemailxhnqzfmxehy3bk5guyhlxbunfyhkcksv4gvx6d3wcf6smad.onion/ )

* [Safe Escrow - trades](http://u4dgrzpfkeokyvthkqz3zxq4b7njpfcx4zgwwos3mjqfvjbnnuqbtpyd.onion/)

#### deprecated

* [hidden wiki - onion网址汇总](https://thehiddenwiki.org/)

* [Silk Road 3.1](http://silkroad4n7fwsrw.onion)

* [暗网中文论坛](http://deepcnxpfgmausrq.onion)


* [The Pirate Bay 种子下载](http://uj3wazyk5u4hnvtk.onion)

* [中文论坛](http://22u75kqyl666joi2.onion)
* [图片网站](http://suicideg4jl25hzn.onion)

* [一系列网址](http://22u75kqyl666joi2.onion/viewtopic.php?f=5&t=129)[More1](http://underdj5ziov3ic7.onion/category/CHINESE/)

* [网址导航](http://torlinkbgs6aabns.onion/)

* [搜索引擎](http://hss3uro2hsxfogfq.onion)

* [Tor 的匿名性真的和你想象中一样强？](https://yq.aliyun.com/articles/136970/)

## FAQ

#### 开启了代理后来关闭 一直连不上提示`New control connection opened from 127.0.0.1.`

卸载重装好了

## Reference

* [编程随想](https://program-think.blogspot.com/)
* [onion-links](https://www.webhostingsecretrevealed.net/blog/security/dark-web-websites-onion-links/)