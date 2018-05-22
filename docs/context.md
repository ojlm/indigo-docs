# 用例上下文
> 目标是用例执行的运行时环境, 包括数据和函数. 用例生成的直接数据源. 来自上下文的渲染变量或脚本需要用 `${` 和 `}` 括起来.

## 模型定义
> 每个用例所处的运行时环境

```scala
CaseContext(
    "_global" -> Map[String, Any], // 全局变量, 系统级配置
    "_g" -> Map[String, Any], // 同上, 简写
    "_job" -> Map[String, Any], // 当前任务有效
    "_scenario" -> Map[String, Any], // 当前场景有效
    "_s" -> Map[String, Any], // 同上, 简写
    "_cases" -> Seq[CaseContext], // 场景下有效, 当前场景的用例列表
    "_prev" -> CaseContext, // 场景下有效, 当前场景中的当前用例的上一个用例
    "_p" -> CaseContext, // 同上, 简写
    "status" -> Int, // 当前用例有效, http 响应码
    "headers" -> Map[String, String], // 当前用例有效, http 响应 headers
    "entity" -> String | Map[String, Any], // 当前用例有效, http 响应体
    "custom_user_defined" -> Any // 当前用例有效, 自定义
)
```

## ContextAction
> 读或写上下文的动作, 如以下类型

### 直接编辑上下文
> 分为: 用例级别, 场景级别, 任务级别

### 调用接口写入上下文
> 应用场景: 没必要写成接口用例时, 认证依赖字段, 外部接口依赖

### 读数据库写入上下文
