```scala
case class JobReport(
    val scheduler: String, // 调度器
    val group: String, // 分组
    val jobName: String, // 名称
    val `type`: String, // 如下 TYPE_*
    val classAlias: String, // 别名
    var startAt: String = null, // 任务开始时间
    var endAt: String = null, // 任务结束时间
    var elapse: Long = 0L, // 任务耗时(毫秒)
    var result: String = JobExecDesc.STATUS_SUCCESS, // 结果, STATUS_*
    var errorMsg: String = StringUtils.EMPTY, // 错误信息
    val node: String = JobReport.hostname, // 运行节点 hostname
    val data: JobReportData = JobReportData(), // 报告数据
)

val TYPE_QUARTZ = "quartz" // 定时任务
val TYPE_CI = "ci" // CI 触发
val TYPE_TEST = "test" // 测试
val TYPE_MANUAL = "manual" // 人工触发

val STATUS_SUCCESS = "success" // 成功
val STATUS_FAIL = "fail" // 失败
val STATUS_WARN = "warn" // 警告, 保留
val STATUS_ABORTED = "aborted" // 终止, 保留

case class JobReportData(
    var cases: Seq[CaseReportItem] = Nil, // 用例报告
    var scenarios: Seq[ScenarioReportItem] = Nil, // 场景报告
    var ext: Map[String, Any] = Map.empty // 扩展字段
)

case class CaseReportItem(
    var id: String, // 用例文档ID
    var title: String, // 用例概括
    var result: CaseResult = null // 用例测试结果 [CaseResult](CaseResult.md)
)
```