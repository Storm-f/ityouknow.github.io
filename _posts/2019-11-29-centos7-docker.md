---
layout: post
title: CentOS7上安装Docker
date: 2019-11-29
categories: CentOS7,Docker
tags: CentOS7,Docker
---
本文介绍如何在Centos7上安装Docker。

## CentOS7 Docker 安装

### 1、 Docker 要求 CentOS 系统的内核版本高于 3.10 ，查看本页面的前提条件来验证你的CentOS 版本是否支持 Docker

通过`uname -r`命令查看你当前的内核版本
```
$ uname -r
```
### 2、 确保 yum 包更新到最新

```
$ yum update
```

### 3、 卸载旧版本(如果安装过旧版本的话)

```
$ yum remove docker  docker-common docker-selinux docker-engine
```

### 4、 安装需要的软件包， yum-util 提供yum-config-manager功能，另外两个是devicemapper驱动依赖的

```
$ yum install -y yum-utils device-mapper-persistent-data lvm2
```

### 5、 设置yum源

中央仓库:
```
$ yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```
阿里云仓库:
```
$ yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

### 6、 查看仓库中所有docker版本，并选择特定版本安装

```
$ yum list docker-ce --showduplicates | sort -r
```

### 7、安装docker

安装最新稳定版本的docker
```
$ yum install docker-ce
```
安装特定版本的docker
```
$ yum install docker-18.09.1
```

### 8、 启动docker

```
$ systemctl start docker
```
开机启动
```
$ systemctl enable docker
```

### 9、 验证是否成功

```
$ docker version
$ docker info
```

### 10、运行hello-world

`$ docker container run hello-world`

```
$ docker container run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

... ...
```
如果运行成功，你会在屏幕上读到下面的输出。
