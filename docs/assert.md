# 断言

## 递归定义
``` typescript
{
  [string]: Assert // 对象的key必须为 jsonpath 或 以下断言短语
}
```

## 短语

### 比较
- `$eq` : 等于
> 基础类型
- `$ne` : 不等于
- `$gt` : 大于
- `$gte`: 大于等于
- `$lt` : 小于
- `$lte`: 小于等于
- `$in` : 在集合(string)中
- `$nin`: 不在集合中
- `$regex`: 正则

### 逻辑
- `$and` : 逻辑与,值为数组需全为真
- `$not` : 逻辑非
- `$nor` : 逻辑或非,值为数组
- `$or`  : 逻辑或,值为数组

### 元素判断
- `$type`: 判断字段值的类型, 支持类型如下

``` scala
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
  /** 数组 */
  val ARRAY = "array"
  /** 对象, Object */
  val MAP = "map"
}
```

### 数组
- `$size` : 判断数组(string)元素个数

### 其他

TODO :heart:

## 示例

``` typescript
{
  "$.entity.body" : {
    "$and" : [
      {
        "$.code" : { "$eq" : "10000" }
      },
      {
        "$.data" : {
          "$and" : [
            { "$type" : "array" },
            { "$size" : 1 },
            {
              "$.[0]" : {
                "$eq" : "one element"
              }
            }
          ]
        }
      }
    ]
  }
}
```