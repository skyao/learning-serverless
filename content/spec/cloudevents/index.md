# CloudEvents

## 介绍

![CloudEvents logo](https://github.com/cncf/artwork/raw/master/cloudevents/horizontal/color/cloudevents-horizontal-color.png)

事件无处不在。 但是，事件发布者倾向于以不同方式描述事件。

缺乏描述事件的常用方法意味着开发人员必须不断重新学习如何接收事件。这也限制了库，工具和基础设施的可能性，以帮助跨环境（如SDK，事件路由器或跟踪系统）发送事件数据。我们可以从事件数据中实现的可移植性和生产力总体上受到阻碍。

来到CloudEvents，这是一种以通用方式描述事件数据的规范。CloudEvents旨在简化跨服务，平台及其他方面的事件声明和发送。

CloudEvents是一项新的努力，已经获得了令人惊讶的行业兴趣，从主要的云提供商到流行的SaaS公司。CloudEvents由Cloud Native Computing Foundation（CNCF）作为沙箱级项目托管。

备注：内容来自 https://github.com/cloudevents/spec

## 历史

CNCF Severless 工作组最初是由 CNCF 技术监督委员会创立的，旨在调查 Serverless 技术和指导 CNCF 在本领域下一步可能展开的相关工作的建议。其中一项建议是创建一个通用的 Event Format，以在不同云供应商提供的Function 之间实现可移植性和事件流处理的互操作性。CloudEvents 规范因此被创建出来。

尽管 CloudEvents 的工作最初是作为 Serverless 工作组的一部分开展的，当规范到达 v0.1 里程碑之后，TOC 批准了 CloudEvents 成为一个独立的 CNCF 沙盒项目。