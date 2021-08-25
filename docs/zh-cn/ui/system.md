# 操作系统 api

> 注意: 这部分 api 是操作系统原生 api, 浏览器内部场景无法使用。操作软件菜单, 系统鼠标事件等

## 获得屏幕和进程窗口信息

```scala
def screenInfo(): util.List[util.Map[String, Object]]
def windowInfo(title: String): util.List[util.Map[String, Object]]
```

## 激活窗口

激活后后续的操作都是相对于激活窗口的

```scala
def activate(pid: Long): System
def activate(pid: Long, idx: Int): System
def activate(title: String): System
def activate(title: String, idx: Int): System
def inactivate(): System
```

## 截图-系统屏幕

```scala
def screenshot(): Array[Byte]
def screenshot(x: Int, y: Int, width: Int, height: Int): Array[Byte]
```

## 屏幕裁剪

```scala
def crop(): ImageElement
def crop(locator: Object): ImageElement
def crop(x: Object, y: Object): ImageElement
def crop(x: Object, y: Object, width: Object, height: Object): ImageElement
```

## 鼠标事件

```scala
def move(x: Int, y: Int): System // 移动到屏幕坐标位置
def click(): System  // 鼠标左键
def midClick(): System // 中间
def rightClick(): System // 右键
def doubleClick(): System // 双击左键
def click(x: Int, y: Int): System // 移动鼠标并左键
def press(): System // 左键按下
def release(): System // 左键释放
def input(value: String): System // 键盘输入
def delay(millis: Int): System
def highlight(x: Int, y: Int, width: Int, height: Int): System // 高亮屏幕区域
```

## 示例

````
* print sys.screenInfo()
* sys.screenshot()
* print sys.windowInfo('idea')
* sys.activate('idea', 0)
* sys.screenshot()
* sys.move(400, 500).rightClick()
* sys.move(500, 500).click()
* sys.crop(200, 200).highlight().screenshot()
* sys.crop(0.5).highlight().screenshot()
* print sys.crop(0.5).ocrExtract()
````

```
* sys.crop().detect()
* sys.crop().detect('gftt', {minDistance:3, useHarris:false})
* sys.crop().detect('mser', {'minArea':100,'maxArea':800})
* sys.crop().detect('harris')
* sys.crop().detect('fast', {threshold:10})
* sys.crop().detect('surf', {hessianThreshold:250,extended:true})
* sys.crop().detect('sift', {nFeatures:0,nOctaveLayers:3})
* sys.crop().detect('morph', {shape:'ellipse',width:16,height:4})
```

```
# 屏幕 (50,20) 宽高 (100,200) 的区域找到`关于`菜单, 点击
* sys.crop(50,20,100,200).find('关于').click()
```
