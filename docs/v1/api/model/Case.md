```scala
case class Case(
  val summary: String, // 用例名称
  val description: String, // 用例描述, 支持 markdown 语法
  val group: String, // 所属组
  val project: String, // 所属项目
  val api: String, // 所属接口文档ID
  val request: Request, // 定义如下 
  val assert: Map[String, Any], // 用例断言, 无固定Schema
  val namespace: String = null, // 用例应用环境(代理)
  val useProxy: Boolean = false, // 是否使用代理
  val env: String = StringUtils.EMPTY, // 使用的环境配置文档 ID
  val useEnv: Boolean = false, // 是否使用环境配置
)
case class Request(
  val protocol: String, // 协议目前支持两种 `http` 和 `https`
  val host: String, // 域 域名或IP, 如: www.baidu.com, 127.1.1.1
  val port: Int, // 端口
  val auth: Authorization, // [查看](./Authorization.md)
  var method: String, // 方法, GET POST
  var path: Seq[KeyValueObject], // 接口路径变量
  var query: Seq[KeyValueObject], // 接口query变量
  var header: Seq[KeyValueObject], // 接口header变量
  var cookie: Seq[KeyValueObject], // 接口cookie变量
  var contentType: String, // 目前只支持 `applicati  `application/x-www-form-urlencoded`, `text/plain`
  var body: Seq[MediaObject], // 消息体内容
)
case class MediaObject(
  contentType: String, // 目前只支持 `applica  `application/x-www-form-urlencoded`, `text/plain`
  data: String // 字符串内容
)
case class KeyValueObject(
  val key: String, // 键
  val value: String, // 值
  enabled: Boolean = true, // 是否启用
)
```