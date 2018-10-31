# 项目接口

## 新增项目

- 地址: `/project/index`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: [Project](../api/model/Project.md)

## 修改项目

- 地址: `/project/update`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: [Project](../api/model/Project.md)

## 查询项目
> 获取所有项目

- 地址: `/project/query?group=`
- 方法: `GET`
- ResponseBody Data:
```scala
Map(
    total: Int, // 符合条件的总数
    list: Seq[{...Project, _id: String}] // 项目模型[Project](../api/model/Project.md)中所有字段加上`_id`(文档ID)组成的数组
)
```
