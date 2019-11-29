---
layout: post
title: Docker安装汉化的GitLab社区版
date: 2019-12-01
categories: Docker,GitLab
tags: GitLab
---
本文介绍使用Docker安装汉化的GitLab社区版。

## 一、 下载GitLab镜像

```
#搜索镜像
$ docker search gitlab
#下载镜像
$ docker pull twang2218/gitlab-ce-zh:latest
```
![](../docker-gitlab-1.jpg)
![](../docker-gitlab-2.jpg)

## 二、 运行GitLab镜像

```
$ docker run -d  \
--name gitlab \
--restart always \
-p 443:443 \
-p 80:80 \
-p 222:22 \
-v /data/gitlab/config:/etc/gitlab \
-v /data/gitlab/logs:/var/log/gitlab \
-v /data/gitlab/data:/var/opt/gitlab \
twang2218/gitlab-ce-zh
# -d：后台运行
# -p：将容器内部端口向外映射
# --name：命名容器名称
# -v：将容器内数据文件夹或者日志、配置等文件夹挂载到宿主机指定目录
```

运行成功后出现一串字符串
![](../docker-gitlab-3.jpg)
