# 脚本

> 后端为`JVM`上的实现, `JavaScript`, `Lua`, `Groovy` 等脚本语言都比较容易集成. 鉴于 `JavaScript` 使用者众多, 且可直接在浏览器中调试运行, 将把 `JavaScript` 作为默认的脚本执行引擎.

## 使用情景

- 用例字段生成
> `${` 和 `}` 包裹, 结果必须是一个字符串 ${Math.random().toString();} 

- 断言中
> $ 为脚本中的当前变量, 脚本结果为 `true` 或 `false`, { "$script" : "$ === 'a'" }, "{ "$script" : "devDatabaseCheck($)" }"
