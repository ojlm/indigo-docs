## 执行上下文

> 上下文本质上是一个`会话级别` 的 `内存结构体` 可以理解为一个 `hashmap`. 上下文中的数据在请求执行过程中会动态变化. Indigo 中提供的一些动态渲染的机制, 场景中前后步骤的数据依赖, 变量的导入导出等机制全是基于上下文实现的.

## 模型定义

```json
{
    "status" : int          // 每个请求响应的状态码，数字. 指 Http 请求中的响应码, 如: 200, 404, 500
    "headers" : {}          // 每个请求响应的消息头，Map. 指 Http 头(headers), map 结构
    "entity" : string or {} // 每个响应的消息体，字符串或Map. Http, Dubbo, MySql 请求的的响应, 如果
    "_env" : {}             // 当前生效的环境配置的自定义变量
    "_g" : {}               // 全局, 预留
    "_j" : {}               // 任务, 一般在任务作用域域级别的变量
    "_s" : {}               // 场景, 一般在场景作用域域级别的变量, 场景中的变量导出一般导出到这个作用域下, 任务中如果有多个场景, 每个场景开始时都会清空初始化
    "_req" : {              // http 请求, 内部 body, 值请求体, json 或 字符串
      "body" : string or {}
    }
}
```

## 如何引用

有以下两种情况会使用

> 1. 用例中变量值或响应中用 `{{` 和 `}}` 括起来的内容（包括 `{{` `}}` ）会渲染成上下文的数据（都是 `$.` 开头的引用变量）

> 2. 断言中

## 示例

### 单个 HTTP 请求

> 执行 `GET https://api.github.com/repos/rust-lang/rust` 后, 上下文中数据应该是

```json
{
  "headers": {
    "Status": "200 OK",
    "Server": "GitHub.com",
    "Access-Control-Allow-Origin": "*",
    "X-Content-Type-Options": "nosniff",
    ...
  },
  "entity": {
    "id": 724712,
    "node_id": "MDEwOlJlcG9zaXRvcnk3MjQ3MTI=",
    "name": "rust",
    "full_name": "rust-lang/rust",
    "private": false,
    ...
    "network_count": 5760,
    "subscribers_count": 1388
  },
  "status": 200
}
```
### 单个 SQL 请求

> 执行 `select * from user limit 2;` 后上下文为

```json
{
  "entity": [
    {
      "sso": 218445,
      "reset_time": "2019-02-14 11:04:04.0",
      "enabled": true,
      "updated_at": "2019-02-14 03:04:04.0",
      "id": 760,
      "username": "duanxinceshirenyuan"
    },
    {
      "sso": 218672,
      "reset_time": "2019-02-14 11:04:04.0",
      "enabled": true,
      "updated_at": "2019-02-14 03:04:04.0",
      "id": 761,
      "username": "gonggongceshiyi"
    }
  ]
}
```
