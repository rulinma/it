# React

[React](https://reactjs.org) is a JavaScript library for building user interfaces.

## 学习指南

* [网站][Build your own React](https://pomb.us/build-your-own-react)
* [网站][A DIY guide to build your own React](https://github.com/pomber/didact)

### React学习路线图

<img src="https://github.com/adam-golab/react-developer-roadmap/raw/master/roadmap-cn.png" alt="React学习路线图"/>

### 核心资料

* [网站][Ant Design of React](https://ant.design/docs/react/introduce)
* [网站][create-react-app](https://github.com/facebook/create-react-app)
* [网站][react-developer-roadmap](https://github.com/adam-golab/react-developer-roadmap)
* [网站][A DIY guide to build your own React](https://github.com/pomber/didact)
* [网站][实现一个 mini 版本的 react](https://blog.ywhoo.cn/docs/framework/react-mini)
* [网站][build-your-own-react](https://pomb.us/build-your-own-react)

### 普通资料

* [网站][UmiJS](https://umijs.org)
* [网站][reactjs-interview-questions](https://github.com/sudheerj/reactjs-interview-questions)

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

## 参考文献
