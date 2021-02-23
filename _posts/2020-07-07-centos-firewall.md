---
layout: post
title: firewalld 防火墙
date: 2020-05-09
categories: firewalld
tags:  firewalld
---
本文主要介绍firewalld 防火墙。

## firewalld 防火墙

语法命令如下：启用区域端口和协议组合
```
$ firewall-cmd [--zone=<zone>] --add-port=<port>[-<port>]/<protocol> [--timeout=<seconds>]
```
端口可以是一个单独的端口 <port> 或者是一个端口范围 <port>-<port>。
协议可以是 tcp 或 udp。

### 查看 firewalld 状态

```
$ systemctl status firewalld
```

### 开启 firewalld

```
$ systemctl start firewalld
```

### 开放端口

```
#--permanent 永久生效,没有此参数重启后失效
$ firewall-cmd --zone=public --add-port=80/tcp --permanent

$ firewall-cmd --zone=public --add-port=1000-2000/tcp --permanent
```

### 重新载入

```
$ firewall-cmd --reload
```

### 查看

```
$ firewall-cmd --zone=public --query-port=80/tcp
```

### 查看所有端口

```
$ firewall-cmd --list-ports
```
 
### 删除

```
$ firewall-cmd --zone=public --remove-port=80/tcp --permanent
```
