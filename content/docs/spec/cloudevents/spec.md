---
date: 2018-10-24T23:00:00+08:00
title: CloudEvents规范
weight: 311
description : "介绍CloudEvents规范"
---


## 介绍

>  备注：以下内容来自 https://github.com/cloudevents/spec

![CloudEvents logo](images/cloudevents-horizontal-color.png)

事件无处不在。然而，事件生产者倾向于以不同的方式来描述事件。

缺乏通用的描述事件的方式意味着开发人员必须不断地重新学习如何消费事件。这也限制了类库、工具和基础设施在跨环境时发送事件数据的潜力，如SDK、事件路由器或跟踪系统等。我们从事件数据中实现的可移植性和生产力总体上受到了阻碍。

CloudEvents是一个用通用格式描述事件数据的规范，以提供跨服务、跨平台和跨系统的互操作性。

CloudEvents得到了大量的行业关注，从主要的云提供商到流行的SaaS公司都有。CloudEvents由云原生计算基金会（CNCF）主办，于2018年5月15日获批为云原生沙盒级项目。

## CloudEvents文档

包括核心规范，可选规范和额外文档三部分。

如果是 CloudEvents 的新手，建议先阅读 Primer，了解规范的目标和设计决策，然后继续阅读核心规范。

由于并非所有事件生产者都会默认生成 CloudEvents，因此有文档描述了将一些常用事件适配到 CloudEvents 的推荐过程，请参阅 CloudEvents Adapters。

## 流程

CloudEvents项目致力于根据[设计目标]({{< relref "spec.md#设计目标" >}})正式确定[规范]({{< relref "spec.md" >}})，设计目标侧重于生成和响应事件的系统之间的互操作性。

为了实现这些目标，项目必须描述：

- 促进互操作性的事件的公共属性
- 一个或多个现在正在使用或计划由其成员构建的通用体系结构
- 如何将事件从生产者传输到消费者，通过至少一种协议
- 识别并解决互操作性所需的任何其他内容


