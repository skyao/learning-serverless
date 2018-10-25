---
date: 2018-10-25T14:51:00+08:00
title: Azure Functions
weight: 420
description : "微软Azure Functions项目"
---

[Azure Functions](https://azure.microsoft.com/zh-cn/services/functions/) 是一种事件驱动型计算体验，通过它可执行采用所选编程语言编写的代码，而不必担心服务器的问题。得益于按需扩展，绝不为闲置容量付费。

## 介绍

### 无服务器计算的介绍

暂时不考虑基础结构，更快地生成应用

#### 无服务器计算的承诺

如果可以将所有时间都花在生成和部署强大应用上，而无需花时间管理服务器，这会有什么不同？由于为你托管了需要运行并缩放应用的基础结构，无服务器计算可做到这一点。将精力集中在业务上。将资源从基础结构管理重定向到创新，使应用更快上市。

#### 什么是无服务器计算？

无服务器计算是服务器、基础结构和操作系统的抽象化。生成无服务器应用时，不需要预配和管理任何服务器，这样便可将注意力从基础结构问题上移开。无服务器计算由云中准实时发生的对事件和触发器的反应驱动。作为完全托管服务，服务器管理和容量规划对开发人员来说不可见，且仅基于消耗的资源或代码运行的实际时间计费。

#### 为什么生成无服务器应用？

- 从完全托管的服务获益

  减轻团队管理服务器的负担。通过利用完全托管的服务，专注于商业逻辑并避免繁重的管理任务。通过无服务器体系结构，只需部署代码，它随即就会以高可用性运行。

- 灵活缩放

  无服务器计算从零扩展到瞬间（几秒钟内）处理数万个并发函数，可匹配任何工作负载，而无需进行缩放配置 - 它对事件和触发器做出准实时反应。

- 只为使用的资源付费

  通过无服务器体系结构，只需为代码运行的时间付费。无服务器计算由事件驱动，一旦由事件触发资源后即会分配这些资源。仅通过次秒级计费方式，对执行代码所用的时间和资源收费。


备注：上面三个是serverless目前的主要卖点，大家的考虑和出发点都差不多，尤其是后面两个。


## 资料

- [Azure Functions Provider Documentation](https://serverless.com/framework/docs/providers/azure/)



## 核心概念

https://serverless.com/framework/docs/providers/azure/guide/intro/

无服务器框架可帮助您使用Azure功能开发和部署无服务器应用程序。 它是一个CLI，提供开箱即用的结构，自动化和最佳实践，使您可以专注于构建由 Functions 和 Events 组成的复杂，事件驱动，无服务器架构。

无服务器框架与其他应用程序框架不同，因为：

- 将代码作为基础设施来管理
- 支持多种语言（Node.js，Python，Java等）

以下是Framework的主要概念以及它们与Azure Functions的关系......

#### Functions

Function是Azure Function。它是一个独立的部署单元，就像微服务一样。它只是部署在云中的代码，通常用于执行单个作业，例如：

- 将用户保存到数据库
- 处理数据库中的文件
- 执行计划任务

您可以在代码中执行多个作业，但我们不建议您在没有充分理由的情况下执行此操作。关注点分离是最好的，框架旨在帮助您轻松开发和部署Function，以及管理大量Function。

#### Events

触发Azure Function执行的任何内容都被框架视为Event。 Event是Azure功能上的平台Event，例如：

- HTTP触发器（例如，用于REST API）
- 预定计时器（例如，每5分钟运行一次）
- 服务总线队列触发器（例如来自另一个Function的工作项）
- 物联网/事件中心消息（例如，来自设备或服务的消息）
- Webhook触发（例如，Github项目更新）
- 和更多...

在无服务器框架中为Azure Function定义事件时，框架将自动将其转换为该事件所需的绑定，并配置Function以侦听它。

#### Services

Service是框架的组织单位。 您可以将其视为项目文件，但您可以为单个应用程序提供多个服务。 您可以在一个名为serverless.yml（或serverless.json或serverless.js）的文件中定义您的Function，触发它们的Event以及Function使用的资源。 它看起来像这样：

```yaml
# serverless.yml

service: users

functions: # Your "Functions"
  usersCreate:
    events: # The "Events" that trigger this function
      - http: true
        x-azure-settings:
          name: req
          methods:
           - post
          route: /users/create
  usersDelete:
    events:
      - http: true
        x-azure-settings:
          name: req
          methods:
           - delete
          route: /users/delete
```

通过运行无服务器部署与Framework一起部署时，serverless.yml中的所有内容都会立即部署。

#### Plugins

您可以使用插件覆盖或扩展Framework的功能。 每个serverless.yml都可以包含一个`plugins：` 属性，可以有多个插件。

```yaml
# serverless.yml

plugins:
  - serverless-plugin-identifier
  - serverless-another-plugin
```

插件是自定义JavaScript代码，用于在无服务器框架内创建新的或扩展现有命令。 无服务器框架只是核心中提供的一组插件。 如果您或您的组织有特定的工作流程，请安装预先编写的插件或编写插件以根据您的需要自定义框架。 外部插件的编写方式与核心插件完全相同。

## TBD

### 俊雄的输入

azure 上， serverless 是作为一个 solution 存在的

serveless solution 的核心产品是 azure functions。

他主要和 event grid / logic apps / azure cosmosdb 是哪个产品组成解决方案

event grid 是支持 cloud events 的 eventing 产品

几个典型的解决方案， application backend/ realtime straming / task automation / saas extension

最后一个应该是 端点 那家新收购公司的应用场景





azure event 产品的核心定位是  event router 。

mapping and routing events from multiple event sources to multiple target systems.