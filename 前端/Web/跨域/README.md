# 跨域

## 基础知识

* [Fetch](https://fetch.spec.whatwg.org/#http-cors-protocol)
* [Access-Control-Allow-Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers)

## 前端开发

* [devServer.proxy
](https://webpack.js.org/configuration/dev-server/#devserverproxy)

## 后端开发

### Nginx配置

Nginx在代理层统一处理。

### 程序配置

可以代码层编码实现功能，注意：一般调试时候使用，产线走Nginx配置比较合理些，有时候本地调试不想开Nginx，可以使用代码实现一下，方便调试。

## 参考文献

1. [跨域资源共享 CORS 详解](http://www.ruanyifeng.com/blog/2016/04/cors.html)
