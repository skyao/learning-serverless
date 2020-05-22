---
date: 2018-10-24T23:10:00+08:00
title: Json事件格式
weight: 316
menu:
  main:
    parent: "spec-cloudevents"
description : "CloudEvents规范中的HJson事件格式"
---

> 备注：内容来自　https://github.com/cloudevents/spec/blob/v1.0/json-format.md



## 2. Attributes

本节定义了 CloudEvents 属性如何映射到 JSON。本规范没有明确映射每个属性，但提供了一个通用映射模型，该模型适用于所有当前和未来的 CloudEvents 属性（包括扩展）。

为明确起见，扩展属性使用与规范定义的属性相同的规则进行序列化。这包括其语法和在 JSON 对象中的位置。特别是，扩展作为顶层 JSON 属性放置。扩展必须被序列化为顶层JSON属性。这个设计决定有很多原因，在Primer中会详细介绍。

### 2.2. Type System Mapping

扩展规范可以为其定义的属性值定义二次映射规则，但必须包括之前定义的主映射。

例如，属性值可能是在 CloudEvents 以外的标准中定义的数据结构，具有正式的 JSON 映射，如果不保留原始格式，可能会有翻译错误或信息丢失的风险。

定义了 JSON 次要映射规则的扩展规范，以及对该规范的任何修订，都必须为提交或修订时属于 CloudEvents 核心的所有其他事件格式定义明确的映射规则。

如果需要，例如在解码地图时，CloudEvents 类型可以通过使用映射表中的规则进行推理来确定，其中唯一潜在的模糊 JSON 数据类型是字符串。当满足映射规则时，该值与相应的 CloudEvents 类型兼容。

## 3. Envelope

每个 CloudEvents 事件可以完全表示为一个 JSON 对象。

这种表示方式必须使用媒体类型 application/cloudevents+json。

给定事件中的所有 REQUIRED 和所有未省略的 OPTIONAL 属性必须成为 JSON 对象的成员，相应的 JSON 对象成员名称与属性名称相匹配，并且成员的类型和值使用类型系统映射。

### 3.1. 对 "data"的处理

在采取行动之前，JSON序列化器必须首先确定数据内容的运行时数据类型。

如果实现确定数据类型为二进制，则必须将值表示为包含Base64编码的二进制值的JSON字符串表达式，并使用成员名data_base64将其存储在JSON对象中。

对于任何其他类型，实现必须将数据值转换为JSON值，并使用成员名data_base64来存储在JSON对象中。

由此可见，在 JSON 序列化的 CloudEvent 中，数据和 data_base64 成员的使用是相互排斥的。

当从 JSON 中解串化 CloudEvents 时，data_base64 成员的存在清楚地表明该值是 Base64 编码的二进制数据，序列化器必须将其解码为二进制的运行时数据类型。当数据成员存在时，它将使用默认的JSON类型映射来解码，用于使用的运行时。

与属性不同的是，根据类型系统映射，值类型被限制为字符串，而产生的数据成员JSON值是不受限制的，可以包含任何有效的JSON。





