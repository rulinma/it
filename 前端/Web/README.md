# Web

## 学习路线图

1. HTML
2. CSS
3. JavaScript
4. NodeJS
5. React或Vue
6. 实战

## Web开发工具

* [工具][Visual Studio Code](https://code.visualstudio.com)
* [工具][CodeSandbox](https://codesandbox.io)
* [工具][CodePen](https://codepen.io)

## 前端优化指南

### AI记单词的优化记录

* Nginx添加gzip压缩
  * [配置参考](../../DevOps/运维/负载均衡/Nginx/README.md)
* 使用Lighthouse排查问题
  * 优化建议
    * 减少未使用的 JavaScript
    * 缩减 JavaScript
    * 移除阻塞渲染的资源
  * 查看Lighhouse TreeMap
    * Q1
  * depcheck检查是否可以去除不必要的依赖
* 使用性能排查问题
* 服务器端优化
  * 使用缓存替换数据库查询

### 推荐资料

* [经典][Best Practices for Speeding Up Your Web Site](https://developer.yahoo.com/performance/rules.html)
  * [雅虎前端优化35条规则翻译](https://github.com/creeperyang/blog/issues/1)

* 前端页面耗时可以参考的时间
  * 0.1秒 : 0.1 秒是用户感知的最小粒度，在这个时间范围内完成的操作被认为是流畅没有延迟的
  * 1.0秒: 1.0 秒内完成的响应认为不会干扰用户的思维流。尽管用户能感觉到延迟，但 0.1 秒 -1.0 秒内完成的操作并不需要给出明显 loading 提示
  * 10秒 : 达到 10 秒用户将无法保持注意力，很可能选择离开做其他事情

* [推荐][2022 前端性能优化最佳实践](https://segmentfault.com/a/1190000041753539)
* [推荐][前端性能优化 24 条建议（2020）](https://segmentfault.com/a/1190000022205291)
* [带你入门前端工程（八）：性能优化](https://www.freecodecamp.org/chinese/news/front-end-engineering-performance-optimization)
* [写给中高级前端关于性能优化的9大策略和6大指标 | 网易四年实践](https://juejin.cn/post/6981673766178783262)
* [推荐][聊一聊前端性能优化](https://juejin.cn/post/6911472693405548557)
* [前端优化的技术点浅析](https://developer.aliyun.com/article/8818)
* [被删的前端游乐场](https://godbasin.github.io/front-end-playground/front-end-basic)
