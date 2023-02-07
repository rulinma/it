# Session

## 什么是Session？

Session代表服务器和客户端一次会话的过程。

维基百科这样解释道：在计算机科学领域来说，尤其是在网络领域，会话（session）是一种持久网络协议，在用户（或用户代理）端和服务器端之间创建关联，从而起到交换数据包的作用机制，session在网络协议（例如telnet或FTP）中是非常重要的部分。

对照Cookie，Session是一种在服务器端保存数据的机制，用来跟踪用户状态的数据结构，可以保存在文件、数据库或者集群中。

当在应用程序的Web页之间跳转时，存储在Session对象中的变量将不会丢失，而会在整个用户会话中一直存在下去。当客户端关闭会话，或者Session超时失效时会话结束。

目前大多数的应用都是用Cookie实现Session跟踪的。第一次创建Session时，服务端会通过在HTTP协议中返回给客户端，在Cookie中记录SessionID，后续请求时传递SessionID给服务，以便后续每次请求时都可分辨你是谁。

### Cookie与Session的区别

* 作用范围不同，Cookie 保存在客户端（浏览器），Session保存在服务器端。
* 有效期不同，Cookie可设置为长时间保持，比如默认登录功能功能，Session一般有效时间较短，客户端关闭或者Session超时都会失效。
* 隐私策略不同，Cookie存储在客户端，信息容易被窃取；Session存储在服务端，相对安全一些。
* 存储大小不同，单个Cookie保存的数据不能超过4K，Session可存储数据远高于Cookie。

### 经验总结

* session目前使用的应该很少了，以前单机还能用用，现在分布式系统了，基本使用token代替。

## 参考文献

1. [网络面经：你真的了解Cookie和Session吗？](https://www.51cto.com/article/679219.html)
2. [COOKIE和SESSION有什么区别？](https://www.zhihu.com/question/19786827)
