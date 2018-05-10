# 用例接口

接口请求必须包含, Cookie `GUAZISSO`, 值为用户登录 SSO 后的 `token`

## 用例新增接口

- 地址: `/case/index`
- 方法: `POST`
- ContentType: `application/json`
- 消息体: [Case](model/Case.md)


