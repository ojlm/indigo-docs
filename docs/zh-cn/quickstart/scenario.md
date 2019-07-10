# 创建一个场景

> 这个场景的作用是: 
1. 请求 `https://api.github.com/repos/rust-lang/rust` 获得响应体里面的 `name` 字段值 
2. 百度检索 `1` 中值.

![](./gif/scenario.gif)

## 1. 进入创建场景的界面

> ![](./images/create-a-scenario-start.png)

## 2. 添加步骤

### 步骤1: 访问 github 接口

> ![](./images/create-a-scenario-step-01-res.png)
> 想使用这个 `name` 的值进行百度检索.

> ![](./images/create-a-scenario-step-01-export.png)
> 把 `name` 值导出到, `场景` 上下文作用域, 变量名仍为 `name`.

### 步骤2: 百度上步的 `name` 值 `rust`

> ![](./images/create-a-scenario-step-02-export.png)
> 这是第二个请求步骤。 `{{$._s.name}}`，用`{{` 和 `}}`指示要用[上下文](/zh-cn/context)中的数据进行渲染或执行脚本。`$._s.name` 指引用上下文中 `场景作用域(s)` 中的 `name` 变量值.

## 3. 测试&新建

> 点击 `测试` 按钮，就可以看到以下步骤二请求中被渲染的值。

> ![](./images/create-a-scenario-test.png)
> ![](./images/create-a-scenario-result.png)
