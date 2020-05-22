---
date: 2018-10-24T23:10:00+08:00
title: HTTP Protocol Binding
weight: 315
menu:
  main:
    parent: "spec-cloudevents"
description : "CloudEvents规范中的HTTP Protocol Binding"
---

> 备注：内容来自　https://github.com/cloudevents/spec/blob/v1.0/http-protocol-binding.md

## 摘要

CloudEvents 的 HTTP 协议绑定定义了如何将事件映射到 HTTP 1.1 请求和响应消息。

## 1. 简介

[CloudEvents](https://github.com/cloudevents/spec/blob/v1.0/spec.md)是事件的结构和元数据描述的标准化且与协议无关的定义。该规范定义了如何在[HTTP 1.1](https://tools.ietf.org/html/rfc7230)请求和响应消息中使用CloudEvents规范中定义的元素。

### 1.1 Conformance

本文档中的关键词 "MUST"、"MUST NOT"、"MUST NOT"、"REQUIRED"、"SHALL"、"SHALL NOT"、"SHOULD"、"SHOULD NOT"、"RECOMMENDED"、"MAY "和 "OPTIONAL "等，应按RFC2119中的解释。

### 1.2 与 HTTP 的关系

本规范没有规定约束特定HTTP方法的使用或处理规则，也没有约束用于传输或请求事件的HTTP目标资源。

事件可以通过所有支持有效载荷体传输的标准或应用程序定义的HTTP请求方法来传输。事件也可以在HTTP响应中以及与允许有效载荷体传输的所有HTTP状态码一起传输。

这里所有显示HTTP方法、HTTP目标URI和HTTP状态码的例子都是非规范性的说明。

本规范也同样适用于与 HTTP 1.1语义兼容的 HTTP/2（RFC7540）。

> 注意：也适用于HTTP/2

### 1.3 内容模式

本规范定义了传输事件的三种内容模式：二进制（binary）、结构化（structured）和批量（batched）。每个符合规范的实现都应该支持二进制（binary）和结构化（structured）模式。

在二进制内容模式下，事件 data 的值被放置到HTTP请求或响应的主体（body）中，并在HTTP Content-Type header中以 datacontenttype属性的值声明其媒体类型；所有其他事件属性都被映射到HTTP头。

在结构化内容模式下，事件元数据属性和事件数据被放置到HTTP请求或响应body中，使用事件格式。

在批量内容模式中，多个事件使用支持批量的事件格式，分批放入单个HTTP请求或响应body中。

### 1.4 事件格式

与结构化内容模式一起使用的事件格式，定义了事件如何以特定的数据格式表达。本规范的所有实现必须支持非批处理的JSON事件格式，但也可以支持任何其他格式，包括专有格式。

事件格式可以额外定义事件批处理的表达方式。这些格式可以与批处理内容模式一起使用。

### 1.5 安全

本规范没有为HTTP引入任何新的安全特性，也没有规定要使用特定的现有特性。本规范同样适用于TLS上的HTTP。

### 2. CloudEvents 属性的使用

本规范没有进一步定义任何核心 CloudEvents 事件属性。

此映射是为了防止变化（包括事件属性的添加和删除），并适应供应商对事件元数据的扩展。

### 2.1 datacontententtype 属性

datacontententtype属性被认为包含一个符合RFC2046的媒体类型表达式。

## 2.2 data

data 被假定为包含由 datacontenttype 属性声明的不透明的应用数据。

应用程序可以自由地以其选择的任何内存中的表示方式来保存信息，但是由于该值是按照本规范中的定义被转接到HTTP中的，因此假设 data 的值是以字节序列的形式提供的。

例如，如果声明的 datacontenttype 为 application/json;charset=utf-8，则期望 data 值以 UTF-8 编码的JSON文本形式提供给HTTP。

## 3. HTTP消息映射

HTTP请求和响应消息的事件绑定是相同的。

内容模式是由事件的发送方选择的，发送方可以是请求方或响应方。可能允许使用特定模式请求事件的手势可能是由应用程序定义的，但这里没有定义。除非被邀约，否则不能使用批量模式，而且手势应该允许接收方选择最大的批处理量。

事件的接收方可以通过检查 Content-Type header 的值来区分这三种模式。如果该值前缀为 CloudEvents 媒体类型 `application/cloudevents`，表示使用已知的事件格式，则接收方使用结构化模式。如果该值前缀为 `application/cloudevents-batch`，则接收器使用批处理模式。否则，则默认为二进制模式。

> 备注：默认是使用二进制模式

如果接收器检测到 CloudEvents 媒体类型，但它无法处理的事件格式（例如 application/cloudevents+avro），它仍然可以将事件作为二进制模式处理，并将其转发到另一方。

## 3.1. 二进制内容模式

二进制的内容模式可以容纳任何形状的事件数据，并允许高效传输，无需转码。

### 3.1.1. HTTP Content Type

对于二进制模式，HTTP Content-Type header值对应于（必须从 CloudEvents datacontenttype 属性中填充或写入）CloudEvents datacontenttype 属性。请注意 ce-datacontenttype HTTP 标头不能也存在于消息中。

### 3.1.2. 事件数据编码

data 字节序列作为HTTP报文Body。

### 3.1.3. Metadata headers

所有其他 CloudEvents 属性（包括扩展）必须单独映射到不同的 HTTP 消息头，并从不同的 HTTP 消息头中映射。

定义了自己属性的 CloudEvents 扩展可以为这些属性定义二级映射到 HTTP 头，特别是当特定属性需要与 HTTP 特性或其他有明确 HTTP 头绑定的规范保持一致时。请注意，这些属性还必须作为带有 ce 前缀的 HTTP 标头出现在 HTTP 报文中，如 HTTP 标头名称中所述。

#### 3.1.3.1. HTTP Header Names

除注明的情况外，所有 CloudEvents 上下文属性（包括扩展）都必须映射到与属性名称相同但前缀为 ce 的 HTTP header中。

Examples:

```
* `time` maps to `ce-time`
* `id` maps to `ce-id`
* `specversion` maps to `ce-specversion`
```

注意：根据HTTP规范，header name是不区分大小写的。

#### 3.1.3.2. HTTP header值

每个 HTTP header的值由相应属性类型的标准字符串表示法构建。

某些 CloudEvents 元数据属性可包含任意 UTF-8 字符串内容，根据 RFC7230 第 3 节，HTTP 标头必须仅使用 US-ASCII 字符集中的可打印字符，并由 CRLF 序列终止，标头值周围有可选的空白。

在应用[RFC7230，第3.2.6节][RFC7230-3-2s6]中描述的 header 编码规则之前，必须按照RFC3986，第2.4节中描述的百分比编码，对字符串值进行百分比编码。

将 HTTP 报文解码为 CloudEvent 时，必须反向应用这些规则 -- RFC7230 第 3.2.6 节对 ASCII 字符串进行解码，然后按照 RFC3986 第 2.4 节中的描述进行单轮百分比解码，以生成有效的 UTF-8 字符串。(注意，应用百分比解码的次数不正确可能导致报文损坏或安全问题)。

#### 3.1.4. Examples

这个例子显示了带有HTTP POST请求的事件与的二进制模式映射：

```
POST /someresource HTTP/1.1
Host: webhook.example.com
ce-specversion: 1.0
ce-type: com.example.someevent
ce-time: 2018-04-05T03:56:24Z
ce-id: 1234-1234-1234
ce-source: /mycontext/subcontext
    .... further attributes ...
Content-Type: application/json; charset=utf-8
Content-Length: nnnn

{
    ... application data ...
}
```

这个例子显示了包含事件的响应：

```
HTTP/1.1 200 OK
ce-specversion: 1.0
ce-type: com.example.someevent
ce-time: 2018-04-05T03:56:24Z
ce-id: 1234-1234-1234
ce-source: /mycontext/subcontext
    .... further attributes ...
Content-Type: application/json; charset=utf-8
Content-Length: nnnn

{
    ... application data ...
}
```



### 3.2. 结构化内容模式

结构化的内容模式将事件元数据和数据保持在有效载荷中，使得同一事件可以在多个路由跳转、多协议之间简单转发。

### 3.2.1. HTTP内容类型

HTTP内容类型头必须设置为事件格式的媒体类型。

JSON 格式的示例。

```
Content-Type: application/cloudevents+json; charset=UTF-8
```

### 3.2.2. 事件数据编码

所选择的事件格式定义了所有属性和数据的表示方式。

然后按照事件格式规范对事件元数据和数据进行渲染，最后得到的数据成为HTTP报文body。

### 3.2.3. metadata header

实现可以包含与二进制模式定义的相同的 HTTP 标头。

所有 CloudEvents 元数据属性都必须映射到有效载荷（Payload）中，即使它们也已经映射到 HTTP header中了。

#### 3.2.4. 示例

这个例子显示了一个JSON事件格式编码的事件，用PUT请求发送：

```
PUT /myresource HTTP/1.1
Host: webhook.example.com
Content-Type: application/cloudevents+json; charset=utf-8
Content-Length: nnnn

{
    "specversion" : "1.0",
    "type" : "com.example.someevent",

    ... further attributes omitted ...

    "data" : {
        ... application data ...
    }
}
```

这个例子显示了一个响应中返回的JSON编码的事件：

```
HTTP/1.1 200 OK
Content-Type: application/cloudevents+json; charset=utf-8
Content-Length: nnnn

{
    "specversion" : "1.0",
    "type" : "com.example.someevent",

    ... further attributes omitted ...

    "data" : {
        ... application data ...
    }
}
```



## 3.3. 批量内容模式

在批量内容模式下，多个事件被批量到一个HTTP请求或响应体中。选择的事件格式必须定义如何表示一个批次。基于JSON格式（任何兼容的实现都必须支持JSON格式），JSON Batch格式是一种支持批处理的事件格式。

### 3.3.1. HTTP 内容类型

HTTP Content-Type头必须设置为事件格式的媒体类型。

JSON Batch 格式的示例。

```
Content-Type: application/cloudevents-batch+json; charset=UTF-8
```

#### 3.3.2. 事件数据编码

所选的事件格式定义了一批事件和所有事件属性和数据的表示方式。

然后根据事件格式规范对事件批进行渲染，结果数据将成为HTTP消息主体。

该批事件可以是空的。所有批处理的 CloudEvents 必须具有相同的 specversion 属性。其他属性可能不同，包括 datacontententtype 属性。

#### 3.2.3 Examples

This example shows two batched CloudEvents, sent with a PUT request:

```
PUT /myresource HTTP/1.1
Host: webhook.example.com
Content-Type: application/cloudevents-batch+json; charset=utf-8
Content-Length: nnnn

[
    {
        "specversion" : "1.0",
        "type" : "com.example.someevent",

        ... further attributes omitted ...

        "data" : {
            ... application data ...
        }
    },
    {
        "specversion" : "1.0",
        "type" : "com.example.someotherevent",

        ... further attributes omitted ...

        "data" : {
            ... application data ...
        }
    }
]
```

This example shows two batched CloudEvents returned in a response:

```
HTTP/1.1 200 OK
Content-Type: application/cloudevents-batch+json; charset=utf-8
Content-Length: nnnn

[
    {
        "specversion" : "1.0",
        "type" : "com.example.someevent",

        ... further attributes omitted ...

        "data" : {
            ... application data ...
        }
    },
    {
        "specversion" : "1.0",
        "type" : "com.example.someotherevent",

        ... further attributes omitted ...

        "data" : {
            ... application data ...
        }
    }
]
```