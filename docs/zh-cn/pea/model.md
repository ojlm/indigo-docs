# 状态模型

> 状态都会同步到 ZK.

## Worker 节点

> zk 路径: `/${root}/workers/${node}`

### 数据

```scala
class MemberStatus(
  var status: String = MemberStatus.WORKER_IDLE,
  var runId: String = StringUtils.EMPTY,
  var start: Long = 0L,
  var end: Long = 0L,
  var code: Int = 0,
  var errMsg: String = null,
)
```

## Reporter 节点

> zk 路径: `/${root}/reporters/${node}`

## 任务节点

> zk 路径: `/${root}/jobs/${runId}`

### 数据

```scala
class ReporterJobStatus(
  var status: String = MemberStatus.REPORTER_RUNNING,
  var runId: String = StringUtils.EMPTY,
  var start: Long = 0L,
  var end: Long = 0L,
  var workers: mutable.Map[String, JobWorkerStatus] = mutable.Map.empty
)
class JobWorkerStatus(
  status: String = MemberStatus.WORKER_IDLE,
  errMsg: String = null,
)
```
