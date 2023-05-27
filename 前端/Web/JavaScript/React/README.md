<!--
 * @Author: rulinma rulinma@gmail.com
 * @Date: 2023-02-17 10:52:49
 * @LastEditors: rulinma rulinma@gmail.com
 * @LastEditTime: 2023-03-07 17:42:30
 * @Description: 程序员学习和实战指南 https://github.com/rulinma/it 获取更多内容
 * @copyright: 马如林保留所有版权
-->
# React

[React](https://reactjs.org) is a JavaScript library for building user interfaces.

## 学习指南

* [网站][官方](https://react.dev/learn)
* [网站][Build your own React](https://pomb.us/build-your-own-react)
* [网站][A DIY guide to build your own React](https://github.com/pomber/didact)

### React学习路线图

<img src="https://github.com/adam-golab/react-developer-roadmap/raw/master/roadmap-cn.png" alt="React学习路线图"/>

### 推荐资料

* [网站][Ant Design of React](https://ant.design/docs/react/introduce)
* [网站][create-react-app](https://github.com/facebook/create-react-app)
* [网站][react-developer-roadmap](https://github.com/adam-golab/react-developer-roadmap)
* [网站][A DIY guide to build your own React](https://github.com/pomber/didact)
* [网站][实现一个 mini 版本的 react](https://blog.ywhoo.cn/docs/framework/react-mini)
* [网站][build-your-own-react](https://pomb.us/build-your-own-react)

* [网站][UmiJS](https://umijs.org)
* [网站][reactjs-interview-questions](https://github.com/sudheerj/reactjs-interview-questions)

* [视频][React入门应该是这样的！！！](https://www.bilibili.com/video/BV1be411w7iF)

### 学习步骤

## 知识点

* React 开发环境，渲染两次的问题
  * [Concurrent mode renders components twice with different identities #17786](https://github.com/facebook/react/issues/17786)
  * [[译]我的 React 组件会渲染两次，我快疯了](https://juejin.cn/post/6858508463274885134>)

* React唯一key问题
  * [列表 & Key](https://zh-hans.reactjs.org/docs/lists-and-keys.html)
  * 参考示例：

  ```javascript
    {
        records &&
        records.map((item: any, index: any) =>
          <li key={index} className="record_detail">
            {renderDetail(item, index)}
          </li>
        )
    }
  ```

* useEffect
  * [React useEffect Hooks](https://www.w3schools.com/react/react_useeffect.asp)

  ```javascript
    useEffect(() => {
      //Runs on every render
    });
  ```

  ```javascript
    useEffect(() => {
      //Runs only on the first render
    }, []);
  ```

  ```javascript
    useEffect(() => {
      //Runs on the first render
      //And any time any dependency value changes
    }, [prop, state]);
  ```

## 功能实战

### 用户权限

* [五星]使用context hooks实现用户认证和访问控制
  * [Authentication with React.js](https://dev.to/ksushiva/authentication-with-react-js-9e4)

## [React和VUE对比](../README.md#react和vue对比)

## 参考文献

1. [redux全局状态管理学习路线之一 : redux&react-redux](https://www.bilibili.com/video/BV1oE411V7RW)
2. [webpack-dev-server简单参数配置](https://juejin.cn/post/6844903913301213191)
3. [webpack](https://webpack.docschina.org)
4. [解决react router路由不生效，首页正常，其他路由均报错：'Cannot GET / ' 问题](https://juejin.cn/post/7129774279427620900)
5. [AntD 组件总览](https://ant.design/components/overview-cn/)
6. [react-router-dom使用指南（最新V6.0.1）](https://zhuanlan.zhihu.com/p/431389907)
7. [how could I fix this mistake of routes in react](https://stackoverflow.com/questions/70267490/how-could-i-fix-this-mistake-of-routes-in-react)
8. [react+antd从头搭建管理后台](https://www.bilibili.com/video/BV197411K737)
9. [react-redux-with-hooks-demo](https://codesandbox.io/s/react-redux-with-hooks-demo-8ixl0h)
10. [redux-thunk](https://github.com/reduxjs/redux-thunk)
11. [推荐][如何从零开始创建React项目（三种方式）](https://juejin.cn/post/6844903953524588552)
12. [CSS 架构之 BEM](https://www.jianshu.com/p/b3472742ec92)
13. [BEM](https://getbem.com/)
