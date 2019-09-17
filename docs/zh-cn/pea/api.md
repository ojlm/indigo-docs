# 接口

# Reporter 节点

## 查看当前运行中的所有任务

> `GET /api/jobs`

## 查看运行中的任务细节信息

> `GET /api/job/:runId`

## 查看所有本地报告

> `GET /api/reporters`

## 获得所有工作节点

> `GET /api/workers`

## 获得所有报告节点

> `GET /api/reporters`

## 查看所有脚本

> `GET /api/simulations`

## 停止工作节点

> `POST /api/stop`

## 执行更新编译

> `POST /api/compile`

## 启动单接口任务

> `GET /api/single`

## 启动脚本任务

> `POST /api/simulation`

## 任务报告链接

> `GET /report/:runId`

# Worker 节点(Gatling)

> 一般不直接调用

## 停止引擎

> `GET /api/gatling/stop`

## 查询引擎状态

> `GET /api/gatling/status`

## 执行单接口任务

> `POST /api/gatling/single`

## 执行脚本任务

> `POST /api/gatling/simulation`

## 监控引擎状态

> `Websocket /api/gatling/monitor`

## 执行编译命令

> `POST /api/gatling/compile`

## 监控编译器输出

> `Websocket /api/gatling/compiler`

## 下载报告日志

> `GET /api/gatling/simulation/:runId`
