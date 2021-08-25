# 系统配置

> 配置文件在发布包的 `./conf/application.conf` 文件. 某些配置可以使用环境变量替换.

```HOCON
# https://www.playframework.com/documentation/latest/Configuration
include "framework.conf"

play.http.secret.key = "wuae_/xG6QUxPLWvXneCm8TH:b]Ki`?Hm0mOom`uahFh3xgTg8[9R_dfjCdpkVPG"
play.http.secret.key = ${?APPLICATION_SECRET}

pea {
  address = ${?ADDRESS}
  port = ${?PORT}
  simulations {
    compileAtStartup = true
    webEditorBaseUrl = "https://github.com/ojlm/pea-simulations/blob/master/src/main/scala/"
    webEditorBaseUrl = ${?WEB_EDITOR_BASE}
  }
  results {
    folder = "./logs"
    folder = ${?RESULTS_FOLDER}
    report {
      logo.href = "https://github.com/ojlm/pea"
      desc.href = "https://github.com/ojlm/pea"
      desc.content = "https://github.com/ojlm/pea"
    }
  }
  zk {
    enabled = true
    role.worker = true
    role.worker = ${?ROLE_WORKER}
    role.reporter = true
    role.reporter = ${?ROLE_REPORTER}
    path = "/pea"
    connectString = "localhost:2181"
    username = ""
    password = ""
  }
  worker {
    protocol = "http"
    // simulation source folder
    source = "./test/simulations"
    source = ${?SIMULATIONS_SOURCE}
    // simulation compile output folder
    output = "./logs/output"
    output = ${?SIMULATIONS_OUTPUT}
    resources = "."
    resources = ${?RESOURCES_FOLDER}
    // external classpath for compiler
    classpath = ""
    classpath = ${?EXTRA_CLASSPATH}
  }
}
```
