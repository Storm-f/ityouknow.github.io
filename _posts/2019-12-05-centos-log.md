---
layout: post
title: Linux系统/var/log日志分析
date: 2019-12-05
categories: Linux
tags: Linux
---
本文介绍Linux系统/var/log各个日志详细信息。

## /var/log/messages

整体系统信息，其中也包含系统启动期间的日志。此外，mail，cron，daemon，kern和auth等内容也记录在var/log/messages日志中。
```
$ cat /var/log/messages
```

## /var/log/dmesg

内核缓冲信息（kernel ring buffer）。在系统启动时，会在屏幕上显示许多与硬件有关的信息。

```
$ cat /var/log/dmesg
```

## /var/log/boot.log

系统启动时的日志。

```
$ cat /var/log/boot.log
```
