# 环境变量接口

## 新增环境

- 地址: `/env/index`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: [Environment](../api/model/Environment.md)

## 修改环境

- 地址: `/env/update`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody:
>```scala
>case class UpdateEnv(
>    id: String, // 用例文档ID
>    cs: Environment // [Environment](../api/model/Environment.md)
>)
>```

## 查询环境
> 获取项目下所有环境

- 地址: `/env/query?project=`
- 方法: `GET`
- ResponseBody Data:
```scala
Map(
    total: Int, // 符合条件的总数
    list: Seq[{...Environment, _id: String}] // [Environment](../api/model/Environment.md)中所有字段加上`_id`(文档ID)组成的数组
)
```
