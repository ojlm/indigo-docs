# 分组接口

## 新增分组

- 地址: `/group/index`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: [Group](../api/model/Group.md)

## 修改分组

- 地址: `/group/update`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: [Group](../api/model/Group.md)

## 查询分组
> 获取所有分组

- 地址: `/group/query`
- 方法: `GET`
- ResponseBody Data:
```scala
Map(
    total: Int, // 符合条件的总数
    list: Seq[{...Group, _id: String}] // 分组模型[Group](../api/model/Group.md)中所有字段加上`_id`(文档ID)组成的数组
)
```
