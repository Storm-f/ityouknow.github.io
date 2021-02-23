---
layout: post
title: linux下tomcat开机启动
date: 2020-02-15
categories: linux,tomcat
tags: linux,tomcat
---
本文主要介绍linux下tomcat开机启动。

## 编辑文件 
```
$ vi /etc/rc.d/rc.local
```

## 添加字段
```
# jdk安装目录
$ export JAVA_HOME=/usr/local/jdk1.8.0_151
$ export JRE_HOME=$JAVA_HOME/jre 
 
# tomcat具体位置
/usr/local/tomcat/apache-tomcat-1/bin/startup.sh start
/usr/local/tomcat/apache-tomcat-2/bin/startup.sh start
/usr/local/tomcat/apache-tomcat-3/bin/startup.sh start
```

#  赋予权限
```
$ chmod +x /etc/rc.d/rc.local
```

## 重启服务
```
$ reboot
```