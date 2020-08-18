# mirror

## 前言

`mirror`项目主要为解决寻找专业摄影师难,线下活动寻找模特难的用户痛点,项目采用现阶段流行技术实现。

## 项目文档

- 文档地址：[准备中](http://)

## 项目介绍

`mirror`项目基于SpringCloudAlibaba+MyBatis实现，可采用Docker容器化部署。

### 组织结构

``` lua
mirror
├── mirror-backend -- 系统接口
├── mirror-mbg -- MyBatisGenerator生成的数据库操作代码
├── mirror-util -- 工具类及通用代码
├── mirror-gateway -- 网关基于nacos
└── mirror-待定 -- 预留位
```
### 表前缀介绍

``` lua
mirror
├── ums_* -- 用户相关
├── pms_* -- 作品相关
├── oms_* -- 订单(约拍)相关
├── sms_* -- 营销相关
└── *_* -- 预留位
```

### 技术选型

#### 使用技术

| 技术                  | 说明                | 地址                                                 |
| -------------------- | ------------------- | --------------------------------------------------- |
| Spring-Cloud-Alibaba | MVC框架            | https://spring.io/projects/spring-boot               |
| Alibaba-Nacos        | 云服务管理平台       | https://github.com/alibaba/nacos                     |
| Alibaba-Sentinel     | 流量控制组件        | https://github.com/rzwitserloot/lombok               |
| Alibaba-Config       | Nacos下的配置中心    | https://github.com/alibaba/nacos                     |
| MyBatis              | ORM框架             | http://www.mybatis.org/mybatis-3/zh/index.html       |
| MyBatisGenerator     | 数据层代码生成      | http://www.mybatis.org/generator/index.html           |
| Swagger-UI           | 文档生产工具        | https://github.com/swagger-api/swagger-ui            |
| Redis                | 分布式缓存          | https://redis.io/                                    |
| Docker               | 应用容器引擎        | https://www.docker.com                               |
| Druid                | 数据库连接池        | https://github.com/alibaba/druid                     |
| LogStash             | 日志收集工具        | https://github.com/logstash/logstash-logback-encoder |
| ActiveMQ             | 消息队列            | https://activemq.apache.org/                         |
| Lombok               | 简化对象封装工具    | https://github.com/rzwitserloot/lombok               |
| Jenkins              | 自动化部署工具      | https://github.com/jenkinsci/jenkins                 |


## 环境搭建

### 开发工具

| 工具           | 说明                | 地址                                            |
| ------------- | ------------------- | ----------------------------------------------- |
| IDEA          | 开发IDE             | https://www.jetbrains.com/idea/download         |
| RedisDesktop  | redis客户端连接工具 | https://redisdesktop.com/download               |
| Robomongo     | mongo客户端连接工具 | https://robomongo.org/download                  |
| X-shell       | Linux远程连接工具   | http://www.netsarang.com/download/software.html |
| Navicat       | 数据库连接工具      | https://navicat.com.cn/products/             |

### 开发环境

| 工具           | 版本号  | 地址                                                         |
| ------------- | ------ | ------------------------------------------------------------ |
| JDK           | 1.8    | https://www.oracle.com/java/technologies/javase-downloads.html |
| Mysql         | 5.7    | https://www.mysql.com/                                       |
| Redis         | 5.0    | https://redis.io/download                                    |
| Elasticsearch | 6.2.2  | https://www.elastic.co/downloads                             |
| ActiveMQ      | 5.15.10 | https://activemq.apache.org/                                 |
| Nginx         | 1.10   | http://nginx.org/en/download.html                            |

### 搭建步骤

> Docker环境部署
- 配置Dockerfile相关信息
- 代码提交至GitLab 
- 通过Jenkins创建任务并配置好项目地址
- 对Jenkins任务配置pom信息:mirror-backend/pom.xml
- 对Jenkins任务配置maven命令:clean package docker:build -DpushImage
- 通过Jenkins进行Build
- 通过Rancher启动服务并配置负载、扩容、缩容等..
- Rancher文档地址:https://rancher2.docs.rancher.cn/