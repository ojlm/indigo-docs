# 图像识别&OCR

## 裁剪区域

裁剪后返回一个 [图像元素](/zh-cn/ui/image-element)

> 函数列表

```scala
// 裁剪函数, 裁剪部分图像
def crop(): ImageElement
// 裁剪页面元素，或数字
def crop(locator: Any): ImageElement
def crop(x: Any, y: Any): ImageElement
def crop(x: Any, y: Any, width: Any, height: Any): ImageElement
```

> 可传入 1 个、2 个或 4 个数字, 整数代表像素，小数代表比率, 示例:

```
* img.corp('.divClass')
# 同 corp(0.5, 0.5) 中间区域，宽高占50%
* img.corp(0.5)
# 中间区域，宽600像素,高占400 像素
* img.corp(600, 400)
# 起点中央，400*400
* img.corp(0.5, 0.5, 400, 400)
```

## 图像点击

```scala
// 图像匹配点击
def click(file: String): Unit
def click(locator: String, file: String): Unit
def click(source: Array[Byte], target: Array[Byte]): Unit
```

> 示例
```
* img.click('#lg', 'baidu.png')
```

## 图像匹配

```scala
// 找到所有匹配到的图片元素
def `match`(file: String): util.List[ImageElement]
def `match`(locator: String, file: String): util.List[ImageElement]
```

## 相似度比较

```scala
// 图片相似度对比
def compare(file: String): Double
def compare(locator: String, file: String): Double
def compare(reference: Array[Byte], file: String): Double
def compare(reference: Array[Byte], target: Array[Byte]): Double
def diff(file: String): Double
def diff(locator: String, file: String): Double
def diff(reference: Array[Byte], target: Array[Byte]): Double
```

> 示例
```
* print img.diff('#lg', 'baidu.png')
* print img.diff('#s_lg_img', 'baidu.png')
* print img.compare('#s_lg_img', 'baidu.png')
```


## 有效区域检测

```scala
// 图像识别区域检测,调试用
def detect(): DetectorResult
def detect(method: String): DetectorResult
def detect(locator: String, method: String, options: util.Map[String, Any]): DetectorResult
def detect(bytes: Array[Byte], method: String, options: util.Map[String, Any]): DetectorResult
```

## OCR 识别

```scala
def click(text: String): Unit
def click(locator: String, text: String): Unit
def extract(): String
def extract(locator: String): String
def extract(locator: String, level: String): String
def extract(locator: String, level: String, negative: Boolean): String
```

| level  | 说明           |
| ------ | -------------- |
| block  | 区域文本       |
| para   | 区分段落       |
| line   | 区分行         |
| word   | 区分单词（默认 |
| symbol | 字符(默认)     |

> 示例

```
* ocr.click('#s-top-left', '视频')
# 识别出整个整个部分的字符
* ocr.extract()
# 第一个参数为定位表达式（提高识别准确率）,第二个是 识别的模式见下表
* ocr.extract('#img', 'word')
# 第三个参数是否对图片进行‘bitwise_not’操作, 如果输入图片是 黑底白字 设置true, 默认 false
* ocr.extract('#img', 'word', true)
```
