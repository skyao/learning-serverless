---
date: 2018-10-25T17:10:00+08:00
title: Lambda Layers
weight: 412
menu:
  main:
    parent: "project-aws-lambda"
description : "Lambda Layers"
---

## 背景

asw 在2018年11月推出两个新功能，声称将使无服务器开发变得更加容易：

- Lambda Layers：一种集中管理在多个函数之间共享代码和数据的方法
- Lambda Runtime API，一个使用任何编程语言或特定语言版本的简单接口，用于开发函数

这两个功能可以一起使用：Runtime可以作为Layer共享，以便开发人员可以在创建Lambda函数时选择它们并使用自己喜欢的编程语言。

## Lambda Layers介绍

构建serverless应用程序时，通常会在Lambda函数之间共享代码。可以是由多个函数使用的自定义的代码，或者是用来简化业务逻辑实现的标准库。

以前，必须将此共享代码与所有使用它的函数一起打包和部署。现在，您可以将常用组件放在ZIP文件中并将其作为Lambda Layer上传。您的函数代码不需要更改，并且可以像通常那样引用Layer中的库。

可以对Layer进行版本控制以管理多个更新，每个版本都是不可变的。删除版本或版本的使用权限被撤销时，之前使用它的函数将继续有效，但您将无法创建新的函数。

在函数的配置中，最多可以引用五个Layer，其中一个Layer可以选择是runtime。调用该函数时，将按照您提供的顺序在 /opt 中安装Layer。顺序很重要，因为Layer都是在同一路径下提取的，因此每个Layer都可能覆盖前一个Layer。这个方式可用于自定义环境。例如，第一个Layer可以是rumtime，第二个Layer可以添加所需库的特定版本。

图层可以在AWS账户内使用，在账户之间共享，也可以与广泛的开发人员社区公开共享。

### Layer的优点

- 实现关注点分离：分离业务逻辑和依赖
- 使函数代码更小，更专注于想要构建的内容
- 加快部署速度，因为必须打包和上载的代码更少了，并且可以重用依赖

## Lambda Runtime API

可以在创建或更新函数时选择自定义runtime。

该函数必须包含（在其代码或Layer中）一个名为bootstrap的可执行文件，负责代码（可以使用任何编程语言）和Lambda环境之间的通信。

运行时bootstrap使用简单的基于HTTP的接口来获取新调用的事件有效负载，并从函数返回响应。有关接口端点和函数处理程序的信息作为环境变量共享。

为了执行代码，您可以使用可在Lambda执行环境中运行的任何内容。例如，您可以为您选择的编程语言提供解释器。

只有要管理或发布自己的rumtime时，才需要了解Runtime API的工作原理。作为开发人员，您可以快速使用作为Layer共享的runtime。

Runtime API是我们在Lambda中支持新语言的未来。

使用运行时和图层无需额外费用。

参考资料：

- [New for AWS Lambda – Use Any Programming Language and Share Common Components](https://amazonaws-china.com/cn/blogs/aws/new-for-aws-lambda-use-any-programming-language-and-share-common-components/)
- [AWS Lambda Layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html) @Lambda developer guide
- [Custom AWS Lambda Runtimes](https://docs.aws.amazon.com/lambda/latest/dg/runtimes-custom.html) @Lambda developer guide