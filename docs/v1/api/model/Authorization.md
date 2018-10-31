```scala
case class Authorization(
  val `type`: String, // 签名类型
  val data: Map[String, Any] // 特定签名类型的数据
)
```