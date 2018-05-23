# 场景

> `N`个`HTTP`接口 顺序执行，第`M`（M+1<=N）个接口在第`M+1`个接口之前触发，且第`M`个接口的返回,是第`M+1`个接口请求的某些字段的组成.

场景的实现基于用例执行上下文, 参考[CaseContext](./context.md)

## 例子

1. 假设场景中的序号1接口返回
```json
{
    "entity" : {
        "code" : 1,
        "msg" : "ok",
        "data" : {
            "userInfo" : {
                "usernmae" : "mr.coco",
                "token" : "123"
            }
        }
    }
}
```
2. 场景中的序号2接口case部分

### 序号2的用例执行时所看到的上下文为
>```json
>{
>    "_global" : {...},
>    "_g" : {...},
>    "_job" : {...},
>    "_scenario" : {...},
>    "_s" : {...},
>    "_cases" : [{ 
>        "entity" : {
>            "code" : 1,
>            "msg" : "ok",
>            "data" : {
>                "userInfo" : {
>                    "usernmae" : "mr.coco",
>                    "token" : "123"
>                }
>            }
>        }
>    }],
>    "_prev" : { 
>        "entity" : {
>            "code" : 1,
>            "msg" : "ok",
>            "data" : {
>                "userInfo" : {
>                    "usernmae" : "mr.coco",
>                    "token" : "123"
>                }
>            }
>        }
>    },
>    "_p" : {
>       "entity" : {
>            "code" : 1,
>            "msg" : "ok",
>            "data" : {
>                "userInfo" : {
>                    "usernmae" : "mr.coco",
>                    "token" : "123"
>                }
>            }
>        }
>     },
>    "status" : {...},
>    "headers" : {...},
>    "entity" : {...}
>}
>```

### 序号2的用例声明示例
```json
{
    "cookie" : [{"key" : "token", "value" : "{{$._prev.entity.data.userInfo.token}}"}]
}
```
其中 `$._prev.entity.data.userInfo.token` 即可取上下文中的内容 `123`. 用 `{{` 和 `}}` 包裹起来

