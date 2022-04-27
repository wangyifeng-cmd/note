# Node.js笔记

***

### vscode没有node.js提示怎么办啊，好烦喏

- 正解 --- 安装依赖，就是帅

```bash
npm install @types/node
```

### Node与 ‘BOM’，’DOM‘两个没有关系

- js的三要素有ES，BOM，DOM，但Node与 ‘BOM’，’DOM‘两个没有关系

### cmd命令行

- 查看是否有安装node.js

  ```bash
  node -v
  ```

- 运行js文件

  ```bash
  node test.js
  ```

- 进入repl（交互式解析器，即可以在里面写js代码，没啥用）

  ```bash
  node
  ```

- 退出repl

  ```
  两次(Ctrl + C)
  ```

- 回到上一个目录

  ```bash
  cd ..
  ```

- 显示目录

  ```bash
  dir
  ```

- 清空上面的bash

  ```bash
  cls
  ```

- 删除文件

  ```bash
  del
  ```

### npm（node package message）

- 在node安装的时候已经自动安装好npm了

### js导入导出

- 导入导出

  - node1.js（导出）

    ```js
    let z = 23
    module.exports = z//导出语法 --- module.exports
    ```

  - node2.js（导入）

    ```js
    let z = require('./node1')//导入语法 --- require
    console.log(z);
    ```

- 导出文件没有传值时，导入的是一个空对象

  - node1.js（导出）

    ```js
    //空 没有导出
    ```

  - ndoe2.js（导入）

    ```js
    let age = require('./node1')
    console.log(age);//{}  默认导出值是一个对象
    ```

- 存在引用关系

  ```js
  module.exports = exports
  ```

  - 所以导入可以简写

    - node1.js（导出）

      ```js
      exports.age = "23"
      
      //相当于
      module.exports = {
           age:23
      }
      ```

    - ndoe2.js（导入）

      ```js
      let age = require('./node1')
      console.log(age);//{ age: '23' }  如果导入文件是简写，最终导入的是一个对象
      ```

  - 问题来了，当用简写exports传的是一个对象时，导入那边接收到的是这个对象吗

    - node1.js（导出）

      ```js
      exports = {
          mm: 18
      }//传一个对象
      ```

    - ndoe2.js（导入）

      ```js
      let age = require('./node1')
      console.log(age);//{} 并不是exports传的对象
      ```

    - 证明接收不到

      ```js
      //原理
      let module = {
          exports: {}
      }
      let exports = module.exports
      exports = { ff: 20 }//改变exports的值
      console.log(module.exports);//{} 证明给exports赋值对象是不会改变module.exports导出的值的
      ```

  - 还有个问题，就是module.exports和exports并存的时候，exports的值是否有影响导出

    - node1.js（导出）

      ```js
      module.exports = {
          x: 10,
          y: 20,
      }
      exports.z = 40
      ```

    - ndoe2.js（导入）

      ```js
      const data = require('./node1');
      console.log(data);//{ x: 10, y: 20 }  不影响
      ```

  - 最终问题：当重复导入同一个模块的时候出现的情况

    - node1.js（导出）

      ```js
      module.exports = {
          x: 18
      }
      ```

    - ndoe2.js（导入）

      ```js
      const age = require('./node1');
      age.name = "gg"//改变导入的对象
      console.log(age);//{ x: 18, name: 'gg' }
      
      //结论：重复引入同一个模块的时候，是不会重新去执行该模块的，而是用之前缓存
      const age2 = require('./node1');
      console.log(age2);//{ x: 18, name: 'gg' }
      ```

      
