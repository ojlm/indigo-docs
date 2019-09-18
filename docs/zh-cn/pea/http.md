# HTTP 示例

## 压测脚本

> 和官方一致, https://gatling.io/docs/current/

```scala
import asura.pea.gatling.PeaSimulation
import io.gatling.core.Predef._
import io.gatling.http.Predef._
import scala.concurrent.duration._

class BaiduSearch extends PeaSimulation {
  // 简单描述, 页面展示
  override val description: String =
    """
      |百度首页. 
      |检索 "Gatling Pea" 关键字. 
      |判断响应是 200 , 返回包括 "Gatling Pea".
      |并发用户: 每秒 1000 个, 持续 1 小时.
      |""".stripMargin

  // http协议公用信息
  val httpProtocol = http
    .baseUrl("https://www.baidu.com") // 公共起始地址
    .acceptHeader("text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8") // 公共头
    .acceptEncodingHeader("gzip, deflate")
    .acceptLanguageHeader("en-US,en;q=0.5")
    .userAgentHeader("Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:16.0) Gecko/20100101 Firefox/16.0")
  // 创建请求, 检索 "Gatling Pea" 关键字
  val search = exec(
    http("检索 Gatling Pea")
      .get("/s?wd=Gatling%20Pea")
      .check(
        status.is(200), // 响应码, 是200
        substring("Gatling Pea").exists, // 返回的 html 中包括 "Gatling Pea" 字符串
      )
  )
  // 创建场景
  val homeScn = scenario("百度首页检索").exec(search)

  // 设置虚拟用户数
  setUp(
    homeScn.inject(constantUsersPerSec(1000) during (1 hour))
  ).protocols(httpProtocol)
}
```