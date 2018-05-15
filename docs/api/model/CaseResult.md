```scala
case class CaseResult(
  id: String, // 用例文档ID
  assert: Map[String, Any], // 用例断言
  context: java.util.Map[String, Any], // 用例上下文
  request: CaseRequest, // 用例请求组成
  statis: Statistic, // 用例相关统计
  result: Map[String, Any] // 断言结果和 `assert` 同构
)
case class CaseRequest(
  url: String, // 用例URL
  headers: Seq[KeyValueObject], // headers
  body: String // http body string
)
case class KeyValueObject(
  val key: String, // 键
  val value: String, // 值
  enabled: Boolean = true, // 是否启用
)
case class Statistic(
  var passed: Int = 0, // 断言通过个数
  var failed: Int = 0, // 断言失败个数
  var isSuccessful: Boolean = true // 用例是否通过
)
```