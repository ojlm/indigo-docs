```scala
case class Job(
    val summary: String, // 概括
    val description: String, // 描述
    val name: String, // 名称
    val group: String, // 分组
    val scheduler: String, // 调度器
    val classAlias: String, // 别名
    val trigger: Seq[JobTrigger], // 触发器们
    val jobData: JobData // 任务数据
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