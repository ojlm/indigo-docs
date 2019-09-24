# 开发文档

## 后端

> 后端的技术栈和 `Gatling` 一致, 使用 `Scala` 语言, 基于 [Akka](https://akka.io/) 和 [Play](https://www.playframework.com/) 框架实现.

## 前端

> 前端使用的是 `Angular` 框架, 主要是 `Typescript` 语言. 使用了阿里开源的 [NG-ZORRO](https://ng.ant.design/docs/introduce/zh) 组件库. 前端的代码放在 `ui` 这个目录下, 应为代码量并不多放在了一块. 前端代码的整个工作流已经了后端 `sbt` 集成好了, 可以一块执行, 当然也可以自己独立运行.

## 开发环境

1. 确保本地安装了后端的构建工具 `sbt` (版本1.2.8) 和 前端的构建工具`yarn`.
2. 在项目目录下执行 `sbt run` 就可以在本地运行和调试. 执行 `sbt dist` 可获得发布版本.
