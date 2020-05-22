---
date: 2018-10-24T23:10:00+08:00
title: SDK需求
weight: 316
menu:
  main:
    parent: "spec-cloudevents"
description : "CloudEvents规范中的SDK需求"
---

> 备注：内容来自　https://github.com/cloudevents/spec/blob/master/SDK.md



本文档的目的是描述针对CloudEvents的新软件开发工具包（SDK）的最低要求。这些SDK的设计和实施是为了增强和加快CloudEvents的集成。作为社区工作的一部分，CloudEvents团队承诺支持和维护以下SDK。

- [CSharp](https://github.com/cloudevents/sdk-csharp)
- [Go SDK](https://github.com/cloudevents/sdk-go)
- [Java SDK](https://github.com/cloudevents/sdk-java)
- [JavaScript SDK](https://github.com/cloudevents/sdk-javascript)
- [Python SDK](https://github.com/cloudevents/sdk-python)
- [Ruby SDK](https://github.com/cloudevents/sdk-ruby)

本文档旨在为 SDK 作者提供指导和要求。本文档旨在与 CloudEvents 规范保持同步更新。

## 技术需求

每个SDK必须满足这些要求。

- 支持CloudEvents 的里程碑版本和正在进行的开发版本。
	* 将Canonical Event编码为特定于传输的编码消息。
	* 将特定于传输的编码消息解码为Canonical事件。
- 熟练使用编程语言。
	* 使用当前的语言版本。
- 支持结构化和二进制编码的HTTP传输渲染。

### 对象模型结构准则

每个SDK将提供一个通用的CloudEvents类/对象/结构，该类/对象/结构表示事件的典型形式。

该 SDK 应使用户能够绕过 CloudEvents Event 对象的特定传输编码和解码。对象的一般流程应该是：

Event (-> Message) -> Transport

和

Transport (-> Message) -> Event

不需要SDK来实现传输的包装器，重点应该是允许编程模型与高层次的Event对象一起工作，并提供工具将Event转化成可以与所选的实现传输一起使用的东西。

在高层次上，SDK需要能够帮助完成以下任务。

- 组合事件。
- 编码事件，给定传输和编码（如果适当的话，将其编码为传输消息）。
- 解码特定于传输的消息、请求或响应（如果适当的话，到一个传输消息）为事件。

#### 组合事件

提供一种方便的方法，既可以组成单一消息，也可以组成许多消息。实现者将需要一种方法来快速建立事件数据并将其转换为CloudEvents编码的事件。在实践中，事件的组成往往有两个方面。

1. 事件创建

	"我有一个格式不是CloudEvent的数据，我想让它成为CloudEvent。"

2. 事件变化

	"我有一个CloudEvents格式化的事件，我需要将它变成不同的事件。"
	"我有一个CloudEvents格式化的事件，我需要修改事件。"

对于SDK语言来说，事件的创建是非常习以为常的。

事件变化往往用访问器模式来解决，比如getters和setter。但是可以利用直接的 key 访问，也可以利用命名的 key 访问器函数。

无论是哪种情况，都必须有一个方法根据参数设置来验证生成的Event对象，最重要的是CloudEvents规范版本。

#### 对事件进行编码/解码

每个SDK都支持对事件进行编码和解码。结构化编码是最容易支持的，因为它只是json，但二进制编码对于每个传输方式来说是相当定制的。

#### 数据

从事件中访问数据有一些考虑，事件可以被编码成base64形式，作为结构化数据，或者像json这样的线上格式。一个SDK必须提供一种方法来将这些格式的数据解压成原生格式。

#### 扩展

支持CloudEventss的扩展又是成语，但镜像数据访问的方法似乎是可行的。

#### 验证

验证必须在单个事件上进行。验证必须考虑到规格版本，以及每个版本的规格所提出的所有要求。

## 文档

每个SDK必须提供至少使用HTTP传输的例子。

- 组成事件。
- 对组成的事件进行编码和发送。
- 接收和解码事件。

