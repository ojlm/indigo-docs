# 部署步骤

## 1. 下载最新发布版

[下载页](/zh-cn/pea/download)

## 2. 解压配置

> 目录结构
```
README.md
bin/            # 启动脚本
conf/           # 配置目录
ext/            # 默认的外部jar包路径
lib/            # 本身依赖
share/          # java doc
```

> ⚠️ 目前对 Zookeeper 有强依赖, 需要提前安装好, 修改配置文件 `conf/application.conf`

> 必须要改的 `pea.zk.connectString` 改成Zookeeper 的链接串地址. 其他都有默认值


```
# https://www.playframework.com/documentation/latest/Configuration
include "framework.conf"

play.http.secret.key = "wuae_/xG6QUxPLWvXneCm8TH:b]Ki`?Hm0mOom`uahFh3xgTg8[9R_dfjCdpkVPG"
play.http.secret.key = ${?APPLICATION_SECRET}

pea {
  // 注册到 zk 上的ip, 默认会选择第一个网卡的ip, 可指定, 可以通过 ADDRESS 环境变量配置
  address = ${?ADDRESS}
  // 同上, 端口号
  port = ${?PORT}
  // 机器标签名
  label = "Pea"
  label = ${?LABEL}
  simulations {
    // 是否在启动时, 编译脚本
    compileAtStartup = true
    webEditorBaseUrl = "https://github.com/ojlm/pea-simulations/blob/master/src/main/scala/"
    webEditorBaseUrl = ${?WEB_EDITOR_BASE}
  }
  results {
    // 报告生成的目录
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
    // 当前节点为 `worker` 角色, 发压节点
    role.worker = true
    role.worker = ${?ROLE_WORKER}
    // 当前节点为 `reporter` 角色, 聚合发压节点报告, 监控状态. `reporter` 节点会保存聚合报告
    role.reporter = true
    role.reporter = ${?ROLE_REPORTER}
    // 注册到 zk 上的目录
    path = "/pea"
    // zk 连接串
    connectString = "localhost:2181"
    // zk 用户名
    username = ""
    // zk 密码
    password = ""
  }
  worker {
    // 现在 `reporter` 通过 http 接口控制 `worker`, 看自己的部署环境可以改成 `https`
    protocol = "http"
    // simulation source folder, 脚本的源码路径
    source = "./test/simulations"
    source = ${?SIMULATIONS_SOURCE}
    // 脚本编译后的输出目录
    output = "./logs/output"
    output = ${?SIMULATIONS_OUTPUT}
    // 资源目录, 用户数据, csv, json, 等文件
    resources = "."
    resources = ${?RESOURCES_FOLDER}
    // 额外的jar包路径, 默认是 ext 目录
    classpath = ""
    classpath = ${?EXTRA_CLASSPATH}
  }
}
```

# 启动

> 前端运行: windows 用户执行: `./bin/pea.bat`, linux: `./bin/pea`

> 后台运行(linux shell): 启动 : `./bin/pea.sh start`, 停止 : `./bin/pea.sh stop`
