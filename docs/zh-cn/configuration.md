# 部署配置

## Indigo 前端配置示例

`nginx` 配置示例,假设后端部署在 `localhost:9000`

```nginx
server {
  listen 80;
  server_name asura.pro;
  index index.html;
  root /var/www/html;
  client_max_body_size 1024m;
  location / {
    try_files $uri $uri/ /index.html;
  }
  location /api/ws {
      proxy_pass http://localhost:9000/api/ws;
      proxy_http_version 1.1;
      proxy_set_header Upgrade $http_upgrade;
      proxy_set_header Connection "Upgrade";
  }
  location /api/ {
    proxy_pass http://localhost:9000/api/;
    proxy_http_version 1.1;
    proxy_connect_timeout 600;
    proxy_read_timeout    600;
    proxy_send_timeout    600;
    chunked_transfer_encoding off;
    proxy_cache off;
  }
  location /openapi {
    proxy_pass http://localhost:9000/openapi;
    proxy_http_version 1.1;
    proxy_connect_timeout 600;
    proxy_read_timeout    600;
    proxy_send_timeout    600;
    chunked_transfer_encoding off;
    proxy_cache off;
  }
  access_log  /var/log/nginx/indigo_access.log;
  error_log   /var/log/nginx/indigo_error.log;
}
```

## Indigo 后端配置示例

### SQL

> 只有 Quartz 定时调度的依赖,https://github.com/asura-pro/asura/blob/master/asura-app/docs/sql/quartz-2.3.4.sql

### ES 系统启动后会自动检测索引和并创建

> 目前无法单独配置,每个 `index` 的 `mapping` 定义：https://github.com/asura-pro/asura/tree/master/asura-core/src/main/scala/asura/core/es/model

> 初始化代码：https://github.com/asura-pro/asura/blob/master/asura-core/src/main/scala/asura/core/es/EsClient.scala

### 配置文件

> `playframework`启动[相关配置](https://www.playframework.com/documentation/2.6.x/ProductionConfiguration)

> source：https://github.com/asura-pro/asura/blob/master/asura-app/conf/application.conf

```HOCON
# https://www.playframework.com/documentation/latest/Configuration

include "framework.conf"
include "mailer.conf"
play.http.secret.key = "wuae_/xG6QUxPLWvXneCm8TH:b]Ki`?Hm0mOom`uahFh3xgTg8[9R_dfjCdpkVPG"
play.http.secret.key = ${?APPLICATION_SECRET}
asura {

  admin = ["indigo"]
  reportBaseUrl = "http://localhost:4200/report/job"

  db {
    url = "jdbc:mysql://localhost:3306/asura?useUnicode=true&characterEncoding=utf-8&zeroDateTimeBehavior=convertToNull"
    user = "root"
    password = "123456"
  }

  job {
    enabled = true
    stdLogFileName = "std.log"
    workDir = "/home/asura/data/job"

    quartz {
      org.quartz.scheduler.instanceId = AUTO
      org.quartz.scheduler.skipUpdateCheck = true

      org.quartz.threadPool.class = org.quartz.simpl.SimpleThreadPool

      org.quartz.jobStore.misfireThreshold = 60000
      org.quartz.jobStore.class = org.quartz.impl.jdbcjobstore.JobStoreTX
      org.quartz.jobStore.driverDelegateClass = org.quartz.impl.jdbcjobstore.StdJDBCDelegate
      org.quartz.jobStore.useProperties = true
      org.quartz.jobStore.tablePrefix = QRTZ_
      org.quartz.jobStore.isClustered = true
      org.quartz.jobStore.clusterCheckinInterval = 20000
      org.quartz.jobStore.dataSource = CommonDS

      org.quartz.dataSource.CommonDS.driver = com.mysql.jdbc.Driver
      org.quartz.dataSource.CommonDS.provider = hikaricp
      org.quartz.dataSource.CommonDS.URL = ${asura.db.url}
      org.quartz.dataSource.CommonDS.user = ${asura.db.user}
      org.quartz.dataSource.CommonDS.password = ${asura.db.password}
      org.quartz.dataSource.CommonDS.maxConnections = 10
      org.quartz.dataSource.CommonDS.validationQuery = select 0 from dual
    }
    default {
      org.quartz.scheduler.instanceName = "default"
      org.quartz.threadPool.threadCount = 10
      org.quartz.threadPool.threadPriority = 5
    }
    system {
      org.quartz.scheduler.instanceName = "system"
      org.quartz.threadPool.threadCount = 1
      org.quartz.threadPool.threadPriority = 5
    }
  }

  es {
    indexPrefix = "asura-"
    // local node just for test, no ik-analyzer support
    useLocalNode = true
    localEsDataDir = "./logs/es"
    url = "http://localhost:9200,localhost:9200?cluster.name=asura"
    // request log online
    onlineLog = [
      {
        tag = "online"
        url = "http://localhost:9200,localhost:9200?cluster.name=asura"
        prefix = "nginx-access-"
        datePattern = "yyyy-MM-dd"
        fieldDomain = "domain"
        fieldMethod = "method"
        fieldUri = "uri"
        fieldRequestTime = "request_time"
        fieldRequestTimeResolution = 1
        fieldRemoteAddr = "remote_addr"
        excludeRemoteAddrs = ["127.0.0.1", "127.0.0.1"]
      }
    ]
  }

  linkerd {
    enabled = false
    namerd = "http://localhost:4180"
    proxyHost = "localhost"
    httpProxyPort = 4140
    httpsProxyPort = 4143
    headerIdentifier = "asura-header"
    httpNs = "http"
  }

  jwt {
    secret = "4e66be05c19667736c1217b5005e290d6352fee6"
  }

  ldap {
    enabled = true
    url = "ldap://localhost"
    searchbase = "dc=example,dc=org"
    bindDn = "cn=admin,dc=example,dc=org"
    password = "admin"
    userFilter = "(uid={user})"
    userIdAttr = "uid"
    userRealNameAttr = "cn"
    userEmailAttr = "mail"
    connectionTimeout = 500
    responseTimeout = 1000
  }

  cluster {
    enabled = true
    hostname = "127.0.0.1"
    hostname = ${?CLUSTER_HOSTNAME}
    port = 2551
    port = ${?CLUSTER_PORT}
    seed-nodes = [
      "akka://ClusterSystem@127.0.0.1:2551",
    ]
    roles = [
      "indigo"
    ]
  }
}
```

### 注意事项

- aeron.rcv.initial.window.length 提示过小

> 启用集群功能时可能会遇到,设置合适的大小如：  
> $ sudo sysctl net.core.rmem_max=131072  
> $ sudo sysctl net.core.rmem_default=131072

## Linkerd 配置示例

[官网参考](https://api.linkerd.io/1.5.1/linkerd/index.html)

```yaml
admin:
  ip: 0.0.0.0
  port: 9990
routers:
- protocol: http
  identifier:
    kind: io.l5d.header
    header: asura-header
  interpreter:
    kind: io.l5d.namerd
    namespace: http
    dst: /$/inet/localhost/4100
  httpAccessLog: logs/access-http.log
  label: indigo-http
  servers:
  - ip: 0.0.0.0
    port: 4140
- protocol: http
  identifier:
    kind: io.l5d.header
    header: asura-header
  interpreter:
    kind: io.l5d.namerd
    namespace: http
    dst: /$/inet/localhost/4100
  httpAccessLog: logs/access-http.log
  label: indigo-https
  client:
    tls:
      disableValidation: true
  servers:
  - ip: 0.0.0.0
    port: 4143
```

## Namerd 配置示例

[官网参考](https://api.linkerd.io/1.5.1/namerd/index.html)

```yaml
admin:
  ip: 0.0.0.0
  port: 9991
storage:
  kind: io.l5d.zk
  pathPrefix: /dtabs
  zkAddrs:
  - host: localhost
    port: 2181
interfaces:
- kind: io.l5d.thriftNameInterpreter
  ip: 0.0.0.0
  port: 4100
- kind: io.l5d.httpController
  ip: 0.0.0.0
  port: 4180
namers:
- kind: io.l5d.serversets
  zkAddrs:
  - host: localhost
    port: 2181
```
