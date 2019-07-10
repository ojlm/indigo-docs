# 简介

`indigo` 目标是成为一个开源的企业级接口相关的应用工具. 支持的协议: `HTTP, HTTPS, MySql, Dubbo`. 实现了 `Postman` 和 `Gatling` 的部分商业功能.

## 应用场景

- 接口的业务测试和监控

> `indigo` 提供了方便的编辑页面, 支持常用数据的格式导入. 丰富可扩展的断言, 定时执行, CI/CD 事件触发, 高可维护.

- 性能测试

> 基于 开源的 [gatling](https://github.com/gatling/gatling) 高性能压测引擎开发的可通过接口调用的分布式压测服务.

- 事件转发/触发器

> 内部的定时执行机制和其他事件(Kafka), 可转换成 接口(http, dubbo, mysql) 请求
