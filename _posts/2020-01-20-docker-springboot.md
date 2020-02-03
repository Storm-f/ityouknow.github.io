---
layout: post
title: Docker部署SpringBoot项目
date: 2020-01-20
categories: Docker,SpringBoot
tags: Docker
---
本文介绍使用Docker部署SpringBoot项目。

## 编写Dockerfile文件

```
# Docker image for springboot file run
# VERSION 0.0.1
# Author: libai
# 基础镜像使用java
FROM java:8
# 作者
MAINTAINER libai <libai@gmail.com>
# VOLUME 指定了临时文件目录为/tmp。
# 其效果是在主机 /var/lib/docker 目录下创建了一个临时文件，并链接到容器的/tmp
VOLUME /tmp
# 将jar包添加到容器中并更名为app.jar
ADD demo-0.0.1-SNAPSHOT.jar app.jar
# 运行jar包
RUN bash -c 'touch /app.jar'
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
```

## 制作镜像

* 在服务器新建一个docker文件夹
* 将 **demo-0.0.1-SNAPSHOT.jar** 和 **Dockerfile** 文件复制到服务器的docker文件夹下
* 执行下面命令

```
$ docker build -t demo-image .
```

## 启动容器

```
# -d 参数是让容器后台运行
# -p 是做端口映射，此时将服务器中的8080端口映射到容器中的8080(项目中端口配置的是8080)端口
$ docker run -d -p 8080:8080 demo-image
```

## 访问网站

浏览器直接访问：http://你的服务器ip地址:8080/
