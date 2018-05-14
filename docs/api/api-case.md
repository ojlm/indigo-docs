# 用例接口

接口请求必须包含, Cookie `GUAZISSO`, 值为用户登录 SSO 后的 `token`

## 用例新增接口

- 地址: `/case/index`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: [Case](../api/model/Case.md)

## 用例删除接口

- 地址: `/case/delete`
- 方法: `GET`

## 用例修改接口

- 地址: `/case/update`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody Data: 
>```scala
>case class UpdateCase(
>    id: String, // 用例文档ID
>    cs: Case // 用例模型 [Case](../api/model/Case.md)
>)
>```

## 用例查询接口

- 地址: `/case/query`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: 
```scala
case class QueryCase(
    group: String, // 分组
    project: String, // 项目
    api: String, // 接口ID
    text: String, // 全文检索, 用例概述和描述
    from = 0, // 分页起始
    size = 10 // 分页大小
)
```
- ResponseBody Data:
```scala
Map(
    total: Int, // 符合条件的总数
    list: Seq[{...Case, _id: String}] // 用例模型 [Case](../api/model/Case.md)中所有字段加上`_id`(用例文档ID)组成的数组
)
```
