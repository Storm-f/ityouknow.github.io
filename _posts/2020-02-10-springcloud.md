---
layout: post
title: Spring Cloud简介
date: 2020-02-10
categories: Spring Cloud
tags: Spring Cloud
---
本文介绍Spring Cloud。

## 微服务

微服务架构是一种架构模式，将单一应用程序划分为一组小的服务，服务之间互相协调、互相配合，为用户提供最终价值。每个服务运行在其独立的进程中，服务之间采用轻量级的通讯机制相互沟通（Restful API、RPC等）。每个服务都围绕着具体的业务进行构建，并且能够被独立部署到生产环境、类生产环境等。

## 微服务的优缺点

### 微服务的优点

* 每个服务足够小，聚焦于一个业务功能或需求
* 松耦合，每个小服务都有意义，无论是开发阶段还是部署阶段
* 可以使用不同的语言开发
* 易于和第三方服务集成，比如Jenkins，Hudson，Bambook
* 每个微服务都有自己的存储能力，可以有自己的数据库，也可以有统一的数据库
* 微服务允许你使用融合最新技术
* 容易扩大开发团队，可以针对某个服务组建开发团队。

### 微服务的缺点

* 开发人员要处理分布式系统的复杂性
* 微服务数量多，运维难度增加
* 系统部署依赖增加
* 各个服务之间通讯成本增加
* 数据的一致性问题
* 系统集成测试
* 性能监控

## Spring Cloud

Spring Cloud是一系列框架的有序集合。它利用Spring Boot的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、消息总线、负载均衡、断路器、数据监控等，都可以用Spring Boot的开发风格做到一键启动和部署。Spring并没有重复制造轮子，它只是将目前各家公司开发的比较成熟、经得起实际考验的服务框架组合起来，通过Spring Boot风格进行再封装屏蔽掉了复杂的配置和实现原理，最终给开发者留出了一套简单易懂、易部署和易维护的分布式系统开发工具包。

## SpringCloud和SpringBoot的关系？

* SpringBoot是微观的，只关注于一个服务的实现。
* SpringCloud是分布式微服务的一站式解决方案，它关注的是宏观的。
* SpringBoot不依赖于SpringCloud，而SpringCloud依赖于SpringBoot。

## 微服务技术栈

微服务条目 | 技术
------------- | -------------
服务开发 | SpringBoot，Spring，SpringMVC
服务配置与管理 | Archaius，Diamond
服务注册与发现 | Eureka，Consul，Zookeeper
服务调用 | 	Restful API，RPC，gRPC
服务熔断器 | Hystrix，Envoy
负载均衡	| Ribbon，Nginx
服务接口调用	| Feign
消息队列	| Kafka，RabbitMQ，ActiveMQ
服务配置中心管理	| SpringCloud Config，Chef
服务路由(API网关)	| SpringCloud Gateway，Zuul
服务监控	| Zabbix，Nagios，Metrice，Spectator
全链路追踪	| Zipkin，Brave，Dapper
服务部署 | Docker，OpenStack，Kubernetes
数据流操作开发包 | SpringCloud Stream
时间消息总线	| SpringCloud Bus
