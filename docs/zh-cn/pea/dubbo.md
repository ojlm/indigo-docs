# Dubbo 示例

## Interface 声明

```scala
public interface GreetingService {
  String sayHello(String name);
}
```

## Provider 实现

```scala
public class GreetingsServiceImpl implements GreetingService {
  @Override
  public String sayHello(String name) {
    return "hi, " + name;
  }
}
```

## 压测脚本

```scala
import asura.pea.dubbo.Predef._
import asura.pea.dubbo.api.GreetingService
import asura.pea.gatling.PeaSimulation
import io.gatling.core.Predef._

class DubboGreetingSimulation extends PeaSimulation {
  override val description: String =
    """
      |Dubbo simulation example
      |""".stripMargin
  val dubboProtocol = dubbo
    .application("gatling-pea")
    .endpoint("127.0.0.1", 20880)
    .threads(10)
  val scn = scenario("dubbo")
    .exec(
      invoke(classOf[GreetingService]) { (service, _) =>
        service.sayHello("pea")      // 调用 sayHello 方法
      }.check(simple { response =>
        response.value == "hi, pea"  // 检查响应内容
      }).check(
        jsonPath("$").is("hi, pea")  // 使用 jsonPath 表达式检查响应内容
      )
    )
  setUp(
    scn.inject(atOnceUsers(10000))  // 直接 10000 并发用户
  ).protocols(dubboProtocol)
}
```

## 报告

![](./images/dubbo-report.png)
