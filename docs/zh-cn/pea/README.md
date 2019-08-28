# Pea

以 [Gatling](https://github.com/gatling/gatling) (Async Scala-Akka-Netty based Load Test Tool) 作为底层执行引擎.

## `Worker` 角色

> 单引擎实例, 执行具体的任务, 同一时间只能一个任务处于执行状态.

### 状态

> /${ROOT}/workers/${node}

- `idle`

> 空闲状态.

- `running`

> 执行任务中.

## `Reporter` 角色

> 控制多个 `Worker` 节点, 执行任务或停止任务, 监控 `Worker` 状态, 收集数据, 生成聚合报告.

### 任务状态

> /${ROOT}/jobs/${runId}. `reporter` 可以同时控制多个任务的执行, 每个任务有以下这些状态.

- `running`

- `reporting`

- `finished`

#### 任务中的 Workers 状态

> 发送任务时的响应, 对应的状态

- `idle`

> 初始状态

- `running`

> 发送负载成功

- `ill`
> 发送负载失败

- `gathering`

> worker 执行负载完成, 收集报告

- `finished`

> 收集报告完成
