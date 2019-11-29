---
layout: post
title: CentOS7上挂载硬盘
date: 2019-11-28
categories: Linux,CentOS7
tags: CentOS7
---
本文介绍如何在Centos7上挂载硬盘。

### 1、 查看所有磁盘：
```
$ fdisk -l
```

![](../mount-disk-1.jpg)

### 2、 新建分区

```
$ fdisk /dev/vdb
```
这里的vdb是要挂载的新硬盘

![](../mount-disk-2.jpg)

输入回车表示默认

查看创建出来的分区
![](../mount-disk-3.jpg)

保存并退出fdisk工具命令行
![](../mount-disk-4.jpg)

### 3、 格式化分区

需要匹配docker默认overlay2存储驱动，建议使用命令：
```
$ mkfs.xfs -n ftype=1 /dev/vdb1
```    

### 4、 将新添加硬盘分区(/dev/vdb1)挂载到指定文件目录(/data)

```
$ mkdir /data
$ mount /dev/vdb1 /data
```
