# ES6

### 箭头函数

- <u>ES6中的箭头函数</u>

```js
const sum = (num1,num2) => {
     return num1 + num2
}
```

- 一个参数

```js
const power = num => {
     return num * num
}
```

- 只有一行代码

```js
const sum = (num1,num2) => num1 + num2

//等同于
const sum = (num1,num2) => {
     return num1 * num2
}
```

- 实例：计时器

```js
//原版
setTimeout(function(){
})

//箭头函数版
setTimeout(() => {
})
```

- 箭头函数中的this

```js
const obj = {
    aaa() {
         //普通函数
        setTimeout(function(){
            setTimeout(function(){
                console.log(this);//window
            });
            setInterval(() => {
                console.log(this);//window
            });
        })
         //箭头函数
        setInterval(() => {
            setTimeout(function(){
                console.log(this);//window
            });
            setInterval(() => {
                console.log(this);//obj
            });
        })
    }
}
```
