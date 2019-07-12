# 代理

> 代理传输层和应用层请求

## HTTP
> 场景: Rest接口用例任务内部执行通过代理服务或直接访问代理服务, 服务端可用端口号做其他业务区分

### 路由表
- 每一行记录组成: `/namespace/service-name => ip-or-domain/port`
> `namespace` 可代表环境,用例的字段. `service-name` 是服务名称,接口的字段. `ip-or-domain` 为最终的目标地址的IP地址或域名, `port` 目标地址端口号

```
/prod/app-client => 10.0.0.1/80
/test/app-client => 10.0.0.2/80
/stage/app-client => 10.0.0.3/80
/mockserver-01/app-clinet => 10.0.0.2/8080
/mockserver-02/app-client => 10.0.0.2/8081
/prod/api-server => api.example.com/80
/test/api-server => api-test.example.com/80
```

## TCP
> 场景: 忽视传输层以上协议, 直接针对源IP做路由, 服务端可用端口号做其他业务区分. e.g: mysql, redis

### 路由表
- 每一行记录组成: `/src-ip => dst-ip/port`
> `src-ip` 代表源IP. `dst-ip` 为最终的目标地址的IP地址或域名, `port` 目标地址端口号

```
/10.1.1.1 => 10.0.0.1/80
/10.1.1.2 => 10.0.0.2/80
```

## SOCKS5
> 场景: 移动手机或开发个人电脑, 本地安装 SOCKS5 客户端, 服务端 SOCKS5 程序 针对 `源IP` 或 `目标IP和端口` 或 `username` 做路由. 如果路由表中没有匹配项, 则直接访问源请求的目标地址, 服务端可用端口号做其他业务区分.

### 路由表
- 每一行记录组成: `/user/username => ip-or-domain/port` 或 `/src/ip => ip-or-domain/port` 或 `/dst/ip-domain/port => ip-or-domain/port`
> `/user/username` 用户. `/src/ip` 源IP. `/dst/ip-domain/port` 目标IP和端口号.

```
/user/app-auto-01 => 10.0.0.1/80
/user/app-auto-02 => api.example.com/8080
/src/10.1.1.1 => mock-server.example.com/80
/dst/10.1.1.2/80 => mock-server.example.com/8080
/dst/api.example.com/80 => mock-server.example.com/80
```
