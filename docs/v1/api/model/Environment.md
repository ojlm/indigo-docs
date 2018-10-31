```scala
case class Environment(
    val summary: String, // 概括
    val description: String, // 描述
    val group: String, // 分组
    val project: String, // 项目
    val protocol: String, // 协议
    val host: String, // 域名或IP, 不包含路径
    val port: Int, // 端口号
    val auth: Authorization, // [Authorization](../../api/model/Authorization.md)
)
```