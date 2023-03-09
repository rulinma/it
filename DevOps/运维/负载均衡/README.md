# 负载均衡

* location匹配
  * location [ = | ~ | ~* | ^~ ] uri { ... }

    ``` text
    =  进行普通字符精确匹配，也就是完全匹配
    ~ 大小写敏感匹配
    ~*  大小写不敏感匹配
    ^~ 使用前缀匹配
    ```

## 参考文献

1. [Full Example Configuration](https://www.nginx.com/resources/wiki/start/topics/examples/full/)
2. [Beginner’s Guide](http://nginx.org/en/docs/beginners_guide.html)
3. [location](http://nginx.org/en/docs/http/ngx_http_core_module.html#location)
4. [nginx 详解 - 详细配置说明](https://juejin.cn/post/6844903727011201037)