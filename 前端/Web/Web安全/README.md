# Web安全

## 学习指南

### base64

* Base64编码解码
  * <https://tool.chinaz.com/Tools/Base64.aspx>

* Javascript一般自带该基础功能，在Chrome下打开控制台可以测试

    ```javascript
    > btoa("123456")
    'MTIzNDU2'
    > atob("MTIzNDU2")
    '123456'
    ```

    特殊字符示例：

    ```javascript
    > btoa(unescape(encodeURIComponent("编码测试")))
    > '57yW56CB5rWL6K+V'
    > decodeURIComponent(escape(atob('57yW56CB5rWL6K+V')))
    > '编码测试'

    > btoa(encodeURIComponent("编码测试"))
    > 'JUU3JUJDJTk2JUU3JUEwJTgxJUU2JUI1JThCJUU4JUFGJTk1'
    > decodeURIComponent(atob('JUU3JUJDJTk2JUU3JUEwJTgxJUU2JUI1JThCJUU4JUFGJTk1'))
    > '编码测试'
    ```

### urlencode urldecode

* UrlEncode编码解码
  * <http://tool.chinaz.com/Tools/urlencode.aspx>

  ```javascript
  > encodeURIComponent("test?")
  'test%3F'
  > decodeURIComponent('test%3F')
  'test?'
  ```

### Base64和URL Encode整合使用

一般前端使用javascript，后端java的代码如下：

```javascript
  // 对content进行Base64，然后再url encode
  encodeURIComponent(btoa(content))
```

```java
  // 对content进行url decode，再解析Base64
  String decodeContent = URLDecoder.decode(content, "utf-8");
  String content = Base64.getDecoder().decode(decodeContent)
```

### 签名算法

#### hmac-sha1

### 加密算法

### 应用实例

```javascript
Signature = urlencode(base64(hmac-sha1(AccessKeySecret,
          VERB + "\n"
          + CONTENT-MD5 + "\n"
          + CONTENT-TYPE + "\n"
          + EXPIRES + "\n"
          + CanonicalizedOSSHeaders
          + CanonicalizedResource)))
```

### 推荐阅读

* [为啥要 base64 编码？](https://www.jianshu.com/p/b611e220ef2d)
* [URL原理、URL编码、URL特殊字符](https://developer.aliyun.com/article/75516)

## 参考文献

1. [前端安全系列（一）：如何防止XSS攻击？](https://tech.meituan.com/2018/09/27/fe-security.html)
2. [https://juejin.cn/post/6912030758404259854](https://juejin.cn/post/6912030758404259854)
