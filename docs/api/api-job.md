# 任务接口

## 支持任务类型
- 地址: `/job/type`
- 方法: `GET`
- RequestBody: 
>```json
{
    "jobTypes" : [{"label" : "", "value" : ""}],
    "schedulers" : [""]
}
>```

## 新建任务
- 地址: `/job/new`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: NewJob
```scala
case class NewJob(
    jobMeta: JobMeta, // 任务元数据
    triggerMeta: TriggerMeta, // 触发器元数据
    jobData: JobData // 任务数据
)
case class JobMeta(
    name: String, // 任务名称
    group: String, // 分组
    desc: String, // 描述
    scheduler: String, // 调度器
    classAlias: String // 别名
)
case class TriggerMeta(
    name: String, // 调度器名称
    group: String, // 分组
    desc: String, // 描述
    cron: String, // cron 表达式
    triggerType: String = TriggerMeta.TYPE_MANUAL, // 触发类型, 如下`
    startNow: Boolean = true, // 是否现在启动
    startDate: Long = 0L, // 开始日期
    endDate: Long = 0L, // 结束日期
    repeatCount: Int = 0, // 重复次数
    interval: Int = 0 // 间隔时间(秒)
)
object TriggerMeta {
    val TYPE_MANUAL = "manual" // 人工
    val TYPE_SIMPLE = "simple" // 简单
    val TYPE_CRON = "cron"     // Cron
    val TYPE_API = "api"       // 接口触发
}
case class JobData(
    cs: Seq[DocRef] = Nil, // 用例数组
    scenario: Seq[DocRef] = Nil, // 场景数组
    ext: Map[String, Any] = Map.empty, // 扩展数据
)
case class DocRef(id: String) // 文档ID
```

## 删除任务
- 地址: `/job/delete`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: DeleteJob
>```scala
>case class DeleteJob(scheduler: String, group: String, name: String, id: String)
>```

## 修改任务
- 地址: `/job/update`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: 
>```scala
>case class UpdateJob(jobMeta: JobMeta, triggerMeta: TriggerMeta, jobData: JobData)
>```

## 暂停任务
> cron 类型

- 地址: `/job/pause`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: 
>```scala
>case class PauseJob(scheduler: String, group: String, name: String)
>```

## 恢复任务
> cron 类型

- 地址: `/job/resume`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: 
>```scala
>case class ResumeJob(scheduler: String, group: String, name: String)
>```

## 任务详情

- 地址: `/job/detail?id=`
- 方法: `GET`
- ResponseBody Data: [Job](../api/model/Job.md)

## 任务执行历史查询

- 地址: `/job/log`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: 
>```scala
>case class QueryJobReport(
>   scheduler: String, // 调度器
>   group: String, // 分组
>   classAlias: String, // 任务别名
>   type: String, // 触发类型, 如下:
>   from: Int, // 分页起始偏移
>   size: Int, // 单页大小
>)
>val TYPE_QUARTZ = "quartz" // 定时任务
>val TYPE_CI = "ci" // CI 触发
>val TYPE_TEST = "test" // 测试
>val TYPE_MANUAL = "manual" // 人工触发
>```

## 任务报告

- 地址: `/job/report/{id}`
- 方法: `GET`
- ResponseBody Data: [JobReport](../api/model/JobReport.md)
