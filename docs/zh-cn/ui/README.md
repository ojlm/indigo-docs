# Indigo UI

这一部分是在 [Karate UI](https://github.com/intuit/karate/tree/master/karate-core) 的基础上做了修改和扩展.

扩展特性包括:

- 支持同时操作多个`driver`, 且自由切换(适用于多人协作, 多人会议, 基于Electron的应用多Webview切换这些场景)
- 新增了一组 [操作系统原生操作指令](/zh-cn/ui/system)
- 新实现的内置 [android driver](/zh-cn/ui/android)
- 服务化: 后台运行, 控制多个浏览器或设备, 推送数据, 提高响应速度. 可以直接作为agent 跟浏览器打包容器部署. 本身也是个代理服务器.
- 集成 ffmpeg, opencv, tesseract, 提供图像识别和OCR的基础指令
- 内置一个 [scrcpy](https://github.com/Genymobile/scrcpy) 的 java/scala 实现, 及以此为基础的...
- Web IDE...
