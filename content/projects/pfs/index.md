# Pivotal Function Service

https://pivotal.io/platform/pivotal-function-service

## 特性

PFS特性介绍，来自PFS网站首页：

- 可插拔构建系统

  PFS具有源到容器的机制，用于简化部署。 使用经过验证的组件如Cloud Foundry Buildpacks。

- 可插拔Event Source

  PFS事件源有助于从各种外部事件源（如GitHub webhooks，blob存储和数据库服务）创建Feeds。

- 可插拔Event Broker

  PFS可以与流行的消息代理轻松连接，如Kafka，Google Pub/Sub和RabbitMQ。 这些为消息传递通道提供了可靠的支持服务。

  > 备注：knative没有RabbitMQ的支持，难道是PFS扩展的？

- 可插拔的Invoker

  Pivotal将继续在PFS中开发riff调用程序模型，使开发人员能够使用简单的语言惯用接口提供流和非流功能代码。

- 事件扩展

  自动缩放，从0到1，从1到N个实例，然后返回到零个实例。

- 在Kubernetes和Istio上运行

  PFS可以帮助您体现Kubernetes和Istio的优势，即使它抽象出两种技术的复杂性。

- 使用带有函数的现代DevOps工作流程

  PFS允许您使用熟悉的，基于容器的工作流程来实现serverless方案。

- 多语种

  PFS支持在您选择的框架中创建函数 - Node.js，Spring / Java，Go，Python和Shell。