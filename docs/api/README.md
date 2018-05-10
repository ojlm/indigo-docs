# Asura 接口

所有HTTP接口返回为 `JSON` 格式定义如下:

## 返回定义
```scala
case class ApiRes(
    code: String = ApiCode.OK,  // 返回码, 含义如下
    msg: String = ApiMsg.SUCCESS, // 返回码对应的消息
    data: Any = null // 返回数据, 类型由特定接口决定
)
```

## 内置返回码
```scala
object ApiCode {
  /** 默认结果码 */
  val DEFAULT = "00000"
  /** API 处理正常,结果可依赖[10000, 20000) */
  val OK = "10000"
  /** API 传参不符合要求[20000, 30000) */
  val INVALID = "20000"
  /** 后端错误或异常[90000, ~] */
  val ERROR = "90000"
  /** 未登陆 */
  val NOT_LOGIN = "90001"
  /** 没有权限 */
  val PERMISSION_DENIED = "90002"
}
```

