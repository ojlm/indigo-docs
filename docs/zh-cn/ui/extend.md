# 扩展指令

适用其他场景扩展指令, 1. 多人协作和多人会议  2. Electron 应用多 webview 切换操作

## 多个 driver

> 用于同时操作多个浏览器

```
Feature: Multiple Driver Feature

  Background:
    * configure newDriver = { type: 'chrome', name: 'd01', default: true, start: true, stop: true, port: 9222}
    * configure newDriver = { type: 'chrome', name: 'd02', start: true, stop: true, port: 9223}

  Scenario: Multiple Driver Scenario
    * driver 'https://github.com/'
    * delay(500)
    * def targetUrl = 'https://github.com/search?q=akka+language:scala'
    * driver targetUrl
    * d01.setUrl('https://github.com/')
    * d02.setUrl('https://github.com/team')
    * delay(500)
    * use driver d02
    * driver 'https://github.com/marketplace'
    * delay(5000)
```

## 中文指令

> 尝试

```
* 打开 'https://github.com/' 网页
* 点击 .divClass 元素
* 等待 1 秒
* 在 .input 元素输入 'aaa'
```
