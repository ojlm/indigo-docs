### hosts 和 Host

#### hosts

`hosts` 一般指一个系统文件. `*nix` 系统中指 `/etc/hosts`, `windows` 中指 `C:\windows\system32\drivers\etc\`. `hosts` 的工作机制可以看下 [百度百科](https://baike.baidu.com/item/hosts/10474546).

#### Host

> ![](./images/http-host.png)

一般指 `Http` 协议中的 [`Host` 头](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Host).
一般浏览器会自动把这个头加上. Nginx 服务器配置中的 [server_name](http://nginx.org/en/docs/http/server_names.html) 默认会匹配这个 头, 来转发到目标服务. 所以使用 代理时, 需要自己手动加个 `Host` 头来命中 Nginx 的配置.
