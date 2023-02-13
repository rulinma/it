# NodeJS

## 学习指南

### 私服

#### verdaccio私服

* [verdaccio](https://verdaccio.org/zh-cn)
  * 一个基于 Node.js 的轻量级私有仓库
  * [github verdaccio](https://github.com/verdaccio/verdaccio)

#### 使用verdaccio

* docker pull verdaccio/verdaccio:nightly-master
* docker run -it --rm --name verdaccio -p 4873:4873 verdaccio/verdaccio
  * <http://localhost:4873>
  * npm adduser --registry http://localhost:4873/
  * npm publish --registry http://localhost:4873/
  * docker exec -it --user root 1e0e7b768557 sh
* npm set registry http://localhost:4873/
  * npm set registry https://registry.npm.taobao.org/
  * npm set registry https://registry.npmjs.org/

#### 应用示例

* cal库
  * package.json

    ``` json
    {
        "name": "cal",
        "version": "1.0.0",
        "description": "rulinma calculate",
        "main": "index.js",
        "scripts": {
            "test": "echo \"Error: no test specified\" && exit 1"
        },
        "keywords": [
            "calculate"
        ],
        "author": "rulinma@qq.com",
        "license": "ISC"
    }
    ```

  * index.js

    ``` javascript
    function foo() {
    console.log('Hello world!');
    }

    const add = (num1, num2) => num1 + num2;

    exports.foo = foo;
    exports.add = add;

    ```

* npm login
* npm publish --registry http://localhost:4873/
  * [http://localhost:4873](http://localhost:4873)可以看到新上传的cal库

* 调用库
  * yarn add cal
  * package.json

    ``` json
    {
        "name": "cali",
        "version": "1.0.0",
        "description": "",
        "main": "index.js",
        "scripts": {
            "test": "echo \"Error: no test specified\" && exit 1"
        },
        "type": "module",
        "keywords": [],
        "author": "",
        "license": "ISC",
        "dependencies": {
            "cal": "^1.0.0"
        }
    }
    ```

  * index.js

    ``` javascript
    import { add, foo } from 'cal'

    let sum = add(1, 2);

    console.log("sum", sum)
    console.log(foo)
    foo()
    console.log(add(11, 22))

    ```

  * 调用

      ``` shell
      > node index.js
      x 3
      [Function: foo]
      Hello world!
      33
      ```

### 推荐资料

* [图书][深入浅出Node.js](http://product.dangdang.com/23371791.html)
