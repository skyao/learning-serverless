---
date: 2018-10-25T09:50:00+08:00
title: 概述
weight: 401
description : "serverless项目概述"
---



## Functions-as-a-Service (FaaS)

将逻辑编写为响应各种事件的小块代码。

- AWS Lambda
- Azure Functions
- 基于Apache OpenWhisk的IBM Cloud Functions
- Google Cloud Functions
- 华为Function Stage 和 Function Graph
- Kubeless
- iron.io
- funktion
- fission
- nuclio

## 时间线

- 虽然按需或“花多少用多少”模式的概念可追溯到2006年和一个名为Zimki的平台
- serverless一词的第一次使用是2012年来自Iron.io的IronWorker产品 ，一个基于容器的分布式按需工作平台。

从那以后，公共云和私有云都出现了更多serverless实现:

- 首先是BaaS产品，例如2011年的Parse和2012年的Firebase（分别由Facebook和谷歌收购）。
- 2014年11月，[AWS Lambda](https://aws.amazon.com/lambda/)推出，这是第一个Serverless平台
- 2016年初在Bluemix上宣布了[IBM OpenWhisk on Bluemix](https://www.ibm.com/cloud-computing/bluemix/openwhisk)（现在是IBM Cloud Functions，其核心开源项目成为[Apache OpenWhisk](http://openwhisk.incubator.apache.org/)）
- [Google Cloud Functions](https://cloud.google.com/functions/)
- [Microsoft Azure Functions](https://azure.microsoft.com/services/functions/)
- [华为Function Stage](http://www.huaweicloud.com/product/functionstage.html)于2017年推出。

在云服务厂商之外，开源社区也涌现出很多优秀的Serverless框架，比如

- [Apache OpenWhisk](https://openwhisk.apache.org/)
- [Spring Cloud Function](http://cloud.spring.io/spring-cloud-function/)
- [Lambada Framework](https://github.com/lambadaframework/lambadaframework)
- [webtask](https://webtask.io/)