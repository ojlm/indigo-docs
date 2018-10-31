# 接口接口


## 新增接口

- 地址: `/api/index`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: [RestApi](../api/model/RestApi.md)

## 修改接口

- 地址: `/api/update`
- 方法: `POST`
- ContentType: `application/json`
- RequestBody: 
>```scala
>case class ApiUpdate(
>   id: String, // api 文档ID
>   api: RestApi // RestApi](../api/model/RestApi.md)
>)
>```

## 查询接口

- 地址: `/api/query?project=`
- 方法: `GET`
