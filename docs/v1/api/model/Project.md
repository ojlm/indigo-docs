```scala
case class Project(
    val id: String, // 唯一标识, 由`字符、数字、-、_、.`组成
    val group: String, // 分组
    val summary: String, // 概括
    val description: String, // 描述
)
```