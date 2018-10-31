```scala
case class RestApi(
    val summary: String, // 用例名称
    val description: String, // 用例描述, 支持 markdown 语法
    val group: String, // 所属组
    val project: String, // 所属项目
    val path: String, // 接口路径
    val method: String, // 接口方法
    val service: String = null, // 接口所属服务
    var deprecated: Boolean = false, // 是否废弃
    var version: String = StringUtils.EMPTY, // 版本号
    var `type`: String = ApiType.REST, // 接口类型, "rest"
    var labels: Seq[LabelRef] = Nil, // 标签
    var schema: RestApiSchema = null, // 接口Schema
)
case class RestApiSchema(
    path: Seq[ParameterSchema], // 路径变量
    query: Seq[ParameterSchema], // query变量
    header: Seq[ParameterSchema], // headers
    cookie: Seq[ParameterSchema], // cookies
    requestBody: HttpRequestBody, // 协议体 schema
    responses: Map[String, HttpResponse], // 键为 `default` 或 http status 响应码
)
case class HttpRequestBody(
    val contentType: String = StringUtils.EMPTY, // 目前支持以下两种
    val jsonBody: JsonSchema = null, // application/json
    val formBody: Seq[ParameterSchema] = null, // application/x-www-form-urlencoded
)
```

```scala
object FieldTypes {
  val BOOLEAN = "boolean"
  /** -128 ~ 127 */
  val BYTE = "byte"
  /** 16-bits, -32,768 ~ 32,767 */
  val SHORT = "short"
  /** 32-bits -2^31 ~ 2^31-1 */
  val INT = "int"
  /** 64-bits, -2^63 ~ 2^63-1 */
  val LONG = "long"
  val FLOAT = "float"
  val DOUBLE = "double"

  val STRING = "string"
  val ARRAY = "array"
  val MAP = "map"
}
trait SchemaObject {
  var description: String
  var `type`: String
}
case class JsonSchema(
                       var description: String,
                       var `type`: String,
                       var properties: Map[String, JsonSchema] = null
                     ) extends SchemaObject {

}
case class ParameterSchema(
                            var name: String,
                            var description: String,
                            var `type`: String,
                          ) extends SchemaObject {

  /**
    * Sets the ability to pass empty-valued parameters.
    * This is valid only for either query or formData parameters and
    * allows you to send a parameter with a name only or an empty value.
    * Default value is false.
    */
  var allowEmptyValue: Boolean = true

  /**
    * for number fields
    */
  var maximum: BigDecimal = -1
  var exclusiveMaximum: Boolean = false
  var minimum: BigDecimal = -1
  var exclusiveMinimum: Boolean = false

  /**
    * for `string` and `array` type, union of `maxLength` and `maxItems`
    */
  var maxSize: Int = -1
  var minSize: Int = -1

  /**
    * `type` is `string`
    * This string should be a valid regular expression
    */
  var pattern: String = null

  var enum: Set[Any] = null

  /**
    * Required if type is `array`. Describes the type of items in the array.
    * Not in `body` or  in `formData` only support basic types, string、numbers、boolean, will only the `type` field is significant
    */
  var items: ArrayItems = null

  /**
    * Not in `body`, Required if type is `array`.
    *
    * Determines the format of the array if type array is used. Possible values are:
    * csv - comma separated values foo,bar.
    * ssv - space separated values foo bar.
    * tsv - tab separated values foo\tbar.
    * pipes - pipe separated values foo|bar.
    * Default value is csv.
    */
  var collectionFormat: String = null

  /**
    * Required if type is `object` and in is `body`.
    */
  var properties: Map[String, SchemaObject] = null

  /**
    * Determines whether this parameter is mandatory.
    * If the parameter is in "path", this property is required and its value MUST be true.
    * Otherwise, the property MAY be included and its default value is false.
    */
  var required: Boolean = false
}
object InType {
  val PATH = "path"
  val QUERY = "query"
  val HEADER = "header"
  /** v3 */
  val COOKIE = "cookie"
  /** v2 */
  val FORM_DATA = "formData"
  /** v2 */
  val BODY = "body"
}
```