# Indigo

<img src="./zh-cn/images/indigo.png" height="144">

[![Build Status](https://travis-ci.org/asura-pro/indigo.svg?branch=master)](https://travis-ci.org/asura-pro/indigo)
![GitHub release](https://img.shields.io/github/release/asura-pro/indigo.svg)
![GitHub](https://img.shields.io/github/license/asura-pro/indigo.svg)

---

## 关于 Indigo

`Indigo` 是一个测试接口的系统. 可以对 `Http(s)`, `Dubbo`, `MySql` 的请求响应进行断言. 一般用于企业内部接口的自动化测试, CI/CD Pipeline 节点, 线上巡检监控.

## 核心特性

- 基于 Web UI 操作, 在线编辑和测试

> 使用 [Typescript](http://www.typescriptlang.org/), [Angular](https://angular.io/), [Ant Design](https://ng.ant.design/docs/introduce/zh) 技术实现. `Indigo` 的定位并非是一个框架而是一个开箱即用的测试系统, 对此设计了一套还算好用的 UI 系统. 有 UI 的好处是, 相对与写脚本, 使用成本及其低, 且比使用脚本效率高 N 倍(大部分情况下, 尤其是数量非常大时). 但和其他基于脚本的接口测试框架相比, 必然缺少了一定的灵活性. 事实上大部分接口测试场景都很简单, 就是响应进行断言并没有很复杂的逻辑(那是业务系统的工作). `Indigo` 内置 Javascript 脚本引擎, 结合场景 其实灵活性也很高的.

- 可维护高数量级的用例, 具备较高的并发执行性能

> 存储引擎, 后端

- 


## 应用场景

- 接口的业务测试和监控

> `indigo` 提供了方便的编辑页面, 支持常用数据的格式导入. 丰富可扩展的断言, 定时执行, CI/CD 事件触发, 高可维护.

- 性能测试

> 基于 开源的 [gatling](https://github.com/gatling/gatling) 高性能压测引擎开发的可通过接口调用的分布式压测服务.

- 事件转发/触发器

> 内部的定时执行机制和其他事件(Kafka), 可转换成 接口(http, dubbo, mysql) 请求

## 和其他类似产品的对比

- Postman
- JMeter
- HttpRunner
- Lego
- ...
