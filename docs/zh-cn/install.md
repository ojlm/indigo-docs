# 安装预览

## 在线Demo预览

> 访问 [https://asura.pro/](https://asura.pro/)（低配主机，如果失败请用其他方式）。 `用户名` 输入任意字符串，`密码` 和 `用户名` 一致即可登录。内部禁用了 Ldap，定时任务，Linkerd 的功能。

## Docker 预览

内部禁用了 Ldap，定时任务，Linkerd 的功能

> 1. 首次执行。创建 `docker-compose.yml` 文件包含以下内容，执行 `docker-compose up`。
> 注意：如果是第一次执行，等启动完成后再执行一次 `docker-compose restart indigo-api` （重启下 `indigo-api` 服务，确保在 `elasticsearch` 中成功建好 index，之后不需要重启）。

```yaml
version: "3"

services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:6.2.2
    ports:
      - "9200:9200"
      - "9300:9300"
    environment:
      discovery.type: "single-node"
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:9200"]
      interval: 30s
      timeout: 10s
      retries: 3
  indigo-api:
    image: asurapro/indigo-api:latest
    ports:
      - "9000:9000"
    links:
      - elasticsearch
    depends_on:
      - elasticsearch
    restart: on-failure
    environment:
      APPLICATION_SECRET: "0><>0zv0oG>JH6>YHq4Hs=5x;ht8VB>x`_lOWo<cb309F3n`k;gy1j;i[cd;zE>u"
  indigo:
    image: asurapro/indigo:latest
    ports:
      - "80:80"
    links:
      - indigo-api
```
> 2. 访问 [localhost:80](http://localhost:80)

> 3. 输入任意相同的用户名和密码

## 下载发布版

相关部署[配置参考](/zh-cn/configuration)

### 前端

> 在这里下载最新的 https://github.com/asura-pro/indigo/releases 发布版本。解压获得前端静态文件。

### 后端

> https://github.com/asura-pro/asura/releases 下载最新的发布版本。解压获得后端程序。

## 编译源码

### 前端

> 前提安装: [nodejs](https://nodejs.org/en/)，[yarn](https://yarnpkg.com/zh-Hans/docs/install)

> 1. `git clone https://github.com/asura-pro/indigo.git`
> 2. `cd indigo`
> 3. `yarn install`
> 4. `yarn run build`

> `./dist` 文件夹中的所有静态资源文件即为发布版本。


### 后端

> 前提安装: [sbt](https://www.scala-sbt.org/download.html)

> 1. `git clone https://github.com/asura-pro/asura.git`
> 2. `cd indigo-api`
> 3. `sbt dist`

> `./target/universal` 中的 `asura-app-${version}.zip` 压缩文件即为发布包。
