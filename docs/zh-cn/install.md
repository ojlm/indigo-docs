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
> WIP

## 编译源码

> WIP
