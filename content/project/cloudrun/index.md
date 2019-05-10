---
date: 2018-10-25T09:51:00+08:00
title: Google Cloud Run产品
weight: 440
description : "Google Cloud Run产品"
---

在旧金山举办的 Google Cloud Next 2019 大会上，Google Cloud Run正式发布。

 Cloud Run是一个类似 Microsoft Azure ACI，AWS Fargate 的容器实例服务。但与 ACI 和 Fargate 这些基于虚拟机技术栈的实现不同，Cloud Run 服务是基于 [Knative](https://github.com/knative/) 的。而 knative 是 Kubernetes 原生的 Serverless 基础设施项目。

这是业界第一个基于 Knative + Kubernetes 的 Serverless 服务。

而且，cloud run 是运行于 gVisor 之上的。