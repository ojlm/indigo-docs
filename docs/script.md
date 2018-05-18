# 脚本

> 内嵌 `JavaScript` 执行器.

## 使用情景

- 用例字段生成
> `${` 和 `}` 包裹, 结果必须是一个字符串 ${Math.random().toString();} 

- 断言中
> $ 为脚本中的当前变量, 脚本结果为 `true` 或 `false`, "$script" : "$ === 'a'"
