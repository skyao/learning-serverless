---
date: 2018-10-24T23:00:00+08:00
title: CloudEvents规范
weight: 310
description : "介绍CloudEvents规范"
---

CloudEvents是一种以通用方式描述事件数据的规范。CloudEvents旨在简化跨服务，平台及其他方面的事件声明和发送。CloudEvents　最初由　CNCF Severless 工作组提出。

> 备注：以下内容来自 https://github.com/cloudevents/spec

## 介绍

![CloudEvents logo](images/cloudevents-horizontal-color.png)

事件无处不在。 但是，事件发布者倾向于以不同方式描述事件。

缺乏描述事件的常用方法意味着开发人员必须不断重新学习如何接收事件。这也限制了库，工具和基础设施的可能性，以帮助跨环境（如SDK，事件路由器或跟踪系统）发送事件数据。我们可以从事件数据中实现的可移植性和生产力总体上受到阻碍。

来到CloudEvents，这是一种以通用方式描述事件数据的规范。CloudEvents旨在简化跨服务，平台及其他方面的事件声明和发送。

CloudEvents是一项新的努力，已经获得了令人惊讶的行业兴趣，从主要的云提供商到流行的SaaS公司。CloudEvents由Cloud Native Computing Foundation（CNCF）作为沙箱级项目托管。

## 历史

CNCF Severless 工作组最初是由 CNCF 技术监督委员会创立的，旨在调查 Serverless 技术和指导 CNCF 在本领域下一步可能展开的相关工作的建议。其中一项建议是创建一个通用的 Event Format，以在不同云供应商提供的Function 之间实现可移植性和事件流处理的互操作性。CloudEvents 规范因此被创建出来。

尽管 CloudEvents 的工作最初是作为 Serverless 工作组的一部分开展的，当规范到达 v0.1 里程碑之后，TOC 批准了 CloudEvents 成为一个独立的 CNCF 沙盒项目。

## 流程

CloudEvents项目致力于根据[设计目标]({{< relref "spec.md#设计目标" >}})正式确定[规范]({{< relref "spec.md" >}})，设计目标侧重于生成和响应事件的系统之间的互操作性。

为了实现这些目标，项目必须描述：

- 促进互操作性的事件的公共属性
- 一个或多个的通用体系结构,现在正在使用或计划由其成员构建
- 如何将事件从生产者传输到消费者，通过至少一种协议
- 识别并解决互操作性所需的任何其他内容


