---
title: "什么是 serverless？"
linkTitle: "什么是 serverless？"
weight: 10
description: >
  什么是 serverless ？
---


### aws

https://aws.amazon.com/what-is/serverless-computing/

Serverless computing is an application development model where you can build and deploy applications on third-party managed server infrastructure. All applications require servers to run. But in the serverless model, a cloud provider manages the routine work; they provision, scale, and maintain the underlying infrastructure. The cloud provider handles several tasks, such as operating system management, security patches, file system and capacity management, load balancing, monitoring, and logging. As a result, your developers can focus on application design and still receive the benefits of cost-effective, efficient, and massively scalable server infrastructure.

无服务器计算是一种应用程序开发模型，基于此模型您可以在第三方托管服务器基础设施上构建和部署应用程序。所有应用程序都需要服务器才能运行。但是在无服务器模型中，云服务提供商管理常规工作；他们预置、扩展和维护底层基础设施。云服务提供商可处理多项任务，例如操作系统管理、安全补丁、文件系统和容量管理、负载平衡、监控和日志记录等。因此，您的开发人员可以专注于应用程序设计，同时仍能受益于经济、高效且可大规模扩展的服务器基础设施。

### Google

https://cloud.google.com/discover/what-is-serverless-computing?hl=en

Serverless computing is a cloud computing execution model that allocates machine resources on an as-used basis. Under a serverless model, developers can build and run applications without having to manage any servers and pay only for the exact amount of resources used. Instead, the cloud service provider is responsible for provisioning, managing, and scaling the cloud infrastructure that runs the application code.

无服务器计算是一种按需分配机器资源的云计算执行模型。在无服务器模式下，开发者无需管理任何服务器即可构建和运行应用程序，仅需为实际使用的资源付费。云服务提供商负责为运行应用程序代码的云基础设施进行配置、管理和扩展。

Serverless computing, despite its name, doesn't eliminate servers. Rather, it streamlines application development by abstracting away routine infrastructure tasks. This means you don't see, configure, manage, or scale the underlying machines running your applications. Essentially, you pay for the server's service, not the server itself.

尽管名称如此，无服务器计算并未消除服务器。它通过抽象化常规基础设施任务来简化应用开发流程。这意味着开发者无需接触、配置、管理或扩展底层运行应用的机器。本质上，您支付的是服务器服务费用，而非服务器本身。

From the development perspective, it’s as if there are no servers at all — developers write the code, deploy it to production, and the cloud provider handles the rest.

从开发视角看，这如同完全不存在服务器——开发者编写代码、部署至生产环境，其余工作均由云服务商处理。

### IBM

https://www.ibm.com/think/topics/serverless

Serverless computing is an application development and execution model that enables developers to build and run application code without provisioning or managing servers or back-end infrastructure.

无服务器计算是一种应用程序开发和执行模型，它使开发人员能够构建和运行应用程序代码，而无需配置或管理服务器或后端基础设施。

### redhat

https://www.redhat.com/en/topics/cloud-native-apps/what-is-serverless

Serverless is a cloud-native development model that allows developers to build and run applications without having to manage servers. The term “serverless” doesn’t mean there are no servers. It means the servers are abstracted away from application development. A cloud provider handles the routine work of provisioning, maintaining, and scaling the server infrastructure. 

无服务器是一种云原生开发模式，允许开发人员构建和运行应用程序而无需管理服务器。术语“无服务器”并非意味着没有服务器，而是指服务器已被从应用程序开发中抽象出来。云服务提供商负责处理服务器基础设施的配置、维护和扩展等日常工作。

With serverless, developers package their code in containers for deployment. Once deployed, serverless apps respond to demand and automatically scale up or down as needed. Serverless offerings from public cloud providers are usually metered on demand using an event-driven execution model. As a result, when a serverless function is sitting idle, it doesn’t cost anything.

采用无服务器架构时，开发者需将代码封装为容器进行部署。部署完成后，无服务器应用将根据需求自动扩展或缩减规模。公共云供应商提供的无服务器服务通常采用事件驱动的执行模型，按需计量计费。因此当无服务器函数处于空闲状态时，不会产生任何费用。

### cloudflare

https://www.cloudflare.com/learning/serverless/what-is-serverless/

Serverless computing is a method of providing backend services on an as-used basis. Servers are still used, but a company that gets backend services from a serverless vendor is charged based on usage, not a fixed amount of bandwidth or number of servers.

https://www.cloudflare.com/zh-cn/learning/serverless/what-is-serverless/

无服务器计算是一种按需提供后端服务的方法。无服务器提供者允许用户编写和部署代码，而不必担心底层基础设施。从无服务器提供商获得后端服务的公司将根据计算量来付费，由于这种服务是自动扩展的，不必预留和付费购买固定数量的带宽或服务器。请注意，虽然名为“无服务器”，实际上依然需要物理服务器，只不过开发人员不需要考虑服务器而已。

### wikipedia

https://en.wikipedia.org/wiki/Serverless_computing

Serverless computing is "a cloud service category in which the customer can use different cloud capability types without the customer having to provision, deploy and manage either hardware or software resources, other than providing customer application code or providing customer data. 

无服务器计算是一种云服务类别，客户无需配置、部署和管理硬件或软件资源（仅需提供客户应用程序代码或客户数据），即可使用不同类型的云能力。

Serverless computing represents a form of virtualized computing."

无服务器计算属于虚拟化计算的一种形式。

Serverless computing enables developers to focus on business logic by abstracting the complities of infrastructure management.

无服务器计算通过抽象化基础设施管理的复杂性，使开发人员能够专注于业务逻辑。

### alibaba

https://www.alibabacloud.com/en/knowledge/what-is-serverless

Serverless architecture, also referred to as FaaS (Functions as a Service) or Backend As A Service, enables the execution of an application via ephemeral and stateless containers; The containers are created right at the moment an event occurs and triggers a need for an action. Thus, it is event driven. Applications, bundled as one or more functions, are uploaded to a platform and then executed, scaled, and billed in response to the exact demand needed at the moment. Serverless does not mean “without a server.” Rather, infrastructure orchestration details are hidden from the user and managed by the serverless platform provider.

无服务器架构，亦称为FaaS（函数即服务）或后端即服务，通过短暂且无状态的容器实现应用程序的执行；这些容器在事件发生并触发操作需求时即时创建，因此属于事件驱动型架构。应用程序被封装为一个或多个函数，上传至平台后，将根据实时需求进行执行、扩展及计费。无服务器架构并非意味着“没有服务器”，而是将基础设施的编排细节隐藏于用户视线之外，由无服务器平台提供商统一管理。

### databricks

https://www.databricks.com/glossary/serverless-computing

Serverless computing is an application development model that allows developers to build, deploy and run applications without managing servers or back-end infrastructure. “Serverless” doesn’t mean servers aren’t used, but that they are fully managed by a cloud service provider or vendor, so developers don’t need to interact with them. The provider handles provisioning the cloud infrastructure required to run the code, scale infrastructure as needed and other infrastructure tasks. This allows developers to focus solely on writing code, integrating applications and managing data, while working with efficient, scalable, fully managed infrastructure.  

无服务器计算是一种应用程序开发模式，允许开发人员在无需管理服务器或后端基础设施的情况下构建、部署和运行应用程序。“无服务器”并非意味着不使用服务器，而是指服务器完全由云服务提供商或供应商管理，开发者无需与之交互。服务商负责配置运行代码所需的云基础设施、按需扩展基础设施以及处理其他基础设施任务。这使开发者能够专注于编写代码、集成应用程序和管理数据，同时利用高效、可扩展且完全托管的基础设施开展工作。