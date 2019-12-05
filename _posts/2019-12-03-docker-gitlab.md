---
layout: post
title: Docker安装汉化的GitLab社区版和GitLab-Runner
date: 2019-12-03
categories: Docker,GitLab,GitLab-Runner
tags: GitLab
---
本文介绍使用Docker安装汉化的GitLab社区版和GitLab-Runner。

## 下载GitLab镜像

```
#搜索镜像
$ docker search gitlab
#下载镜像
$ docker pull twang2218/gitlab-ce-zh:latest
```
![](../docker-gitlab-1.jpg)
![](../docker-gitlab-2.jpg)

## 运行GitLab镜像

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
# --name：命名容器名称
# -p：将容器内部端口向外映射
# -v：将容器内数据文件夹或者日志、配置等文件夹挂载到宿主机指定目录
```

运行成功后出现一串字符串
![](../docker-gitlab-3.jpg)

进入GitLab容器
```
$ docker exec -it gitlab /bin/bash
```

## 下载GitLab-Runner镜像

```
#搜索镜像
$ docker search gitlab-runner
#下载镜像
$ docker pull gitlab/gitlab-runner:latest
```

## 运行GitLab-Runner镜像
```
$ docker run -d \
  --name gitlab-runner \
  --restart always \
  -v /data/gitlab-runner/config:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:latest
```

## 注册Runner

```
$ docker exec -it gitlab-runner gitlab-ci-multi-runner register
```

![](../docker-gitlab-4.jpg)

输入注册相关信息
```
Please enter the gitlab-ci coordinator URL:
# 示例：http://gitlab.alibaba-inc.com/ci
Please enter the gitlab-ci token for this runner:
# xxxxxx
Please enter the gitlab-ci description for this runner:
# 示例：qd_api_runner
Please enter the gitlab-ci tags for this runner (comma separated):
# 示例：hwy
Whether to run untagged builds [true/false]:
# true
Please enter the executor: docker, parallels, shell, kubernetes, docker-ssh, ssh, virtualbox, docker+machine, docker-ssh+machine:
# docker
Please enter the default Docker image (e.g. ruby:2.1):
# maven:3-jdk-8
```

注册完成:

![](../docker-gitlab-5.jpg)
