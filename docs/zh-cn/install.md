# 安装预览

## 下载发布版

相关部署[配置参考](/zh-cn/configuration)

### 0.6.0
[百度云下载](https://pan.baidu.com/s/1Eh51T3qY2kV0i5h2TU2wdg)

## Docker 预览

> TBD

## 编译源码

### 前端

> 前提安装: [nodejs](https://nodejs.org/en/), [yarn](https://yarnpkg.com/zh-Hans/docs/install)

> 1. `git clone https://github.com/asura-pro/indigo.git`
> 2. `cd indigo`
> 3. `yarn install`
> 4. `yarn run build`

> `./dist` 文件夹中的所有静态资源文件即为发布版本.

### 后端

> 前提安装: [sbt](https://www.scala-sbt.org/download.html)

> 1. `git clone https://github.com/asura-pro/asura.git`
> 2. `cd indigo-api`
> 3. `sbt dist`

> `./target/universal` 中的 `asura-app-${version}.zip` 压缩文件即为发布包.
