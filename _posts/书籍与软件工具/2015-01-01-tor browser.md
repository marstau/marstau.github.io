---
layout: post
title: tor browser
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---


#### 查ip和浏览器指纹[More](https://browserleaks.com/ip)[More2](https://whoer.net/)


#### 自己搭建网桥[More](https://community.torproject.org/relay/setup/bridge/)[More2](https://community.torproject.org/relay/setup/bridge/post-install/)


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
RunAsDaemon 1
BridgeRelay 1

# Replace "TODO1" with a Tor port of your choice.  This port must be externally
# reachable.  Avoid port 9001 because it's commonly associated with Tor and
# censors may be scanning the Internet for this port.
# just write:
# ORPort 1.2.3.4:443
# where 1.2.3.4 would be your public IPv4
ORPort TODO1

ServerTransportPlugin obfs4 exec /usr/local/bin/obfs4proxy

# Replace "TODO2" with an obfs4 port of your choice.  This port must be
# externally reachable and must be different from the one specified for ORPort.
# Avoid port 9001 because it's commonly associated with
# Tor and censors may be scanning the Internet for this port.
ServerTransportListenAddr obfs4 0.0.0.0:TODO2

# Local communication port between Tor and obfs4.  Always set this to "auto".
# "Ext" means "extended", not "external".  Don't try to set a specific port
# number, nor listen on 0.0.0.0.
ExtORPort auto

# Replace "<address@email.com>" with your email address so we can contact you if
# there are problems with your bridge.  This is optional but encouraged.
ContactInfo <address@email.com>

# Pick a nickname that you like for your bridge.  This is optional.
Nickname PickANickname
```

```
sudo semanage port -a -t tor_port_t -p tcp [TODO1]
sudo semanage port -a -t tor_port_t -p tcp [TODO2]
```

replace `TODO1` to 10000, `TODO2` to 10002 above.

```
systemctl enable --now tor
systemctl restart tor
systemctl status tor
```

output following means success, log file:

```
: Bootstrapped 10% (conn_done): Connected to a relay
: Bootstrapped 14% (handshake): Handshaking with a relay
: Bootstrapped 15% (handshake_done): Handshake with a relay done
: Bootstrapped 75% (enough_dirinfo): Loaded enough directory info to build circuits
: Bootstrapped 90% (ap_handshake_done): Handshake finished with a relay to build circuits
: Bootstrapped 95% (circuit_create): Establishing a Tor circuit
: Bootstrapped 100% (done): Done
: Now checking whether IPv4 ORPort x.x.x.x:10000 is reachable... (this may take up to 20 minutes -- look for log messages indicating success)
: Self-testing indicates your ORPort x.x.x.x:10000 is reachable from the outside. Excellent. Publishing server descriptor.
: Performing bandwidth self-test...done.
```


```
/var/log/tor/log
/var/log/syslog
```
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
Bridge obfs4 <IP ADDRESS>:<PORT> <FINGERPRINT> cert=k27hqWApaAmlRzDdkekpXnRcLGI3XJQgGh6PvSfPV8ejWWQqkXmZxO37yYe5HzLvMuJ0dg iat-mode=0
```

[reachable test](https://bridges.torproject.org/scan/)

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

## Reference

* [编程随想](https://program-think.blogspot.com/)
* [onion-links](https://www.webhostingsecretrevealed.net/blog/security/dark-web-websites-onion-links/)