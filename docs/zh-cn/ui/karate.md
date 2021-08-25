# Karate UI

![](./images/driver-hello-world.jpeg)

> 本地执行兼容所有的原生karate指令, 这个文档主要是部分常用指令的中文翻译。
> 
> 翻译自[karate-core](https://github.com/intuit/karate/blob/3a9d5148c3e0ae167736174527040abb8d7fc536/karate-core/README.md)
> 

## 输出&调试

```
* print 'the value of a is:', a
* print html('body')
* def myJson = { foo: 'bar', baz: [1, 2, 3] }
* print 'the value of myJson is:', myJson
```

## 浏览器相关

### driver.url

获取当前浏览器url

```
* match driver.url == webUrlBase + '/page-02'
```

### driver.dimensions

获取浏览器窗口位置和大小

```
* driver.dimensions = { x: 0, y: 0, width: 300, height: 800 }
```

```
* def dims = driver.dimensions
```

返回json object ```{ x: '#number', y: '#number', width: '#number', height: '#number' }```

## CSS/XPath 选择器

支持标准的 [`CSS`](https://www.runoob.com/cssref/css-selectors.html) 和 [`XPath`](https://www.runoob.com/xpath/xpath-syntax.html) 选择器

```
* input('input[name=someName]', 'test input')
* click("//input[@name='commit']")
```

## 通配符(文本)选择器

通过元素的`text content`选择. 表达式以 `{}` 和 `{^}` 为前缀。这种好处选择器的好处是不用理解CSS的`class names`和XPath的文档结构

```html
<a>点击</a>
<div>请点击我</div>
```

| 示例| 说明 |
|---|----|
|click('{}点击')	    | 文本是`点击`的第一个元素(任意标签) |
|click('{a}点击')     | 第一个`a` 元素且文本是`点击` |
|click('{^}点击')     | 文本包含`点击`的第一个元素|
|click('{^span}点击') | 第一个`span`元素且文本包含`点击`|
|click('{div:2}点击') | 第二个`div`且文本是`点击`|
|click('{span/a}点击')| 第一个`a`且父元素是个`span`且文本是`点击`|
|click('{^*:4}点击')  | 第四个元素(任意标签)且文本包含`点击`|


## 截图

### screenshot

可以对整个窗口或特定元素截图

```
* screenshot()
* screenshot('#id')
```

## 元素操作:点击,输入,高亮等

### click

在指定元素上触发一个点击事件, 注意这个点击就是 DOM 元素的 `click()`, 如果这个元素不支持 `click` 就无效可能报错. 另一种模拟点击的是使用 `mouse()`

```
* click('input[name=someName]')
```

### mouse
```
* mouse().move(100, 200).go()
* mouse().move('#eg02RightDivId').click()
# 拖拽
* mouse().down().move('#eg02LeftDivId').up()
* mouse('#menuItem32').click()
* mouse(100, 200).go()
* waitUntilEnabled('#someBtn').mouse().click()
```

### focus
```
* focus('.myClass')
```

### clear
```
* clear('#myInput')
```

### scroll
窗口滚动到指定元素
```
* scroll('#myInput')
```

### highlight
高亮指定元素, 主要用于调试
```
* highlight('#eg01DivId')
* highlightAll('input')
```

## 获取元素属性

### html

返回元素的 [outerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/outerHTML)

```
* html('#eg01DivId')
```

### text

返回 [textContent](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)

```
* text('.myClass')
```

### value
```
* value('.myClass')
```

### attribute

通过[属性名](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute)获取属性值

```
* attribute('#eg01SubmitId', 'type')
```

### exists

返回 `true` 或 `false`

```
* var buttonExists = exists('#myButton')
* var labelExists = exists('#myLabel')
* if (buttonExists && !labelExists) karate.fail('button exists but label does not')
```

## 等待/执行JS

### waitFor
等待某个元素渲染完成

```
* waitFor('#eg01WaitId').click()
```

### waitForUrl
等待url跳转
```
* waitForUrl('/some/path')
* def actualUrl = waitForUrl('/some/path')
```

### delay
等待N`毫秒`
```
* delay(1000)
```

### script
在浏览器端执行JS(会直接当做字符串传给浏览器执行,注意转义字符)
```
* script("1 + 2")
* script("console.log('hello world')")
* script('#eg01WaitId', "function(e){ return e.innerHTML }")

```

## 操作Cookie

### 通过 `name` 获取cookie

```
* def cookie1 = { name: 'foo', value: 'bar' }
* match cookie('foo') contains cookie1
```

### 设置 cookie

跳转url前设置cookie

```
* driver 'about:blank'
* def myCookie = { name: 'hello', value: 'world', domain: '.mycompany.com' }
* cookie(myCookie)
* match driver.cookies contains '#(^myCookie)'
```

### 删除 cookie

```
* deleteCookie('foo')
```

## 断言

### assert

判断后面的表达式是不是 `true`. 更强大的的断言方式使用 `match`

```
* def color = 'red '
* def num = 5
* assert color + num == 'red 5'
```

```
* assert 3 == script("1 + 2")
```


### match

#### 基本匹配(等于、不等)

```
* match html('#eg01DivId') == '<div id="eg01DivId">this div is outside the iframe</div>'
* match text('.myClass') == 'Class Locator Test'
* match value('.myClass') == 'some value'
* match attribute('#eg01SubmitId', 'type') == 'submit'
* match script('#eg01WaitId', "function(e){ return e.innerHTML }") == 'APPEARED!'
* match script('#eg01WaitId', '_.innerHTML') == 'APPEARED!'
```

```
* def test = { foo: 'bar' }
* match test != { foo: 'baz' }
```

#### 文本匹配

等价 `assert`
```
* match hello == 'Hello World!'
* assert hello == 'Hello World!'
```

是否包含
```
* def hello = 'Hello World!'
* match hello contains 'World'
* match hello !contains 'blah'
```

