# Http

### http协议的特点

## HTTP 1.1
### http1.1改进点
1. 持久化连接

通过Connection:keep-alive 进行长连接，保证TCP链路能够被复用，避免重新建立链接，节省资源。
2. 管道机制

基于持久化链接，同一个TCP链接可以支持多Http请求的发送。
3. 对头阻塞

## HTTP 2.0

### http2有什么改进？

1. HTTP2使用的是二进制传送，HTTP1.X是文本（字符串）传送。

2. 支持多路复用

3. HTTP2头部压缩

4. 支持服务器推送

### websocket协议和 HTTP2 有关系么？
### http2 和 1.1 的 pipeline 有啥区别？
### HTTP2 和 1.1 的 keep alive 啥区别？