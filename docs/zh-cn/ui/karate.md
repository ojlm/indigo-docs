# Karate UI

> 翻译自[1.0.0](https://github.com/intuit/karate/blob/44e40a8b10d223586a871c01e05da4b63afff5dd/karate-core/README.md)
> , 让UI自动化更简单
> ![](./images/driver-hello-world.jpeg)

# 索引

<table>
<tr>
  <th>配置</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=driver"><code>driver</code></a>
    | <a href="#/zh-cn/ui/karate?id=configure-driver"><code>configure driver</code></a>
    | <a href="#/zh-cn/ui/karate?id=configure-driver"><code>configure newDriver</code></a>
    | <a href="#/zh-cn/ui/karate?id=timeout"><code>timeout()</code></a>
    | <a href="#/zh-cn/ui/karate?id=driversessionid"><code>driver.sessionId</code></a>
  </td>
</tr>
<tr>
  <th>概念</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=syntax">Syntax</a>
    | <a href="#/zh-cn/ui/karate?id=special-keys">Special Keys</a>
    | <a href="#/zh-cn/ui/karate?id=short-cuts">Short Cuts</a>
    | <a href="#/zh-cn/ui/karate?id=chaining">Chaining</a> 
    | <a href="#/zh-cn/ui/karate?id=function-composition">Function Composition</a>
    | <a href="#/zh-cn/ui/karate?id=script">Browser JavaScript</a>
    | <a href="#/zh-cn/ui/karate?id=debugging">Debugging</a>
    | <a href="#/zh-cn/ui/karate?id=retry">Retries</a>
    | <a href="#/zh-cn/ui/karate?id=wait-api">Waits</a>
    | <a href="#/zh-cn/ui/karate?id=distributed-testing">Distributed Testing</a>
    | <a href="#/zh-cn/ui/karate?id=proxy">Proxy</a>
    | <a href="#/zh-cn/ui/karate?id=intercepting-http-requests">Intercepting HTTP Requests</a>
    | <a href="#/zh-cn/ui/karate?id=file-upload">File Upload</a>
    | <a href="#/zh-cn/ui/karate?id=code-reuse">Code Reuse</a>
    | <a href="#/zh-cn/ui/karate?id=hybrid-tests">Hybrid Tests</a>
  </td>
</tr>
<tr>
  <th>选择器</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=locators">Locator Types</a>
    | <a href="#/zh-cn/ui/karate?id=wildcard-locators">Wildcards</a> 
    | <a href="#/zh-cn/ui/karate?id=friendly-locators">Friendly Locators</a> 
    | <a href="#/zh-cn/ui/karate?id=tree-walking">Tree Walking</a>
    | <a href="#/zh-cn/ui/karate?id=rightof"><code>rightOf()</code></a>
    | <a href="#/zh-cn/ui/karate?id=leftOf"><code>leftOf()</code></a>
    | <a href="#/zh-cn/ui/karate?id=above"><code>above()</code></a>
    | <a href="#/zh-cn/ui/karate?id=below"><code>below()</code></a>
    | <a href="#/zh-cn/ui/karate?id=near"><code>near()</code></a>
    | <a href="#/zh-cn/ui/karate?id=locator-lookup">Locator Lookup</a>
  </td>
</tr>
<tr>
  <th>浏览器</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=driverurl"><code>driver.url</code></a>
    | <a href="#/zh-cn/ui/karate?id=driverdimensions"><code>driver.dimensions</code></a>
    | <a href="#/zh-cn/ui/karate?id=refresh"><code>refresh()</code></a>
    | <a href="#/zh-cn/ui/karate?id=reload"><code>reload()</code></a> 
    | <a href="#/zh-cn/ui/karate?id=back"><code>back()</code></a>
    | <a href="#/zh-cn/ui/karate?id=forward"><code>forward()</code></a>
    | <a href="#/zh-cn/ui/karate?id=maximize"><code>maximize()</code></a>
    | <a href="#/zh-cn/ui/karate?id=minimize"><code>minimize()</code></a>
    | <a href="#/zh-cn/ui/karate?id=fullscreen"><code>fullscreen()</code></a>
    | <a href="#/zh-cn/ui/karate?id=quit"><code>quit()</code></a>
  </td>
</tr>
<tr>
  <th>页面</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=dialog"><code>dialog()</code></a>    
    | <a href="#/zh-cn/ui/karate?id=switchpage"><code>switchPage()</code></a>
    | <a href="#/zh-cn/ui/karate?id=switchFrame"><code>switchFrame()</code></a> 
    | <a href="#/zh-cn/ui/karate?id=close"><code>close()</code></a>    
    | <a href="#/zh-cn/ui/karate?id=drivertitle"><code>driver.title</code></a>
    | <a href="#/zh-cn/ui/karate?id=screenshot"><code>screenshot()</code></a>    
    | <a href="#/zh-cn/ui/karate?id=pdf"><code>pdf()</code></a>    
  </td>
</tr>
<tr>
  <th>动作</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=click"><code>click()</code></a>
    | <a href="#/zh-cn/ui/karate?id=input"><code>input()</code></a>
    | <a href="#/zh-cn/ui/karate?id=submit"><code>submit()</code></a>
    | <a href="#/zh-cn/ui/karate?id=focus"><code>focus()</code></a>
    | <a href="#/zh-cn/ui/karate?id=clear"><code>clear()</code></a>
    | <a href="#/zh-cn/ui/karate?id=valueset"><code>value(set)</code></a>   
    | <a href="#/zh-cn/ui/karate?id=select"><code>select()</code></a>
    | <a href="#/zh-cn/ui/karate?id=scroll"><code>scroll()</code></a>
    | <a href="#/zh-cn/ui/karate?id=mouse"><code>mouse()</code></a>
    | <a href="#/zh-cn/ui/karate?id=highlight"><code>highlight()</code></a>
    | <a href="#/zh-cn/ui/karate?id=highlightall"><code>highlightAll()</code></a>
  </td>
</tr>
<tr>
  <th>状态</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=html"><code>html()</code></a>
    | <a href="#/zh-cn/ui/karate?id=text"><code>text()</code></a>
    | <a href="#/zh-cn/ui/karate?id=value"><code>value()</code></a>
    | <a href="#/zh-cn/ui/karate?id=attribute"><code>attribute()</code></a>
    | <a href="#/zh-cn/ui/karate?id=enabled"><code>enabled()</code></a>
    | <a href="#/zh-cn/ui/karate?id=exists"><code>exists()</code></a>
    | <a href="#/zh-cn/ui/karate?id=optional"><code>optional()</code></a>    
    | <a href="#/zh-cn/ui/karate?id=locate"><code>locate()</code></a>    
    | <a href="#/zh-cn/ui/karate?id=locateall"><code>locateAll()</code></a>
    | <a href="#/zh-cn/ui/karate?id=position"><code>position()</code></a>
  </td>
</tr>
<tr>
  <th>等待 / 运行JS</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=retry"><code>retry()</code></a>
    | <a href="#/zh-cn/ui/karate?id=waitfor"><code>waitFor()</code></a>    
    | <a href="#/zh-cn/ui/karate?id=waitforany"><code>waitForAny()</code></a>
    | <a href="#/zh-cn/ui/karate?id=waitforurl"><code>waitForUrl()</code></a>
    | <a href="#/zh-cn/ui/karate?id=waitfortext"><code>waitForText()</code></a>
    | <a href="#/zh-cn/ui/karate?id=waitforenabled"><code>waitForEnabled()</code></a>
    | <a href="#/zh-cn/ui/karate?id=waitforresultcount"><code>waitForResultCount()</code></a>  
    | <a href="#/zh-cn/ui/karate?id=waituntil"><code>waitUntil()</code></a>    
    | <a href="#/zh-cn/ui/karate?id=delay"><code>delay()</code></a>
    | <a href="#/zh-cn/ui/karate?id=script"><code>script()</code></a>
    | <a href="#/zh-cn/ui/karate?id=scriptall"><code>scriptAll()</code></a>
    | <a href="#/zh-cn/ui/karate?id=karate-vs-the-browser">Karate vs the Browser</a>
  </td>
</tr>
<tr>
  <th>Cookies</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=cookie"><code>cookie()</code></a>
      <a href="#/zh-cn/ui/karate?id=cookieset"><code>cookie(set)</code></a>
    | <a href="#/zh-cn/ui/karate?id=drivercookies"><code>driver.cookies</code></a>
    | <a href="#/zh-cn/ui/karate?id=deletecookie"><code>deleteCookie()</code></a>
    | <a href="#/zh-cn/ui/karate?id=clearcookies"><code>clearCookies()</code></a>
  </td>
</tr>
<tr>
  <th>Chrome</th>
  <td>
      <a href="#/zh-cn/ui/karate?id=chrome-java-api">Java API</a>
    | <a href="#/zh-cn/ui/karate?id=driverpdf"><code>driver.pdf()</code></a>
    | <a href="#/zh-cn/ui/karate?id=driverscreenshotfull"><code>driver.screenshotFull()</code></a>
    | <a href="#/zh-cn/ui/karate?id=driverintercept"><code>driver.intercept()</code></a>
    | <a href="#/zh-cn/ui/karate?id=driverinputfile"><code>driver.inputFile()</code></a>
    | <a href="#/zh-cn/ui/karate?id=driveremulatedevice"><code>driver.emulateDevice()</code></a>
    | <a href="#/zh-cn/ui/karate?id=scriptawait"><code>driver.scriptAwait()</code></a> 
  </td> 
</tr>
</table>

# Driver 配置

## `configure driver`

使用默认安装目录下的本地chrome

```cucumber
* configure driver = { type: 'chrome' }
```

定制启动路径或脚本, `chrome` 为系统环境变量下的可执行文件.

```cucumber
* configure driver = { type: 'chrome', executable: 'chrome' }
```

使用 WebDriver, 如 `chromedriver`:

```cucumber
{ type: 'chromedriver', port: 9515, executable: 'chromedriver' }
```

| key                 | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `type`              | 参考 [driver types](#driver-types)                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `executable`        | 设置后会启动这个命令. 如果不在 [`PATH`](https://www.java.com/en/download/help/path.xml) 中, 需要指定完整目录                                                                                                                                                                                                                                                          |
| `start`             | 默认 `true`, 尝试运行 `executable` - 如果 `executable` 没有设置, 就会使用系统默认的                                                                                                                                                                                                                                                                                                                          |
| `stop`              | 可选, 默认是 `true`, 测试脚本执行完后关闭driver                                                                                                                                                                                                                                                                                      |
| `port`              | 可选, 不设置将使用默认的端口号                                                                                                                                                                                                                                                                                                                                                                                                     |
| `host`              | 可选, 默认是`localhost`, 可设置成服务端ip                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `headless`          | [headless 模式](https://developers.google.com/web/updates/2017/04/headless-chrome) 仅适用 `{ type: 'chrome' }`                                                                                                                                                                                                                                                                        |
| `showDriverLog`     | 默认 `false`, 报告中包含http请求                                                                                                                                                                                                                                                                                                                                                                              |
| `showProcessLog`    | 默认 `false`, 报告中包含进程日志                                                                                                                                                                                                                                                                                                                                                                                               |
| `addOptions`        | 默认 `null`, `executable` 额外的启动参数, 数组格式, 如: `['--no-sandbox', '--windows-size=1920,1080']`                                                                                                                                                                                                                                                                                                                      |
| `webDriverUrl`      | 查看 [`webDriverUrl`](#webdriverurl)                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `webDriverSession`  | 查看 [`webDriverSession`](#webdriversession)                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `highlight`         | 默认 `false`, 演示中比较适合用, [选择器](#locators) 当前指定的 HTML 元素会高亮 `highlightDuration` 时间                                                                                                                                                                                                                                                                     |
| `highlightDuration` | 高亮时间, 默认 3000 (毫秒)                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `attach`            | 可选, `type: 'chrome'` 和 `start: false` 可用, 链接 Chrome DevTools 中 `targetUrl` 包含此字符串的会话                                                                                                                                                                                                                                                                                                                     |
| `startUrl`            | 可选, `type: 'chrome'` 和 `start: false` 可用, 链接 Chrome DevTools 中 `targetUrl` 或 `title` 包含此字符串的会话                                                                                                                                                                                                                                                                                                                     |
| `userDataDir`       | 可选, 默认情况会给浏览器自动创建个用户目录, 如果想保存历史记录可以指定个固定的, 如果driver是 Chrome, 会传递给 `--user-data-dir`.  |


## `configure newDriver`

`configure driver` 会设置默认的dirver, 只有在 driver url 时才会初始化. `configure newDriver` 会直接进行初始化drive, 如果需要同时启动多个driver时使用这种方式. 除了上面的参数, 添加了两个额外的参数.

| key                 |  描                   述                                 |
| ------------------- | ------------------------------------------------------  |
| `name`            |  必填, driver 的名字, 步骤中可以通过名字前缀指定使用特定的driver  |
| `default`         |  可选, 该driver 设置成默认driver                             |


## Driver 类型

推荐使用 `chrome`.

| 类型                                                                                    | 默认端口号     | 默认执行目录                                                                                                                                     | 描述                                                                                                                                      |
| --------------------------------------------------------------------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| [`chrome`](https://chromedevtools.github.io/devtools-protocol/)                         | 9222         | mac: `/Applications/Google Chrome.app/Contents/MacOS/Google Chrome` <br/>win: `C:/Program Files (x86)/Google/Chrome/Application/chrome.exe`    | 本地chrome通过 [DevTools protocol](https://chromedevtools.github.io/devtools-protocol/) 实现                                     |
| [`msedge`](https://docs.microsoft.com/en-us/microsoft-edge/)                            | 9222         | mac: `/Applications/Microsoft Edge.app/Contents/MacOS/Microsoft Edge` <br/>win: `C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe` | 基于 Chromium 的 Microsoft Edge, 通过 [DevTools protocol](https://docs.microsoft.com/en-us/microsoft-edge/devtools-protocol-chromium) |
| [`chromedriver`](https://sites.google.com/a/chromium.org/chromedriver/home)             | 9515         | `chromedriver`                                                                                                                                 | W3C Chrome Driver                                                                                                                                |
| [`geckodriver`](https://github.com/mozilla/geckodriver)                                 | 4444         | `geckodriver`                                                                                                                                  | W3C Gecko Driver (Firefox)                                                                                                                       |
| [`safaridriver`](https://webkit.org/blog/6900/webdriver-support-in-safari-10/)          | 5555         | `safaridriver`                                                                                                                                 | W3C Safari Driver                                                                                                                                |
| [`msedgedriver`](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) | 9515         | `msedgedriver`                                                                                                                                 | W3C Microsoft Edge WebDriver                                   |
| [`mswebdriver`](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)  | 17556        | `MicrosoftWebDriver`                                                                                                                           | Microsoft Edge "Legacy" WebDriver                                                                                                                |
| [`iedriver`](https://github.com/SeleniumHQ/selenium/wiki/InternetExplorerDriver)        | 5555         | `IEDriverServer`                                                                                                                               | IE (11 only) Driver                                                                                                                              |

# 选择器

除了自身扩展的语法, `/` 开头的代表 `XPath` 其他的是 `CSS selector`.

```cucumber
* input('input[name=someName]', 'test input')
* submit().click("//input[@name='commit']")
```

| 平台                    | 前缀 | 方法                                      | 例子                                         |
| --------------------------- | ------ | ------------------------------------------ | ----------------------------------------------- |
| web                         | (none) | css selector                               | `input[name=someName]`                          |
| web                         | `/`    | xpath                                      | `//input[@name='commit']`                       |
| web                         | `{}`   | [完整的文本匹配](#wildcard-locators)         | `{a}Click Me`                                   |
| web                         | `{^}`  | [前缀文本匹配](#wildcard-locators)           | `{^a}Click Me`                                  |

## 通配符-选择器


| 选择器示例                    | 描述                                                                                                   |
| --------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `click('{a}Click Me')`      | 找到的第一个文本(text-content)是`Click Me`的`<a>`标签                                                             |
| `click('{}Click Me')`       | 找到的第一个文本是`Click Me`的任意标签                             |
| `click('{^}Click')`         | 找到的第一个文本包含`Click`的任意标签                                  |
| `click('{^span}Click')`     | 找到的第一个文本包含`Click`的`<span>`标签                                                |
| `click('{div:2}Click Me')`  | 找到的第二个文本是`Click Me`的`div`标签                                           |
| `click('{span/a}Click Me')` | 找到文本是`Click Me`的`a`标签且其父标签是`span` |
| `click('{^*:4}Me')`         | 找到文本包含`Me`的第四个任意标签, `{*:4}` 可以简写成 `{:4}`                      |


# 关键字

[`driver`](#syntax) JS 对象, 控制浏览器, [`match`](https://github.com/intuit/karate#prepare-mutate-assert) 断言语句

## `driver`

导航到新地址. 这个步骤会使用 [configured](#configure-driver) 的配置初始化 [`driver`](#syntax) 实例, 后续的步骤才能使用.

```cucumber
* driver 'https://github.com/login'
```

# Syntax

使用内置的 `driver` JS 对象进行UI操作. 在使用 [`driver`](#driver) 关键字导航到某个网页后初始化.

## Methods

为了使用方便, 使用默认的时, 可以省略 "`driver.`" 前缀. 比如:

```cucumber
* driver.input('#eg02InputId', Key.SHIFT)
* match driver.text('#eg02DivId') == '16'
```

可以简写成:

```cucumber
* input('#eg02InputId', Key.SHIFT)
* match text('#eg02DivId') == '16'
```

```cucumber
* match driver.url contains 'page-01'
* driver.url = webUrlBase + '/page-02'
```

### 链式调用


```cucumber
# retry 返回 "Driver" 实例
* retry().click('#someId')
```

```cucumber
# waitUntilEnabled() 返回 "Element" 实例
* waitUntilEnabled('#someBtn').click()
```

```cucumber
* retry(5, 10000).waitUntilEnabled('#someBtn').click()
```

移动鼠标 [mouse()](#mouse) 到 `[x, y]` 然后点击:

```cucumber
* mouse(100, 200).click()
```

```cucumber
* rightOf('{}Input On Right').input('input right')
```


# 语法

## `driver.url`

获取当前的url并断言. 例如:

```cucumber
* match driver.url == webUrlBase + '/page-02'
```

```cucumber
* driver.url = 'http://localhost:8080/test'
```

## `driver.title`

获取当前页面的标题. 如:

```cucumber
* match driver.title == 'Test Page'
```

如果重载页面后立刻断言可能会出错, 需要等待或者使用[`waitForUrl()`](#waitforurl)

## `driver.dimensions`

设置浏览器窗口位置和大小:

```cucumber
 * driver.dimensions = { x: 0, y: 0, width: 300, height: 800 }
```

```cucumber
* def dims = driver.dimensions
```

返回json: `{ x: '#number', y: '#number', width: '#number', height: '#number' }`

## `position()`

获取元素位置和大小

```cucumber
* def pos = position('#someid')
```

返回格式: `{ x: '#number', y: '#number', width: '#number', height: '#number' }`

## `input()`

```cucumber
* input('input[name=someName]', 'test input')
```

第二个参数可以是列表

```cucumber
* input('input[name=someName]', ['test', ' input', Key.ENTER])
```

可选的第三个参数为每次输入的时间间隔(毫秒)

```cucumber
* input('input[name=someName]', ['a', 'b', 'c', Key.ENTER], 200)
```


```cucumber
* input('input[name=someName]', 'type this slowly', 100)
```

```cucumber
* input('body', Key.ESCAPE)
```

### 特殊按键

特殊按键像 `ENTER`, `TAB` 等:

```cucumber
* input('#someInput', 'test input' + Key.ENTER)
```

## `submit()`

Karate has an [elegant approach](#chaining) to handling any action such as [`click()`](#click) that results in a new page load. You "signal" that a submit is expected by calling the `submit()` function (which returns a `Driver` object) and then "[chaining](#chaining)" the action that is expected to trigger a page load.

```cucumber
When submit().click('*Page Three')
```

The advantage of this approach is that it works with any of the actions. So even if your next step is the [`ENTER` key](#special-keys), you can do this:

```cucumber
When submit().input('#someform', Key.ENTER)
```

Karate will do the best it can to detect a page change and wait for the load to complete before proceeding to _any_ step that follows.

You can even mix this into [`mouse()`](#mouse) actions.

For some SPAs (Single Page Applications) the detection of a "page load" may be difficult because page-navigation (and the browser history) is taken over by JavaScript. In such cases, you can always fall-back to a [`waitForUrl()`](#waitforurl) or a more generic [`waitFor()`](#waitfor).

### `waitForUrl()` instead of `submit()`

Sometimes, because of an HTTP re-direct, it can be difficult for Karate to detect a page URL change, or it will be detected too soon, causing your test to fail. In such cases, you can use [`waitForUrl()`](#waitforurl).

Note that it uses a string "contains" match, so you just need to supply a portion of the URL you are expecting.

So instead of this, which uses [`submit()`](#submit):

```cucumber
Given driver 'https://google.com'
And input('input[name=q]', 'karate dsl')
When submit().click('input[name=btnI]')
Then match driver.url == 'https://github.com/intuit/karate'
```

You can do this. Note that `waitForUrl()` will also act as an assertion, so you don't have to do an extra [`match`](https://github.com/intuit/karate#match).

```cucumber
Given driver 'https://google.com'
And input('input[name=q]', 'karate dsl')
When click('input[name=btnI]')
And waitForUrl('https://github.com/intuit/karate')
```

And you can even [chain](#chaining) a [`retry()`](#retry) before the `waitForUrl()` if you know that it is going to take a long time:

```cucumber
And retry(5, 10000).waitForUrl('https://github.com/intuit/karate')
```

### `waitFor()` instead of `submit()`

This is very convenient to use for the _first_ element you need to interact with on a freshly-loaded page. It can be used instead of `waitForUrl()` and you can still perform a page URL assertion as seen below.

Here is an example of waiting for a search box to appear after a [`click()`](#click), and note how we re-use the [`Element`](#chaining) reference returned by `waitFor()` to proceed with the flow. We even slip in a page-URL assertion without missing a beat.

```cucumber
When click('{a}Find File')
And def search = waitFor('input[name=query]')
Then match driver.url == 'https://github.com/intuit/karate/find/master'
Given search.input('karate-logo.png')
```

Of course if you did not care about the page URL assertion (you can still do it later), you could do this

```cucumber
waitFor('input[name=query]').input('karate-logo.png')
```

## `delay()`

Of course, resorting to a "sleep" in a UI test is considered a very bad-practice and you should always use [`retry()`](#retry) instead. But sometimes it is un-avoidable, for example to wait for animations to render - before taking a [screenshot](#screenshot). The nice thing here is that it returns a `Driver` instance, so you can [chain](#chaining) any other method and the "intent" will be clear. For example:

```cucumber
* delay(1000).screenshot()
```

The other situation where we have found a `delay()` un-avoidable is for some super-secure sign-in forms - where a few milliseconds delay _before_ hitting the submit button is needed.

## `click()`

Just triggers a click event on the DOM element:

```cucumber
* click('input[name=someName]')
```

Also see [`submit()`](#submit) and [`mouse()`](#mouse).

## `select()`

You can use this for plain-vanilla `<select>` boxes that have not been overly "enhanced" by JavaScript. Nowadays, most "select" (or "multi-select") user experiences are JavaScript widgets, so you would be needing to fire a [`click()`](#click) or two to get things done. But if you are really dealing with an HTML `<select>`, then read on.

There are four variations and use the [locator](#locators) prefix conventions for _exact_ and _contains_ matches against the `<option>` text-content.

```cucumber
# select by displayed text
Given select('select[name=data1]', '{}Option Two')

# select by partial displayed text
And select('select[name=data1]', '{^}Two')

# select by `value`
Given select('select[name=data1]', 'option2')

# select by index
Given select('select[name=data1]', 2)
```

If you have trouble with `<select>` boxes, try using [`script()`](#script) to execute custom JavaScript within the page as a work-around.

## `focus()`

```cucumber
* focus('.myClass')
```

## `clear()`

```cucumber
* clear('#myInput')
```

If this does not work, try [`value(selector, value)`](#valueset).

## `scroll()`

Scrolls to the element.

```cucumber
* scroll('#myInput')
```

Since a `scroll()` + [`click()`](#click) (or [`input()`](#input)) is a common combination, you can [chain](#chaining) these:

```cucumber
* scroll('#myBtn').click()
* scroll('#myTxt').input('hello')
```

## `mouse()`

This returns an instance of [`Mouse` on which you can chain actions](#chaining). A common need is to move (or hover) the mouse, and for this you call the `move()` method.

The `mouse().move()` method has two forms. You can pass 2 integers as the `x` and `y` co-ordinates or you can pass the [locator](#locators) string of the element to move to. Make sure you call `go()` at the end - if the last method in the chain is not `click()` or `up()`.

```cucumber
* mouse().move(100, 200).go()
* mouse().move('#eg02RightDivId').click()
# this is a "click and drag" action
* mouse().down().move('#eg02LeftDivId').up()
```

You can even chain a [`submit()`](#submit) to wait for a page load if needed:

```cucumber
* mouse().move('#menuItem').submit().click();
```

Since moving the mouse is a common task, these short-cuts can be used:

```cucumber
* mouse('#menuItem32').click()
* mouse(100, 200).go()
* waitUntilEnabled('#someBtn').mouse().click()
```

These are useful in situations where the "normal" [`click()`](#click) does not work - especially when the element you are clicking is not a normal hyperlink (`<a href="">`) or `<button>`.

The rare need to "double-click" is supported as a `doubleClick()` method:

```cucumber
* mouse('#myBtn').doubleClick()
```

## `close()`

Close the page / tab.

## `quit()`

Closes the browser. You normally _never_ need to use this in a test, Karate will close the browser automatically after a `Scenario` unless the `driver` instance was created before entering the `Scenario`.

## `html()`

Get the [`outerHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/outerHTML), so will include the markup of the selected element. Useful for [`match contains`](https://github.com/intuit/karate#match-contains) assertions. Example:

```cucumber
And match html('#eg01DivId') == '<div id="eg01DivId">this div is outside the iframe</div>'
```

## `text()`

Get the [`textContent`](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent). Example:

```cucumber
And match text('.myClass') == 'Class Locator Test'
```

## `value()`

Get the HTML form-element [`value`](https://www.w3schools.com/jsref/prop_text_value.asp). Example:

```cucumber
And match value('.myClass') == 'some value'
```

## `value(set)`

Set the HTML form-element [value](https://www.w3schools.com/jsref/prop_text_value.asp). Example:

```cucumber
When value('#eg01InputId', 'something more')
```

## `attribute()`

Get the HTML element [attribute value by attribute name](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute). Example:

```cucumber
And match attribute('#eg01SubmitId', 'type') == 'submit'
```

## `enabled()`

If the element is `enabled` and not `disabled`:

```cucumber
And match enabled('#eg01DisabledId') == false
```

Also see [`waitUntil()`](#waituntil) for an example of how to wait _until_ an element is "enabled" or until any other element property becomes the target value.

## `waitForUrl()`

Very handy for waiting for an expected URL change _and_ asserting if it happened.

For convenience, it will do a string contains match (not an exact match) so you don't need to worry about `http` vs `https` for example. It will also return a string which is the _actual_ URL in case you need to use it for further actions in the test script.

```cucumber
# note that you don't need the full url
* waitForUrl('/some/path')

# if you want to get the actual url for later use
* def actualUrl = waitForUrl('/some/path')
```

See [`waitForUrl()` instead of `submit()`](#waitforurl-instead-of-submit). Also see [waits](#wait-api).

## `waitForText()`

This is just a convenience short-cut for `waitUntil(locator, "_.textContent.includes('" + expected + "')")` since it is so frequently needed. Note the use of the JavaScript [`String.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes) function to do a _text contains_ match for convenience. The need to "wait until some text appears" is so common, and with this - you don't need to worry about dealing with white-space such as line-feeds and invisible tab characters.

Of course, try not to use single-quotes within the string to be matched, or escape them using a back-slash (`\`) character.

```cucumber
* waitForText('#eg01WaitId', 'APPEARED')
```

And if you really need to scan the whole page for some text, you can use this, but it is better to be more specific for better performance:

```cucumber
* waitForText('body', 'APPEARED')
```

## `waitForEnabled()`

This is just a convenience short-cut for `waitUntil(locator, '!_.disabled')` since it is so frequently needed:

```cucumber
And waitForEnabled('#someId').click()
```

Also see [waits](#wait-api).

## `waitForResultCount()`

A very powerful and useful way to wait until the _number_ of elements that match a given locator is equal to a given number. This is super-useful when you need to wait for say a table of slow-loading results, and where the table may contain fewer elements at first. There are two variations. The first will simply return a `List` of [`Element`](#chaining) instances.

```cucumber
  * waitForResultCount('div#eg01 div', 4)
```

Most of the time, you just want to wait until a certain number of matching elements, and then move on with your flow, and in that case, the above is sufficient. If you need to actually do something with each returned `Element`, see [`locateAll()`](#locateall) or the option below.

The second variant takes a third argument, which is going to do the same thing as the [`scriptAll()`](#scriptall) method:

```cucumber
  When def list = waitForResultCount('div#eg01 div', 4, '_.innerHTML')
  Then match list == '#[4]'
  And match each list contains '@@data'
```

So in a _single step_ we can wait for the number of elements to match _and_ extract data as an array.

## `waitFor()`

This is typically used for the _first_ element you need to interact with on a freshly loaded page. Use this in case a [`submit()`](#submit) for the previous action is un-reliable, see the section on [`waitFor()` instead of `submit()`](#waitfor-instead-of-submit)

This will wait until the element (by [locator](#locators)) is present in the page and uses the configured [`retry()`](#retry) settings. This will fail the test if the element does not appear after the configured number of re-tries have been attempted.

Since `waitFor()` returns an [`Element`](#chaining) instance on which you can call "chained" methods, this can be the pattern you use, which is very convenient and readable:

```cucumber
And waitFor('#eg01WaitId').click()
```

Also see [waits](#wait-api).

## `waitForAny()`

Rarely used - but accepts multiple arguments for those tricky situations where a particular element may or may _not_ be present in the page. It returns the [`Element`](#chaining) representation of whichever element was found _first_, so that you can perform conditional logic to handle accordingly.

But since the [`optional()`](#optional) API is designed to handle the case when a given [locator](#locators) does _not_ exist, you can write some very concise tests, _without_ needing to examine the returned object from `waitForAny()`.

Here is a real-life example combined with the use of [`retry()`](#retry):

```cucumber
* retry(5, 10000).waitForAny('#nextButton', '#randomButton')
* optional('#nextButton').click()
* optional('#randomButton').click()
```

If you have more than two locators you need to wait for, use the single-argument-as-array form, like this:

```cucumber
* waitForAny(['#nextButton', '#randomButton', '#blueMoonButton'])
```

Also see [waits](#wait-api).

## `optional()`

Returns an [`Element`](src/main/java/com/intuit/karate/driver/Element.java) (instead of `exists()` which returns a boolean). What this means is that it can be [chained](#chaining) as you expect. But there is a twist ! If the [locator](#locators) does _not_ exist, any attempt to perform actions on it will _not_ fail your test - and silently perform a "no-op".

This is designed specifically for the kind of situation described in the example for [`waitForAny()`](#waitforany). If you wanted to check if the `Element` returned exists, you can use the `present` property "getter" as follows:

```cucumber
* assert optional('#someId').present
```

But what is most useful is how you can now _click only if element exists_. As you can imagine, this can handle un-predictable dialogs, advertisements and the like.

```cucumber
* optional('#elusiveButton').click()
# or if you need to click something else
* if (exists('#elusivePopup')) click('#elusiveButton')
```

And yes, you _can_ use an [`if` statement in Karate](https://github.com/intuit/karate#conditional-logic) !

Note that the `optional()`, `exists()` and `locate()` APIs are a little different from the other `Element` actions, because they will _not_ honor any intent to [`retry()`](#retry) and _immediately_ check the HTML for the given locator. This is important because they are designed to answer the question: "_does the element exist in the HTML page **right now** ?_"

Note that the "opposite" of `optional()` is [`locate()`](#locate) which will fail if the element is not present.

If all you need to do is check whether an element exists and fail the test if it doesn't, see [`exists()`](#exists) below.

## `exists()`

This method returns a boolean (`true` or `false`), perfect for asserting if an element exists and failing the test if not.

## `waitUntil()`

Wait for the _browser_ JS expression to evaluate to `true`. Will poll using the [retry()](#retry) settings configured.

```cucumber
* waitUntil("document.readyState == 'complete'")
```

Note that the JS here has to be a "raw" string that is simply sent to the browser as-is and evaluated there. This means that you cannot use any Karate JS objects or API-s such as `karate.get()` or `driver.title`. So trying to use `driver.title == 'My Page'` will _not_ work, instead you have to do this:

```cucumber
* waitUntil("document.title == 'My Page'")
```

Also see [Karate vs the Browser](#karate-vs-the-browser).

### `waitUntil(locator,js)`

A very useful variant that takes a [locator](#locators) parameter is where you supply a JavaScript "predicate" function that will be evaluated _on_ the element returned by the locator in the HTML DOM. Most of the time you will prefer the short-cut boolean-expression form that begins with an underscore (or "`!`"), and Karate will inject the JavaScript DOM element reference into a variable named "`_`".

Here is a real-life example:

> One limitation is that you cannot use double-quotes _within_ these expressions, so stick to the pattern seen below.

```cucumber
And waitUntil('.alert-message', "_.innerHTML.includes('Some Text')")
```

### Karate vs the Browser

One thing you need to get used to is the "separation" between the code that is evaluated by Karate and the JavaScript that is sent to the _browser_ (as a raw string) and evaluated. Pay attention to the fact that the [`includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes) function you see in the above example - is pure JavaScript.

The use of `includes()` is needed in this real-life example, because [`innerHTML()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML) can return leading and trailing white-space (such as line-feeds and tabs) - which would cause an exact "`==`" comparison in JavaScript to fail.

But guess what - this example is baked into a Karate API, see [`waitForText()`](#waitfortext).

For an example of how JavaScript looks like on the "Karate side" see [Function Composition](#function-composition).

This form of `waitUntil()` is very useful for waiting for some HTML element to stop being `disabled`. Note that Karate will fail the test if the `waitUntil()` returned `false` - _even_ after the configured number of [re-tries](#retry) were attempted.

```cucumber
And waitUntil('#eg01WaitId', "function(e){ return e.innerHTML == 'APPEARED!' }")

# if the expression begins with "_" or "!", Karate will wrap the function for you !
And waitUntil('#eg01WaitId', "_.innerHTML == 'APPEARED!'")
And waitUntil('#eg01WaitId', '!_.disabled')
```

Also see [`waitForEnabled()`](#waitforenabled) which is the preferred short-cut for the last example above, also look at the examples for [chaining](#chaining) and then the section on [waits](#wait-api).

### `waitUntil(function)`

A _very_ powerful variation of [`waitUntil()`](#waituntil) takes a full-fledged JavaScript function as the argument. This can loop until _any_ user-defined condition and can use any variable (or Karate or [Driver JS API](#syntax)) in scope. The signal to stop the loop is to return any not-null object. And as a convenience, whatever object is returned, can be re-used in future steps.

This is best explained with an example. Note that [`scriptAll()`](#scriptall) will return an array, as opposed to [`script()`](#script).

```cucumber
When search.input('karate-logo.png')

# note how we return null to keep looping
And def searchFunction =
  """
  function() {
    var results = scriptAll('.js-tree-browser-result-path', '_.innerText');
    return results.size() == 2 ? results : null;
  }
  """

# note how we returned an array from the above when the condition was met
And def searchResults = waitUntil(searchFunction)

# and now we can use the results like normal
Then match searchResults contains 'karate-core/src/main/resources/karate-logo.png'
```

The above logic can actually be replaced with Karate's built-in short-cut - which is [`waitForResultCount()`](#waitforresultcount) Also see [waits](#wait-api).

## Function Composition

The above example can be re-factored in a very elegant way as follows, using Karate's [native support for JavaScript](https://github.com/intuit/karate#javascript-functions):

```cucumber
# this can be a global re-usable function !
And def innerText = function(locator){ return scriptAll(locator, '_.innerText') }

# we compose a function using another function (the one above)
And def searchFunction =
  """
  function() {
    var results = innerText('.js-tree-browser-result-path');
    return results.size() == 2 ? results : null;
  }
  """
```

The great thing here is that the `innnerText()` function can be defined in a [common feature](https://github.com/intuit/karate#multiple-functions-in-one-file) which all your scripts can re-use. You can see how it can be re-used anywhere to scrape the contents out of _any_ HTML tabular data, and all you need to do is supply the [locator](#locators) that matches the elements you are interested in.

Also see [Karate vs the Browser](#karate-vs-the-browser).

## `retry()`

For tests that need to wait for slow pages or deal with un-predictable element load-times or state / visibility changes, Karate allows you to _temporarily_ tweak the internal retry settings. Here are the few things you need to know.

### Retry Defaults

The [default retry settings](https://github.com/intuit/karate#retry-until) are:

- `count`: 3, `interval`: 3000 milliseconds (try three times, and wait for 3 seconds before the next re-try attempt)
- it is recommended that you stick to these defaults, which should suffice for most applications
- if you really want, you can change this "globally" in [`karate-config.js`](https://github.com/intuit/karate#configuration) like this:
  - `configure('retry', { count: 10, interval: 5000 });`
- or _any time_ within a script (`*.feature` file) like this:
  - `* configure retry = { count: 10, interval: 5000 }`

### Retry Actions

By default, all actions such as [`click()`](#click) will _not_ be re-tried - and this is what you would stick to most of the time, for tests that run smoothly and _quickly_. But some troublesome parts of your flow _will_ require re-tries, and this is where the `retry()` API comes in. There are 3 forms:

- `retry()` - just signals that the _next_ action will be re-tried if it fails, using the [currently configured retry settings](https://github.com/intuit/karate#retry-until)
- `retry(count)` - the next action will _temporarily_ use the `count` provided, as the limit for retry-attempts
- `retry(count, interval)` - _temporarily_ change the retry `count` _and_ retry `interval` (in milliseconds) for the next action

And since you can [chain](#chaining) the `retry()` API, you can have tests that clearly express the "_intent to wait_". This results in easily understandable one-liners, _only_ at the point of need, and to anyone reading the test - it will be clear as to _where_ extra "waits" have been applied.

Here are the various combinations for you to compare using [`click()`](#click) as an example.

| Script                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `click('#myId')`                 | Try to stick to this _default_ form for 95% of your test. If the element is not found, the test will fail immediately. But your tests will run smoothly and super-fast.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `waitFor('#myId').click()`       | Use [`waitFor()`](#waitfor) for the _first_ element on a newly loaded page or any element that takes time to load after the previous action. For the best performance, use this _only if_ using [`submit()`](#submit) for the (previous) action (that triggered the page-load) [is not reliable](#waitfor-instead-of-submit). It uses the currently configured [retry settings](#retry-defaults). With the [defaults](#retry-defaults), the test will fail after waiting for 3 x 3000 ms which is 9 seconds. Prefer this instead of any of the options below, or in other words - stick to the defaults as far as possible. |
| `retry().click('#myId')`         | This happens to be exactly equivalent to the above ! When you request a `retry()`, internally it is just a `waitFor()`. Prefer the above form as it is more readable. The advantage of this form is that it is easy to quickly add (and remove) when working on a test in development mode.                                                                                                                                                                                                                                                                                                                                 |
| `retry(5).click('#myId')`        | Temporarily use `5` as the max retry attempts to use _and_ apply a "wait". Since `retry()` expresses an intent to "wait", the `waitFor()` can be omitted for the [chained](#chained) action.                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `retry(5, 10000).click('#myId')` | Temporarily use `5` as the max retry attempts _and_ 10 seconds as the time to wait before the next retry attempt. Again like the above, the `waitFor()` is implied. The test will fail if the element does not load within 50 seconds.                                                                                                                                                                                                                                                                                                                                                                                      |

### Wait API

The set of built-in functions that start with "`wait`" handle all the cases you would need to typically worry about. Keep in mind that:

- all of these examples _will_ [`retry()`](#retry) internally by default
- you can prefix a [`retry()`](#retry-actions) _only_ if you need to over-ride the settings for _this_ "wait" - as shown in the second row

| Script                                                     | Description                                                                                                                                                    |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`waitFor('#myId')`](#waitfor)                             | waits for an element as described above                                                                                                                        |
| `retry(10).waitFor('#myId')`                               | like the above, but temporarily over-rides the settings to wait for a [longer time](#retry-actions), and this can be done for _all_ the below examples as well |
| [`waitForUrl('google.com')`](#waitforurl)                  | for convenience, this uses a string _contains_ match - so for example you can omit the `http` or `https` prefix                                                |
| [`waitForText('#myId', 'appeared')`](#waitfortext)         | frequently needed short-cut for waiting until a string appears - and this uses a "string contains" match for convenience                                       |
| [`waitForEnabled('#mySubmit')`](#waitforenabled)           | frequently needed short-cut for `waitUntil(locator, '!_disabled')`                                                                                             |
| [`waitForResultCount('.myClass', 4)`](#waitforresultcount) | wait until a certain number of rows of tabular data is present                                                                                                 |
| [`waitForAny('#myId', '#maybe')`](#waitforany)             | handle if an element may or _may not_ appear, and if it does, handle it - for e.g. to get rid of an ad popup or dialog                                         |
| [`waitUntil(expression)`](#waituntil)                      | wait until _any_ user defined JavaScript statement to evaluate to `true` in the browser                                                                        |
| [`waitUntil(function)`](#waituntilfunction)                | use custom logic to handle _any_ kind of situation where you need to wait, _and_ use other API calls if needed                                                 |

Also see the examples for [chaining](#chaining).

## `script()`

Will actually attempt to evaluate the given string as JavaScript within the browser.

```cucumber
* assert 3 == script("1 + 2")
```

To avoid problems, stick to the pattern of using double-quotes to "wrap" the JavaScript snippet, and you can use single-quotes within.

```cucumber
* script("console.log('hello world')")
```

A more useful variation is to perform a JavaScript `eval` on a reference to the HTML DOM element retrieved by a [locator](#locators). For example:

```cucumber
And match script('#eg01WaitId', "function(e){ return e.innerHTML }") == 'APPEARED!'
# which can be shortened to:
And match script('#eg01WaitId', '_.innerHTML') == 'APPEARED!'
```

Normally you would use [`text()`](#text) to do the above, but you get the idea. Expressions follow the same short-cut rules as for [`waitUntil()`](#waituntil).

Here is an interesting example where a JavaScript event can be triggered on a given HTML element:

```cucumber
* waitFor('#someId').script("_.dispatchEvent(new Event('change'))")
```

For an advanced example of simulating a drag and drop operation see [this answer on Stack Overflow](https://stackoverflow.com/a/60800181/143475).

Also see the plural form [`scriptAll()`](#scriptall).

## `scriptAll()`

Just like [`script()`](#script), but will perform the script `eval()` on _all_ matching elements (not just the first) - and return the results as a JSON array / list. This is very useful for "bulk-scraping" data out of the HTML (such as `<table>` rows) - which you can then proceed to use in [`match`](https://github.com/intuit/karate#match) assertions:

```cucumber
# get text for all elements that match css selector
When def list = scriptAll('div div', '_.textContent')
Then match list == '#[3]'
And match each list contains '@@data'
```

See [Function Composition](#function-composition) for another good example. Also see the singular form [`script()`](#script).

### `scriptAll()` with filter

`scriptAll()` can take a third argument which has to be a JavaScript "predicate" function, that returns a boolean `true` or `false`. This is very useful to "filter" the results that match a desired condition - typically a text comparison. For example if you want to get only the cells out of a `<table>` that contain the text "data" you can do this:

```cucumber
* def list = scriptAll('div div', '_.textContent', function(x){ return x.contains('data') })
* match list == ['data1', 'data2']
```

> Note that the JS in this case is run by _Karate_ not the browser, so you use the Java `String.contains()` API not the JavaScript `String.includes()` one.

See also [`locateAll()` with filter](#locateall-with-filter).

## `driver.scriptAwait()`

Only supported for `type: 'chrome'` - this will wait for a JS promise to resolve and then return the result as a JSON object. Here is an [example](../karate-e2e-tests/src/test/java/axe/axe.feature):

```cucumber
* def axeResponse = driver.scriptAwait('axe.run()')
```

## `locate()`

Rarely used, but when you want to just instantiate an [`Element`](src/main/java/com/intuit/karate/driver/Element.java) instance, typically when you are writing custom re-usable functions, or using an element as a "waypoint" to access other elements in a large, complex "tree".

```cucumber
* def e = locate('.some-div')
# now you can have multiple steps refer to "e"
* e.locate('.something-else').input('foo')
* e.locate('.some-button').click()
```

Note that `locate()` will fail the test if the element was not found. Think of it as just like [`waitFor()`](#waitfor) but without the "wait" part.

See also [`locateAll()`](#locateall).

## `locateAll()`

This will return _all_ elements that match the [locator](#locator) as a list of [`Element`](src/main/java/com/intuit/karate/driver/Element.java) instances. You can now use Karate's [core API](https://github.com/intuit/karate#the-karate-object) and call [chained](#chaining) methods. Here are some examples:

```cucumber
# find all elements with the text-content "Click Me"
* def elements = locateAll('{}Click Me')
* match karate.sizeOf(elements) == 7
* elements[6].click()
* match elements[3].script('_.tagName') == 'BUTTON'
```

Take a look at how to [loop and transform](https://github.com/intuit/karate#json-transforms) data for more ideas.

### `locateAll()` with filter

`locateAll()` can take a second argument which has to be a JavaScript "predicate" function, that returns a boolean `true` or `false`. This is very useful to "filter" the results that match a desired condition - typically a text comparison.

Imagine a situation where you want to get only the element where a certain attribute value _starts with_ some text - and then click on it. A plain CSS selector won't work - but you can do this:

```cucumber
* def filter = function(x){ return x.attribute('data-label').startsWith('somePrefix_') }
* def list = locateAll('div[data-label]', filter)
* list[0].click()
```

The `filter` function above, will be called for each [`Element`](src/main/java/com/intuit/karate/driver/Element.java) - which means that you can call methods on it such as [`Element.attribute(name)`](#chaining) in this case. Note that the JS function in this case is run by _Karate_ not the browser, so you use the Java `String.startsWith()` API.

Since you can call `Element.script()` - _any_ kind of filtering will be possible. For example here is the equivalent of the example above. Note the combination of "Karate JavaScript" and ["JS that runs in the browser"](#karate-vs-the-browser):

```cucumber
* def filter = function(x){ return x.script("_.getAttribute('data-label')").startsWith('somePrefix_') }
* def list = locateAll('div[data-label]', filter)
* list[0].click()
```

See also [`scriptAll()` with filter](#scriptall-with-filter).

## `refresh()`

Normal page reload, does _not_ clear cache.

## `reload()`

_Hard_ page reload, which _will_ clear the cache.

## `back()`

## `forward()`

## `maximize()`

## `minimize()`

## `fullscreen()`

## `cookie(set)`

Set a cookie. The method argument is JSON, so that you can pass more data in addition to the `value` such as `domain` and `url`. Most servers expect the `domain` to be set correctly like this:

```cucumber
Given def myCookie = { name: 'hello', value: 'world', domain: '.mycompany.com' }
When cookie(myCookie)
Then match driver.cookies contains '#(^myCookie)'
```

> Note that you can do the above as a one-liner like this: `* cookie({ name: 'hello', value: 'world' })`, just keep in mind here that then it would follow the rules of [Enclosed JavaScript](https://github.com/intuit/karate#enclosed-javascript) (not [Embedded Expressions](https://github.com/intuit/karate#embedded-expressions))

### Hybrid Tests

If you need to set cookies _before_ the target URL is loaded, you can start off by navigating to `about:blank` like this:

```cucumber
# perform some API calls and initialize the value of "token"
* driver 'about:blank'
* cookie({ name: 'my.auth.token', value: token, domain: '.mycompany.com' })
# now you can jump straight into your home page and bypass the login screen !
* driver baseUrl + '/home'
```

This is very useful for "hybrid" tests. Since Karate combines API testing capabilities, you can sign-in to your SSO store via a REST end-point, and then drop cookies onto the browser so that you can bypass the user log-in experience. This can be a huge time-saver !

Note that the API call (or the routine that gets the required data) can be made to run only once for the whole test-suite using [`karate.callSingle()`](https://github.com/intuit/karate#hooks).

## `cookie()`

Get a cookie by name. Note how Karate's [`match`](https://github.com/intuit/karate#match) syntax comes in handy.

```cucumber
* def cookie1 = { name: 'foo', value: 'bar' }
And match driver.cookies contains '#(^cookie1)'
And match cookie('foo') contains cookie1
```

## `driver.cookies`

See above examples.

## `deleteCookie()`

Delete a cookie by name:

```cucumber
When deleteCookie('foo')
Then match driver.cookies !contains '#(^cookie1)'
```

## `clearCookies()`

Clear all cookies.

```cucumber
When clearCookies()
Then match driver.cookies == '#[0]'
```

## `dialog()`

There are two forms. The first takes a single boolean argument - whether to "accept" or "cancel". The second form has an additional string argument which is the text to enter for cases where the dialog is expecting user input.

```cucumber
# cancel
* dialog(false)

# enter text and accept
* dialog(true, 'some text')
```

Also works as a "getter" to retrieve the text of the currently visible dialog:

```cucumber
* match driver.dialog == 'Please enter your name:'
```

## `switchPage()`

When multiple browser tabs are present, allows you to switch to one based on page title _or_ URL.

```cucumber
When switchPage('Page Two')
```

For convenience, a string "contains" match is used. So you can do this, without needing the `https://` part:

```cucumber
* switchPage('mydomain.com/dashboard')
```

You can also switch by page index if you know it:

```cucumber
* switchPage(1)
```

## `switchFrame()`

This "sets context" to a chosen frame (or `<iframe>`) within the page. There are 2 variants, one that takes an integer as the param, in which case the frame is selected based on the order of appearance in the page:

```cucumber
When switchFrame(0)
```

Or you use a [locator](#locators) that points to the `<iframe>` element that you need to "switch to".

```cucumber
When switchFrame('#frame01')
```

After you have switched, any future actions such as [`click()`](#click) would operate within the "selected" `<iframe>`. To "reset" so that you are back to the "root" page, just switch to `null` (or integer value `-1`):

```cucumber
When switchFrame(null)
```

## `screenshot()`

There are two forms, if a [locator](#locators) is provided - only that HTML element will be captured, else the entire browser viewport will be captured. This method returns a byte array.

This will also do automatically perform a [`karate.embed()`](https://github.com/intuit/karate#karate-embed) - so that the image appears in the HTML report.

```cucumber
* screenshot()
# or
* screenshot('#someDiv')
```

If you want to disable the "auto-embedding" into the HTML report, pass an additional boolean argument as `false`, e.g:

```cucumber
* screenshot(false)
# or
* screenshot('#someDiv', false)
```

## `pdf()`

To create paginated pdf document from the page loaded.

```cucumber
* def pdfDoc = pdf({'orientation': 'landscape'})
* karate.write(pdfDoc, "pdfDoc.pdf")
```

## `highlight()`

To visually highlight an element in the browser, especially useful when working in the [debugger](https://github.com/intuit/karate/wiki/IDE-Support#vs-code-karate-plugin). Uses the [configured `highlightDuration`](#configure-driver).

```cucumber
* highlight('#eg01DivId')
```

## `highlightAll()`

Plural form of the above.

```cucumber
* highlightAll('input')
```

## `timeout()`

Rarely used, but sometimes for only some parts of your test - you need to tell the browser to wait for a very slow loading page. Behind the scenes, this sets the HTTP communication "read timeout". This does the same thing as the `timeout` key in the [driver config](#configure-driver) - but is designed so that you can change this "on the fly", _during_ the flow of a test.

Note that the duration is in milliseconds. As a convenience, to "reset" the value to what was initially set, you can call `timeout()` with no argument:

```cucumber
# wait 3 minutes if needed for page to load
* timeout(3 * 60 * 1000)
* driver 'http://mydomain/some/slow/page'
# reset to defaults for the rest of the test ...
* timeout()
```

## `driver.sessionId`

Only applies to WebDriver based driver sessions, and useful in case you need the session id to download any test-reports / video etc.

```cucumber
* def sessionId = driver.sessionId
```

## Tree Walking

The [Element](#chaining) API has "getters" for the following properties:

- `parent`
- `children` (returns an array of `Element`-s)
- `firstChild`
- `lastChild`
- `previousSibling`
- `nextSibling`

This can be convenient in some cases, for example as an alternative to [Friendly Locators](#friendly-locators). For example, where it is easy (or you already have a reference) to locate some element and you want to use that as a "base" to perform something on some other element which may not have a unique `id` or css / XPath locator.

```cucumber
* locate('#someDiv').parent.firstChild.click()
* locate('#foo').parent.children[3].click()
```

Also note that [`locate()`](#locate) and [`locateAll()`](#locateall) can be called _on_ an [`Element`](#chaining), so that the "search scope" is limited to that `Element` and it's children.

# Debugging

You can use the [Visual Studio Karate entension](https://github.com/intuit/karate/wiki/IDE-Support#vs-code-karate-plugin) for stepping through and debugging a test. You can see a [demo video here](https://twitter.com/KarateDSL/status/1167533484560142336). We recommend that you get comfortable with this because it is going to save you lots of time. And creating tests may actually turn out to be fun !

When you are in a hurry, you can pause a test in the middle of a flow just to look at the browser developer tools to see what CSS selectors you need to use. For this you can use [`karate.stop()`](../#karate-stop) - but of course, _NEVER_ forget to remove this before you move on to something else !

```cucumber
* karate.stop(9000)
```

And then you would see something like this in the console:

```
*** waiting for socket, type the command below:
curl http://localhost:9000
in a new terminal (or open the URL in a web-browser) to proceed ...
```

In most IDE-s, you would even see the URL above as a clickable hyperlink, so just clicking it would end the `stop()`. This is really convenient in "dev-local" mode. The integer port argument is mandatory and you have to choose one that is not being used.

# Code Reuse

You will often need to move steps (for e.g. a login flow) into a common feature that can be called from multiple test-scripts. When using a browser-driver, a [`call` in "shared scope"](https://github.com/intuit/karate#shared-scope) _has_ to be used. This means:

- a single driver instance is used for any [`call`-s](https://github.com/intuit/karate#call), even if nested
- even if the driver is instantiated (using the [`driver`](#driver) keyword) within a "called" feature - it will remain in the context after the `call` returns

A typical pattern will look like this:

```cucumber
Feature: main

Background:
* call read('login.feature')

Scenario:
* click('#someButton')
# the rest of your flow
```

Where `login.feature` would look something like:

```
Feature: login

Scenario:
* configure driver = { type: 'chrome' }
* driver urlBase + '/login'
* input('#username', 'john')
* input('#password', 'secret')
* click('#loginButton')
* waitForUrl('/dashboard')
```

There are many ways to parameterize the driver config or perform environment-switching, read [this](https://stackoverflow.com/a/60581024/143475) for more details.

Note [`callonce`](https://github.com/intuit/karate#callonce) is not supported for a `driver` instance. Separate `Scenario`-s that can run in parallel are encouraged. If you really want a long-running flow that combines steps from multiple features, you can make a `call` to each of them from the single "top-level" `Scenario`.

```cucumber
Feature: main

Background:
* call read('login.feature')

Scenario:
* call read('some.feature')
* call read('another.feature@someTag')
```

Best-practice would be to implement [Hybrid Tests](#hybrid-tests) where the values for the auth-cookies are set only once for the whole test-suite using [`karate.callSingle()`](https://github.com/intuit/karate#hooks).

# Locator Lookup

Other UI automation frameworks spend a lot of time encouraging you to follow a so-called "[Page Object Model](https://martinfowler.com/bliki/PageObject.html)" for your tests. The Karate project team is of the opinion that things can be made simpler.

One indicator of a _good_ automation framework is how much _work_ a developer needs to do in order to perform any automation action - such as clicking a button, or retrieving the value of some HTML object / property. In Karate - these are typically _one-liners_. And especially when it comes to test-automation, we have found that attempts to apply patterns in the pursuit of code re-use, more often than not - results in hard-to-maintain code, and severely impacts _readability_.

That said, there is some benefit to re-use of just [locators](#locators) and Karate's support for [JSON](https://github.com/intuit/karate#json) and [reading files](https://github.com/intuit/karate#reading-files) turns out to be a great way to achieve [DRY](https://en.wikipedia.org/wiki/Don't_repeat_yourself)-ness in tests. Here is one suggested pattern you can adopt.

First, you can maintain a JSON "map" of your application locators. It can look something like this. Observe how you can mix different [locator types](#locators), because they are all just string-values that behave differently depending on whether the first character is a "`/`" (XPath), "`{}`" ([wildcard](#wildcard-locators)), or not (CSS). Also note that this is _pure JSON_ which means that you have excellent IDE support for syntax-coloring, formatting, indenting, and ensuring well-formed-ness. And you can have a "nested" heirarchy, which means you can neatly "name-space" your locator reference look-ups - as you will see later below.

```json
{
  "testAccounts": {
    "numTransactions": "input[name=numTransactions]",
    "submit": "#submitButton"
  },
  "leftNav": {
    "home": "{}Home",
    "invoices": "{a}Invoices",
    "transactions": "{^}Transactions"
  },
  "transactions": {
    "addFirst": ".transactions .qwl-secondary-button",
    "descriptionInput": ".description-cell input",
    "description": ".description-cell .header5",
    "amount": ".amount-cell input"
  }
}
```

Karate has [great options for re-usability](https://github.com/intuit/karate#calling-other-feature-files), so once the above JSON is saved as `locators.json`, you can do this in a `common.feature`:

```cucumber
* call read 'locators.json'
```

This looks deceptively simple, but what happens is very interesting. It will inject all top-level "keys" of the JSON file into the Karate "context" as global [variables](https://github.com/intuit/karate#def). In normal programming languages, global variables are a _bad thing_, but for test-automation (when you know what you are doing) - this can be _really_ convenient.

> For those who are wondering how this works behind the scenes, since `read` refers to the [`read()`](https://github.com/intuit/karate#reading-files) function, the behavior of [`call`](https://github.com/intuit/karate#calling-javascript-functions) is that it will _invoke_ the function _and_ use what comes after it as the solitary function argument. And this `call` is using [shared scope](https://github.com/intuit/karate#shared-scope).

So now you have `testAccounts`, `leftNav` and `transactions` as variables, and you have a nice "name-spacing" of locators to refer to - within your different feature files:

```cucumber
* input(testAccounts.numTransactions, '0')
* click(testAccounts.submit)
* click(leftNav.transactions)

* retry().click(transactions.addFirst)
* retry().input(transactions.descriptionInput, 'test')
```

And this is how you can have all your locators defined in one place and re-used across multiple tests. You can experiment for yourself (probably depending on the size of your test-automation team) if this leads to any appreciable benefits, because the down-side is that you need to keep switching between 2 files - when writing and maintaining tests.

# Intercepting HTTP Requests

You can selectively re-direct some HTTP requests that the browser makes - into a [Karate test-double](https://github.com/intuit/karate/tree/master/karate-netty) ! This gives you some powerful options, for example you can simulate Ajax and [XHR](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) failures, or even replace entire widgets or sections of the page with "fake" HTML. The unified use of Karate test-doubles means that you can script dynamic responses and handle incoming URL, query-string and header variations. The following scenario will make this clear.

We will use this page: [`https://www.seleniumeasy.com/test/dynamic-data-loading-demo.html`](https://www.seleniumeasy.com/test/dynamic-data-loading-demo.html) - as an example. When a button on this page is clicked, a request is made to [`https://api.randomuser.me/?nat=us`](https://api.randomuser.me/?nat=us) - which returns some JSON data. That data is used to make _yet another_ request to fetch a JPEG image from e.g. [`https://randomuser.me/api/portraits/women/34.jpg`](https://randomuser.me/api/portraits/women/34.jpg). Finally, the page is updated to display the first-name, last-name and the image.

What we will do is intercept any request to a URL pattern `*randomuser.me/*` and "fake" a response. We can return JSON and even an image using a mock like this:

```cucumber
@ignore
Feature:

Background:
* configure cors = true
* def count = 0

Scenario: pathMatches('/api/{img}')
* def response = read('billie.jpg')
* def responseHeaders = { 'Content-Type': 'image/jpeg' }

Scenario:
* def count = count + 1
* def lastName = 'Request #' + count
* def response = read('response.json')
```

Refer to the [Karate test-doubles documentation](https://github.com/intuit/karate/tree/master/karate-netty) for details. We [configure cors = true](https://github.com/intuit/karate/tree/master/karate-netty#configure-cors) to ensure that the browser does not complain about cross-origin requests. If the request is for `/api/*`, the first `Scenario` matches - else the last one is a "catch all". Note how we can even serve an image with the right `Content-Type` header. And the returned JSON is dynamic, the `lastName` will modify [`response.json`](../karate-demo/src/test/java/driver/mock/response.json) via an [embedded-expression](https://github.com/intuit/karate#embedded-expressions).

## `driver.intercept()`

All we need to do now is to tell Chrome to intercept some URL patterns and use the above mock-server feature-file:

```cucumber
Feature: intercepting browser requests

Scenario:
* configure driver = { type: 'chrome' }
* driver 'https://www.seleniumeasy.com/test/dynamic-data-loading-demo.html'
* driver.intercept({ patterns: [{ urlPattern: '*randomuser.me/*' }], mock: 'mock-01.feature' })
* click('{}Get New User')
* delay(2000)
* screenshot()
```

- `driver.intercept()` is supported only for the driver type `chrome`
- you can route multiple URL patterns to the same Karate mock-feature, the format of each array-element under `patterns` can be found [here](https://chromedevtools.github.io/devtools-protocol/tot/Fetch/#type-RequestPattern).
  - the `*` wildcard (most likely what you need) will match any number of characters, e.g. `*myhost/some/path/*`
  - `?` will match any single character
  - `\` can be used as an "escape" character
- `driver.intercept()` can be called only once during a `Scenario`, which means only one mock-feature can be used - but a mock-feature can have any number of `Scenario` "routes"
- the `mock` value supports any [Karate file-reading prefix](https://github.com/intuit/karate#reading-files) such as `classpath:`
- if you need to set up HTTP mocks _before_ even loading the first page, you can use `about:blank` for the first URL used for the `driver` init - similar to how you can pre-set a [`cookie()`](#cookieset).

The entire example can be found [here](../karate-demo/src/test/java/driver/mock/demo-01.feature) - and here is a [video](https://twitter.com/KarateDSL/status/1248996522357739521). Note how the "fake" [`response.json`](../karate-demo/src/test/java/driver/mock/response.json) is tiny compared to the "real" JSON, because we know that only a few data-elements are needed for the UI to work in this case.

## Intercepting All Requests

If you use `*` as the `urlPattern` _every_ request can be routed to the mock ! And if you use the following mock, it will actually act as a ["pass-through" proxy](https://github.com/intuit/karate/tree/master/karate-netty#karateproceed) - but with the advantage that every single request and response will be emitted to `target/karate.log`. You may be able to turn this into a custom "record-replay" framework, or do other interesting things. Yes, you can modify the request or response if needed !

```cucumber
@ignore
Feature:

Scenario:
* karate.proceed()
```

And here is the [test script](../karate-demo/src/test/java/driver/mock/demo-02.feature):

```cucumber
Feature: intercepting all requests !

Scenario:
* configure driver = { type: 'chrome' }
* driver 'about:blank'
* driver.intercept({ patterns: [{ urlPattern: '*' }], mock: 'mock-02.feature' })
* driver 'https://github.com/login'
```

# Emulate Device

## `driver.emulateDevice()`

Emulating a device is supported natively only by type: `chrome`. You need to call a method on the `driver` object directly:

The example below has the width, height and userAgent for iPhone X.

```cucumber
  And driver.emulateDevice(375, 812, 'Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1')
```

# File Upload

There are multiple options, choose the one that fits you best.

## `driver.inputFile()`

File-upload is supported natively only by type: `chrome`. You need to call a method on the `driver` object directly. Here is an [example](../karate-demo/src/test/java/driver/demo/demo-05.feature) that you can try:

```cucumber
* configure driver = { type: 'chrome' }
* driver 'http://the-internet.herokuapp.com/upload'
* driver.inputFile('#file-upload', 'billie.jpg')
* submit().click('#file-submit')
* waitForText('#uploaded-files', 'billie.jpg')
```

The `driver.inputFile()` can take an array or varargs as the second argument. Note how Karate is able to resolve a [relative path](https://github.com/intuit/karate#reading-files) to an actual OS file-path behind the scenes. If you want to point to a real file, use the `file:` prefix.

## Using `multipart file`

This is the recommended, browser-agnostic approach that uses Karate's core-competency as an HTTP API client i.e. [`multipart file`](https://github.com/intuit/karate#multipart-file).

Here is how the example above looks like:

```cucumber
* url 'http://the-internet.herokuapp.com/upload'
* multipart file file = { read: 'billie.jpg', filename: 'billie.jpg', contentType: 'image/jpg' }
* method post
```

Validation can be performed if needed on the response to this HTTP `POST` which may be HTML, and the [`karate.extract()`](https://github.com/intuit/karate#karate-extract) API may come in useful.

In real-life flows, you may need to pass cookies from the [browser](#cookie) to the [Karate HTTP client](https://github.com/intuit/karate#cookie), so that you can simulate any flows needed after this step.

## Using Karate Robot

[Karate Robot](https://github.com/intuit/karate/tree/master/karate-robot) is designed for desktop application testing, but since you can click on anything in the viewport, you can achieve what you may not be able to with other automation frameworks. [Here](../karate-robot/src/test/java/robot/core/upload.feature) is the same example using this approach, where a couple of images need to be saved as part of the test-script:

```cucumber
* driver 'http://the-internet.herokuapp.com/upload'
* robot { window: '^Chrome', highlight: true }
# since we have the driver active, the "robot" namespace is needed
* robot.waitFor('choose-file.png').click().delay(1000)
* robot.input('/Users/pthomas3/Desktop' + Key.ENTER)
* robot.waitFor('file-name.png').click()
* robot.input(Key.ENTER).delay(1000)
* submit().click('#file-submit')
* waitForText('#uploaded-files', 'billie.jpg')
* screenshot()
```

A video of the above execution can be viewed [here](https://twitter.com/ptrthomas/status/1253373486384295936).

# Chrome Java API

Karate also has a Java API to automate the Chrome browser directly, designed for common needs such as converting HTML to PDF - or taking a screenshot of a page. Here is an [example](../karate-demo/src/test/java/driver/screenshot/ChromePdfRunner.java):

```java
import com.intuit.karate.FileUtils;
import com.intuit.karate.driver.chrome.Chrome;
import java.io.File;
import java.util.Collections;

public class Test {

    public static void main(String[] args) {
        Chrome chrome = Chrome.startHeadless();
        chrome.setLocation("https://github.com/login");
        byte[] bytes = chrome.pdf(Collections.EMPTY_MAP);
        FileUtils.writeToFile(new File("target/github.pdf"), bytes);
        bytes = chrome.screenshot();
        // this will attempt to capture the whole page, not just the visible part
        // bytes = chrome.screenshotFull();
        FileUtils.writeToFile(new File("target/github.png"), bytes);
        chrome.quit();
    }

}
```

Note that in addition to `driver.screenshot()` there is a `driver.screenshotFull()` API that will attempt to capture the whole "scrollable" page area, not just the part currently visible in the viewport.

The parameters that you can optionally customize via the `Map` argument to the `pdf()` method are documented here: [`Page.printToPDF `](https://chromedevtools.github.io/devtools-protocol/tot/Page/#method-printToPDF).

If Chrome is not installed in the default location, you can pass a String argument like this:

```java
Chrome.startHeadless(executable)
// or
Chrome.start(executable)
```

For more control or custom options, the `start()` method takes a `Map<String, Object>` argument where the following keys (all optional) are supported:

- `executable` - (String) path to the Chrome executable or batch file that starts Chrome
- `headless` - (Boolean) if headless
- `maxPayloadSize` - (Integer) defaults to 4194304 (bytes, around 4 MB), but you can override it if you deal with very large output / binary payloads

## `driver.screenshotFull()`

Only supported for driver type [`chrome`](#driver-types). See [Chrome Java API](#chrome-java-api). This will snapshot the entire page, not just what is visible in the viewport.

# Proxy

For driver type [`chrome`](#driver-types), you can use the `addOption` key to pass command-line options that [Chrome supports](https://www.linuxbabe.com/desktop-linux/configure-proxy-chromium-google-chrome-command-line):

```cucumber
* configure driver = { type: 'chrome', addOptions: [ '--proxy-server="https://somehost:5000"' ] }
```

For the WebDriver based [driver types](#driver-types) like `chromedriver`, `geckodriver` etc, you can use the [`webDriverSession`](#webdriversession) configuration as per the [W3C WebDriver spec](https://w3c.github.io/webdriver/#proxy):

```cucumber
* def session = { capabilities: { browserName: 'chrome', proxy: { proxyType: 'manual', httpProxy: 'somehost:5000' } } }
* configure driver = { type: 'chromedriver', webDriverSession: '#(session)' }
```

